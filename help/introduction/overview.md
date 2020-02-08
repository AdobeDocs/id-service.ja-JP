---
description: Adobe Experience cloudでのExperience Cloud IDサービスの役割。
seo-description: Experience Cloud IDサービス（旧称、訪問者IDサービスまたはMarketing Cloud IDサービス）を使用すると、顧客属性やオーディエンスなどのExperience cloudサービスの共通の識別フレームワークを有効にできます。
seo-title: Experience Cloud IDサービスの概要
title: Experience Cloud IDサービスの概要
translation-type: tm+mt
source-git-commit: 6342ea02c74e6d1c96f987c5f2620246602ce6c5

---


# Experience Cloud IDサービスの概要

The [!UICONTROL Experience Cloud Identity Service] enables the common identification framework for Experience Cloud Core Services (such as customer attributes and audiences) solutions in the Experience Platform Identity Service.

>[!NOTE]
>
> IDサービスへの参照は、略語、またはECID、Marketing Cloud IDサービス(MID)、訪問者IDサービスなどの旧称として表示される場合があります。 これらは、 [!UICONTROL Experience Cloud IDサービスを参照します]。 また、 [!UICONTROL Experience Platform Identity Serviceも表示されます]。 明確にするには：

* [!UICONTROL エクスペリエンスプラットフォームIDサービス]:IDをリンクするサービス。 これは、ユーザーベースのエクスペリエンス管理のためのデバイスリンクサービスです。
* [!UICONTROL Experience Cloud IDサービス] (ECID):サイト訪問者に割り当てられた一意の永続的なID。 これは、プラットフォームIDサービスで使用できる特定のエンティティです。

組織が ID サービスを実装する場合、この ID を使用することで、同じサイト訪問者およびそのデータを様々な Experience Cloud ソリューションで識別できます。

![](assets/ecid.png)

また、この ID サービスは、様々なソリューション専用 ID（例：Analytics AID）を置き換えることができます。そして、[顧客 ID と認証状態](/help/reference/authenticated-state.md)機能を使用すると、ID サービスを通じて顧客 ID を Experience Cloud に渡すことが可能になります。ただし、ID サービスは、既に登録されたソリューションのみと連携することに注意してください。登録していない製品には ID サービスからアクセスできません。

いずれは、ID サービスは、多くの現在および将来の Experience Cloud 機能、強化、サービスにとって不可欠な要素になります。現在、ID サービスは、[Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html)、[Audience Manager](http://www.adobe.com/marketing-cloud/data-management-platform.html) および [Target](http://www.adobe.com/marketing-cloud/testing-targeting.html) をサポートしています。さらに、Adobe Experience Cloud Device Co-op に参加する場合に必要です。ID サービスを実装していない場合、今が移行戦略を検討し始めるチャンスです。ID サービスの重要性と役割について詳しくは、[なぜ新しい Experience Cloud Identity Service に注目すべきか](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/)/を参照してください。

## 機能の概要

まとめると、ID サービスには以下の機能があります。

* プロファイルと ID をリンクするために使用できる共通キーまたは ID を作成する。
* 複数のソリューションをまたいで一意にデバイスを識別する。
* 顧客のドメインにファーストパーティ Cookie を設定し、同ドメインでトラッキングをおこなえるようにする。詳しくは、 cookieおよびExperience Cloud IDサービス [に関するドキュメントを参照](https://docs.adobe.com/content/help/en/id-service/using/intro/cookies.html) してください。
* エイリアス と ID マッピングを Experience Cloud の顧客とパートナーから受け取る。
* Experience Cloud 内の ID 同期を管理する。
* 広告技術エコシステム全体にわたり様々なサードパーティとの ID 同期をサポートする。

## ID サービスの要件

ID サービスを使用し始める前に、ソリューションおよびその他の Adobe コードライブラリは、[要件](/help/reference/requirements.md)を満たす必要があります。

* [Cookie と Experience Cloud Identity Service](cookies.md)：ID サービスは組織 ID、Experience Cloud AMCV Cookie および demdex Cookie を使用して、サイト訪問者固有の永続的な識別子を作成して保存します。これらの Cookie により、ID サービスでは異なるドメインをまたいで訪問者を追跡できるようになり、異なる Experience Cloud ソリューション間でデータの共有が可能になります。
* [Experience Cloud Identity Service による ID のリクエスト方法と設定方法](id-request.md)：ID リクエストと応答プロセスの概要です。個々のサイト、異なる複数のサイトおよびそれぞれ独自の組織 ID を持つ異なる Experience Cloud ユーザーによって管理されるサイトに対する ID の割り当て例を示しています。
* [ID 同期と一致率について](match-rates.md)：Adobe Media Manager および ID サービスを含む、ID 同期プロセスと Experience Cloud Identity Service の一致率の概要です。
