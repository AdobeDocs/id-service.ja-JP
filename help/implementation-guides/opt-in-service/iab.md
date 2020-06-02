---
description: IAB Transparency and Consent Framework（TCF）用のオプトインの Audience Manager プラグインを使用して、同社の同意管理プラットフォーム（CMP）に接続します。
seo-description: IAB Transparency and Consent Framework（TCF）用の Audience Manager プラグインを使用して、同社の同意管理プラットフォーム（CMP）に接続します。
seo-title: IAB フレームワークを使用したオプトインサービスの使用
title: IAB フレームワークを使用したオプトインサービスの使用
uuid: 8df39d9c-c016-490e-b4db-d02e4044b480
translation-type: ht
source-git-commit: bb61c33491cb67795d58575c5dca5fa2ba4c372f
workflow-type: ht
source-wordcount: '502'
ht-degree: 100%

---


# IAB フレームワークを使用したオプトインサービスの使用 {#using-opt-in-services-with-iab-framework}

IAB TCF 用のオプトインの Audience Manager プラグインを使用して、同社の同意管理プラットフォーム（CMP）に接続します。

[IAB Transparency and Consent Framework（TCF）](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/)を使用している Audience Manager のお客様は、IAB TCF 用のオプトインの Audience Manager プラグインで同意管理プラットフォーム（CMP）に接続できます。オプトインは、（ECID）JavaScript ライブラリ内に組み込まれている機能です。CMP 内で設定された訪問者の設定に応じて、個々のアドビソリューションライブラリを無効化することができます。ECID ライブラリに IAB TCF 用 Audience Manager プラグインが実装されると、訪問者の設定は、IAB TCF 対応の CMP からオプトインへ自動的にマッピングされます。これらの環境設定により、Audience Manager ベースのライブラリ（DIL および ECID）と、同意を受信したときの関連する呼び出しが有効になります。

## IAB をサポートする CMP の実装 {#section-9fd2403b548947dbb1921ac6ff9d0c82}

オプトインを IAB TCF と統合するには、以下の手順を完了する必要があります。

1. IAB をサポートし [IAB ベンダーとして登録されている](https://vendorlist.consensu.org/vendorlist.json) CMP を実装するか、IAB TCF の仕様を実装する社内 CMP を開発して IAB TCF に登録します。
1. Adobe JS を読み込む前に、`__cmp` を定義するか読み込みます。

詳細については、[Interactive Advertising Bureau のドキュメント](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/v1.1%20Implementation%20Guidelines.md)を参照してください。

## ECID Javascript ライブラリ内で IAB TCF 用 Audience Manager プラグインを有効にする {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>オプトインは ECID 4.0 以降でのみ利用できます。

Adobe Experience Platform Launch を使用して、サイトのオプトインおよび IAB TCF 用 Audience Manager プラグインの両方を実装します。IAB で手動でオプトインを有効にする場合は、訪問者オブジェクト内で次の設定が true に設定されていることを確認してください。

```
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,   
  isIabContext: true   
});
```

設定が正しく構成されると、CMP および IAB TCF の同意条件に応じて、ECID および DIL ライブラリが有効／無効になります。

>[!IMPORTANT]
>
>Audience Manager では、*目的 1、10 に対する同意が必要です*。また、Cookie をデプロイして ID 同期を開始または有効化するために、ベンダーの同意が必要です。IAB TCF 用の Audience Manager プラグインについては、[こちら](https://docs.adobe.com/content/help/ja-JP/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html)の Audience Manager ドキュメントを参照してください。

オプトインおよび IAB TCF 用 Audience Manager プラグインの両方を検証する方法について詳しくは、[こちら](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0)の検証ガイドの使用例 4 を参照してください。

## 関連ドキュメント {#section-55da1110051a4b39b1037803f4a7b264}

* [IAB Transparency and Consent Framework（TCF）](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) - IAB 標準の詳細
* [アドビのオプトイン](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360) - プラットフォームソリューションでの同意管理に必要なコンポーネントであるオプトインの詳細
* [Audience Manager](https://docs.adobe.com/content/help/ja-JP/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html) の IAB Transparency and Consent Framework（TCF）サポート
* [プライバシーの選択肢](https://www.adobe.com/jp/privacy/opt-out.html#customeruse) - ユーザーが自由にプライバシーを選択できる権利として、他のグローバルなオプトアウトツールを使用してすべてのデータ収集からオプトアウトすることもできます。グローバルなオプトアウトは、オプトインおよび IAB TCF の検証よりも優先されます。

