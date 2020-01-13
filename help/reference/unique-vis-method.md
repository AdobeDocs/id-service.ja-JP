---
title: 個別訪問者数の識別
description: Adobe ECID（ID サービス）のドキュメント
translation-type: ht
source-git-commit: 453a14a4b725dd14f445b089d083a83a5d2ffaa4

---


# 個別訪問者数の識別

複数のコンテキストをまたいで個別訪問者を識別する方法には、この決定の正確性を確保するために優先順位付けされたシーケンスが含まれます。次の表に、この優先順位付けされたシーケンスを示します。


 
| 使用された注文 | クエリパラメーター（コレクションのメソッド）| post_visid_type 列の値 | 次の場合に表示 |
|--- |--- |--- |--- |
| 1 | [vid（s.visitorID）](https://marketing.adobe.com/resources/help/ja_JP/sc/implement/visid_custom.html) | 0 |s.visitorID が設定済みである。| 
| 2 | [aid（s_vi cookie）](https://marketing.adobe.com/resources/help/ja_JP/sc/implement/visid_analytics.html) | 3 | 訪問者 ID サービスをデプロイする前に訪問者が既に s_vi cookie を持っていた、または訪問者 ID [猶予期間](https://marketing.adobe.com/resources/help/ja_JP/mcvid/mcvid_grace_period.html)が設定済みである。 |
| 3 | [mid（ID サービスによって設定された AMCV_ cookie）](https://marketing.adobe.com/resources/help/ja_JP/mcvid/) | 5 | 訪問者のブラウザーが cookie（ファーストパーティ）を受け入れ、ID サービスがデプロイ済みである。 |
| 4 | [fid（H.25.3 以降でのフォールバック cookie、または JavaScript 版 AppMeasurement）](https://marketing.adobe.com/resources/help/ja_JP/sc/implement/visid_fallback.html) | 4 | 訪問者のブラウザーが cookie（ファーストパーティ）を受け入れる。 |
| 5 | [HTTP モバイル購読者ヘッダー](https://marketing.adobe.com/resources/help/ja_JP/sc/implement/visid_mobile.html) | 2 | デバイスがモバイルデバイスとして認識される。 |
| 6 | [IP アドレス、ユーザーエージェント、ゲートウェイ IP アドレス](https://marketing.adobe.com/resources/help/ja_JP/sc/implement/visid_fallback.html) | 1 | 訪問者のブラウザーが cookie を受け入れない。  


個別訪問者数のレポート方法について詳しくは、[Analytics の個別訪問者数](https://docs.adobe.com/content/help/ja-JP/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html)を参照してください。
