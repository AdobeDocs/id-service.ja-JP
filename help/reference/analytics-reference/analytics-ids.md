---
description: Experience Cloud Identity Service は、従来の Analytics 訪問者 ID 方式を置き換えるものです。
keywords: ID サービス
title: Analytics および Experience Cloud ID の設定
exl-id: 7399ea16-d13e-452c-b8d9-8d0699566aa2
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 100%

---

# Analytics および Experience Cloud ID の設定 {#setting-analytics-and-experience-cloud-ids}

Experience Cloud Identity Service は、従来の Analytics 訪問者 ID 方式を置き換えるものです。

ID サービスの実装後、AppMeasurement の前にこのコードが実行されます。ID サービスは Experience Cloud および Analytics の ID を取得するので、AppMeasurement が読み込まれたときには、これらの値が利用できる状態になっています。

AppMeasurement が読み込まれると、Experience Cloud および Analytics の ID の値が ID サービスからリクエストされ、各サーバーコールでデータ収集サーバーに送信されます。ID サービスは訪問者 ID を決定してそれを AppMeasurement に渡すだけなので、各ページでは ID サービスを AppMeasurement JavaScript ファイルの前にインクルードして実装しておく必要があります。

## Analytics ID プロセスの変更点 {#section-79bb86ae63f546419bb1a7ef5e710462}

[!DNL Experience Cloud] ID サービスに移行する際の大きな変更点は、データ収集 Web サーバーから返された HTTP ヘッダーを使用するのではなく、JavaScript を使用して ID Cookie を設定することです。この変更を理解できるように、以下の節でこの 2 つの方法を使用して Cookie を設定する方法について説明します。

**HTTP ヘッダー**

Web サーバーからの HTTP 応答がブラウザーの Cookie に設定されます。この処理により、`s_vi` Cookie が設定されます。`s_vi` Cookie は Analytics 訪問者を識別するものです。設定された Cookie は、以後そのサーバーに送信されるすべての HTTP リクエストに含まれます。

リクエストがアドビのデータ収集サーバーに送信されると、ヘッダーで `s_vi` Cookie の有無がチェックされます。この Cookie がリクエストに含まれている場合、この Cookie を使用して訪問者が識別されます。この Cookie がリクエストに含まれていない場合、サーバーは一意の [!DNL Experience Cloud] ID を生成し、それを HTTP 応答ヘッダー内に Cookie として設定した後、リクエストとともに返送します。この Cookie はブラウザーに保存され、その後のサイト訪問の際にデータ収集サーバーに返送されます。このしくみによって、複数回訪問する訪問者を識別できます。

ただし、Apple Safari などの一部のブラウザーでは、サードパーティ Cookie が受け入れられません。サードパーティ Cookie とは、現在の Web サイト以外のドメインからブラウザーに設定される Cookie のことです。また、Safari では、訪問者が訪問したことのないサードパーティドメインの Cookie がブロックされます。例えば、`mysite.com` を表示しているとき、データ収集サーバーが `mysite.omtrdc.net` である場合は、`mysite.omtrdc.net` からの HTTP ヘッダーで返された Cookie はブラウザーによって拒否される可能性があります。

この状況を避けるために、多くのお客様はデータ収集サーバーに対して CNAME レコードを実装しています。これは、[ファーストパーティ Cookie を実装する](https://docs.adobe.com/content/help/ja-JP/core-services/interface/ec-cookies/cookies-first-party.html)効果的な方法の 1 つです。お客様のドメインのホスト名をデータ収集サーバーにマッピングするように CNAME レコードを設定すると（例えば、`metrics.mysite.com` を `mysite.omtrdc.net` にマッピングする）、データ収集ドメインは Web サイトのドメインと一致するので、[!DNL Experience Cloud] ID Cookie が保存されます。この方法により、ID サービスの Cookie が保存される可能性が上がります。ただし、CNAME レコードを設定して、データ収集サーバーの SSL 証明書を維持する必要があるので、オーバーヘッドが発生します。

**JavaScript**

JavaScript は、ファーストパーティドメイン（現在の Web サイトのドメイン）の Cookie セットの読み取りと書き込みを実行できます。これにより、[!DNL Experience Cloud] ID サービスではすべての訪問者 ID を含む `AMCV_###@AdobeOrg` Cookie を設定できるので、トラッキングサーバーのドメインが Web サイトのドメインと一致していない場合でも、訪問者 ID Cookie を保存できます。CNAME レコードおよび SSL 証明書を使用するオーバーヘッドが不要となるので、ほとんどの場合においてこの方法で ID サービス Cookie を設定することをお勧めします。

<!---However, there are a few situations where setting the cookie in the HTTP header is beneficial for cross-domain tracking, which is described in [Data Collection CNAMEs and Cross-Domain Tracking](../../reference/analytics-reference/cname.md#concept-4df91f8a30ad4ec7a01eb943d579cc9d).-->

## カスタム Analytics ID {#section-b6a7bd19e9ff432390010062450808f6}

`s.visitorID` を使用して顧客 ID を設定すると、Analytics でユーザーを特定しやすくなります。しかし、`s.visitorID` を使用して訪問者を特定する場合は、ID サービスを用いて Analytics データをエクスポートまたはインポートする統合機能を使用できません。

これには共有オーディエンス、Analytics for Target（A4T）、顧客属性などが該当しますが、これらに限定されません。これらの統合機能では、カスタム Analytics ID の設定はサポート対象外となります。

## Analytics 訪問者 ID の順序 {#section-de1dc9fc9b6d4388995b70e35b8bcddf}

訪問者 ID サービスをデプロイすると、Analytics で訪問者を識別するために次の 5 つの方法を使用できることになります（次の表では、優先度の高い順に並べています）。

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
   <td colname="col1"> <p> <img id="image_9F3E58898A1B4F40BBDEF5ADE362E55C" src="assets/step1_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://docs.adobe.com/content/help/ja-JP/analytics/implementation/vars/config-vars/visitorid.html" format="http" scope="external">vid（s.visitorID）</a> </p> </td> 
   <td colname="col3"> <p>s.visitorID が設定されている場合 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_77A06981672745B6AEA8BB4D55911CCA" src="assets/step2_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://docs.adobe.com/content/help/ja-JP/core-services/interface/ec-cookies/cookies-analytics.html" format="http" scope="external">aid（s_vi Cookie）</a> </p> </td> 
   <td colname="col3"> <p><span class="keyword">Experience Cloud</span> ID サービスをデプロイする前に、訪問者に既存の s_vi Cookie がある場合、または<a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local">猶予期間</a>を設定している場合。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_0A950B1A6B004387AFEE8EED882739CB" src="assets/step3_icon.png" /> </p> </td> 
   <td colname="col2"> <p>mid（Experience Cloud 訪問者 ID サービスによって設定される AMCV_ Cookie） </p> </td> 
   <td colname="col3"> <p>訪問者のブラウザーがファーストパーティ Cookie を受け入れる場合 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_6F0ED8FE3EF846CA8E6ECCC3C0070D85" src="assets/step4_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://docs.adobe.com/content/help/ja-JP/id-service/using/reference/analytics-reference/analytics-ids.html" format="http" scope="external">fid（H.25.3 以降の代替の Cookie、または JavaScript 版 AppMeasurement）</a> </p> </td> 
   <td colname="col3"> <p>ブラウザーがサードパーティ Cookie を受け入れず、Analytics トラッキングサーバーがサードパーティトラッキングサーバーとして設定されている場合 </p> <p> <p>注意：<span class="codeph">fid</span> は、従来の識別子で、サイトに ID サービスを実装している場合、使用されません。この場合、ファーストパーティである<a href="../../introduction/cookies.md" format="dita" scope="local"> AMCV cookie</a> がもう使用していないので、<span class="codeph"> fid</span> は必要ありません。fid は、レガシーコードをサポートするために、および歴史的な理由により、保持されています。 </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_23D8C0EB69EC4084BC237B5B98C036F4" src="assets/step5_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://docs.adobe.com/content/help/ja-JP/analytics/components/metrics/unique-visitors.html" format="http" scope="external"> IP アドレス、ユーザーエージェント、ゲートウェイ IP アドレス</a> </p> </td> 
   <td colname="col3"> <p>訪問者のブラウザーが Cookie を受け入れない場合。 </p> </td> 
  </tr> 
 </tbody> 
</table>

ほとんどのシナリオでは 1 回の呼び出しに 2 ～ 3 種類の ID が存在しますが、Analytics では、最も優先度の高い ID が正式な [!DNL Experience Cloud] ID として使用されます。例えば、&#39;vid&#39; クエリパラメーターに格納されるカスタム訪問者 ID を設定している場合は、この ID が、同じヒットで存在する他の ID よりも優先して使用されます。

>[!MORELIKETHIS]
>
>* [Analytics ID の操作の順序](../../reference/analytics-reference/analytics-order-of-operations.md#concept-b92935b4fff545adb4773f3728bc15ef)

