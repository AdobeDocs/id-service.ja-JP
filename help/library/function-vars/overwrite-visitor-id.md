---
description: このプロパティは、訪問者のExperience CloudとAnalytics IDが1つのドメインから2つ目のドメインに移動すると、それらを上書きします。 IDを上書きするには、IDサービスを所有し、各ドメインに実装している必要があります。 このコードでは、制御していないドメインのIDを上書きできません。
keywords: ID Service
seo-description: このプロパティは、訪問者のExperience CloudとAnalytics IDが1つのドメインから2つ目のドメインに移動すると、それらを上書きします。 IDを上書きするには、IDサービスを所有し、各ドメインに実装している必要があります。 このコードでは、制御していないドメインのIDを上書きできません。
seo-title: overwriteCrossDomainMCIDAndAID
title: overwriteCrossDomainMCIDAndAID
uuid: 8e48127a-ac62-4ea0-9756-2a27b20ecbcf
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 19%

---


# overwriteCrossDomainMCIDAndAID{#overwritecrossdomainmcidandaid}

このプロパティは、訪問者のExperience CloudとAnalytics IDが1つのドメインから2つ目のドメインに移動すると、それらを上書きします。 IDを上書きするには、IDサービスを所有し、各ドメインに実装している必要があります。 このコードでは、制御していないドメインのIDを上書きできません。

**構文：** `Visitor.overwriteCrossDomainMCIDAndAID: true|false`（デフォルトは `false`）

**コードサンプル**

JavaScriptコードは次の例のようになります。

```js
//Call the ID service 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE", { 
     ... 
 
     //Set overwrite property 
     overwriteCrossDomainMCIDAndAID: true 
}); 
```

**使用例**

サイト訪問者を追跡するために、ID サービスは、[!DNL Experience Cloud] ID（MID）をブラウザー Cookie に書き込みます。次の表のリストと、別のドメインのIDサービスによって設定された既存のMIDを上書きする場合の一般的な使用例を説明します。

<table id="table_FC1AF6551D6646E0BF1C4FB7C1316EBB"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 使用例 </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>異なるドメインランディングページの訪問者の識別</b> </p> </td> 
   <td colname="col2"> <p>ドメイン A および B を所有しているとします。この場合、以下の場合に <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> を設定できます。 </p> <p> 
     <ul id="ul_FB4704BFE7134F1688E34BF1A36627B7"> 
      <li id="li_FF71FD1FB9DD4702B675A140FAD2B481">各ドメインには独自のランディングページがあります。 </li> 
      <li id="li_78F75469D32D473B93148B46D35E67F1">訪問者には、ドメインBへの以前の訪問から、既にcookie（およびMID）が設定されています。 </li> 
      <li id="li_305CE5138EEB43D3BF9CE38D1E7FFA04">訪問者がドメインAからドメインBに来る場合は、一貫して識別する必要がある。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>ランディングページとコンバージョンページの間の訪問者の特定</b> </p> </td> 
   <td colname="col2"> <p>ドメイン A および B を所有しているとします。この場合、以下の場合に <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> を設定できます。 </p> 
    <ul id="ul_7BEBFD523A2F47AFB6963536E43692D0"> 
     <li id="li_71586080489340E2A6C0B263F231E3DE">ドメインAはランディングページです。 </li> 
     <li id="li_4E3D3CB380EE4F1BAC4CD752194AE8DE">ドメインBは、個別のコンバージョン、予約、またはその他のワークフローの最後のページです。 </li> 
     <li id="li_FB393B16CFAC4D2D9B2328EBA4573C1A">訪問者には、ドメインBへの以前の訪問から既にcookie（およびMID）が設定されており、これらは、サーバー側MIDよりも望ましくないクライアント側MIDであることがわかっている。 </li> 
     <li id="li_36FC138530A4476A995C0F9FD73C41DE">訪問者がドメインAからドメインBに来る場合は、一貫して識別する必要がある。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>モバイルアプリからWebブラウザーへの訪問者の識別</b> </p> </td> 
   <td colname="col2"> <p>この使用例は、少し異なります。 モバイルアプリからWebサイトに移動するユーザーの識別に関係します。 この場合、訪問者には、既にモバイルアプリによってローカルにMIDが設定されており、Webサイトのcookieには別のMIDが設定されています。 <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> を設定して、ブラウザーの Cookie に設定された MID をモバイルアプリで設定された MID で上書きできます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

