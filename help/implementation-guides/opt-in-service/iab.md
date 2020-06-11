---
description: IAB Transparency and Consent Framework（TCF）用のオプトインの Audience Manager プラグインを使用して、同社の同意管理プラットフォーム（CMP）に接続します。
seo-description: IAB Transparency and Consent Framework（TCF）用の Audience Manager プラグインを使用して、同社の同意管理プラットフォーム（CMP）に接続します。
seo-title: IAB フレームワークを使用したオプトインサービスの使用
title: IAB フレームワークを使用したオプトインサービスの使用
uuid: 8df39d9c-c016-490e-b4db-d02e4044b480
translation-type: tm+mt
source-git-commit: 4c37c8dd3b76dbf17b955864f0562363350eaecd
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 71%

---


# IAB フレームワークを使用したオプトインサービスの使用 {#using-opt-in-services-with-iab-framework}

>[!IMPORTANT] 次のドキュメントはIAB 2.0にのみ適用されます。IAB 2.0と連携するには、訪問者.jsバージョン5.0を使用する必要があります。

オプトインのIAB Transparency and Consent Framework(TCF)プラグインを使用して、Consent Management Platform(CMP)に接続します。

IAB TCFを使用しているAdobeオーディエンスマネージャーのお客様は、 [IAB TCF](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) (Consent Management Platform)をオプトインのIAB TCFプラグインと接続できます。 オプトインは、（ECID）JavaScript ライブラリ内に組み込まれている機能です。CMP 内で設定された訪問者の設定に応じて、個々のアドビソリューションライブラリを無効化することができます。ECIDライブラリでオプトインのIAB TCFプラグインが実装されると、IAB TCFをサポートするCMPからの訪問者環境設定が自動的にオプトインにマッピングされます。 これらの環境設定により、Audience Manager ベースのライブラリ（DIL および ECID）と、同意を受信したときの関連する呼び出しが有効になります。

## IAB をサポートする CMP の実装 {#section-9fd2403b548947dbb1921ac6ff9d0c82}

オプトインを IAB TCF と統合するには、以下の手順を完了する必要があります。

1. IAB をサポートし [IAB ベンダーとして登録されている](https://vendorlist.consensu.org/vendorlist.json) CMP を実装するか、IAB TCF の仕様を実装する社内 CMP を開発して IAB TCF に登録します。
1. Adobe JS を読み込む前に、`__tcfapi` を定義するか読み込みます。

詳細については、[Interactive Advertising Bureau のドキュメント](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/TCFv2/TCF-Implementation-Guidelines.md)を参照してください。

## Enable Opt-in&#39;s IAB TCF plugin within your ECID Javascript Library {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>オプトインは ECID 4.0 以降でのみ利用できます。

Adobe Experience Platform Launchを使用して、サイトにオプトインのIAB TCFプラグインを実装します。 IAB で手動でオプトインを有効にする場合は、訪問者オブジェクト内で次の設定が true に設定されていることを確認してください。

```javascript
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,
  isIabContext: true
});
```

設定が正しく構成されると、CMP および IAB TCF の同意条件に応じて、ECID および DIL ライブラリが有効／無効になります。

>[!IMPORTANT]
>
>Audience Manager では、*目的 1、10 に対する同意が必要です*。また、Cookie をデプロイして ID 同期を開始または有効化するために、ベンダーの同意が必要です。Read more about the Opt-in&#39;s IAB TCF plugin in Audience Manager documentation [here](https://docs.adobe.com/content/help/ja-JP/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html).

For more information on how to validate Opt-in&#39;s IAB TCF plugin, check use case #4 in the validation guide [here](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0).

## 関連ドキュメント {#section-55da1110051a4b39b1037803f4a7b264}

* [IAB Transparency and Consent Framework（TCF）](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) - IAB 標準の詳細
* [アドビのオプトイン](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360) - プラットフォームソリューションでの同意管理に必要なコンポーネントであるオプトインの詳細
* [Audience Manager](https://docs.adobe.com/content/help/ja-JP/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html) の IAB Transparency and Consent Framework（TCF）サポート
* [プライバシーの選択肢](https://www.adobe.com/jp/privacy/opt-out.html#customeruse) - ユーザーが自由にプライバシーを選択できる権利として、他のグローバルなオプトアウトツールを使用してすべてのデータ収集からオプトアウトすることもできます。グローバルなオプトアウトは、オプトインおよび IAB TCF の検証よりも優先されます。