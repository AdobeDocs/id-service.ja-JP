---
description: 訪問者 ID サービスを導入すると、以下の 5 つの方法で、Analytics で訪問者を識別できます。
keywords: ID サービス
seo-description: 訪問者 ID サービスを導入すると、以下の 5 つの方法で、Analytics で訪問者を識別できます。
seo-title: Analytics ID の操作の順序
title: Analytics ID の操作の順序
uuid: cb1d136e-093f-43b0- a7e1-96f1e61fdad0
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Analytics ID の操作の順序{#order-of-operations-for-analytics-ids}

訪問者 ID サービスを導入すると、以下の 5 つの方法で、Analytics で訪問者を識別できます。

ほとんどのシナリオでは 1 回の呼び出しに 2 ～ 3 種類の ID が存在しますが、Analytics では、最も優先度の高い ID が正式な [!DNL Experience Cloud] ID として使用されます。例えば、`vid` クエリパラメーターに格納されるカスタム訪問者 ID を設定している場合は、この ID が、同じヒットで存在する他の ID よりも優先して使用されます。詳しくは、AnalyticsおよびExperience Cloud ID [](../../mcvid-reference/mcvid-analytics-reference/mcvid-analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6) の設定を参照してください。

<table id="table_D267D36451F643D1BB68AF6FEAA6AD1A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 使用される順序 </th> 
   <th colname="col2" class="entry"> クエリパラメーター（収集方法） </th> 
   <th colname="col3" class="entry"> 次の場合に存在 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>1<sup></sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_custom" format="http" scope="external">vid（s.visitorID）</a> </p> </td> 
   <td colname="col3"> <p><span class="codeph">s.visitorID</span> が設定されている </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>2<sup></sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_analytics" format="http" scope="external">aid（s_vi Cookie）</a> </p> </td> 
   <td colname="col3"> <p><span class="keyword"> Experience Cloud</span> IDサービスを展開する前に、訪問者に既存のs_ vi cookieがあったか、 <a href="../../mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md" format="dita" scope="local"> 猶予期間</a> が設定されています。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>3<sup></sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="../../mcvid-introduction/mcvid-cookies.md#section-7ff7d96d6e4141b08a84a75a63d7814c" format="dita" scope="local">Experience Cloud ID（MID）</a> </p> </td> 
   <td colname="col3"> <p>訪問者のブラウザーがファーストパーティ Cookie を受け入れる場合。これは、AMCV Cookie で設定されます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>4<sup></sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_fallback" format="http" scope="external">fid（H.25.3 以降の代替の Cookie、または JavaScript 版 AppMeasurement）</a> </p> </td> 
   <td colname="col3"> <p>ブラウザーがサードパーティ Cookie を受け入れず、Analytics トラッキングサーバーがサードパーティトラッキングサーバーとして設定されている場合 </p> <p> <p>注意：<span class="codeph">fid</span> は、従来の識別子で、サイトに ID サービスを実装している場合、使用されません。この場合、 <span class="codeph"> ファースト</span> パーティの <a href="../../mcvid-introduction/mcvid-cookies.md" format="dita" scope="local"> AMCV cookie</a> は古いので、fidは不要です。fid は、レガシーコードをサポートするために、および歴史的な理由により、保持されています。 </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>5<sup></sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_fallback" format="http" scope="external"> IP アドレス、ユーザーエージェント、ゲートウェイ IP アドレス</a> </p> </td> 
   <td colname="col3"> <p>訪問者のブラウザーが Cookie を受け入れない場合。 </p> </td> 
  </tr> 
 </tbody> 
</table>

