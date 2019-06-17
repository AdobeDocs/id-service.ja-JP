---
description: オプトインサービスは、Experience Cloudソリューションで使用される単一の参照ポイントとして実装されます（オプトインのカテゴリと呼ばれます）。訪問者のデバイスでcookieを作成するかどうかを決定します。
seo-description: オプトインサービスは、Experience Cloudソリューションで使用される単一の参照ポイントとして実装されます（オプトインのカテゴリと呼ばれます）。訪問者のデバイスでcookieを作成するかどうかを決定します。
seo-title: オプトインサービスの設定
title: オプトインサービスの設定
uuid: f1c27139- Propf2-4122- af12- c839cfc82e6e
translation-type: tm+mt
source-git-commit: ae65e9c7da5ac9cbe22de3f956bcd7cbef2052a7

---


# オプトインサービスの設定{#setting-up-opt-in-service}

オプトインサービスは、Experience Cloudソリューションで使用される単一の参照ポイントとして実装されます（オプトインのカテゴリと呼ばれます）。訪問者のデバイスでcookieを作成するかどうかを決定します。

オプトインサービスは [、Experience Cloud ID（ECID）](https://marketing.adobe.com/resources/help/en_US/mcvid/) にバンドルされているJavaScriptライブラリで、オブジェクトとしてグローバル `adobe` オブジェクトのVisitor `adobe.optIn` JSに存在します。インストールされているオプトインサービスでは、訪問者がアドビソリューションに一度にオプトインできるか、または各ユーザーに対する権限のためにソリューションを表示するかを指定できます。オプトインサービスの同意管理機能を使用すると、特定のプライバシー要件に応じて様々な設定を行うことができます。

オプトインサービスを使用すると、訪問者が一度にアドビソリューションにオプトインできるか、または各ユーザーに対する権限のためにソリューションを表示するかを指定できます。承認プロセスが完了し、顧客によって記録されると、CMP の訪問者の承認は、関連する同意の要求に対応するためにすべてのアドビソリューションで取得できます。

## 前提条件 {#section-c39246f45e514c8ea9fdbe6f7ffa3ad0}

1. ECID バージョン 4.0。

   最新の ECID リリースを[ダウンロード](https://github.com/Adobe-Marketing-Cloud/id-service/releases)してください。

1. サポートしているライブラリ：

   * ECID 4.0 以降
   * AppMeasurement 2.11 以降
   * DIL 9.0
   * AT.js バージョン 1.7.0
   * AT.js Launch 拡張のバージョン 9.0
   * （Analytics の場合）拡張 1.6 を含む AppMeasurement 2.11
   * （Target の場合）拡張 0.9.1

1. オプトインで使用する同意管理フレームワークを熟知し、その他の前提条件を把握します。

   <!--
   For IAB, see here for additional pre-reqs.
   -->

1. 会社のプライバシー要件は、GDPR に準拠し続けるために選んだ方法に対して特異的になります。社内のプライバシー担当チームから同意前の状態での使用が認められているライブラリに注意してください。

[Adobe Launch](https://docs.adobelaunch.com/) を使用すると、[オプトイン拡張機能](../../mcvid-implementation-guides/opt-in-service/launch.md) を使用してオプトインサービスを設定します。

## オプトインカテゴリ {#section-9ab0492ab4414f0ca16dc08d3a905f47}

訪問者のオプトインの環境設定は Adobe Experience Cloud ソリューションとは相対的で、各ソリューションがカテゴリとして表されます。カテゴリは `adobe.OptInCategories` オブジェクトで指定されます。例えば、ECID コンポーネントは `adobe.OptInCategories`.`ECID`をインストールします。以下は、`adobe.OptInCategories` の定義です。

オプトインの設定は、カテゴリごとに管理されます。ここでは、各 Experience Cloud ソリューションはカテゴリで表されます。

```
adobe.OptInCategories = { 
    AAM: "aam", 
    TARGET: "target",  
    ANALYTICS: "aa", 
    ECID: "ecid", 
     
};
```

オプトインサービスを使用すると、サイトで使用する各アドビソリューションごとに訪問者の権限設定を設定できます。このオブジェクトでは、承認済みのカテゴリごとに訪問者の設定を保存するライブラリが用意されており、承認プロセスで各カテゴリの「確認」または「拒否」設定を 1 つずつ受け取るシーケンシャルフローがサポートされています。複数のソリューション（カテゴリ）をまとめてオプトインするか、個別のソリューションとしてオプトインするかを設定できます。アドビソリューションのすべてのソリューションはオプトインサービスに依存し、ソリューションに許可が付与されていない限り、cookieは生成されません。オプトインでは、現在の訪問者の同意設定をさまざまな方法で指定および更新できます。この節では、オプトインサービスの環境設定の設定例を示します。関数とパラメーターの完全なリストについては [、オプトインAPIリファレンス](../../mcvid-implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867) を参照してください。

オプトインサービス設定は、グローバルオブジェクトをインスタンス化する訪問者JS `getInstance()` 関数に提供 `adobe` されます。オプトインサービスの訪問者JS [設定の](../../mcvid-implementation-guides/opt-in-service/api.md#section-d66018342baf401389f248bb381becbf) 一覧を以下に示します。

**グローバルな`Visitor`オブジェクトの初期化におけるオプトインの設定例**

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

訪問者は、サイトを訪問中にいつでも、CMP を使用して初めて環境設定を設定したり、設定した設定を変更したりできます。Visitor JS が初期設定で初期化された後、訪問者の権限を変更できます。同意 [する同意文のリストに](../../mcvid-implementation-guides/opt-in-service/api.md#section-c3d85403ff0d4394bd775c39f3d001fc) ついては、「同意の変更」を参照してください。

<!--
<p> *** <b>sample code block </b>*** </p>
-->

## オプトインワークフロー {#section-70cd243dec834c8ea096488640ae20a5}

オプトインサービスは、複数のリクエストサイクルにわたって権限を収集できるワークフローをサポートし、環境設定は一度に1つずつ提供されます。以下の関数を使用して * に *true`shouldWaitForComplete` を指定すると、ソリューションでは、1 つのソリューションまたは全カテゴリのサブセットに対する同意を収集してから、次のソリューションまたは全カテゴリの別のサブセットに対する同意を収集することができます。最初の呼び出しから、フローの最後に `adobe.optIn.status` 呼び出さ ** れるまで `adobe.optIn.complete()` プロパティが保留されます。この呼び出し後、ステータスは *complete* に設定されます。

```
adobe.optIn.approve(['AAM', 'ECID'], true); 
adobe.optIn.deny(['ANALYTICS'], true); 
adobe.optIn.complete();
```

[ワークフローの設定を参照](../../mcvid-implementation-guides/opt-in-service/api.md#section-2c5adfa5459c4e72b96d2693123a53c2)してください。

## 訪問者のオプトイン権限の確認 {#section-f136a9024e054d84881e6667fb7c94eb}

訪問者が権限を変更したときに、承認ストアをオプトインサービスで行われた変更と同期するために、結果の権限に関するインサイトが必要になります。訪問者の設定を確認するには、次の例のように[権限関数](../../mcvid-implementation-guides/opt-in-service/api.md#section-7fe57279b5b44b4f8fe47e336df60155)を使用します。

**fetchPermissions のサンプル**

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

上記のサンプルおよびこのドキュメントで取り上げている関数、プロパティおよび設定の詳細については、[API ドキュメント](../../mcvid-implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867)を参照してください。

## 訪問者の環境設定の保存 {#section-ef2884ae67e34879bf7c7c3372706c9f}

オプトインサービスには、開発環境またはCRMを使用できない環境に適した環境の環境設定を保存するオプションがあります。設定プロパティをtrue `isOptInStorageEnabled` と *指定すると、オプトインサービスが* トリガーされ、ドメイン内の訪問者のシステムにcookieが作成されます。

`adobe.optIn` オブジェクトはステートレスであり、保存メカニズムは備えていません。その代わり、既存の同意管理プラットフォーム（CMP）でカスタムデータの保存が許可されている場合にそのプラットフォームでアドビの同意設定を管理することを目的としています。また、訪問者のブラウザーの Cookie に訪問者の設定を保存することもできます。オプトインサービスにユーザーの環境設定を提供するには、次の2つのオプションがあります。

* 同意の永続性ソリューションで、それが訪問者のブラウザーのCMPまたはcookieであるかどうかにかかわらず、訪問者の好みをタイムリーに取得するには、訪問者の初期化時に、オプトインサービスにそれらを提供できます。
* ただし、取得が長くなる可能性がある場合や、非同期プロセスとして最適な機能を提供する場合は、サービス `approve()` の関数を使用して、それらの設定が正常に読み込まれた後にそれらの設定を指定できます。

