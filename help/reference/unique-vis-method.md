---
title: 個別訪問者数の識別
description: Adobe ECID（ID サービス）のドキュメント
translation-type: tm+mt
source-git-commit: 8ad5ae179540596913fccc59070aecc57b09f586
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 56%

---


# 個別訪問者数の識別

複数のコンテキストをまたいで個別訪問者を識別する方法には、この決定の正確性を確保するために優先順位付けされたシーケンスが含まれます。次の表に、この優先順位付けされたシーケンスを示します。


| 使用順序 | クエリパラメーター（収集メソッド） | post_visid_type列の値 | 次の場合に表示 |
|---|---|---|---|
|  1  | vid [s.visitorID](https://docs.adobe.com/content/help/ja-JP/analytics/technotes/visitor-identification.html)  | 0  | `s.visitorID` が設定されている場合)。 |
|  2  | aid  [s_vi cookie](https://docs.adobe.com/content/help/ja-JP/analytics/technotes/visitor-identification.html)  | 3  | Visitor had an existing s_vi cookie before you deployed the Visitor ID service, or you have a Visitor ID [grace period](https://docs.adobe.com/content/help/ja-JP/id-service/using/reference/analytics-reference/grace-period.html) configured.  |
|  3  | IDサービスによって設定されるmid[AMCV_ cookie](https://docs.adobe.com/content/help/ja-JP/id-service/using/home.html)  |  5  |  訪問者のブラウザーがcookie（ファーストパーティ）を受け入れ、[!UICONTROL IDサービス]がデプロイされている。  |
|  4  | fid [fallback cookie on H.25.3 or newer, or AppMeasurement for JavaScript](https://docs.adobe.com/content/help/ja-JP/analytics/technotes/visitor-identification.html)  |  4  |  訪問者のブラウザーがcookie（ファーストパーティ）を受け入れる場合。  |
|  5  |  [HTTPモバイル加入者ヘッダー](https://docs.adobe.com/content/help/ja-JP/analytics/technotes/visitor-identification.html)  |  2  |  デバイスがモバイルデバイスとして認識される。  |
|  6  |  [IP Address, User Agent, Gateway IP Address](https://docs.adobe.com/content/help/ja-JP/analytics/technotes/visitor-identification.html)  |  1  |  訪問者のブラウザーがcookieを受け入れません。 |

個別訪問者数のレポート方法について詳しくは、[Analytics の個別訪問者数](https://docs.adobe.com/content/help/ja-JP/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html)を参照してください。
