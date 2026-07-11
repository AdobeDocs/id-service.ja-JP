---
description: Adobe Visitor ID サービスは、CX Enterprise アプリケーションとサービスの共通ID フレームワークを有効にします。 これは、ECIDと呼ばれる一意の永続的なIDをサイト訪問者に割り当てることで機能します。
keywords: 訪問者ID サービス；ECID
title: Adobe Visitor ID Service
exl-id: fe1368db-06ca-4c79-b655-b7064e316d74
TQID: https://experienceleague.adobe.com/xzEgzuN2NnyOnhCPocQikOXHFRU6zmLWLGdrJL4C3GM
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 433
ht-degree: 30%

---

# Adobe Visitor ID Service {#experience-cloud-id-service}

>[!BEGINSHADEBOX]

訪問者ID サービスは、[Experience Platform ID サービス &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=ja)の&#x200B;**not**&#x200B;です。 Visitor ID サービスは、このガイドで説明されている`VisitorAPI.js` JavaScript ライブラリで、Adobe Analytics、Audience ManagerおよびTargetのECIDを設定します。 デバイスやシステムをまたいでIDを統合された顧客プロファイルに解決するAdobe Experience Platform サービスを探している場合は、代わりに[Experience Platform ID サービスの概要](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=ja)を参照してください。

>[!ENDSHADEBOX]

Adobe Visitor ID サービスは、CX Enterprise アプリケーションとサービスの共通ID フレームワークを有効にします。 これは、ECIDと呼ばれる一意の永続的なIDをサイト訪問者に割り当てることで機能します。

## ID のメインエンティティについて

アドビがどのように訪問者を一意に識別し、ID 情報を解決しているかを深く理解するには、以下の分類を参照してください。

* **訪問者ID サービス**：訪問者ID サービス **は、ECID**&#x200B;の設定を担当します。 詳しくは、[訪問者ID サービスの概要](./introduction/overview.md)を参照してください。
* **ECID**: ECIDは、Adobe Experience PlatformおよびAdobe CX Enterprise アプリケーション全体で人とデバイスを識別するために使用される共有ID名前空間です。 ECID について詳しくは、[ECID の概要](https://experienceleague.adobe.com/ja/docs/experience-platform/identity/features/ecid)を参照してください。
* **Experience Platform ID サービス**：Experience Platform ID サービスは、デバイスやシステム間で ID を橋渡しすることで、顧客とその行動を包括的に把握できるようにします。 詳しくは、[Experience Platform ID サービスの概要](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=ja)を参照してください。

## 基本を学ぶ

* [訪問者ID サービスの概要](introduction/overview.md)：訪問者ID サービスの機能とCX Enterpriseへの組み込み方法について説明します。
* [訪問者ID サービスの要件](reference/requirements.md)：訪問者ID サービスを実装する前に、ソリューションとコードライブラリが前提条件を満たしていることを確認してください。
* [実装方法](implementation-guides/implementation-methods.md): [&#x200B; タグ &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=ja)を使用した標準実装と非標準の直接統合方法を比較します。

## ドキュメントの参照

**実装**

* [実装ガイド](implementation-guides/implementation-guides.md)
* [訪問者ID サービスとの直接統合](implementation-guides/direct-integration.md)
* [オプトインサービスの概要](implementation-guides/opt-in-service/optin-overview.md)
* [訪問者ID サービスのテストと検証](implementation-guides/test-verify.md)

**API リファレンス**

* [訪問者ID サービス APIの概要](library/library.md)
* [getVisitorValues](library/get-set/getvisitorvalues.md)
* [idSyncContainerID](library/function-vars/idsyncontainerid.md)

**よくある質問（FAQ）**

* [訪問者ID サービスに関するFAQ](faq-intro/faq.md)
* [他のCX エンタープライズソリューションに関するFAQ](faq-intro/other-faq.md)

## その他のリソース

* GitHub上の[ECID JavaScript ライブラリ リリース &#x200B;](https://github.com/Adobe-Marketing-Cloud/id-service/releases)
* [訪問者ID サービスのリリースノート](release-notes/notes-2022.md)
* [Adobeプライバシーセンター](http://www.adobe.com/jp/privacy.html)
* [Adobe CX Enterpriseのドキュメント](https://experienceleague.adobe.com/docs/home.html?lang=ja)

