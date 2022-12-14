---
description: Adobe Experience Cloud における Experience Cloud Identity Service の役割です。
title: Experience CloudID サービスの概要
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
source-git-commit: f7c25f5ebd0690c56c081422949eb34f1f277ae1
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 36%

---

# Experience CloudID サービスの概要

Experience CloudID サービスは、アプリケーションサービス用の共通の ID フレームワークをExperience Cloudにします。 Experience CloudID サービスを使用して、 [Experience CloudID (ECID)](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html).

ECID は、Adobe Experience PlatformおよびExperience Cloudアプリケーション全体で使用される共有 ID 名前空間で、訪問者の行動を追跡し、各デバイスに一意の識別子が割り当てられ、複数のセッション間で保持されます。

>[!TIP]
>
>Experience CloudID サービス、Experience PlatformID サービスおよび ECID は 3 つです **異なる** エンティティ。

Experience CloudID サービスは、様々なアプリケーション固有の ID を置き換え、 [顧客 ID と認証状態](/help/reference/authenticated-state.md) 機能を使用して、独自の顧客 ID をExperience Cloudに渡すことができます。

>[!NOTE]
>
>Experience CloudID サービスは、購読しているExperience Cloudアプリケーションサービスでのみ機能し、購読していない場合は、他のアプリケーションサービスへのアクセスを提供しません。

Experience CloudID サービスは、次のアプリケーションをサポートしています。

* [Adobe Analytics](https://business.adobe.com/products/analytics/web-analytics.html)
* [Audience Manager](https://business.adobe.com/products/audience-manager/adobe-audience-manager.html)
* [Adobe Target](https://business.adobe.com/products/target/adobe-target.html)

いずれは、ID サービスは、多くの現在および将来の Experience Cloud 機能、強化、サービスにとって不可欠な要素になります。現在、ID サービスは、[Analytics](http://www.adobe.com/jp/marketing-cloud/web-analytics.html)、[Audience Manager](http://www.adobe.com/jp/marketing-cloud/data-management-platform.html) および [Target](http://www.adobe.com/jp/marketing-cloud/testing-targeting.html) をサポートしています。ID サービスを実装していない場合、今が移行戦略を検討し始めるチャンスです。

## 機能の概要

要約すると、Experience CloudID サービスは次の点に役立ちます。

* 複数のアプリケーションをまたいで 1 台のデバイス上の訪問者を一意に識別します。
* 同じドメインでトラッキングを確実に行えるように、顧客のドメインにファーストパーティ Cookie を設定します。詳しくは、[Cookie と Experience Cloud ID サービス](./cookies.md)に関するドキュメントを参照してください。
* エイリアス と ID マッピングを Experience Cloud の顧客とパートナーから受け取る。
* Experience Cloud 内の ID 同期を管理する。
* 広告技術エコシステム全体にわたり様々なサードパーティとの ID 同期をサポートする。

## Experience CloudID サービスの要件

ソリューションおよびその他のAdobeコードライブラリは、 [特定の要件](/help/reference/requirements.md) を参照してください。

* [Cookie とExperience CloudID サービス](cookies.md):Experience CloudID サービス ID サービスは、組織 ID、Experience CloudAMCV Cookie および demdex Cookie を使用して、サイト訪問者固有の永続的な識別子を作成して保存します。 これらの Cookie を使用すると、ID サービスは異なるドメインをまたいで訪問者を追跡し、異なるドメインソリューション間でデータExperience Cloudを共有できます。
* [Experience Cloud Identity Service による ID のリクエスト方法と設定方法](id-request.md)：ID リクエストと応答プロセスの概要です。個々のサイト、異なる複数のサイトおよびそれぞれ独自の組織 ID を持つ異なる Experience Cloud ユーザーによって管理されるサイトに対する ID の割り当て例を示しています。
* [ID 同期と一致率について](match-rates.md):Adobe Media Optimizerおよび ID サービスを含む、ID 同期プロセスとExperience CloudID サービスの一致率の概要です。
