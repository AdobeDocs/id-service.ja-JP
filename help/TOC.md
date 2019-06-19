---
cloud: platform- cloud
product: IDサービス
audience: エンドユーザー
user-guide-title: Experience Platform IDサービスヘルプ
user-guide-url: /content/help/en/id-service/using/home.html
translation-type: tm+mt
source-git-commit: 1af38efa5e85c09548a6dee6c9c550900f90a8ed

---


# IDサービスヘルプ {#using}

+ [IDサービスヘルプ](home.md)
+ 概要 {#intro}
   + [概要](introduction/overview.md)
   + [IDサービスについて](introduction/about-id-service.md)
   + [CookieとIDサービス](introduction/cookies.md)
   + [IDサービスによるIDの要求と設定](introduction/id-request.md)
   + [同期と一致率について](introduction/match-rates.md)
+ 導入ガイド {#implementation-guides}
   + [導入ガイド](implementation-guides/implementation-guides.md)
   + [実装方法](implementation-guides/implementation-methods.md)
   + [Launch を使用した実装](implementation-guides/ecid-implement-with-launch.md)
   + [DTM を使用した実装](implementation-guides/standard.md)
   + [Analytics用に実装](implementation-guides/setup-analytics.md)
   + [Target用の実装](implementation-guides/setup-target.md)
   + [AnalyticsおよびAudience Managerの実装](implementation-guides/setup-aam-analytics.md)
   + [Analytics、Audience ManagerおよびTargetの実装](implementation-guides/setup-aam-analytics-target.md)
   + [A4Tとサーバー側の実装によるIDサービスの使用](implementation-guides/ecid-a4t-target.md)
   + [IDサービスとの直接統合](implementation-guides/direct-integration.md)
   + [直接統合の使用例](implementation-guides/direct-integration-examples.md)
   + [IDサービスのテストと検証](implementation-guides/test-verify.md)
   + オプトインドキュメント {#opt-in-service}
      + [オプトインサービスの概要](implementation-guides/opt-in-service/optin-overview.md)
      + [オプトインサービスの設定](implementation-guides/opt-in-service/getting-started.md)
      + [オプトインサービスの検証](implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [Launch を使用したオプトインの設定](implementation-guides/opt-in-service/launch.md)
      + [DTM を使用したオプトインの設定](implementation-guides/opt-in-service/optin-dtm.md)
      + [オプトインの使用例](implementation-guides/opt-in-service/use-cases.md)
      + [オプトインリファレンス](implementation-guides/opt-in-service/api.md)
      + [（ベータ） IABフレームワークを使用したオプトインサービスの使用](implementation-guides/opt-in-service/iab.md)
+ IDサービスAPI {#id-service-api}
   + [IDサービスAPIの概要](library/library.md)
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
      + [isCoopSafe](library/function-vars/coopsafe.md)
      + [loadTimeout](library/function-vars/loadtimeout.md)
      + [overwriteCrossDomainMCIDAndAID](library/function-vars/overwrite-visitor-id.md)
      + [resetBeforeVersion](library/function-vars/resetbeforeversion.md)
      + [sdidParamExpiry](library/function-vars/sdidparamexpiry.md)
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
   + [リファレンス概要](reference/reference.md)
   + Analytics リファレンス {#analytics-reference}
      + [Analyticsリファレンス概要](reference/analytics-reference/analytics-reference.md)
      + [AnalyticsとIDの設定](reference/analytics-reference/analytics-ids.md)
      + [Analytics ID の操作の順序](reference/analytics-reference/analytics-order-of-operations.md)
      + [IDサービス移行の判断ポイント](reference/analytics-reference/migration-decisions.md)
      + [IDサービスの移行シナリオ](reference/analytics-reference/migration-scenarios.md)
      + [AnalyticsおよびIDリクエスト](reference/analytics-reference/legacy-analytics.md)
      + [データ収集 CNAME およびクロスドメイントラッキング](reference/analytics-reference/cname.md)
      + [JavaScript を利用したサーバー側実装](reference/analytics-reference/server-side.md)
      + [IDサービスの猶予期間](reference/analytics-reference/grace-period.md)
   + [コンテンツセキュリティポリシーとIDサービス](reference/csp.md)
   + [IDサービスでのCOPPAのサポート](reference/coppa.md)
   + [IDサービスでのCORSのサポート](reference/cors.md)
   + [顧客 ID と認証状態](reference/authenticated-state.md)
   + [Safari ITP世界のECIDライブラリメソッド](reference/ecid-library-methods.md)
   + [AMCV cookieまたはIDサービスからの地域およびユーザーIDの取得](reference/regions.md)
   + [IDサービスの要件](reference/requirements.md)
   + [ビデオハートビートとIDサービス](reference/heartbeat.md)
   + [Data WorkbenchとIDサービス](reference/dwb.md)
+ よくある質問（FAQ） {#faqs}
   + [FAQの概要](faq-intro/faq-intro.md)
   + [IDサービスFAQ](faq-intro/faq.md)
   + [AnalyticsおよびIDサービスFAQ](faq-intro/analytics-faq.md)
   + [他の Experience Cloud ソリューションに関する FAQ](faq-intro/other-faq.md)
+ IDサービスのリリースノート {#release-notes}
   + [2019 年リリースノート](release-notes/release-notes.md)
   + [2018 年リリースノート](release-notes/notes-2018.md)
   + [2017 年リリースノート](release-notes/notes-2017.md)
   + [2016 年リリースノート](release-notes/notes-2016.md)
   + [2015 年リリースノート](release-notes/notes-2015.md)
