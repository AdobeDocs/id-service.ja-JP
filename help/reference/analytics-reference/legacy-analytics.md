---
description: Experience Platform IDサービスが従来のAnalytics IDとどのように連携するかの概要を説明します。
keywords: ID サービス
seo-description: Experience Platform IDサービスが従来のAnalytics IDとどのように連携するかの概要を説明します。
seo-title: Analytics と Experience Cloud ID のリクエスト
title: Analytics と Experience Cloud ID のリクエスト
uuid: 28beed16-7ef9-4824-8e82-853930756eca
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Analytics と Experience Cloud ID のリクエスト{#analytics-and-experience-cloud-id-requests}

Experience Platform IDサービスが従来のAnalytics IDとどのように連携するかの概要を説明します。

## 概要 {#section-64d8523ff7634cb987d0c6480f587dd3}

以前は、Experience Platform IDサービスはAdobe Analyticsと緊密に統合されていました。現在も ID サービスは Analytics の重要な要素ですが、[!DNL Experience Cloud]Experience Cloud の他のソリューションや機能に対しても重要な役割を担うようになっています。この履歴により、Analytics IDのチェックまたは書き込みは、エクスペリエンスプラットフォームIDサービスのリクエストおよび [IDセットのIDで説明されている汎用プロセスとは少し異なります。](../../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a)IDチェックの操作の順序について詳しくは、AnalyticsおよびExperience Cloud ID [の設定を](../../reference/analytics-reference/analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6)参照してください。

## AMCV Cookie がブラウザーに設定されていない {#section-cccf10cd775e4a95a7e98d3c3c0ff9a9}

[!DNL Experience Cloud]（AMCV） cookie が存在しない場合、[!DNL Adobe]　への ID サービス呼び出しでは、従来の Analytics ID の有無によって異なる応答が生成されます。従来の [!DNL Analytics] ID は [s_vi Cookie](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/?f=cookies_analytics.html) に保存されます。次の表は、s_ vi cookie の状態に基づいて ID が AMCV cookie にどのように書き込まれるかを示します。

<table id="table_DC85FECE26DD424E841BA1059AF1E57F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> s_vi Cookie のステータス </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b> s_vi Cookie が設定されていない</b> </p> </td> 
   <td colname="col2"> <p>ID サービスは訪問者に <span class="keyword">Experience Cloud</span> ID（MID）を割り当てます。この MID は、<span class="keyword">Analytics</span> およびその他の <span class="keyword">Experience Cloud</span> ソリューションに対して訪問者を識別します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>s_vi Cookie が設定されている</b> </p> </td> 
   <td colname="col2"> <p>s_ vi cookieを持つサイト訪問者が最初にエクスペリエンスプラットフォームIDサービスに遭遇すると、このサービスは次のようになります。 </p> 
    <ul id="ul_BE584810280D4874AF802A9247011787"> 
     <li id="li_AA395B09A3174AF78F3EC10053E2E4F5">s_vi Cookie に保存されている <span class="keyword">Analytics</span> ID を AMCV Cookie に書き込みます。この情報は <span class="keyword">Analytics</span> ID（AID）として書き込まれます。この操作により訪問者数が影響を受けることはありません。<i></i><span class="keyword">Analytics</span> は引き続き従来の ID を使用してユーザーを識別します。 </li> 
     <li id="li_8735DE21FEA542BA8024109B8FE1E2ED">MID を AMCV Cookie に書き込みます。MID はユーザーを異なるソリューションで識別します。 </li> 
    </ul> <p> <p>注意: <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local"> 猶予期間</a>の場合、データセンターの応答には常にs_ vi cookieに保存されているレガシーIDが含まれます。猶予期間中、従来の ID は AID 値として AMCV Cookie に書き込まれます。 </p> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>s_ fid cookieによって識別されるユーザーには、従来のFID値がAMCV cookieに移行されません。s_fid Cookie を使用する場合、s_vi Cookie がなく（前述の説明を参照）サイトの新規訪問者であるかのように、ユーザーが移行されます。詳しくは、[Analytics Cookie](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/?f=cookies_analytics.html) を参照してください。

## AMCV Cookie がブラウザーに設定されている {#section-01c088fc565c4b24ba1722c7cc240310}

AMCV Cookie が存在する場合、 はその MID を [!DNL Analytics] 識別子として使用します（その Cookie に従来の [!DNL Analytics]Analytics ID 値がない場合）。