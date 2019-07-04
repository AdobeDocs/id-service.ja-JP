---
description: Adobe Experience Cloud での Experience Cloud ID サービスの役割です。
keywords: ID サービス
seo-description: Adobe Experience Cloud での Experience Cloud ID サービスの役割です。
seo-title: ID サービスについて
title: 概要
uuid: c52d6155-00a0-4fc5-9d8e-5ce00b8d01e6
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# ID サービスについて{#aboutidservice}

Adobe Experience Cloud での Experience Cloud ID サービスの役割です。

<!--
mcvid-functionality.xml
-->

## Experience Cloud ID サービス：コアサービスの基礎的要素 {#section-2de0eb1d65664e92a4d8bbb167b84bde}

Experience Cloud ID サービスは、Experience Cloud コアサービス、ソリューション、顧客属性、People コアサービスのオーディエンスのための、共通の識別フレームワークです。サイト訪問者に一意の永続的 ID を割り当てることで機能します。組織が ID サービスを実装する場合、この ID を使用することで、同じサイト訪問者およびそのデータを様々な Experience Cloud ソリューションで識別できます。

![](assets/ecid.png)

また、この ID サービスは、様々なソリューション専用 ID（例：Analytics AID）を置き換えることができます。そして、[顧客 ID と認証状態](../mcvid-reference/mcvid-authenticated-state.md)機能を使用すると、ID サービスを通じて顧客 ID を [!DNL Experience Cloud] に渡すことが可能になります。ただし、ID サービスは、既に登録されたソリューションのみと連携することに注意してください。登録していない製品には ID サービスからアクセスできません。

いずれは、ID サービスは、多くの現在および将来の [!DNL Experience Cloud] 機能、強化、サービスにとって不可欠な要素になります。現在、ID サービスは [Analytics](http://www.adobe.com/jp/marketing-cloud/web-analytics.html)、[Audience Manager](http://www.adobe.com/jp/marketing-cloud/data-management-platform.html)、および [Target](http://www.adobe.com/jp/marketing-cloud/testing-targeting.html) をサポートしています。さらに、[!DNL Adobe Experience Cloud] Device Co-op に参加する場合に必要です。ID サービスを実装していない場合、今が移行戦略を検討し始めるチャンスです。ID サービスの重要性と役割について詳しくは、[なぜ新しい Experience Cloud ID サービスに注目すべきか](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/)を参照してください。

## 機能の概要 {#section-96555473455c4bf8924c2d56ff4f3255}

まとめると、ID サービスには以下の機能があります。

* プロファイルと ID をリンクするために使用できる共通キーまたは ID を作成する。
* 複数のソリューションをまたいで一意にデバイスを識別する。
* 顧客のドメインにファーストパーティ Cookie を設定し、同ドメインでトラッキングをおこなえるようにする。詳しくは、[Experience Cloud](../mcvid-introduction/mcvid-cookies.md) を参照してください。
* エイリアス と ID マッピングを [!DNL Experience Cloud] の顧客とパートナーから受け取る。
* [!DNL Experience Cloud] 内の ID 同期を管理する。
* 広告技術エコシステム全体にわたり様々なサードパーティとの ID 同期をサポートする。
