---
cloud: experience-cloud
product: ID サービス
audience: エンドユーザー
user-guide-title: IDサービスヘルプ
user-guide-url: /content/help/en/id-service/using/mcvid-home.html
translation-type: tm+mt
source-git-commit: 1dd8b109f7e9567b5f72747ecc653d35d0942413

---


# IDサービスヘルプ {#using}

+ [Experience Cloud ID サービス](mcvid-home.md)
+ 概要 {#mcvid-introduction}
   + [概要](mcvid-introduction/mcvid-overview.md)
   + [IDサービスについて](mcvid-introduction/mcvid-about-id-service.md)
   + [Cookie と Experience Cloud ID サービス](mcvid-introduction/mcvid-cookies.md)
   + [Experience Cloud IDサービスのリクエストとIDの設定方法](mcvid-introduction/mcvid-id-request.md)
   + [ID同期と一致率について](mcvid-introduction/mcvid-match-rates.md)
+ 導入ガイド {#implementation-guides}
   + [導入ガイド](mcvid-implementation-guides/mcvid-implementation-guides.md)
   + [実装方法](mcvid-implementation-guides/mcvid-implementation-methods.md)
   + [Launch を使用した実装](mcvid-implementation-guides/ecid-implement-with-launch.md)
   + [Dynamic Tag Managementによる実装](mcvid-implementation-guides/mcvid-standard.md)
   + [Experience Cloud ID サービスの Analytics への実装](mcvid-implementation-guides/mcvid-setup-analytics.md)
   + [Experience Cloud ID サービスの Target への実装](mcvid-implementation-guides/mcvid-setup-target.md)
   + [Experience Cloud ID サービスの Analytics および Audience Manager への実装](mcvid-implementation-guides/mcvid-setup-aam-analytics.md)
   + [Experience Cloud ID サービスの Analytics、Audience Manager および Target への実装](mcvid-implementation-guides/mcvid-setup-aam-analytics-target.md)
   + [Target のサーバー側実装を使用する A4T での Experience Cloud ID サービスの使用](mcvid-implementation-guides/ecid-a4t-target.md)
   + [Experience Cloud ID サービスとの直接統合](mcvid-implementation-guides/mcvid-direct-integration.md)
   + [直接統合の使用例](mcvid-implementation-guides/mcvid-direct-integration-examples.md)
   + [Experience Cloud IDサービスのテストと検証](mcvid-implementation-guides/mcvid-test-verify.md)
   + オプトインドキュメント {#opt-in-service}
      + [オプトインサービスの概要](mcvid-implementation-guides/opt-in-service/mcvid-optin-overview.md)
      + [オプトインサービスの設定](mcvid-implementation-guides/opt-in-service/getting-started.md)
      + [オプトインサービスの検証](mcvid-implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [Launch を使用したオプトインの設定](mcvid-implementation-guides/opt-in-service/launch.md)
      + [DTM を使用したオプトインの設定](mcvid-implementation-guides/opt-in-service/optin-dtm.md)
      + [オプトインの使用例](mcvid-implementation-guides/opt-in-service/use-cases.md)
      + [オプトインリファレンス](mcvid-implementation-guides/opt-in-service/api.md)
      + [（ベータ） IABフレームワークを使用したオプトインサービスの使用](mcvid-implementation-guides/opt-in-service/iab.md)
+ ID サービスの API {#id-service-api}
   + [IDサービスAPIの概要](mcvid-library/mcvid-library.md)
   + 設定 {#configurations}
      + [設定の概要](mcvid-library/mcvid-function-vars/mcvid-function-vars.md)
      + [audienceManagerServer および audienceManagerServerSecure](mcvid-library/mcvid-function-vars/mcvid-subdomain-config.md)
      + [cookieDomain](mcvid-library/mcvid-function-vars/mcvid-cookiedomain.md)
      + [cookieLifetime](mcvid-library/mcvid-function-vars/mcvid-cookielifetime.md)
      + [disableIdSyncs](mcvid-library/mcvid-function-vars/mcvid-disableidsync.md)
      + [disableThirdPartyCalls](mcvid-library/mcvid-function-vars/mcvid-disablethirdpartycalls.md)
      + [disableThirdPartyCookies](mcvid-library/mcvid-function-vars/mcvid-disable-cookies.md)
      + [idSyncAttachIframeOnWindowLoad](mcvid-library/mcvid-function-vars/mcvid-idsyncattachiframeonwindowload.md)
      + [idSyncContainerID](mcvid-library/mcvid-function-vars/mcvid-idsyncontainerid.md)
      + [idSyncSSLUseAkamai](mcvid-library/mcvid-function-vars/mcvid-idsyncssluseakamai.md)
      + [isCoopSafe](mcvid-library/mcvid-function-vars/mcvid-coopsafe.md)
      + [loadTimeout](mcvid-library/mcvid-function-vars/mcvid-loadtimeout.md)
      + [overwriteCrossDomainMCIDAndAID](mcvid-library/mcvid-function-vars/mcvid-overwrite-visitor-id.md)
      + [resetBeforeVersion](mcvid-library/mcvid-function-vars/mcvid-resetbeforeversion.md)
      + [sdidParamExpiry](mcvid-library/mcvid-function-vars/mcvid-sdidparamexpiry.md)
      + [secureCookie](mcvid-library/mcvid-function-vars/mcvid-securecookie.md)
      + [useCORSOnly](mcvid-library/mcvid-function-vars/mcvid-use-cors-only.md)
      + [whitelistParentDomain および whitelistIframeDomains](mcvid-library/mcvid-function-vars/mcvid-whitelistdomain.md)
   + メソッド {#methods}
      + [メソッド](mcvid-library/mcvid-get-set/mcvid-get-set.md)
      + [appendSupplementalDataIDTo](mcvid-library/mcvid-get-set/mcvid-appendsupplementaldataidto.md)
      + [appendVisitorIDsTo（クロスドメイントラッキング）](mcvid-library/mcvid-get-set/mcvid-appendvisitorid.md)
      + [callTimeOut メソッド](mcvid-library/mcvid-get-set/mcvid-timeout-functions.md)
      + [URL またはデータソースによる ID 同期](mcvid-library/mcvid-get-set/mcvid-idsync.md)
      + [getInstance](mcvid-library/mcvid-get-set/mcvid-getinstance.md)
      + [getAnalyticsVisitorID](mcvid-library/mcvid-get-set/mcvid-getanalyticsvisitorid.md)
      + [getCustomerIDs](mcvid-library/mcvid-get-set/mcvid-getcustomerids.md)
      + [setCustomerIDs](mcvid-library/mcvid-get-set/mcvid-setcustomerids.md)
      + [getMarketingCloudVisitorID](mcvid-library/mcvid-get-set/mcvid-getmcvid.md)
      + [getLocationHint](mcvid-library/mcvid-get-set/mcvid-getlocationhint.md)
      + [getVisitorValues](mcvid-library/mcvid-get-set/mcvid-getvisitorvalues.md)
      + [isClientSideMarketingCloudVisitorID](mcvid-library/mcvid-get-set/mcvid-client-side-id.md)
      + [resetState](mcvid-library/mcvid-get-set/mcvid-resetstate.md)
+ リファレンス {#reference}
   + [リファレンス概要](mcvid-reference/mcvid-reference.md)
   + Analytics リファレンス {#analytics-reference}
      + [Analyticsリファレンス概要](mcvid-reference/mcvid-analytics-reference/mcvid-analytics-reference.md)
      + [Analytics および Experience Cloud ID の設定](mcvid-reference/mcvid-analytics-reference/mcvid-analytics-ids.md)
      + [Analytics ID の操作の順序](mcvid-reference/mcvid-analytics-reference/mcvid-analytics-order-of-operations.md)
      + [Experience Cloud ID サービス移行の判断ポイント](mcvid-reference/mcvid-analytics-reference/mcvid-migration-decisions.md)
      + [Experience Cloud ID サービスの移行シナリオ](mcvid-reference/mcvid-analytics-reference/mcvid-migration-scenarios.md)
      + [Analytics と Experience Cloud ID のリクエスト](mcvid-reference/mcvid-analytics-reference/mcvid-legacy-analytics.md)
      + [データ収集 CNAME およびクロスドメイントラッキング](mcvid-reference/mcvid-analytics-reference/mcvid-cname.md)
      + [JavaScript を利用したサーバー側実装](mcvid-reference/mcvid-analytics-reference/mcvid-server-side.md)
      + [ID サービスの猶予期間](mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md)   
   + [コンテンツセキュリティポリシーおよび Experience Cloud ID サービス](mcvid-reference/mcvid-csp.md)
   + [Experience Cloud ID サービスでの COPPA のサポート](mcvid-reference/mcvid-coppa.md)
   + [Experience Cloud ID サービスでの CORS のサポート](mcvid-reference/mcvid-cors.md)
   + [顧客 ID と認証状態](mcvid-reference/mcvid-authenticated-state.md)
   + [Safari ITP世界のECIDライブラリメソッド](mcvid-reference/ecid-library-methods.md)
   + [AMCV Cookie または ID サービスからの地域およびユーザー ID の取得](mcvid-reference/mcvid-regions.md)
   + [Experience Cloud ID サービスの要件](mcvid-reference/mcvid-requirements.md)
   + [ビデオハートビートと Experience Cloud ID サービス](mcvid-reference/mcvid-heartbeat.md)
   + [Data Workbench と Experience Cloud ID サービス](mcvid-reference/mcvid-dwb.md)
+ よくある質問（FAQ） {#faqs}
   + [FAQの概要](mcvid-faq-intro/mcvid-faq-intro.md)
   + [ID サービス FAQ](mcvid-faq-intro/mcvid-faq.md)
   + [Analytics と ID サービスに関する FAQ](mcvid-faq-intro/mcvid-analytics-faq.md)
   + [他の Experience Cloud ソリューションに関する FAQ](mcvid-faq-intro/mcvid-other-faq.md)
+ IDサービスのリリースノート {#release-notes}
   + [2019 年リリースノート](mcvid-release-notes/mcvid-release-notes.md)
   + [2018 年リリースノート](mcvid-release-notes/mcvid-notes-2018.md)
   + [2017 年リリースノート](mcvid-release-notes/mcvid-notes-2017.md)
   + [2016 年リリースノート](mcvid-release-notes/mcvid-notes-2016.md)
   + [2015 年リリースノート](mcvid-release-notes/mcvid-notes-2015.md)
