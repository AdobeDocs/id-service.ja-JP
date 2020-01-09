---
title: 個別訪問者数の識別
description: Adobe ECID（IDサービス）のドキュメント
translation-type: tm+mt
source-git-commit: 453a14a4b725dd14f445b089d083a83a5d2ffaa4

---


# 個別訪問者数の識別

複数のコンテキスト間の個別訪問者を識別する方法は、この決定の正確性を確保するために優先順位付けされたシーケンスを含む。 次の表に、この優先順位付けされたシーケンスを示します。


 
|注文が使用されました|クエリパラメータ（コレクションのメソッド）| post_visid_type列の値|次の場合に表示 ||—|—|—|— || 1 |[vid (s.visitorID)](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_custom.html)| 0 |s.visitorIDが設定されています。| 
| 2 | [aid (s_vi cookie)](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_analytics.html) | 3 |Visitor had an existing s_vi cookie before you deployed the Visitor ID service, or you have a Visitor ID [grace period](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid_grace_period.html) configured. || 3 |[mid(AMCV_ cookie set by Identity Service)](https://marketing.adobe.com/resources/help/en_US/mcvid/)| 5 |訪問者のブラウザーがcookie（ファーストパーティ）を受け入れ、IDサービスがデプロイされます。 || 4 |[fid （H.25.3以降でのフォールバックcookie、またはJavaScript版AppMeasurement）](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_fallback.html)| 4 |訪問者のブラウザーがcookie（ファーストパーティ）を受け入れる。 || 5 |[HTTPモバイル購読者ヘッダー](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_mobile.html)| 2 |デバイスはモバイルデバイスとして認識されます。 || 6 |[IPアドレス、ユーザーエージェント、ゲートウェイIPアドレス](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_fallback.html)| 1 |訪問者のブラウザーがcookieを受け入れません。 |


実訪問者数のレポート方法について詳しくは、Analyticsの実訪問者数 [を参照してください](https://docs.adobe.com/content/help/en/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html)。
