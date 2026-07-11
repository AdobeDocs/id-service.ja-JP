---
audience: end-user
user-guide-title: Adobe Visitor ID サービスのヘルプ
breadcrumb-title: 訪問者ID サービスガイド
user-guide-description: Adobe Visitor ID Serviceは、CX Enterpriseのすべてのソリューションをまたいで訪問者を識別する、ユニバーサルで永続的なIDを提供します。 CX Enterpriseのソリューションおよびサービスの従来のID生成コードを置き換えるのに役立ちます。
user-guide-url: /content/help/en/id-service/using/home.html
source-git-commit: 7621dc8925235bd3cf159a404741bd02fc9b6a77
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 45%

---


# Adobe Visitor ID サービスのヘルプ {#using}

+ [訪問者ID サービスのヘルプ](home.md)
+ 概要 {#intro}
   + [概要](introduction/overview.md)
   + [訪問者ID サービスについて](introduction/about-id-service.md)
   + [Cookieと訪問者ID サービス](introduction/cookies.md)
   + [訪問者ID サービスがIDをリクエストおよび設定する方法](introduction/id-request.md)
   + [同期と一致率について](introduction/match-rates.md)
+ 実装 {#implementation}
   + [実装方法](implementation-guides/implementation-methods.md)
   + [実装ガイド](implementation-guides/implementation-guides.md)
   + [タグを使用した実装](implementation-guides/ecid-implement-with-launch.md)
   + [Analyticsの実装](https://experienceleague.adobe.com/ja/docs/analytics/implementation/id/overview){target=_blank}
   + [Target への実装](implementation-guides/setup-target.md)
   + [Analytics および Audience Manager への実装](implementation-guides/setup-aam-analytics.md)
   + [Analytics、Audience Manager および Target への実装](implementation-guides/setup-aam-analytics-target.md)
   + [A4TおよびTargetのサーバーサイド実装での訪問者ID サービスの使用](implementation-guides/ecid-a4t-target.md)
   + [訪問者ID サービスとの直接統合](implementation-guides/direct-integration.md)
   + [直接統合のユースケース](implementation-guides/direct-integration-examples.md)
   + [訪問者ID サービスのテストと検証](implementation-guides/test-verify.md)
   + オプトインサービス {#opt-in-service}
      + [オプトインサービスの概要](implementation-guides/opt-in-service/optin-overview.md)
      + [オプトインサービスの設定](implementation-guides/opt-in-service/getting-started.md)
      + [オプトインサービスの検証](implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [タグを使用したオプトインの設定](implementation-guides/opt-in-service/launch.md)
      + [ユーザーの同意に基づいた顧客体験のエンタープライズアクティビティの管理](implementation-guides/opt-in-service/use-opt-in-to-control-experience-cloud-activities-based-on-user-consent.md)
      + [オプトインのユースケース](implementation-guides/opt-in-service/use-cases.md)
      + [オプトインのリファレンス](implementation-guides/opt-in-service/api.md)
      + [IAB フレームワークでのオプトインサービスの使用](implementation-guides/opt-in-service/iab.md)
+ 訪問者ID サービス API {#id-service-api}
   + [訪問者ID サービス APIの概要](library/library.md)
   + 設定 {#configurations}
      + [設定の概要](library/function-vars/function-vars.md)
      + [audienceManagerServer および audienceManagerServerSecure](library/function-vars/subdomain-config.md)
      + [cookieDomain](library/function-vars/cookiedomain.md)
      + [cookieLifetime](library/function-vars/cookielifetime.md)
      + [disableIdSyncs](library/function-vars/disableidsync.md)
      + [disableThirdPartyCalls](library/function-vars/disablethirdpartycalls.md)
      + [disableThirdPartyCookies](library/function-vars/disable-cookies.md)
      + [idSyncAttachIframeOnWindowLoad](library/function-vars/idsyncattachiframeonwindowload.md)
      + [idSyncContainerID](library/function-vars/idsyncontainerid.md)
      + [idSyncSSLUseAkamai](library/function-vars/idsyncssluseakamai.md)
      + [loadTimeout](library/function-vars/loadtimeout.md)
      + [overwriteCrossDomainMCIDAndAID](library/function-vars/overwrite-visitor-id.md)
      + [resetBeforeVersion](library/function-vars/resetbeforeversion.md)
      + [sdidParamExpiry](library/function-vars/sdidparamexpiry.md)
      + [セキュア設定と SameSite 設定](library/function-vars/secure-samesite-config.md)
      + [secureCookie](library/function-vars/securecookie.md)
      + [useCORSOnly](library/function-vars/use-cors-only.md)
      + [whitelistParentDomain および whitelistIframeDomains](library/function-vars/whitelistdomain.md)
   + メソッド {#methods}
      + [メソッド](library/get-set/get-set.md)
      + [appendSupplementalDataIDTo](library/get-set/appendsupplementaldataidto.md)
      + [appendVisitorIDsTo（クロスドメイントラッキング）](library/get-set/appendvisitorid.md)
      + [callTimeOut メソッド](library/get-set/timeout-functions.md)
      + [URL またはデータソースによる ID 同期](library/get-set/idsync.md)
      + [getInstance](library/get-set/getinstance.md)
      + [getAnalyticsVisitorID](library/get-set/getanalyticsvisitorid.md)
      + [getCustomerIDs](library/get-set/getcustomerids.md)
      + [setCustomerIDs](library/get-set/setcustomerids.md)
      + [getMarketingCloudVisitorID](library/get-set/getmcvid.md)
      + [getLocationHint](library/get-set/getlocationhint.md)
      + [getVisitorValues](library/get-set/getvisitorvalues.md)
      + [isClientSideMarketingCloudVisitorID](library/get-set/client-side-id.md)
      + [resetState](library/get-set/resetstate.md)
+ リファレンス {#reference}
   + [リファレンスの概要](reference/reference.md)
   + [Google Chrome SameSite のラベル付けの変更](reference/chrome-samesite-labelling.md)
   + [コンテンツセキュリティポリシーと訪問者ID サービス](reference/csp.md)
   + [訪問者ID サービスでのCOPPA サポート](reference/coppa.md)
   + [訪問者ID サービスでのCORS サポート](reference/cors.md)
   + [顧客 ID と認証状態](reference/authenticated-state.md)
   + [Safari ITP の世界における ECID ライブラリのメソッド](reference/ecid-library-methods.md)
   + [ユニーク訪問者数の識別](reference/unique-vis-method.md)
   + [AMCV Cookieまたは訪問者ID サービスからリージョンとユーザーIDを取得する](reference/regions.md)
   + [Visitor ID サービスの要件](reference/requirements.md)
   + [ビデオハートビートと訪問者ID サービス](reference/heartbeat.md)
   + [setCustomerIDs の SHA256 ハッシュサポート](reference/hashing-support.md)
+ よくある質問（FAQ） {#faqs}
   + [FAQ の概要](faq-intro/faq-intro.md)
   + [訪問者ID サービスに関するFAQ](faq-intro/faq.md)
   + [他のCX エンタープライズソリューションに関するFAQ](faq-intro/other-faq.md)
+ 訪問者ID サービスのリリースノート {#release-notes}
   + [2022年リリースノート](release-notes/notes-2022.md)
   + [2021年リリースノート](release-notes/notes-2021.md)
   + [2020 年リリースノート](release-notes/notes-2020.md)
   + [2019 年リリースノート](release-notes/notes-2019.md)
   + [2018 年リリースノート](release-notes/notes-2018.md)
   + [2017 年リリースノート](release-notes/notes-2017.md)
   + [2016 年リリースノート](release-notes/notes-2016.md)
   + [2015 年リリースノート](release-notes/notes-2015.md)
