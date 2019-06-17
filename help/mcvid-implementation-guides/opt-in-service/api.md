---
description: オプトインライブラリおよび設定用 API のリファレンスです。
seo-description: オプトインライブラリおよび設定用 API のリファレンスです。
seo-title: オプトインリファレンス
title: オプトインリファレンス
uuid: d5023a34-2f3e-464d- b21f-579b2f416ce6
translation-type: tm+mt
source-git-commit: 1c6dc1871ee2e7b8d1f510576836519f7383b809

---


# オプトインリファレンス{#opt-in-reference}

オプトインライブラリおよび設定用 API のリファレンスです。

同意の設定は、カテゴリとしてオプトインの関数に指定します。

```
adobe.OptInCategories = { 
    "AAM": "aam", 
    "ANALYTICS": "aa", 
    "ECID": "ecid", 
    "TARGET": "target" 
}
```

## オプトインの設定パラメーター {#section-d66018342baf401389f248bb381becbf}

このセクションでは、API を使用してオプトインを設定する方法について説明します。設定および実装の大部分は、Launch 拡張を使用しておこなうことができます。

オプトイン設定は、グローバルオブジェクトをインスタンス化する訪問者JavaScript `getInstance()` 関数で提供 `adobe` されます。オプトインサービスに関連する訪問者JS設定を以下に示します。

**`doesOptInApply (boolean or function that evaluates to a boolean)`**:

false の場合は、訪問者がオプトインをおこなう必要はありません。結果として、オプトインまたはオプトアウトの対象となるカテゴリに関わらず、Experience Cloud では Cookie が作成されます。この設定では、全体的にオプトインの有効と無効を切り替えます。

**`preOptInApprovals (Object <adobe.OptInCategories enum: boolean>)`**

訪問者が環境を設定していない場合に承認または拒否するカテゴリを定義します。これは、組織の初期設定と呼ばれます。

**`previousPermissions (Object<adobe.OptInCategories enum: boolean>)`**

訪問者が明示的に指定した環境設定。この設定で指定した権限により、組織の初期設定が上書きされます（`previousPermissions` は `preOptInApprovals` を上書きします）。

**`isOptInStorageEnabled (boolean)`**

オプトインを有効にして（現在のお客様のドメイン内にある）ファーストパーティ Cookie に権限を保存します

（オプション） **`optInCookiesDomain (string)`**

オプトイン Cookie に使用するファーストパーティドメインまたはサブドメイン（`isOptInStorageEnabled` が true の場合）

（オプション） **`optInStorageExpiry (integer)`**

デフォルトの有効期限 13 ヶ月を上書きする秒数

## 同意変更パラメーター {#section-c3d85403ff0d4394bd775c39f3d001fc}

訪問者は、サイトを訪問中にいつでも、CMP を使用して初めて環境設定を設定したり、設定した設定を変更したりできます。Visitor JS が初期設定で初期化されたら、以下の関数を使用して訪問者の権限を変更できます。

**`adobe.optIn.approve(categories, shouldWaitForComplete)`**

リスト内のすべてのカテゴリに対して訪問者を承認、つまりオプトインする関数。shouldWaitForComplete パラメーターの詳細については、[オプトインワークフロー](../../mcvid-implementation-guides/opt-in-service/getting-started.md#section-70cd243dec834c8ea096488640ae20a5)を参照してください。

**`adobe.optIn.deny(categories, shouldWaitForComplete)`**

指定したすべてのカテゴリに対して訪問者を拒否、つまりオプトアウトする関数。

**`adobe.optIn.approveAll()`**:

サイトの権限に対するリクエストが指定されている場合、訪問者ブランケットは、cookieを作成したり、 `approveAll()``denyAll()`cookieを作成したり、その応答を基にして、サイトに対するcookieの作成権限を付与または拒否します。

**`adobe.optIn.denyAll()`**:

サイトの権限に対するリクエストが指定されている場合、訪問者ブランケットは、cookieを作成したり、 `approveAll()``denyAll()`cookieを作成したり、応答を作成したりするために、サイトに対するアクセス権限を付与または拒否します。

## オプトインワークフローのパラメーター {#section-2c5adfa5459c4e72b96d2693123a53c2}

オプトインでは、環境設定を 1 つずつ指定するような、複数回のリクエストサイクルで権限を収集できるワークフローがサポートされています。以下の関数を使用して * 設定に *true`shouldWaitForComplete` を指定すると、ソリューションでは、1 つのソリューションまたは全カテゴリのサブセットに対する同意を収集してから、次のソリューションまたは全カテゴリの別のサブセットに対する同意を収集することができます。最初の呼び出しから、フローの最後に `adobe.optIn.status` 呼び出されるまで `adobe.optIn.complete()` プロパティが保留されます。この呼び出し後、ステータスは *Complete* に設定されます。

**`adobe.optIn.approve(categories, shouldWaitForComplete)`**

リスト内のすべてのカテゴリに対して訪問者を承認、つまりオプトインする関数。

`adobe.optIn.deny(categories, shouldWaitForComplete)`

指定したすべてのカテゴリに対して訪問者を拒否、つまりオプトアウトする関数。

`adobe.optIn.complete()`

訪問者の環境設定リクエストに対して続行する approve() および deny() の呼び出しの集計をトリガーする関数。オプトインの変更をサブスクライブする場合（以下の `adobe.optIn.fetchPermissions(callback, shouldAutoSubscribe`) を参照）、コールバックがトリガーされるのは、この関数が呼び出されたときだけです。

## 訪問者オプトイン権限のパラメーター {#section-7fe57279b5b44b4f8fe47e336df60155}

任意の時点で訪問者のオプトイン権限を収集するには、以下の権限関数のいずれかを使用します。

`adobe.optIn.permissions`

訪問者が許可または拒否した Experience Cloud のすべてのソリューションをカテゴリとしてリストするオブジェクト。

`adobe.optIn.isApproved(categories)`

すべてのカテゴリが承認されている場合、この関数は true を返します。

`adobe.optIn.fetchPermissions(callback, shouldAutoSubscribe)`

権限のリストを非同期で取得します。コールバックは、権限の許可または拒否プロセスが完了すると、権限のリストで呼び出されます。* の値に *true`shouldAutoSubscribe` を指定すると、将来のオプトインの変更に備えてコールバックが登録されます。`adobe.OptIn` のプロパティを以下に示します。

**`permissions`**

訪問者の例によって許可または拒否されたすべてのExperience Cloudソリューションをカテゴリとして一覧表示するオブジェクト。 `{ aa: true, ecid: false, aam: true... }`

**`status`**

* pending
* changed
* complete

**`doesOptInApply`**

true または false。初期化で指定した設定を表します。

**`isPending`**

status の値に応じて true または false。まだ明示的に権限を承認または拒否していない訪問者について、このプロパティでは true が返されます。

**`isComplete`**

status の値に応じて true または false。ワークフロー形式の同意が開始されたものの完了していない場合、このプロパティでは false が返されることがあります。

## オプトインオブジェクトのメソッド {#section-e0417801a82548d199d833010033e433}

**`approve(categories, shouldWaitForComplete)`**

**`categories`**：承認する 1 つ以上のカテゴリ。次に例を示します。 `adobe.optIn.approve([adobe.OptInCategories.AAM, adobe.OptInCategories.ECID])`**`shouldWaitForComplete`**
:（オプション） booleanパラメーター（デフォルトではfalse）。true を渡した場合は、`adobe.optIn.complete()` () を呼び出すまで承認プロセスが完了しません。このプロセスはワークフローに似ています。

```
<codeblock>
  adobe.optIn.approve(adobe.OptInCategories.ANALYTICS, 
         true); adobe.optIn.approve(adobe.OptInCategories.ECID, true); 
         adobe.optIn.complete() 
</codeblock>
```

**`deny(categories, shouldWaitForComplete)`**

* 1 つ以上のカテゴリを渡すと、承認済みかどうかがチェックされます。
* カテゴリを渡さない場合は、利用可能なすべてのカテゴリがチェックされます。

**`isApproved(categories)`**

1 つ以上のカテゴリが顧客によって承認されているかどうかをチェックします。

**`isPreApproved(categories)`**

1 つ以上のカテゴリが顧客によって事前承認されているかどうかをチェックします（これらのカテゴリが `preOptInApprovals` 設定で渡された場合）。

**`fetchPermissions(callback, shouldAutoSubscribe)`**

権限のリストを取得する非同期 API。コールバックは、権限の許可または拒否プロセスが完了すると、権限のリストで呼び出されます。**`shouldAutoSubscribe`:** ヘルパーユーティリティは、このコールバックを将来のすべてのイベントに自動的にサブスクライブします。つまり、オプトインで承認または拒否がトリガーされるたびに、このコールバックが呼び出されます。これにより、手動でイベントにサブスクライブしなくても、常に更新されます。

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
>パラメーターを `shouldWaitForComplete` 承認または拒否する場合にのみ使用します。この API により、承認プロセスが完了します。例: `adobe.optIn.complete()`.

**`approveAll()`:**

既存のカテゴリをすべて承認します。

**`denyAll()`**

既存のカテゴリをすべて拒否します。

## オプトインオブジェクトのイベント {#section-06f25b33cab54bafb053183e937fb710}

**`complete`:**

承認プロセスが完了したときにイベントトリガーを完了します。このイベントを渡す `shouldWaitForComplete`ことなく承認/拒否を呼び出す場合は、この `approveAll`イベント `denyAll`トリガーをトリガーします。また、`shouldWaitForComplete` を渡した場合は、`complete` が呼び出されるとこのイベントがトリガーされます。

**例**

```
<codeph>
  adobe.optIn.on("complete", callback); 
</codeph>
```
