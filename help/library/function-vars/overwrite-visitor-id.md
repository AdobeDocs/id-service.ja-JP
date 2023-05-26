---
description: あるドメインから別のドメインに訪問者が移動すると、訪問者の Experience Cloud ID と Analytics ID がこのプロパティで上書きされます。 ID を上書きするには、各ドメインで ID サービスを所有し実装してあることが必要です。 このコードでは、制御の対象でないドメインで ID を上書きできません。
keywords: ID サービス
title: overwriteCrossDomainMCIDAndAID
exl-id: 726261b1-c8d0-4b12-b0cb-52d7e21e7fac
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 100%

---

# overwriteCrossDomainMCIDAndAID{#overwritecrossdomainmcidandaid}

あるドメインから別のドメインに訪問者が移動すると、訪問者の Experience Cloud ID と Analytics ID がこのプロパティで上書きされます。 ID を上書きするには、各ドメインで ID サービスを所有し実装してあることが必要です。 このコードでは、制御の対象でないドメインで ID を上書きできません。

**構文：** `Visitor.overwriteCrossDomainMCIDAndAID: true|false`（デフォルトは `false`）

**コードサンプル**

JavaScript コードは次の例のようになります。

```js
//Call the ID service 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE", { 
     ... 
 
     //Set overwrite property 
     overwriteCrossDomainMCIDAndAID: true 
}); 
```

**使用例**

サイト訪問者を追跡するために、ID サービスは、[!DNL Experience Cloud] ID（MID）をブラウザー Cookie に書き込みます。別のドメインの ID サービスで設定された既存の MID を上書きした方がよい一般的なユースケースの一覧と説明を次の表に示します。

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
      <li id="li_FF71FD1FB9DD4702B675A140FAD2B481">ドメインごとに独自のランディングページがある。 </li> 
      <li id="li_78F75469D32D473B93148B46D35E67F1">訪問者には、ドメイン B への以前の訪問によって既に cookie（および MID）が設定されている。 </li> 
      <li id="li_305CE5138EEB43D3BF9CE38D1E7FFA04">訪問者がドメイン A からドメイン B に移動した場合、訪問者を一貫して識別する必要がある。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>ランディングページおよびコンバージョンページ間の訪問者の識別</b> </p> </td> 
   <td colname="col2"> <p>ドメイン A および B を所有しているとします。この場合、以下の場合に <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> を設定できます。 </p> 
    <ul id="ul_7BEBFD523A2F47AFB6963536E43692D0"> 
     <li id="li_71586080489340E2A6C0B263F231E3DE">ドメイン A はランディングページである。 </li> 
     <li id="li_4E3D3CB380EE4F1BAC4CD752194AE8DE">ドメイン B は、別個のコンバージョンページ、ブッキングページ、他のワークフロー最終ページのいずれかである。 </li> 
     <li id="li_FB393B16CFAC4D2D9B2328EBA4573C1A">訪問者には、ドメイン B への以前の訪問によって既に cookie（および MID）が設定されており、これらがサーバーサイド MID よりも望ましくないクライアントサイド MID であることがわかっている。 </li> 
     <li id="li_36FC138530A4476A995C0F9FD73C41DE">訪問者がドメイン A からドメイン B に移動した場合、訪問者を一貫して識別する必要がある。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>モバイルアプリから web ブラウザーに移動する訪問者の識別</b> </p> </td> 
   <td colname="col2"> <p>このユースケースは少し異なります。 ユーザーがモバイルアプリから web サイトに移動するときに、ユーザーを識別する必要があります。この場合、訪問者には、既にモバイルアプリによってローカルに MID が設定されており、web サイトの cookie には別の MID が設定されています。 <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> を設定して、ブラウザーの Cookie に設定された MID をモバイルアプリで設定された MID で上書きできます。 </p> </td> 
  </tr> 
 </tbody> 
</table>
