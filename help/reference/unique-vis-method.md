---
title: 個別訪問者数の識別
description: Adobe ECID（ID サービス）のドキュメント
translation-type: tm+mt
source-git-commit: 8ad5ae179540596913fccc59070aecc57b09f586
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 100%

---


# 個別訪問者数の識別

複数のコンテキストをまたいで個別訪問者を識別する方法には、この決定の正確性を確保するために優先順位付けされたシーケンスが含まれます。次の表に、この優先順位付けされたシーケンスを示します。


| 使用順序 | クエリパラメーター（収集方法） | post_visid_type 列の値 | 以下の場合に表示される |
|---|---|---|---|
|  1  | vid [s.visitorID](https://docs.adobe.com/content/help/ja-JP/analytics/technotes/visitor-identification.html)  | 0  | `s.visitorID` が設定されている。 |
|  2  | aid [s_vi cookie](https://docs.adobe.com/content/help/ja-JP/analytics/technotes/visitor-identification.html)  | 3  | 訪問者 ID サービスをデプロイする前に訪問者が既に s_vi cookie を持っていた、または訪問者 ID [猶予期間](https://docs.adobe.com/content/help/ja-JP/id-service/using/reference/analytics-reference/grace-period.html)が設定済みである。 |
|  3  | mid [ID サービスによって設定される AMCV_ cookie](https://docs.adobe.com/content/help/ja-JP/id-service/using/home.html) |  5  |  訪問者のブラウザーが cookie（ファーストパーティ）を受け入れ、[!UICONTROL ID サービス]がデプロイされている。 |
|  4  | fid [H.25.3 以降の代替の cookie、または JavaScript 版 AppMeasurement](https://docs.adobe.com/content/help/ja-JP/analytics/technotes/visitor-identification.html) |  4  |  訪問者のブラウザーが cookie（ファーストパーティ）を受け入れる。  |
|  5  |  [HTTP モバイル加入者ヘッダー](https://docs.adobe.com/content/help/ja-JP/analytics/technotes/visitor-identification.html) |  2  |  デバイスがモバイルデバイスとして認識されている。  |
|  6  |  [IP アドレス、ユーザーエージェント、ゲートウェイ IP アドレス](https://docs.adobe.com/content/help/ja-JP/analytics/technotes/visitor-identification.html) |  1  |  訪問者のブラウザーで cookie が許可されていない。 |

個別訪問者数のレポート方法について詳しくは、[Analytics の個別訪問者数](https://docs.adobe.com/content/help/ja-JP/analytics/components/metrics/unique-visitors.translate.html)を参照してください。
