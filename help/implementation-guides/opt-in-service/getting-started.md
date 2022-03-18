---
description: Experience Cloud ソリューション（オプトインではカテゴリーと呼ばれます）で使用される単一の参照ポイントとしてオプトインサービスを実装し、訪問者のデバイスで Cookie を作成するかどうかを決定します。
title: オプトインサービスの設定
exl-id: 6e8a6531-9924-4523-a842-cb4614a7a7a0
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '908'
ht-degree: 100%

---

# オプトインサービスの設定{#setting-up-opt-in-service}

Experience Cloud ソリューション（オプトインではカテゴリーと呼ばれます）で使用される単一の参照ポイントとしてオプトインサービスを実装し、訪問者のデバイスで Cookie を作成するかどうかを決定します。

オプトインサービスは、Experience Cloud ID（ECID）にバンドルされた JavaScript ライブラリであり、Visitor JS のグローバルな `adobe` オブジェクトに `adobe.optIn` オブジェクトとして存在します。インストールされたオプトインサービスを使用すると、訪問者が複数のアドビソリューションのオプトインを一度に実行するか、それぞれの権限に合わせてソリューションを順番に表示するかを指定できます。オプトインサービスの同意管理機能を使用すると、固有のプライバシー要件に応じたさまざまな設定での実装が可能になります。

オプトインサービスを使用すると、訪問者が複数のアドビソリューションのオプトインを一度に実行するか、それぞれの権限に合わせてソリューションを順番に表示するかを指定できます。承認プロセスが完了し、顧客によって記録されると、CMP の訪問者の承認は、関連する同意の要求に対応するためにすべてのアドビソリューションで取得できます。

## 前提条件 {#section-c39246f45e514c8ea9fdbe6f7ffa3ad0}

1. ECID バージョン 4.0。

   アドビの最新 ECID リリースを[ダウンロード](https://github.com/Adobe-Marketing-Cloud/id-service/releases)してください。

1. 補助ライブラリ：

   * ECID 4.0 以降
   * AppMeasurement 2.11 以降
   * DIL 9.0
   * AT.js バージョン 1.7.0
   * AT.js Launch 拡張バージョン 9.0
   * Analytics の場合、App Measurement 2.11（拡張機能 1.6 付き）
   * Target の場合、拡張機能 0.9.1

1. オプトインで使用する同意管理フレームワークに精通し、その他の前提条件を理解していること。

   <!--
   For IAB, see here for additional pre-reqs.
   -->

1. 会社のプライバシー要件は、GDPR への準拠を選択する方法によって異なります。 会社のプライバシーチームが事前同意状態で使用しても問題ないライブラリを確認してください。

[Adobe Launch](https://experienceleague.adobe.com/docs/launch/using/home.html?lang=ja) を使用している場合は、[オプトイン拡張機能](../../implementation-guides/opt-in-service/launch.md)を活用してオプトインサービスを設定します。

## オプトインのカテゴリー {#section-9ab0492ab4414f0ca16dc08d3a905f47}

訪問者のオプトインの環境設定は Adobe Experience Cloud ソリューションとは相対的で、各ソリューションがカテゴリーとして表されます。カテゴリーは `adobe.OptInCategories` オブジェクトで指定されます。例えば、ECID コンポーネントは `adobe.OptInCategories` となります。`ECID`をインストールします。以下は、`adobe.OptInCategories` の定義です。

オプトインの設定は、カテゴリーごとに管理されます。ここでは、各 Experience Cloud ソリューションはカテゴリーで表されます。

```
adobe.OptInCategories = { 
    AAM: "aam", 
    TARGET: "target",  
    ANALYTICS: "aa", 
    ECID: "ecid", 
     
};
```

オプトインサービスにより、サイトで使用されるアドビソリューションごとに訪問者の権限設定を設定できます。このオブジェクトでは、承認済みのカテゴリーごとに訪問者の設定を保存するライブラリが用意されており、承認プロセスで各カテゴリーの「確認」または「拒否」設定を 1 つずつ受け取るシーケンシャルフローがサポートされています。複数のソリューション（カテゴリー）をまとめてオプトインするか、個別のソリューションとしてオプトインするかを設定できます。
アドビソリューションのクライアント側ライブラリはすべて、オプトインサービスに依存しており、ソリューションに権限が付与されない限り Cookie を生成しません。オプトインでは、現在の訪問者の同意設定をさまざまな方法で指定および更新できます。このセクションでは、オプトインサービスの設定例を示します。機能とパラメーターのリストについては、[オプトイン API リファレンス](../../implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867)を参照してください。

オプトインサービスの設定は、グローバルな `getInstance()` オブジェクトをインスタンス化する Visitor JS `adobe` 関数で指定します。以下に、オプトインサービス用の Visitor JS [設定](../../implementation-guides/opt-in-service/api.md#section-d66018342baf401389f248bb381becbf)を示します。

**グローバルな `Visitor` オブジェクトの初期化におけるオプトインの設定例**

```
// FORMAT: Object<adobe.OptInCategories enum: boolean> 
var preOptInApprovalsConfig = {}; 
preOptInApprovals[adobe.OptInCategories.ANALYTICS] = true; 
  
// FORMAT: Object<adobe.OptInCategories enum: boolean> 
// If you are storing the OptIn permissions on your side (in a cookie you manage or in a CMP), 
// you have to provide those permissions through the previousPermissions config. 
// previousPermissions will overwrite preOptInApprovals. 
var previousPermissionsConfig = {}; 
previousPermissionsConfig[adobe.OptInCategories.AAM] = true; 
previousPermissionsConfig[adobe.OptInCategories.ANALYTICS] = false; 
  
Visitor.getInstance("YOUR_ORG_ID", { 
    "doesOptInApply": true, // NOTE: This can be a function that evaluates to true or false. 
    "preOptInApprovals": preOptInApprovalsConfig, 
    "previousPermissions": previousPermissionsConfig, 
    "isOptInStorageEnabled": true 
});
```

**同意に対する変更の処理**

訪問者は、サイトに滞在している間はいつでも、初めて環境設定を行ったり、CMP を使用して環境設定を変更したりできます。 初期設定で訪問者 JS を初期化したら、訪問者の権限を変更できます。 同意を管理するための関数の一覧については、[同意の変更](../../implementation-guides/opt-in-service/api.md#section-c3d85403ff0d4394bd775c39f3d001fc)を参照してください。

<!--
<p> *** <b>sample code block </b>*** </p>
-->

## オプトインワークフロー {#section-70cd243dec834c8ea096488640ae20a5}

オプトインサービスでは、複数回のリクエストサイクルで権限を収集でき、環境設定が 1 つずつおこなわれるワークフローがサポートされています。以下の関数を使用して *に* true`shouldWaitForComplete` を指定すると、ソリューションでは、1 つのソリューションまたは全カテゴリーのサブセットに対する同意を収集してから、次のソリューションまたは全カテゴリーの別のサブセットに対する同意を収集することができます。最初の呼び出しから、フローの最後に `adobe.optIn.status` が呼び出されるまで、*プロパティは* pending`adobe.optIn.complete()` になります。この呼び出し後、ステータスは *complete* に設定されます。

```
adobe.optIn.approve(['AAM', 'ECID'], true); 
adobe.optIn.deny(['ANALYTICS'], true); 
adobe.optIn.complete();
```

[ワークフローの設定](../../implementation-guides/opt-in-service/api.md#section-2c5adfa5459c4e72b96d2693123a53c2)を参照してください。

## 訪問者のオプトイン権限の確認 {#section-f136a9024e054d84881e6667fb7c94eb}

訪問者が自身の権限を変更した場合は、変更後の権限を調査して、オプトインサービスでおこなわれた変更を同意ストアと同期する必要があります。[権限関数](../../implementation-guides/opt-in-service/api.md#section-7fe57279b5b44b4f8fe47e336df60155)を使用して、訪問者の環境設定を調べます。次に例を示します。

**fetchPermissions サンプル**

```
optIn.fetchPermissions(function (permissions) { 
    // Here you can check if your category has been approved or not. 
    // We recommend using optIn.isApproved() to check for permissions because it abstracts out the details of knowing exactly how the permissions list looks like. 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
});

OR: You can pass in shouldAutoSubscribe as true, your callback will be used to subscribe to all OptIn events going forward:

function callback() { 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
}

optIn.fetchPermissions(callback, true);
```

これらおよびこのドキュメントに記載されているあらゆる関数、プロパティ、設定の詳細については、[API ドキュメント](../../implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867)を参照してください。

## 訪問者の設定の保存 {#section-ef2884ae67e34879bf7c7c3372706c9f}

オプトインサービスでは、開発環境や CRM を使用できない環境に適した同意設定を保存することができます。`isOptInStorageEnabled` 設定プロパティを *true* として指定すると、オプトインサービスにより、ドメイン内の訪問者のシステムに Cookie が作成されます。

`adobe.optIn` オブジェクトはステートレスであり、保存メカニズムは備えていません。カスタムデータの保存が許可されている場合は、代わりに、既存の同意管理プラットフォーム（CMP）でアドビの同意設定を管理することを目的しています。 または、訪問者の環境設定を訪問者のブラウザー上の Cookie に保存できます。 オプトインサービスにユーザーの環境設定を指定する方法は 2 つあります。

* CMP か訪問者のブラウザーの Cookie かに関わらず、同意保持ソリューションで訪問者の設定をタイムリーに取得できる場合は、Visitor の初期化中にこれらの設定をオプトインサービスに指定できます。
* ただし、取得プロセスに時間がかかる場合や、非同期プロセスとして最善の役割を果たしている場合には、サービスの `approve()` 関数を使用して、読み込みに成功したときにこれらの設定を指定できます。
