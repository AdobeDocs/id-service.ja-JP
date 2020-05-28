---
description: IAB Transparency and Consent Framework（TCF）用のオプトインの Audience Manager プラグインを使用して、同社の同意管理プラットフォーム（CMP）に接続します。
seo-description: IAB Transparency and Consent Framework（TCF）用の Audience Manager プラグインを使用して、同社の同意管理プラットフォーム（CMP）に接続します。
seo-title: IAB フレームワークを使用したオプトインサービスの使用
title: IAB フレームワークを使用したオプトインサービスの使用
uuid: 8df39d9c-c016-490e-b4db-d02e4044b480
translation-type: tm+mt
source-git-commit: bb61c33491cb67795d58575c5dca5fa2ba4c372f
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 66%

---


# IAB フレームワークを使用したオプトインサービスの使用 {#using-opt-in-services-with-iab-framework}

IAB TCF 用のオプトインの Audience Manager プラグインを使用して、同社の同意管理プラットフォーム（CMP）に接続します。

[IAB Transparency and Consent Framework（TCF）](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/)を使用している Audience Manager のお客様は、IAB TCF 用のオプトインの Audience Manager プラグインで同意管理プラットフォーム（CMP）に接続できます。オプトインは、（ECID）JavaScript ライブラリ内に組み込まれている機能です。CMP 内で設定された訪問者の設定に応じて、個々のアドビソリューションライブラリを無効化することができます。IAB TCF用のオーディエンスマネージャープラグインがECIDライブラリと共に実装される場合、IAB TCFをサポートするCMPからの訪問者環境設定が自動的にオプトインにマッピングされます。 これらの環境設定により、Audience Manager ベースのライブラリ（DIL および ECID）と、同意を受信したときの関連する呼び出しが有効になります。

## IAB をサポートする CMP の実装 {#section-9fd2403b548947dbb1921ac6ff9d0c82}

オプトインをIAB TCFと統合するには、次の手順を実行する必要があります。

1. Implement a CMP that supports IAB and is [registered as an IAB vendor](https://vendorlist.consensu.org/vendorlist.json) or develop an in-house CMP that implements the IAB TCF spec, and register as a CMP with IAB TCF.
1. Adobe JS を読み込む前に、`__cmp` を定義するか読み込みます。

詳細については、[Interactive Advertising Bureau のドキュメント](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/v1.1%20Implementation%20Guidelines.md)を参照してください。

## ECID Javascript ライブラリ内で IAB TCF 用 Audience Manager プラグインを有効にする {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>オプトインは、ECID 4.0以降でのみ使用できます。

Adobe Experience Platform Launch を使用して、サイトのオプトインおよび IAB TCF 用 Audience Manager プラグインの両方を実装します。IABで手動でオプトインを有効にする場合は、訪問者オブジェクト内で次の設定がtrueに設定されていることを確認してください。

```
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,   
  isIabContext: true   
});
```

設定が正しく構成されると、CMPおよびIAB TCFの同意条件に応じて、ECIDおよびDILライブラリが有効/無効になります。

>[!IMPORTANT]
>
>Audience Manager needs consent for *Purpose 1 and Purpose 10, plus vendor consent* in order to deploy cookies and initiate or honor ID syncs. IAB TCF 用の Audience Manager プラグインについては、[こちら](https://docs.adobe.com/content/help/ja-JP/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html)の Audience Manager ドキュメントを参照してください。

オプトインおよび IAB TCF 用 Audience Manager プラグインの両方を検証する方法について詳しくは、[こちら](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0)の検証ガイドの使用例 4 を参照してください。

## 関連ドキュメント {#section-55da1110051a4b39b1037803f4a7b264}

* [IAB Transparency and Consent Framework（TCF）](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) - IAB 標準の詳細
* [アドビのオプトイン](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360) - プラットフォームソリューションでの同意管理に必要なコンポーネントであるオプトインの詳細
* IAB Transparency and Consent Framework (TCF) Support [in Audience Manager](https://docs.adobe.com/content/help/ja-JP/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html)
* [プライバシーの選択肢](https://www.adobe.com/jp/privacy/opt-out.html#customeruse) - ユーザーが自由にプライバシーを選択できる権利として、他のグローバルなオプトアウトツールを使用してすべてのデータ収集からオプトアウトすることもできます。グローバルオプトアウトは、オプトインおよびIAB TCF検証よりも優先されます

