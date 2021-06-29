---
description: 訪問者 ID サービスをデプロイすると、以下の 5 つの方法で、Analytics で訪問者を識別できます。
keywords: ID サービス
title: Analytics ID の操作の順序
exl-id: 8ee340fe-ef3b-40e6-9441-7ee0c9e20357
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: ht
source-wordcount: '300'
ht-degree: 100%

---

# Analytics ID の操作の順序 {#order-of-operations-for-analytics-ids}

訪問者 ID サービスをデプロイすると、以下の 5 つの方法で、Analytics で訪問者を識別できます。

ほとんどのシナリオでは 1 回の呼び出しに 2 ～ 3 種類の ID が存在しますが、Analytics では、最も優先度の高い ID が正式な [!DNL Experience Cloud] ID として使用されます。例えば、`vid` クエリパラメーターに格納されるカスタム訪問者 ID を設定している場合は、この ID が、同じヒットで存在する他の ID よりも優先して使用されます。[Analytics ID と Experience Cloud ID の設定](../../reference/analytics-reference/analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6)を参照してください。

<table id="table_D267D36451F643D1BB68AF6FEAA6AD1A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 使用順序 </th> 
   <th colname="col2" class="entry"> クエリパラメーター（収集方法） </th> 
   <th colname="col3" class="entry"> 以下の場合に表示される </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b><sup>1</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://experienceleague.adobe.com/docs/analytics/implementation/vars/config-vars/visitorid.html?lang=ja" format="http" scope="external">vid（s.visitorID）</a> </p> </td> 
   <td colname="col3"> <p><span class="codeph">s.visitorID</span> が設定されている </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>2<sup></sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-analytics.html?lang=ja" format="http" scope="external">aid（s_vi Cookie）</a> </p> </td> 
   <td colname="col3"> <p><span class="keyword">Experience Cloud</span> ID サービスをデプロイする前に、訪問者に既存の s_vi Cookie がある場合、または<a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local">猶予期間</a>を設定している場合。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>3<sup></sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="../../introduction/cookies.md#section-7ff7d96d6e4141b08a84a75a63d7814c" format="dita" scope="local">Experience Cloud ID（MID）</a> </p> </td> 
   <td colname="col3"> <p>訪問者のブラウザーがファーストパーティ Cookie を受け入れる場合。これは、AMCV Cookie で設定されます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>4<sup></sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://experienceleague.adobe.com/docs/id-service/using/reference/analytics-reference/analytics-ids.html?lang=ja" format="http" scope="external">fid（H.25.3 以降の代替の Cookie、または JavaScript 版 AppMeasurement）</a> </p> </td> 
   <td colname="col3"> <p>ブラウザーがサードパーティ Cookie を受け入れず、Analytics トラッキングサーバーがサードパーティトラッキングサーバーとして設定されている場合 </p> <p> <p>注意：<span class="codeph">fid</span> は、従来の識別子で、サイトに ID サービスを実装している場合、使用されません。この場合、ファーストパーティである<a href="../../introduction/cookies.md" format="dita" scope="local"> AMCV cookie</a> がもう使用していないので、<span class="codeph"> fid</span> は必要ありません。fid は、レガシーコードをサポートするために、および歴史的な理由により、保持されています。 </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>5<sup></sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://experienceleague.adobe.com/docs/analytics/technotes/visitor-identification.html?lang=ja" format="http" scope="external"> IP アドレス、ユーザーエージェント、ゲートウェイ IP アドレス</a> </p> </td> 
   <td colname="col3"> <p>訪問者のブラウザーが Cookie を受け入れない場合。 </p> </td> 
  </tr> 
 </tbody> 
</table>
