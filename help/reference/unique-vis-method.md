---
title: 個別訪問者数の識別
description: Adobe ECID（ID サービス）のドキュメント
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# 個別訪問者数の識別

複数のコンテキストをまたいで個別訪問者を識別する方法には、この決定の正確性を確保するために優先順位付けされたシーケンスが含まれます。次の表に、この優先順位付けされたシーケンスを示します。 
| 使用された注文 | クエリパラメーター（コレクションのメソッド）| post_visid_type 列の値 | 次の場合に表示 |
|--- |--- |--- |--- |
| 1 | [vid（s.visitorID）](https://docs.adobe.com/content/help/ja-JP/analytics/technotes/visitor-identification.html) | 0 |s.visitorID が設定済みである。|
| 2 | [aid (s_vi cookie)](https://docs.adobe.com/content/help/ja-JP/analytics/technotes/visitor-identification.html) | 3 |Visitor had an existing s_vi cookie before you deployed the Visitor ID service, or you have a Visitor ID [grace period](https://docs.adobe.com/content/help/ja-JP/id-service/using/reference/analytics-reference/grace-period.html) configured. |
| 3 | [mid（ID サービスによって設定された AMCV_ cookie）](https://docs.adobe.com/content/help/ja-JP/id-service/using/home.html) | 5 | 訪問者のブラウザーが cookie（ファーストパーティ）を受け入れ、ID サービスがデプロイ済みである。 |
| 4 | [fid（H.25.3 以降でのフォールバック cookie、または JavaScript 版 AppMeasurement）](https://docs.adobe.com/content/help/ja-JP/analytics/technotes/visitor-identification.html) | 4 | 訪問者のブラウザーが cookie（ファーストパーティ）を受け入れる。 |
| 5 | [HTTP モバイル購読者ヘッダー](https://docs.adobe.com/content/help/ja-JP/analytics/technotes/visitor-identification.html) | 2 | デバイスがモバイルデバイスとして認識される。 |
| 6 | [IP アドレス、ユーザーエージェント、ゲートウェイ IP アドレス](https://docs.adobe.com/content/help/ja-JP/analytics/technotes/visitor-identification.html) | 1 | 訪問者のブラウザーが cookie を受け入れない。  

個別訪問者数のレポート方法について詳しくは、[Analytics の個別訪問者数](https://docs.adobe.com/content/help/ja-JP/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html)を参照してください。
