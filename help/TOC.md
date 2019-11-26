---
cloud: platform-cloud
product: ID Service
audience: end-user
user-guide-title: Experience Cloud Identity Service Help
user-guide-url: /content/help/en/id-service/using/home.html
translation-type: ht
source-git-commit: cb75ac6a9d7a5a001fcb0a1d9d978d3845a4e829

---


# Experience Cloud Identity Service ヘルプ {#using}

+ [ID サービスヘルプ](home.md)
+ 概要 {#intro}
   + [概要](introduction/overview.md)
   + [ID サービスについて](introduction/about-id-service.md)
   + [Cookie と ID サービス](introduction/cookies.md)
   + [ ID サービスによる ID のリクエスト方法と設定方法](introduction/id-request.md)
   + [同期と一致率について](introduction/match-rates.md)
+ 実装 {#implementation}
   + [実装方法](implementation-guides/implementation-methods.md)
   + [実装ガイド](implementation-guides/implementation-guides.md)
   + [Experience Platform Launch を使用した実装](implementation-guides/ecid-implement-with-launch.md)
   + [DTM を使用した実装](implementation-guides/standard.md)
   + [Analytics の実装](implementation-guides/setup-analytics.md)
   + [Target の実装](implementation-guides/setup-target.md)
   + [Analytics および Audience Manager の実装](implementation-guides/setup-aam-analytics.md)
   + [Analytics、Audience Manager および Target の実装](implementation-guides/setup-aam-analytics-target.md)
   + [Target のサーバー側実装を使用する A4T での ID サービスの使用](implementation-guides/ecid-a4t-target.md)
   + [ID サービスとの直接統合](implementation-guides/direct-integration.md)
   + [直接統合の使用例](implementation-guides/direct-integration-examples.md)
   + [ ID サービスのテストと検証](implementation-guides/test-verify.md)
   + オプトインサービス {#opt-in-service}
      + [オプトインサービスの概要](implementation-guides/opt-in-service/optin-overview.md)
      + [オプトインサービスの設定](implementation-guides/opt-in-service/getting-started.md)
      + [オプトインサービスの検証](implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [Experience Platform Launch を使用したオプトインの設定](implementation-guides/opt-in-service/launch.md)
      + [DTM を使用したオプトインの設定](implementation-guides/opt-in-service/optin-dtm.md)
      + [オプトインの使用例](implementation-guides/opt-in-service/use-cases.md)
      + [オプトインリファレンス](implementation-guides/opt-in-service/api.md)
      + [（ベータ）IAB フレームワークを使用したオプトインサービスの使用](implementation-guides/opt-in-service/iab.md)
+ ID サービスの API {#id-service-api}
   + [ID サービス API の概要](library/library.md)
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
   + [Reference の概要](reference/reference.md)
   + Analytics リファレンス {#analytics-reference}
      + [Analytics リファレンスの概要](reference/analytics-reference/analytics-reference.md)
      + [Analytics および Experience Cloud ID の設定](reference/analytics-reference/analytics-ids.md)
      + [Analytics ID の操作の順序](reference/analytics-reference/analytics-order-of-operations.md)
      + [ID サービス移行の判断ポイント](reference/analytics-reference/migration-decisions.md)
      + [ID サービスの移行シナリオ](reference/analytics-reference/migration-scenarios.md)
      + [Analytics および ID のリクエスト](reference/analytics-reference/legacy-analytics.md)
      + [データ収集 CNAME およびクロスドメイントラッキング](reference/analytics-reference/cname.md)
      + [JavaScript を利用したサーバー側実装](reference/analytics-reference/server-side.md)
      + [ID サービスの猶予期間](reference/analytics-reference/grace-period.md)
   + [コンテンツセキュリティポリシーおよび ID サービス](reference/csp.md)
   + [ID サービスでの COPPA のサポート](reference/coppa.md)
   + [ID サービスでの CORS のサポート](reference/cors.md)
   + [顧客 ID と認証状態](reference/authenticated-state.md)
   + [Safari ITP での ECID ライブラリの手法](reference/ecid-library-methods.md)
   + [AMCV Cookie または ID サービスからの地域およびユーザー ID の取得](reference/regions.md)
   + [ID サービスの要件](reference/requirements.md)
   + [ビデオハートビートと ID サービス](reference/heartbeat.md)
   + [Data Workbench と ID サービス](reference/dwb.md)
   + [setCustomerIDs の SHA256 ハッシュサポート](reference/hashing-support.md)
+ よくある質問（FAQ） {#faqs}
   + [FAQ の概要](faq-intro/faq-intro.md)
   + [ID サービス FAQ](faq-intro/faq.md)
   + [Analytics と ID サービスに関する FAQ](faq-intro/analytics-faq.md)
   + [他の Experience Cloud ソリューションに関する FAQ](faq-intro/other-faq.md)
+ ID サービスのリリースノート {#release-notes}
   + [2019 年リリースノート](release-notes/release-notes.md)
   + [2018 年リリースノート](release-notes/notes-2018.md)
   + [2017 年リリースノート](release-notes/notes-2017.md)
   + [2016 年リリースノート](release-notes/notes-2016.md)
   + [2015 年リリースノート](release-notes/notes-2015.md)
