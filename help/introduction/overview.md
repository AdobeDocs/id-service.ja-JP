---
description: Adobe Experience Cloud における Experience Cloud Identity Service の役割です。
seo-description: Experience Cloud ID サービス（以前の訪問者 ID サービスまたは Marketing Cloud ID サービス）を使用すると、顧客属性やオーディエンスなど、Experience Cloud サービス向けの共通識別フレームワークを有効にします。
seo-title: Experience Cloud ID サービスの概要
title: Experience Cloud ID サービスの概要
translation-type: tm+mt
source-git-commit: 98b72f87b188debd6a5f6b86822c3f714647de61
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 76%

---


# Experience Cloud ID サービスの概要

[!UICONTROL Experience Cloud ID サービス]は、Experience Platform ID サービスにおける Experience Cloud コアサービス（顧客属性やオーディエンスなど）ソリューションのための共通の識別フレームワークです

>[!NOTE]
>
> ECID、Marketing Cloud ID サービス（MID）、訪問者 ID サービスなど、略語や以前の名前で ID サービスを表す場合があります。これらは、[!UICONTROL Experience Cloud ID サービス]を表しています。また、[!UICONTROL Experience Platform ID サービス]を目にすることもあります。これらの違いをまとめると次のようになります。

* [!UICONTROL Experience Platform ID サービス]：ID をリンクさせるサービス。ユーザーベースのエクスペリエンス管理を実現するための、デバイスリンクサービスです。
* [!UICONTROL Experience Cloud ID サービス]（ECID）：サイト訪問者に割り当てられた一意の永続的 ID。Platform ID サービスで使用できる特定のエンティティです。

組織が ID サービスを実装している場合、この ID を使用すれば、異なる Experience Cloud ソリューション内で、同じサイト訪問者と彼らのデータを識別できます。

![](assets/ecid-new.png)

また、IDサービスは、様々なソリューション固有のID（例：Analytics AID）を置き換えることができます。 また、[顧客IDと認証状態](/help/reference/authenticated-state.md)機能を使用して、IDサービスを使用して独自の顧客IDをExperience Cloudに渡すことができます。 ただし、IDサービスは、既に登録済みのソリューションとのみ機能します。 登録していない製品は、他の製品にアクセスできません。

いずれは、ID サービスは、多くの現在および将来の Experience Cloud 機能、強化、サービスにとって不可欠な要素になります。現在、ID サービスは、[Analytics](http://www.adobe.com/jp/marketing-cloud/web-analytics.html)、[Audience Manager](http://www.adobe.com/jp/marketing-cloud/data-management-platform.html) および [Target](http://www.adobe.com/jp/marketing-cloud/testing-targeting.html) をサポートしています。さらに、Adobe Experience Cloud Device Co-op に参加する場合に必要です。ID サービスを実装していない場合、今が移行戦略を検討し始めるチャンスです。ID サービスの重要性と役割について詳しくは、[なぜ新しい Experience Cloud Identity Service に注目すべきか](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/)/を参照してください。

## 機能の概要

要約すると、IDサービスは次のようになります。

* プロファイルとIDのリンクに使用できる共通キーまたはIDを作成します。
* 複数のソリューションにわたってデバイスを一意に識別します。
* 同じドメインでトラッキングを確実に行うように、顧客のドメインにファーストパーティCookieを設定します。 詳しくは、[cookieとExperience CloudIDサービス](https://docs.adobe.com/content/help/ja-JP/id-service/using/intro/cookies.html)のドキュメントを参照してください。
* エイリアス と ID マッピングを Experience Cloud の顧客とパートナーから受け取る。
* Experience Cloud 内の ID 同期を管理する。
* 広告技術エコシステム全体にわたり様々なサードパーティとの ID 同期をサポートする。

## IDサービスの要件

IDサービスを使用する前に、ソリューションおよび他のAdobeコードライブラリが[特定の要件](/help/reference/requirements.md)を満たしている必要があります。

* [Cookie と Experience Cloud Identity Service](cookies.md)：ID サービスは組織 ID、Experience Cloud AMCV Cookie および demdex Cookie を使用して、サイト訪問者固有の永続的な識別子を作成して保存します。これらの Cookie により、ID サービスでは異なるドメインをまたいで訪問者を追跡できるようになり、異なる Experience Cloud ソリューション間でデータの共有が可能になります。
* [Experience Cloud Identity Service による ID のリクエスト方法と設定方法](id-request.md)：ID リクエストと応答プロセスの概要です。個々のサイト、異なる複数のサイトおよびそれぞれ独自の組織 ID を持つ異なる Experience Cloud ユーザーによって管理されるサイトに対する ID の割り当て例を示しています。
* [ID 同期と一致率について](match-rates.md)：Adobe Media Manager および ID サービスを含む、ID 同期プロセスと Experience Cloud Identity Service の一致率の概要です。
