---
description: Adobe Experience Cloud における Experience Cloud Identity Service の役割です。
title: Experience Cloud ID サービスの概要
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
source-git-commit: f7c25f5ebd0690c56c081422949eb34f1f277ae1
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 100%

---

# Experience Cloud ID サービスの概要

Experience Cloud ID サービスは、Experience Cloud アプリケーションサービスの共通の ID フレームワークを実現します。Experience Cloud ID サービスを使用すると、[Experience Cloud ID（ECID）](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html?lang=ja)を設定できます。

ECID は、Adobe Experience Platform および Experience Cloud アプリケーションで横断的に使用される共有の ID 名前空間です。訪問者の行動の追跡と、複数のセッションにわたって保持される一意の ID を各デバイスに確実に割り当てることを目的とします。

>[!TIP]
>
>Experience Cloud ID サービス、Experience Platform ID サービス および ECID は、3 つの&#x200B;**異なる**&#x200B;エンティティです。

Experience Cloud ID サービスは、アプリケーション固有の様々な ID の代わりとなり、[顧客 ID と認証状態](/help/reference/authenticated-state.md)機能を使用して、独自の顧客 ID を Experience Cloud に渡せるようにします。

>[!NOTE]
>
>Experience Cloud ID サービスは、購読している Experience Cloud アプリケーションサービスでのみ機能し、購読していない場合は他のアプリケーションサービスへのアクセスを提供しません。

Experience Cloud ID サービスは、次のアプリケーションをサポートしています。

* [Adobe Analytics](https://business.adobe.com/jp/products/analytics/web-analytics.html)
* [Audience Manager](https://business.adobe.com/jp/products/audience-manager/adobe-audience-manager.html)
* [Adobe Target](https://business.adobe.com/jp/products/target/adobe-target.html)

いずれは、ID サービスは、現在および将来の多くの Experience Cloud 機能、機能強化およびサービスにとって不可欠なコンポーネントになります。現在、ID サービスは、[Analytics](http://www.adobe.com/jp/marketing-cloud/web-analytics.html)、[Audience Manager](http://www.adobe.com/jp/marketing-cloud/data-management-platform.html) および [Target](http://www.adobe.com/jp/marketing-cloud/testing-targeting.html) をサポートしています。ID サービスを実装していない場合、今が移行戦略を検討し始めるチャンスです。

## 機能の概要

まとめると、Experience Cloud ID サービスは以下の目的に役立ちます。

* 1 台のデバイスで複数のアプリケーションにわたって訪問者を一意に識別します。
* 同じドメインでトラッキングを確実に行えるように、顧客のドメインにファーストパーティ Cookie を設定します。詳しくは、[Cookie と Experience Cloud ID サービス](./cookies.md)に関するドキュメントを参照してください。
* エイリアス と ID マッピングを Experience Cloud の顧客とパートナーから受け取る。
* Experience Cloud 内の ID 同期を管理する。
* 広告技術エコシステム全体にわたり様々なサードパーティとの ID 同期をサポートする。

## Experience Cloud ID サービスの要件

ID サービスを使用するには、お使いのソリューションおよび他のアドビコードライブラリが[特定の要件](/help/reference/requirements.md)を満たしている必要があります。

* [Cookie と Experience Cloud ID サービス](cookies.md)：Experience Cloud ID サービスでは、組織 ID、Experience Cloud AMCV Cookie および demdex Cookie を使用して、サイト訪問者の一意の永続的な識別子を作成し保存します。これらの Cookie により、ID サービスで異なるドメインをまたいで訪問者を追跡できるようになり、異なる Experience Cloud ソリューション間でのデータ共有が可能になります。
* [Experience Cloud Identity Service による ID のリクエスト方法と設定方法](id-request.md)：ID リクエストと応答プロセスの概要です。個々のサイト、異なる複数のサイトおよびそれぞれ独自の組織 ID を持つ異なる Experience Cloud ユーザーによって管理されるサイトに対する ID の割り当て例を示しています。
* [ID 同期と一致率について](match-rates.md)：Adobe Media Manager や ID サービスなどの Experience Cloud ID サービスにおける ID 同期プロセスと一致率の概要です。
