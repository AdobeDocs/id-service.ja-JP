---
title: ユニーク訪問者数の識別
description: Adobe ECID（ID サービス）のドキュメント
exl-id: 379dbf0a-814d-4348-9ac4-d0e8fc13b9dc
source-git-commit: c65816530ae2269b216f60b9b0450077e5aaac2f
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 100%

---

# ユニーク訪問者数の識別

複数のコンテキストをまたいでユニーク訪問者を識別する方法には、この決定の正確性を確保するために優先順位付けされたシーケンスが含まれます。次の表に、この優先順位付けされたシーケンスを示します。


| 使用順序 | クエリパラメーター（収集方法） | post_visid_type 列の値 | 以下の場合に表示される |
|---|---|---|---|
|  1  | vid [s.visitorID](https://experienceleague.adobe.com/docs/analytics/implementation/vars/config-vars/visitorid.html?lang=ja)  | 0  | `s.visitorID` が設定されている。 |
|  2  | aid [s_vi cookie](https://experienceleague.adobe.com/docs/core-services/interface/administration/ec-cookies/cookies-analytics.html?lang=ja#section-5d50a078de444d12b7d927d68ff3b679)  | 3  | 訪問者 ID サービスをデプロイする前に訪問者が既に s_vi cookie を持っていた、または訪問者 ID [猶予期間](https://experienceleague.adobe.com/docs/id-service/using/reference/analytics-reference/grace-period.html?lang=ja)が設定済みである。 |
|  3  | mid [ID サービスによって設定される AMCV_ cookie](../introduction/cookies.md) |  5  | 訪問者のブラウザーが Cookie（ファーストパーティ）を受け入れ、[!DNL Identity Service] がデプロイされている。 |
|  4  | fid [H.25.3 以降の代替の cookie、または JavaScript 版 AppMeasurement](https://experienceleague.adobe.com/docs/core-services/interface/administration/ec-cookies/cookies-analytics.html?lang=ja#section-65e33f9bfc264959ac1513e2f4b10ac7) |  4  |  訪問者のブラウザーが cookie（ファーストパーティ）を受け入れる。  |
|  5  |  [HTTP モバイル加入者ヘッダー](https://experienceleague.adobe.com/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-reference.html?lang=ja) |  2  |  デバイスがモバイルデバイスとして認識されている。  |
|  6  |  [IP アドレス、ユーザーエージェント、ゲートウェイ IP アドレス](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html?lang=ja) |  1  |  訪問者のブラウザーで cookie が許可されていない。 |

{style="table-layout:auto"}

ユニーク訪問者数のレポート方法について詳しくは、[Analytics のユニーク訪問者数](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html?lang=ja)を参照してください。
