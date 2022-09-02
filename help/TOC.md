---
cloud: platform-cloud
audience: end-user
user-guide-title: Experience Cloud ID サービスのヘルプ
breadcrumb-title: ID サービスガイド
user-guide-description: ID サービスは、Experience Cloud のすべてのソリューションで訪問者を識別する永続的な汎用 ID を提供します。このサービスを、Analytics、Audience Manager、Target などのサービスや、その他の Experience Cloud のソリューションまたは機能の ID 生成コードの代わりに使用できます。
user-guide-url: /content/help/en/id-service/using/home.html
source-git-commit: 953a4932e581a7a0019bec354201be4bc39f8b6b
workflow-type: ht
source-wordcount: '398'
ht-degree: 100%

---


# Experience Cloud ID サービスのヘルプ {#using}

+ [ID サービスのヘルプ](home.md)
+ 概要 {#intro}
   + [概要](introduction/overview.md)
   + [ID サービスについて](introduction/about-id-service.md)
   + [Cookie と ID サービス](introduction/cookies.md)
   + [ID サービスによる ID のリクエスト方法と設定方法](introduction/id-request.md)
   + [同期と一致率について](introduction/match-rates.md)
+ 実装 {#implementation}
   + [実装方法](implementation-guides/implementation-methods.md)
   + [実装ガイド](implementation-guides/implementation-guides.md)
   + [Experience Platform タグを使用した実装](implementation-guides/ecid-implement-with-launch.md)
   + [Analytics の実装](implementation-guides/setup-analytics.md)
   + [Target への実装](implementation-guides/setup-target.md)
   + [Analytics および Audience Manager への実装](implementation-guides/setup-aam-analytics.md)
   + [Analytics、Audience Manager および Target への実装](implementation-guides/setup-aam-analytics-target.md)
   + [A4T での ID サービスの使用と Target のサーバーサイド実装](implementation-guides/ecid-a4t-target.md)
   + [ID サービスとの直接統合](implementation-guides/direct-integration.md)
   + [直接統合のユースケース](implementation-guides/direct-integration-examples.md)
   + [ID サービスのテストと検証](implementation-guides/test-verify.md)
   + オプトインサービス {#opt-in-service}
      + [オプトインサービスの概要](implementation-guides/opt-in-service/optin-overview.md)
      + [オプトインサービスの設定](implementation-guides/opt-in-service/getting-started.md)
      + [オプトインサービスの検証](implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [Experience Platform Launch を使用したオプトインの設定](implementation-guides/opt-in-service/launch.md)
      + [DTM を使用したオプトインの設定](implementation-guides/opt-in-service/optin-dtm.md)
      + [ユーザーの同意に基づいて Experience Cloud アクティビティを制御する](implementation-guides/opt-in-service/use-opt-in-to-control-experience-cloud-activities-based-on-user-consent.md)
      + [オプトインのユースケース](implementation-guides/opt-in-service/use-cases.md)
      + [オプトインのリファレンス](implementation-guides/opt-in-service/api.md)
      + [IAB フレームワークでのオプトインサービスの使用](implementation-guides/opt-in-service/iab.md)
+ ID Service API {#id-service-api}
   + [ID Service API の概要](library/library.md)
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
   + Analytics リファレンス {#analytics-reference}
      + [Analytics リファレンスの概要](reference/analytics-reference/analytics-reference.md)
      + [CNAME 実装の概要](reference/analytics-reference/cname.md)
      + [Analytics および Experience Cloud ID の設定](reference/analytics-reference/analytics-ids.md)
      + [Analytics ID の操作の順序](reference/analytics-reference/analytics-order-of-operations.md)
      + [ID サービス移行の決定ポイント](reference/analytics-reference/migration-decisions.md)
      + [ID サービスの移行シナリオ](reference/analytics-reference/migration-scenarios.md)
      + [Analytics および ID のリクエスト](reference/analytics-reference/legacy-analytics.md)
      + [JavaScript を利用したサーバー側実装](reference/analytics-reference/server-side.md)
      + [ID サービスの猶予期間](reference/analytics-reference/grace-period.md)
   + [Google Chrome SameSite のラベル付けの変更](reference/chrome-samesite-labelling.md)
   + [コンテンツセキュリティポリシーおよび ID サービス](reference/csp.md)
   + [ID サービスでの COPPA のサポート](reference/coppa.md)
   + [ID サービスでの CORS のサポート](reference/cors.md)
   + [顧客 ID と認証状態](reference/authenticated-state.md)
   + [Safari ITP の世界における ECID ライブラリのメソッド](reference/ecid-library-methods.md)
   + [ユニーク訪問者数の識別](reference/unique-vis-method.md)
   + [AMCV Cookie または ID サービスからの地域 ID およびユーザー ID の取得](reference/regions.md)
   + [ID サービスの要件](reference/requirements.md)
   + [ビデオのハートビートと ID サービス](reference/heartbeat.md)
   + [Data Workbench と ID サービス](reference/dwb.md)
   + [setCustomerIDs の SHA256 ハッシュサポート](reference/hashing-support.md)
+ よくある質問（FAQ） {#faqs}
   + [FAQ の概要](faq-intro/faq-intro.md)
   + [ID サービスに関する FAQ](faq-intro/faq.md)
   + [Analytics と ID サービスに関する FAQ](faq-intro/analytics-faq.md)
   + [他の Experience Cloud ソリューションに関する FAQ](faq-intro/other-faq.md)
+ ID サービスのリリースノート{#release-notes}
   + [2020 年リリースノート](release-notes/release-notes.md)
   + [2019 年リリースノート](release-notes/notes-2019.md)
   + [2018 年リリースノート](release-notes/notes-2018.md)
   + [2017 年リリースノート](release-notes/notes-2017.md)
   + [2016 年リリースノート](release-notes/notes-2016.md)
   + [2015 年リリースノート](release-notes/notes-2015.md)
+ [TOC に非表示の分析テスト](analytics-test-file-hidetoc.md)
