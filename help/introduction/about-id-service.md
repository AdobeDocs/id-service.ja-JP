---
description: Adobe Experience Cloud での Experience Cloud Identity Service の役割です。
keywords: ID Service
seo-description: Adobe Experience Cloud での Experience Cloud Identity Service の役割です。
seo-title: ID サービスについて
title: 概要
uuid: c52d6155-00a0-4fc5-9d8e-5ce00b8d01e6
translation-type: tm+mt
source-git-commit: ec67177fc6491e4c8cea835d198574c9fdb4b01f
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 69%

---


# ID サービスについて {#aboutidservice}

Adobe Experience Cloud での Experience Cloud Identity Service の役割です。

<!--
mcvid-functionality.xml
-->

## Experience Cloud Identity Service：コアサービスの基礎的要素 {#section-2de0eb1d65664e92a4d8bbb167b84bde}

Experience Cloud Identity Service は、Experience Cloud コアサービス、ソリューション、顧客属性、オーディエンスのための、共通の識別フレームワークです。ID サービスは、サイト訪問者に一意の永続的な ID を割り当てることで機能します。組織が ID サービスを実装している場合、この ID を使用すれば、異なる Experience Cloud ソリューション内で、同じサイト訪問者と彼らのデータを識別できます。

![](assets/ecid-new.png)

また、IDサービスは、様々なソリューション固有のID（例：Analytics AID）を置き換えることができます。 And, through the [Customer IDs and Authentication States](../reference/authenticated-state.md) functionality, the ID service lets you pass in your own customer IDs to the [!DNL Experience Cloud]. ただし、IDサービスは、既に登録済みのソリューションとのみ機能します。 登録していない製品は、他の製品にアクセスできません。

いずれは、ID サービスは、多くの現在および将来の [!DNL Experience Cloud] 機能、強化、サービスにとって不可欠な要素になります。現在、ID サービスは、[Analytics](http://www.adobe.com/jp/marketing-cloud/web-analytics.html)、[Audience Manager](http://www.adobe.com/jp/marketing-cloud/data-management-platform.html) および [Target](http://www.adobe.com/jp/marketing-cloud/testing-targeting.html) をサポートしています。さらに、[!DNL Adobe Experience Cloud] Device Co-op に参加する場合に必要です。ID サービスを実装していない場合、今が移行戦略を検討し始めるチャンスです。ID サービスの重要性と役割について詳しくは、[なぜ新しい Experience Cloud Identity Service に注目すべきか](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/)/を参照してください。

## 機能の概要 {#section-96555473455c4bf8924c2d56ff4f3255}

要約すると、IDサービスは次のようになります。

* プロファイルとIDのリンクに使用できる共通キーまたはIDを作成します。
* 複数のソリューションにわたってデバイスを一意に識別します。
* 同じドメインでトラッキングを確実に行うように、顧客のドメインにファーストパーティCookieを設定します。 [Experience Cloud](../introduction/cookies.md) に関する説明を参照してください。
* エイリアス と ID マッピングを [!DNL Experience Cloud] の顧客とパートナーから受け取る。
* [!DNL Experience Cloud] 内の ID 同期を管理する。
* 広告技術エコシステム全体にわたり様々なサードパーティとの ID 同期をサポートする。
