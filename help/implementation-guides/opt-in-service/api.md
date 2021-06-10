---
description: オプトインライブラリおよび設定用 API のリファレンスです。
title: オプトインリファレンス
exl-id: aa61aed7-695b-47e4-a922-9841e00aa09d
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '886'
ht-degree: 100%

---

# オプトインリファレンス {#opt-in-reference}

オプトインライブラリおよび設定用 API のリファレンスです。

同意の設定は、カテゴリーとしてオプトインの関数に指定します。

```
adobe.OptInCategories = { 
    "AAM": "aam", 
    "ANALYTICS": "aa", 
    "ECID": "ecid", 
    "TARGET": "target" 
}
```

## オプトイン設定パラメーター {#section-d66018342baf401389f248bb381becbf}

このセクションでは、API を使用してオプトインを設定する方法について説明します。設定および実装の大部分は、Experience Platform Launch 拡張を使用しておこなうことができます。

オプトインの設定は、グローバルな `getInstance()` オブジェクトをインスタンス化する、Visitor JavaScript `adobe` 関数で指定されます。以下に、オプトインサービスに関連した Visitor JS 設定を示します。

**`doesOptInApply (boolean or function that evaluates to a boolean)`**：

false の場合は、訪問者がオプトインする必要がないことを示します。 結果として、オプトインまたはオプトアウトの対象となるカテゴリーに関わらず、Experience Cloud では Cookie が作成されます。この設定は、オプトインを全体的に有効または無効にします。

**`preOptInApprovals (Object <adobe.OptInCategories enum: boolean>)`**

訪問者が環境を設定していない場合に承認または拒否するカテゴリーを定義します。これは、組織の初期設定と呼ばれます。

**`previousPermissions (Object<adobe.OptInCategories enum: boolean>)`**

訪問者が明示的に指定した環境設定。この設定で指定した権限により、組織の初期設定が上書きされます（`previousPermissions` は `preOptInApprovals` を上書きします）。

**`isOptInStorageEnabled (boolean)`**

オプトインを有効にして（現在のお客様のドメイン内にある）ファーストパーティ Cookie に権限を保存します

 （オプション）**`optInCookiesDomain (string)`**

オプトイン Cookie に使用するファーストパーティドメインまたはサブドメイン（`isOptInStorageEnabled` が true の場合）

 （オプション）**`optInStorageExpiry (integer)`**

13 か月のデフォルト有効期間を上書きする秒数

## 同意パラメーターの変更 {#section-c3d85403ff0d4394bd775c39f3d001fc}

訪問者は、サイトでのエクスペリエンス中はいつでも、初めて環境設定を行ったり、CMP を使用して環境設定を変更したりできます。 初期設定で訪問者 JS を初期化したら、次の関数を使用して訪問者の権限を変更できます。

**`adobe.optIn.approve(categories, shouldWaitForComplete)`**

リスト内のすべてのカテゴリーに対して訪問者を承認、つまりオプトインする関数。shouldWaitForComplete パラメーターについて詳しくは、[オプトインワークフロー](../../implementation-guides/opt-in-service/getting-started.md#section-70cd243dec834c8ea096488640ae20a5)を参照してください。

**`adobe.optIn.deny(categories, shouldWaitForComplete)`**

指定したすべてのカテゴリーに対して訪問者を拒否、つまりオプトアウトする関数。

**`adobe.optIn.approveAll()`**：

サイトで Cookie を作成するための権限を訪問者が一括で許可または拒否するように、サイトで作成する権限に関するリクエストをフレーズ化する場合は、応答に応じて `approveAll()` または `denyAll()` を使用します。

**`adobe.optIn.denyAll()`**：

サイトで Cookie を作成するための権限を訪問者が一括で許可または拒否するように、サイトで作成する権限に関するリクエストをフレーズ化する場合は、応答に応じて `approveAll()` または `denyAll()` を使用します。

## オプトインワークフローのパラメーター {#section-2c5adfa5459c4e72b96d2693123a53c2}

オプトインでは、環境設定を 1 つずつ指定するような、複数回のリクエストサイクルで権限を収集できるワークフローがサポートされています。以下の関数を使用して *設定に* true`shouldWaitForComplete` を指定すると、ソリューションでは、1 つのソリューションまたは全カテゴリーのサブセットに対する同意を収集してから、次のソリューションまたは全カテゴリーの別のサブセットに対する同意を収集することができます。最初の呼び出しから、フローの最後に `adobe.optIn.status` が呼び出されるまで、`adobe.optIn.complete()` プロパティは pending になります。この呼び出し後、ステータスは *Complete* に設定されます。

**`adobe.optIn.approve(categories, shouldWaitForComplete)`**

リスト内のすべてのカテゴリーに対して訪問者を承認、つまりオプトインする関数。

`adobe.optIn.deny(categories, shouldWaitForComplete)`

指定したすべてのカテゴリーに対して訪問者を拒否、つまりオプトアウトする関数。

`adobe.optIn.complete()`

訪問者の環境設定リクエストに対して続行する approve() および deny() の呼び出しの集計をトリガーする関数。オプトインの変更をサブスクライブする場合（以下の `adobe.optIn.fetchPermissions(callback, shouldAutoSubscribe` を参照）、コールバックがトリガーされるのは、この関数が呼び出されたときだけです。

## 訪問者オプトイン権限のパラメーター {#section-7fe57279b5b44b4f8fe47e336df60155}

任意の時点で訪問者のオプトイン権限を収集するには、以下の権限関数のいずれかを使用します。

`adobe.optIn.permissions`

訪問者が許可または拒否した Experience Cloud のすべてのソリューションをカテゴリーとしてリストするオブジェクト。

`adobe.optIn.isApproved(categories)`

すべてのカテゴリーが承認されている場合、この関数は true を返します。

`adobe.optIn.fetchPermissions(callback, shouldAutoSubscribe)`

権限のリストを非同期で取得します。 権限の付与／拒否プロセスが完了すると、コールバックが権限のリストとともに呼び出されます。 `shouldAutoSubscribe`の値に *true* を指定すると、将来のオプトインの変更に備えてコールバックが登録されます。`adobe.OptIn` のプロパティを以下に示します。

**`permissions`**

訪問者が許可または拒否した Experience Cloud の全ソリューションをカテゴリーとしてリストするオブジェクト。例：`{ aa: true, ecid: false, aam: true... }`

**`status`**

* 保留中
* 変更済み
* complete

**`doesOptInApply`**

true または false。初期化で指定した設定を表します。

**`isPending`**

ステータス値に応じて true または false。 まだ明示的に権限を受け入れたり拒否したりしていない訪問者の場合は、このプロパティのオプトインが true と報告されます

**`isComplete`**

ステータス値に応じて true または false。 ワークフロースタイルの同意が開始されたが完了していない場合は、このプロパティのオプトインが false と報告されることがあります。

## オプトインオブジェクトのメソッド {#section-e0417801a82548d199d833010033e433}

**`approve(categories, shouldWaitForComplete)`**

**`categories`**：承認する 1 つ以上のカテゴリー。例：`adobe.optIn.approve([adobe.OptInCategories.AAM, adobe.OptInCategories.ECID])`
**`shouldWaitForComplete`**：（オプション）boolean パラメーター（デフォルトでは false）。true を渡した場合は、`adobe.optIn.complete()` を呼び出すまで承認プロセスが完了しません。このプロセスはワークフローに似ています。

```
<codeblock>
  adobe.optIn.approve(adobe.OptInCategories.ANALYTICS, 
         true); adobe.optIn.approve(adobe.OptInCategories.ECID, true); 
         adobe.optIn.complete() 
</codeblock>
```

**`deny(categories, shouldWaitForComplete)`**

* 1 つ以上のカテゴリーを渡すと、承認済みかどうかがチェックされます。
* カテゴリーを渡さない場合は、利用可能なすべてのカテゴリーがチェックされます。

**`isApproved(categories)`**

1 つ以上のカテゴリーが顧客によって承認されているかどうかをチェックします。

**`isPreApproved(categories)`**

1 つ以上のカテゴリーが顧客によって事前承認されているかどうかをチェックします。（これらのカテゴリーが `preOptInApprovals` 設定で渡された場合）。

**`fetchPermissions(callback, shouldAutoSubscribe)`**

権限のリストを取得する非同期 API。 権限の付与／拒否プロセスが完了すると、コールバックが権限のリストとともに呼び出されます。 **`shouldAutoSubscribe`:**&#x200B;ヘルパーユーティリティは、このコールバックを今後のすべてのイベントに自動的にサブスクライブさせます。 つまり、オプトインで承認または拒否がトリガーされるたびに、コールバックが呼び出されます。 このようにして、自分でイベントにサブスクライブしなくても、常に更新されます。

**例**

`fetchPermissions`

```
optIn.fetchPermissions(function (permissions) { 
    // Here you can check if your category has been approved or not. 
    // We recommend using `optIn.isApproved()` to check for permissions because it abstracts  
       out the details of knowing exactly how the `permissions` list looks like. 
 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
});

// OR: You can pass in `shouldAutoSubscribe` as true, your callback will be used to subscribe  
to all OptIn events going forward:

function callback() { 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
} 
 
optIn.fetchPermissions(callback, true);
```

**`complete()`:**

>[!NOTE]
>
>`shouldWaitForComplete` パラメーターを approve または deny に渡した場合にのみ使用してください。この API により、承認プロセスが完了します。例：`adobe.optIn.complete()`。

**`approveAll()`:**

既存のカテゴリーをすべて承認します。

**`denyAll()`**

既存のカテゴリーをすべて拒否します。

## オプトインオブジェクトのイベント {#section-06f25b33cab54bafb053183e937fb710}

**`complete`:**

承認プロセスが完了したときにイベントトリガーを完了します。`shouldWaitForComplete` を渡さずに approve または deny を呼び出すか、`approveAll` または `denyAll` を呼び出すと、このイベントがトリガーされます。また、`shouldWaitForComplete` を渡した場合は、`complete` が呼び出されるとこのイベントがトリガーされます。

**例**

```
<codeph>
  adobe.optIn.on("complete", callback); 
</codeph>
```
