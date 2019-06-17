---
description: Adobe Experience Cloud での Experience Cloud ID サービスの役割です。
seo-description: Experience Cloud ID サービスは、Experience Cloud コアサービス、ソリューション、顧客属性、People コアサービスのオーディエンスのための、共通の識別フレームワークです。
seo-title: IDサービスの概要
title: 概要
uuid: null
translation-type: tm+mt
source-git-commit: 1c6dc1871ee2e7b8d1f510576836519f7383b809

---


# 概要

Experience Cloud ID サービスは、Experience Cloud コアサービス、ソリューション、顧客属性、People コアサービスのオーディエンスのための、共通の識別フレームワークです。サイト訪問者に一意の永続的 ID を割り当てることで機能します。組織が ID サービスを実装する場合、この ID を使用することで、同じサイト訪問者およびそのデータを様々な Experience Cloud ソリューションで識別できます。

![](assets/ecid.png)

また、この ID サービスは、様々なソリューション専用 ID（例：Analytics AID）を置き換えることができます。そして、[顧客 ID と認証状態](/help/mcvid-reference/mcvid-authenticated-state.md)機能を使用すると、ID サービスを通じて顧客 ID を Experience Cloud に渡すことが可能になります。ただし、ID サービスは、既に登録されたソリューションのみと連携することに注意してください。登録していない製品には ID サービスからアクセスできません。

いずれは、ID サービスは、多くの現在および将来の Experience Cloud 機能、強化、サービスにとって不可欠な要素になります。現在、ID サービスは、[Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html)、[Audience Manager](http://www.adobe.com/marketing-cloud/data-management-platform.html) および [Target](http://www.adobe.com/marketing-cloud/testing-targeting.html) をサポートしています。さらに、Adobe Experience Cloud Device Co-op に参加する場合に必要です。ID サービスを実装していない場合、今が移行戦略を検討し始めるチャンスです。ID サービスの重要性と役割について詳しくは、[Why the Experience Cloud ID Service Should be on Your Radar](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/) を参照してください。

## 機能概要

まとめると、ID サービスには以下の機能があります。

* プロファイルと ID をリンクするために使用できる共通キーまたは ID を作成する。
* 複数のソリューションをまたいで一意にデバイスを識別する。
* 顧客のドメインにファーストパーティ Cookie を設定し、同ドメインでトラッキングをおこなえるようにする。詳しくは、 Experience Cloud.
* エイリアス と ID マッピングを Experience Cloud の顧客とパートナーから受け取る。
* Experience Cloud 内の ID 同期を管理する。
* 広告技術エコシステム全体にわたり様々なサードパーティとの ID 同期をサポートする。

## ID サービスの要件

ID サービスを使用し始める前に、ソリューションおよびその他の Adobe コードライブラリは、[特定の要件](/help/mcvid-reference/mcvid-requirements.md) を参照してください。

* [cookieとExperience Cloud IDサービス](mcvid-cookies.md):IDサービスは、組織ID、Experience Cloud AMCV cookieおよびdemdex cookieを使用して、サイト訪問者の一意の永続的な識別子を作成して保存します。これらの Cookie により、ID サービスでは異なるドメインをまたいで訪問者を追跡できるようになり、異なる Experience Cloud ソリューション間でデータの共有が可能になります。
* [Experience Cloud IDサービスのリクエストとIDの設定](mcvid-id-request.md)方法:IDリクエストと応答プロセスの概要です。個々のサイト、異なる複数のサイトおよびそれぞれ独自の組織 ID を持つ異なる Experience Cloud ユーザーによって管理されるサイトに対する ID の割り当て例を示しています。
* [ID同期と一致率について](mcvid-match-rates.md):Adobe Media ManagerやIDサービスなど、ID同期プロセスとExperience Cloud IDサービスの一致率の概要を示します。