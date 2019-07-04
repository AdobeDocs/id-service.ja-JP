---
description: このプロパティは、あるドメインから 2 番目のドメインに移動すると、訪問者の Experience Cloud および Analytics ID を上書きします。ID を上書きするには、ID サービスを所有し、各ドメインに実装している必要があります。このコードは、制御していないドメインの ID を上書きできません。
keywords: ID サービス
seo-description: このプロパティは、あるドメインから 2 番目のドメインに移動すると、訪問者の Experience Cloud および Analytics ID を上書きします。ID を上書きするには、ID サービスを所有し、各ドメインに実装している必要があります。このコードは、制御していないドメインの ID を上書きできません。
seo-title: overwriteCrossDomainMCIDAndAID
title: overwriteCrossDomainMCIDAndAID
uuid: 8e48127a-ac62-4ea0-9756-2a27b20ecbcf
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# overwriteCrossDomainMCIDAndAID{#overwritecrossdomainmcidandaid}

このプロパティは、あるドメインから 2 番目のドメインに移動すると、訪問者の Experience Cloud および Analytics ID を上書きします。ID を上書きするには、ID サービスを所有し、各ドメインに実装している必要があります。このコードは、制御していないドメインの ID を上書きできません。

**構文：** `Visitor.overwriteCrossDomainMCIDAndAID: true|false`（デフォルトは `false`）

**コードサンプル**

JavaScript コードは、以下の例のようになります。

```js
//Call the ID service 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE", { 
     ... 
 
     //Set overwrite property 
     overwriteCrossDomainMCIDAndAID: true 
}); 
```

**使用例**

サイト訪問者を追跡するために、ID サービスは、[!DNL Experience Cloud] ID（MID）をブラウザー Cookie に書き込みます。以下の表に、別のドメインの ID サービスによって設定された既存の MID を上書きしたい場合の一般的な使用例を示して説明します。

<table id="table_FC1AF6551D6646E0BF1C4FB7C1316EBB"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 使用例 </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>様々なドメインのランディングページでの訪問者の識別</b> </p> </td> 
   <td colname="col2"> <p>ドメイン A および B を所有しているとします。この場合、以下の場合に <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> を設定できます。 </p> <p> 
     <ul id="ul_FB4704BFE7134F1688E34BF1A36627B7"> 
      <li id="li_FF71FD1FB9DD4702B675A140FAD2B481">各ドメインに独自のランディングページがある。 </li> 
      <li id="li_78F75469D32D473B93148B46D35E67F1">訪問者には、ドメイン B への以前の訪問から、既に Cookie（および MID）が設定されている。 </li> 
      <li id="li_305CE5138EEB43D3BF9CE38D1E7FFA04">訪問者がドメイン A からドメイン B に来る場合、一貫して識別したい。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>ランディングページとコンバージョンページの間での訪問者の識別</b> </p> </td> 
   <td colname="col2"> <p>ドメイン A および B を所有しているとします。この場合、以下の場合に <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> を設定できます。 </p> 
    <ul id="ul_7BEBFD523A2F47AFB6963536E43692D0"> 
     <li id="li_71586080489340E2A6C0B263F231E3DE">ドメイン A はランディングページである。 </li> 
     <li id="li_4E3D3CB380EE4F1BAC4CD752194AE8DE">ドメイン B は、個別のコンバージョン、予約、またはその他のワークフローの最後のページである。 </li> 
     <li id="li_FB393B16CFAC4D2D9B2328EBA4573C1A">訪問者には、ドメイン B への以前の訪問から、既に Cookie（および MID）が設定されていて、それらは、サーバー側 MID よりも望ましくないクライアント側 MID であることがわかっている。 </li> 
     <li id="li_36FC138530A4476A995C0F9FD73C41DE">訪問者がドメイン A からドメイン B に来る場合、一貫して識別したい。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>モバイルアプリから Web ブラウザーへの訪問者の識別</b> </p> </td> 
   <td colname="col2"> <p>この事例は、少し異なります。モバイルアプリから Web サイトに移動するユーザーの識別に関係します。この場合、訪問者は既にモバイルアプリによってローカルで MID が設定されていて、Web サイトの Cookie には別の MID が設定されています。<span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> を設定して、ブラウザーの Cookie に設定された MID をモバイルアプリで設定された MID で上書きできます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

