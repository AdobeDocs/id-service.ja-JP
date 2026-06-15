---
description: 同意管理プラットフォーム（CMP）をオプトインの IAB Transparency and Consent Framework（TCF）用 Audience Manager プラグインに接続します。
title: IAB フレームワークを使用したオプトインサービスの使用
exl-id: 9ac9b232-0797-4e77-a611-9cf5d17a5cb7
TQID: https://experienceleague.adobe.com/70QH1BoRSSbiw7cMfRjrHmiSxQLbuiHcWAG5b-xVOLw
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: d3cdead0-685a-4489-9250-4bb709942f66id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 518
ht-degree: 96%

---

# IAB フレームワークを使用したオプトインサービスの使用{#using-opt-in-services-with-iab-framework}

>[!IMPORTANT]
>
>次のドキュメントは、IAB 2.0にのみ適用されます。 ユーザーは、IAB 2.0を操作するには、Visitor.js バージョン 5.0を使用する必要があります。

オプトインの IAB Transparency and Consent Framework（TCF）プラグインを使用して、同意管理プラットフォーム（CMP）に接続します。

[IAB TCF](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) を使用する Adobe Audience Manager のお客様は、オプトインの IAB TCF プラグインを使用して、Consent Management Platform（CMP）に接続できます。 オプトインは、（ECID）JavaScript ライブラリ内に組み込まれている機能です。CMP 内で設定された訪問者の設定に応じて、個々のアドビソリューションライブラリを無効化することができます。 ECID ライブラリにオプトインの IAB TCF プラグインが実装されると、訪問者の設定は、IAB TCF 対応の CMP からオプトインへ自動的にマッピングされます。 これらの環境設定により、Audience Manager ベースのライブラリ（DIL および ECID）と、同意を受信したときの関連する呼び出しが有効になります。

## IAB をサポートする CMP の実装 {#section-9fd2403b548947dbb1921ac6ff9d0c82}

オプトインを IAB TCF と統合するには、以下の手順を完了する必要があります。

1. IAB をサポートし IAB ベンダーとして登録されている CMP を実装するか、IAB TCF の仕様を実装している社内 CMP を開発して IAB TCF に登録します。
1. Adobe JS を読み込む前に、`__tcfapi` を定義するか読み込みます。

詳細については、[Interactive Advertising Bureau のドキュメント](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/TCFv2/TCF-Implementation-Guidelines.md)を参照してください。

## ECID Javascript ライブラリ内でのオプトイン IAB TCF プラグインの有効化 {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>オプトインは ECID 4.0 以降でのみ利用できます。

Adobe Experience Platform Launch を使用して、サイトにオプトインの IAB TCF プラグインを実装します。 IAB で手動でオプトインを有効にする場合は、訪問者オブジェクト内で次の設定が true に設定されていることを確認してください。

```javascript
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,
  isIabContext: true
});
```

設定が正しく構成されると、CMP および IAB TCF の同意条件に応じて、ECID および DIL ライブラリが有効／無効になります。

>[!IMPORTANT]
>
>Audience Manager では、*目的 1、10 に対する同意が必要です*。また、Cookie をデプロイして ID 同期を開始または有効化するために、ベンダーの同意が必要です。 オプトインの IAB TCF プラグインの詳細については、[こちら](https://experienceleague.adobe.com/docs/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html?lang=ja)にある Audience Manager のドキュメントを参照してください。

オプトインのび IAB TCF プラグインを検証する方法について詳しくは、[こちら](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0)の検証ガイドの使用例 4 を参照してください。

## 関連ドキュメント {#section-55da1110051a4b39b1037803f4a7b264}

* [IAB Transparency and Consent Framework（TCF）](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) - IAB 標準の詳細
* [アドビのオプトイン](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360) - プラットフォームソリューションでの同意管理に必要なコンポーネントであるオプトインの詳細
* [Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html?lang=ja) の IAB Transparency and Consent Framework（TCF）サポート
* [プライバシーの選択肢](https://www.adobe.com/jp/privacy/opt-out.html#customeruse) - ユーザーが自由にプライバシーを選択できる権利として、他のグローバルなオプトアウトツールを使用してすべてのデータ収集からオプトアウトすることもできます。 グローバルなオプトアウトは、オプトインおよび IAB TCF の検証よりも優先されます。

