---
description: Adobe Experience Cloud における Experience Cloud Identity Service の役割です。
keywords: ID サービス
title: 概要
exl-id: d907e299-bde0-4b5f-8c16-867a4eaa8be1
source-git-commit: 2c87022baeb09a8767d0d9627bf2b607c51b2503
workflow-type: ht
source-wordcount: '310'
ht-degree: 100%

---

# ID サービスについて{#aboutidservice}

Adobe Experience Cloud における Experience Cloud Identity Service の役割です。

<!--
mcvid-functionality.xml
-->

## Experience Cloud Identity Service：コアサービスの基礎的要素 {#section-2de0eb1d65664e92a4d8bbb167b84bde}

Experience Cloud Identity Service は、Experience Cloud コアサービス、ソリューション、顧客属性、オーディエンスのための、共通の識別フレームワークです。ID サービスは、サイト訪問者に一意の永続的な ID を割り当てることで機能します。組織が ID サービスを実装している場合、この ID を使用すれば、異なる Experience Cloud ソリューション内で、同じサイト訪問者と彼らのデータを識別できます。

![](assets/ecid-new.png)

また、ID サービスは、ソリューション固有の様々な ID（例：Analytics AID）を置き換えることができます。[顧客 ID と認証状態](../reference/authenticated-state.md)機能を使用すると、ID サービスを通じて顧客 ID を [!DNL Experience Cloud] に渡すことが可能になります。ただし、ID サービスは、登録済みのソリューションに対してのみ機能します。 登録していない他の製品には、アクセスできません。

いずれは、ID サービスは、多くの現在および将来の [!DNL Experience Cloud] 機能、強化、サービスにとって不可欠な要素になります。現在、ID サービスは、[Analytics](http://www.adobe.com/jp/marketing-cloud/web-analytics.html)、[Audience Manager](http://www.adobe.com/jp/marketing-cloud/data-management-platform.html) および [Target](http://www.adobe.com/jp/marketing-cloud/testing-targeting.html) をサポートしています。さらに、[!DNL Adobe Experience Cloud] Device Co-op に参加する場合に必要です。ID サービスを実装していない場合、今が移行戦略を検討し始めるチャンスです。

## 機能の概要 {#section-96555473455c4bf8924c2d56ff4f3255}

要約すると、ID サービスの機能は次のとおりです。

* プロファイルと ID のリンクに使用できる共通キーまたは ID を作成します。
* 複数のソリューションにわたってデバイスを一意に識別します。
* 同じドメインでトラッキングを確実に行えるように、顧客のドメインにファーストパーティ Cookie を設定します。[Experience Cloud](../introduction/cookies.md) に関する説明を参照してください。
* エイリアス と ID マッピングを [!DNL Experience Cloud] の顧客とパートナーから受け取る。
* [!DNL Experience Cloud] 内の ID 同期を管理する。
* 広告技術エコシステム全体にわたり様々なサードパーティとの ID 同期をサポートする。
