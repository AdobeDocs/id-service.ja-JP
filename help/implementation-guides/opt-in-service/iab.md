---
description: IAB Transparency and Consent Framework（TCF）用のオプトインの Audience Manager プラグインを使用して、同社の同意管理プラットフォーム（CMP）に接続します。
seo-description: IAB Transparency and Consent Framework（TCF）用の Audience Manager プラグインを使用して、同社の同意管理プラットフォーム（CMP）に接続します。
seo-title: （ベータ）IAB フレームワークを使用したオプトインサービスの使用
title: （ベータ）IAB フレームワークを使用したオプトインサービスの使用
uuid: 8df39d9c-c016-490e-b4db-d02e4044b480
translation-type: tm+mt
source-git-commit: 65947bf4078222561060501178bf28b3c6cfed7c

---


# （ベータ）IAB フレームワークを使用したオプトインサービスの使用 {#beta-using-opt-in-services-with-iab-framework}

オプトインのOpt-in's Audience Manager Plugin for IAB TCFを使用して、Consent Management Platform(CMP)を接続します。

[IAB Transparency and Consent Framework（TCF）](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/)を使用している Audience Manager のお客様は、IAB TCF 用のオプトインの Audience Manager プラグインで同意管理プラットフォーム（CMP）に接続できます。オプトインは、（ECID）JavaScript ライブラリ内に組み込まれている機能です。CMP 内で設定された訪問者の設定に応じて、個々のアドビソリューションライブラリを無効化することができます。IAB TCF用のAudience ManagerプラグインがECIDライブラリで実装されると、IAB準拠のCMPからの訪問者の環境設定が自動的にオプトインにマッピングされます。 これらの環境設定により、Audience Manager ベースのライブラリ（DIL および ECID）と、同意を受信したときの関連する呼び出しが有効になります。

## IAB をサポートする CMP の実装 {#section-9fd2403b548947dbb1921ac6ff9d0c82}

オプトインを IAB 同意と統合するには、以下の手順を完了する必要があります。

1. IAB をサポートし [IAB ベンダーとして登録されている](https://vendorlist.consensu.org/vendorlist.json) CMP を実装するか、IAB の仕様を実装する社内 CMP を開発して IAB Europe に登録します。
1. Adobe JS を読み込む前に、`__cmp` を定義するか読み込みます。

詳細については、[Interactive Advertising Bureau のドキュメント](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/v1.1%20Implementation%20Guidelines.md)を参照してください。

## ECID Javascriptライブラリ内でのIAB用Audience Managerプラグインの有効化 {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>オプトインは ECID 4.0 以降でのみ利用できます。

Adobe Experience Platform Launchを使用して、サイト用のIAB TCF用のオプトインとAudience Managerプラグインの両方を実装します。 オプトイン用の IAB を手動で有効化する場合は、Visitor オブジェクト内で以下の設定が true になっていることを確認してください。

```
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,   
  isIabContext: true   
});
```

設定が適切におこなわれると、CMP および IAB フレームワークの同意条件に応じて、ECID ライブラリおよび DIL ライブラリが有効化または無効化されます。

>[!IMPORTANT]
>
>Audience Manager では、*目的 1、2、5 に対する同意が必要です*。また、Cookie をデプロイして ID 同期を開始または有効化するために、ベンダーの同意が必要です。Audience Managerのドキュメントで、IAB TCF用Audience Managerプラグインについて詳しくはこちらを参照して [ください](https://docs.adobe.com/help/en/audience-manager/user-guide/overview/gdpr/aam-iab-plugin.html)。

For more information on how to validate both Opt-in and the Audience Manager plug-in for IAB, check use case #4 in the validation guide [here](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0).

## 関連ドキュメント {#section-55da1110051a4b39b1037803f4a7b264}

* [IAB Transparency and Consent Framework（TCF）](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) - IAB 標準の詳細
* [アドビのオプトイン](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360) - プラットフォームソリューションでの同意管理に必要なコンポーネントであるオプトインの詳細
* [Audience Manager](https://marketing-beta.adobe.com/resources/help/aam/iab-support/aam-iab-support.html) での IAB Transparency and Consent Framework（TCF）のサポート
* [プライバシーの選択肢](https://www.adobe.com/privacy/opt-out.html#customeruse) - ユーザーが自由にプライバシーを選択できる権利として、他のグローバルなオプトアウトツールを使用してすべてのデータ収集からオプトアウトすることもできます。グローバルなオプトアウトは、オプトインおよび IAB の検証よりも優先されます。

