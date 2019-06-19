---
description: Adobe Experience CloudのExperience Platform IDサービスの役割。
keywords: ID サービス
seo-description: Adobe Experience CloudのExperience Platform IDサービスの役割。
seo-title: IDサービスについて
title: 概要
uuid: c52d6155-00a0-4fc5-9d8e-5ce00b8d01e6
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# IDサービスについて{#aboutidservice}

Adobe Experience CloudのExperience Platform IDサービスの役割。

<!--
mcvid-functionality.xml
-->

## Experience Platform IDサービス:コアサービスの基本要素 {#section-2de0eb1d65664e92a4d8bbb167b84bde}

Experience Platform IDサービスでは、Experience Cloudコアサービス、ソリューション、顧客属性およびPeopleコアサービスのオーディエンスに対して共通の識別フレームワークが有効になります。サイト訪問者に一意の永続的 ID を割り当てることで機能します。組織が ID サービスを実装する場合、この ID を使用することで、同じサイト訪問者およびそのデータを様々な Experience Cloud ソリューションで識別できます。

![](assets/ecid.png)

また、この ID サービスは、様々なソリューション専用 ID（例：Analytics AID）を置き換えることができます。そして、[顧客 ID と認証状態](../reference/authenticated-state.md)機能を使用すると、ID サービスを通じて顧客 ID を [!DNL Experience Cloud] に渡すことが可能になります。ただし、ID サービスは、既に登録されたソリューションのみと連携することに注意してください。登録していない製品には ID サービスからアクセスできません。

いずれは、ID サービスは、多くの現在および将来の [!DNL Experience Cloud] 機能、強化、サービスにとって不可欠な要素になります。現在、ID サービスは、[Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html)、[Audience Manager](http://www.adobe.com/marketing-cloud/data-management-platform.html) および [Target](http://www.adobe.com/marketing-cloud/testing-targeting.html) をサポートしています。さらに、[!DNL Adobe Experience Cloud] Device Co-op に参加する場合に必要です。ID サービスを実装していない場合、今が移行戦略を検討し始めるチャンスです。IDサービスの重要性と役割について詳しくは [、&quot;Experience Platform IDサービスの使用について」を参照](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/)してください。

## 機能概要 {#section-96555473455c4bf8924c2d56ff4f3255}

まとめると、ID サービスには以下の機能があります。

* プロファイルと ID をリンクするために使用できる共通キーまたは ID を作成する。
* 複数のソリューションをまたいで一意にデバイスを識別する。
* 顧客のドメインにファーストパーティ Cookie を設定し、同ドメインでトラッキングをおこなえるようにする。詳しくは、 [Experience Cloud](../introduction/cookies.md).
* エイリアス と ID マッピングを [!DNL Experience Cloud] の顧客とパートナーから受け取る。
* 内部でID同期を管理 [!DNL Experience Cloud]します。
* 広告技術エコシステム全体にわたり様々なサードパーティとの ID 同期をサポートする。
