---
description: Adobe CX EnterpriseのVisitor ID サービスの役割。
title: Adobe Visitor ID サービスの概要
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
TQID: https://experienceleague.adobe.com/fkT81V3iLEz2irg-3SDoyx733RNhqa2zWV1FgiXoYO4
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 497
ht-degree: 18%

---

# Adobe Visitor ID サービスの概要

Adobe Visitor ID サービスは、CX Enterprise Application Servicesの共通ID フレームワークを有効にします。 訪問者ID サービスを使用して、[ECID](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html?lang=ja)を設定できます。

ECIDは、Adobe Experience PlatformとCX Enterprise アプリケーションで使用される共有ID名前空間です。訪問者の行動を追跡し、各デバイスに複数のセッションに永続化できる一意のIDを割り当てることができます。

>[!TIP]
>
>訪問者ID サービス、Experience Platform ID サービス、およびECIDは、3つの&#x200B;**異なる** エンティティです。

訪問者ID サービスは、異なるアプリケーション固有のIDを置き換え、[顧客IDと認証状態](/help/reference/authenticated-state.md)機能を使用して、独自の顧客IDをCX Enterpriseに渡すことができます。

>[!NOTE]
>
>訪問者ID サービスは、お客様が購読しているCX エンタープライズ アプリケーション サービスでのみ機能し、購読していない場合は他のアプリケーション サービスへのアクセスを提供しません。

訪問者ID サービスは、次のアプリケーションをサポートしています。

* [Adobe Analytics](https://business.adobe.com/jp/products/analytics/web-analytics.html)
* [Audience Manager](https://business.adobe.com/jp/products/audience-manager/adobe-audience-manager.html)
* [Adobe Target](https://business.adobe.com/jp/products/target/adobe-target.html)

今後、訪問者ID サービスは、現在および将来の多くのCX エンタープライズ機能、機能強化、サービスの不可欠なコンポーネントとなります。 現在、訪問者ID サービスは[Analytics](http://www.adobe.com/jp/marketing-cloud/web-analytics.html)、[Audience Manager](http://www.adobe.com/jp/marketing-cloud/data-management-platform.html)、[Target](http://www.adobe.com/jp/marketing-cloud/testing-targeting.html)をサポートしています。 訪問者ID サービスを実装していない場合は、今から移行戦略の検討を開始します。

## 機能の概要

要約すると、訪問者ID サービスは次の機能をサポートします。

* 1 台のデバイスで複数のアプリケーションにわたって訪問者を一意に識別します。
* 同じドメインでトラッキングを確実に行えるように、顧客のドメインにファーストパーティ Cookie を設定します。 詳しくは、[cookieおよび訪問者ID サービス ](./cookies.md)のドキュメントを参照してください。
* CX Enterpriseの顧客およびパートナーからエイリアスとID マッピングを受信します。
* CX Enterprise内のID同期を管理します。
* 広告技術エコシステム全体にわたり様々なサードパーティとの ID 同期をサポートする。

## 訪問者ID サービスの要件

ソリューションおよびその他のAdobe コードライブラリは、訪問者ID サービスを使用する前に[特定の要件](/help/reference/requirements.md)を満たしている必要があります。

* [Cookieと訪問者ID サービス ](cookies.md)：訪問者ID サービスは、IMS組織ID、CX エンタープライズ AMCV Cookie、およびdemdex Cookieを使用して、サイト訪問者の一意の永続的なIDを作成および保存します。 こうしたCookieにより、Visitor ID Serviceは様々なドメインをまたいで訪問者を追跡し、様々なCX Enterprise ソリューション間でのデータ共有を可能にします。
* [訪問者ID サービスがIDを要求および設定する方法](id-request.md): ID要求および応答プロセスの概要。 これらの例では、個々のサイト、異なるサイト、および独自のIMS組織IDを持つ異なるCX Enterprise顧客が管理するサイトのID割り当てについて説明します。
* [ID同期と一致率について](match-rates.md): Adobe Media OptimizerとVisitor ID サービスを含む、Visitor ID サービスでのID同期プロセスと一致率の概要。

