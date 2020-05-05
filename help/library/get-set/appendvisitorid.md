---
description: この関数を使用すると、ブラウザーがサードパーティcookieをブロックした場合に、複数のドメインで訪問者のExperience Cloud IDを共有できます。 この関数を使用するには、ID サービスを実装し、ソースドメインおよび宛先ドメインを所有している必要があります。VisitorAPI.js バージョン 1.7.0 以降で利用できます。
keywords: ID Service
seo-description: この関数を使用すると、ブラウザーがサードパーティcookieをブロックした場合に、複数のドメインで訪問者のExperience Cloud IDを共有できます。 この関数を使用するには、ID サービスを実装し、ソースドメインおよび宛先ドメインを所有している必要があります。VisitorAPI.js バージョン 1.7.0 以降で利用できます。
seo-title: appendVisitorIDsTo（クロスドメイントラッキング）
title: appendVisitorIDsTo（クロスドメイントラッキング）
uuid: 06b453ee-73c5-4625-82d9-877ad2b4f702
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# appendVisitorIDsTo（クロスドメイントラッキング）{#appendvisitoridsto-cross-domain-tracking}

この関数を使用すると、ブラウザーがサードパーティcookieをブロックした場合に、複数のドメインで訪問者のExperience Cloud IDを共有できます。 この関数を使用するには、ID サービスを実装し、ソースドメインおよび宛先ドメインを所有している必要があります。VisitorAPI.js バージョン 1.7.0 以降で利用できます。

内容：

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-7251d88befd440b4b79520e33c5aa44a" format="dita" scope="local"> ブラウザーでサードパーティ Cookie がブロックされている場合の複数のドメインをまたいだ訪問者の追跡 </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-62d55f7f986542b0b9238e483d50d7b0" format="dita" scope="local"> 訪問者 ID コードサンプルの追加 </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-168e313df6054af0a7e27b9fa0d69640" format="dita" scope="local"> Dynamic Tag Management（DTM）および SDK のサポート </a> </li> 
</ul>

## ブラウザーでサードパーティ Cookie がブロックされている場合の複数のドメインをまたいだ訪問者の追跡 {#section-7251d88befd440b4b79520e33c5aa44a}

ID サービスは、ユーザーがサイトを訪問したときにファーストパーティ Cookie とサードパーティ Cookie をブラウザーに書き込みます（[Cookie と Experience Cloud Identity Service ](../../introduction/cookies.md)を参照）。ファーストパーティcookieには、その訪問者の一意のIDであるMIDが含まれます。 サードパーティcookieには、IDサービスがMIDを生成する際に使用する別のIDが含まれます。 ブラウザーがこのサードパーティCookieをブロックした場合、IDサービスは次の操作を行えません。

* サイト訪問者が別のドメインに移動する際に、そのサイトドメインの一意のIDを再生成してください。
* 組織が所有する異なるドメイン間で訪問者を追跡します。

この問題を解決するには、` Visitor.appendVisitorIDsTo( *`url`*)` を実装します。このプロパティを使用すると、ブラウザーがサードパーティcookieをブロックしている場合でも、IDサービスは複数のドメインにわたってサイト訪問者を追跡できます。 次のように機能します。

* 訪問者が同じ組織の他のドメインを参照すると、` Visitor.appendVisitorIDsTo( *`url`*)` によって、元のドメインから宛先ドメインへの URL リダイレクトのクエリパラメーターとして MID が追加されます。
* 宛先訪問者のIDのリクエストをアドビに送信する代わりに、宛先ドメインのIDサービスコードがURLからMIDを抽出します。 このリクエストにはサードパーティ Cookie が含まれますが、この場合、サードパーティ Cookie を利用できません。
* 宛先ページのIDサービスコードは、渡されたMIDを使用して訪問者を追跡します。

詳しくは、コードサンプルを参照してください。

## 訪問者 ID コードサンプルの追加 {#section-62d55f7f986542b0b9238e483d50d7b0}

次の例では、` Visitor.appendVisitorIDsTo( *`url`*)` の基本を学ぶことができます。設定が完了すると、JavaScript コードは以下の例のようになります。

```js
//Code on Domain A 
var destinationURL = "www.destination.com"; 
 
//Call the ID service 
var visitor = Visitor.getInstance(...); 
 
//Append visitor IDs to the destination URL 
var destinationURLWithVisitorIDs = visitor.appendVisitorIDsTo(destinationURL); 
     //Result of appendVisitorIDsTo includes destination URL, Experience Cloud ID (MCMID), and Analytics ID (MCAID) 
     "www.destination.com?adobe_mc=MCMID=1234|MCAID=5678 
<draft-comment>
  |TS=123675879 
</draft-comment>" 
 
//Redirect to the destination
```

## Dynamic Tag Management（DTM）および SDK のサポート {#section-168e313df6054af0a7e27b9fa0d69640}

<table id="table_6E7152B4FD2B4C4D8C9477C68204C4FF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> サポート対象 </th> 
   <th colname="col2" class="entry"> 詳しくは、 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>DTM</b> </p> </td> 
   <td colname="col2"> <p> <a href="https://helpx.adobe.com/jp/dtm/kb/how-to-set-marketing-cloud-id-service-helper-function-in-adobe-d.html" format="https" scope="external"> DTM で appendVisitorIDTo 関数を設定する </a> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>SDK</b> </p> </td> 
   <td colname="col2"> 
    <ul id="ul_9D7933FF68EE4C71BAE999B3747F8398"> 
     <li id="li_9036C76AAECC4E639C23020C0C9F2AF8"> <a href="https://docs.adobe.com/content/help/en/mobile-services/android/experience-cloud-android/mc-methods.html" format="https" scope="external"> Android ID サービスメソッド </a> </li> 
     <li id="li_E49D357905584674BFDFE348345B3849"> <a href="https://docs.adobe.com/content/help/en/mobile-services/ios/exp-cloud-ios/mc-methods.html" format="https" scope="external"> iOS ID サービスメソッド </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

