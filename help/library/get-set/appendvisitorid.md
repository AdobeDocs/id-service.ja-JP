---
description: この関数を使用すると、ブラウザーでサードパーティ Cookie がブロックされている場合でも、複数のドメインにまたがって訪問者の Experience Cloud ID を共有できます。この関数を使用するには、ID サービスを実装し、ソースドメインおよび宛先ドメインを所有している必要があります。VisitorAPI.js バージョン 1.7.0 以降で利用できます。
keywords: ID サービス
seo-description: この関数を使用すると、ブラウザーでサードパーティ Cookie がブロックされている場合でも、複数のドメインにまたがって訪問者の Experience Cloud ID を共有できます。この関数を使用するには、ID サービスを実装し、ソースドメインおよび宛先ドメインを所有している必要があります。VisitorAPI.js バージョン 1.7.0 以降で利用できます。
seo-title: appendVisitorIDsTo（クロスドメイントラッキング）
title: appendVisitorIDsTo（クロスドメイントラッキング）
uuid: 06b453ee-73c5-4625-82d9-877ad2b4f702
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# appendVisitorIDsTo（クロスドメイントラッキング）{#appendvisitoridsto-cross-domain-tracking}

この関数を使用すると、ブラウザーでサードパーティ Cookie がブロックされている場合でも、複数のドメインにまたがって訪問者の Experience Cloud ID を共有できます。この関数を使用するには、ID サービスを実装し、ソースドメインおよび宛先ドメインを所有している必要があります。VisitorAPI.js バージョン 1.7.0 以降で利用できます。

内容：

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-7251d88befd440b4b79520e33c5aa44a" format="dita" scope="local"> ブラウザーでサードパーティ Cookie がブロックされている場合に複数のドメインをまたいで訪問者を追跡する </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-62d55f7f986542b0b9238e483d50d7b0" format="dita" scope="local"> 訪問者 ID コードサンプルを追加する </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-168e313df6054af0a7e27b9fa0d69640" format="dita" scope="local"> Dynamic Tag Management（DTM）および SDK のサポート </a> </li> 
</ul>

## ブラウザーでサードパーティ Cookie がブロックされている場合に複数のドメインをまたいで訪問者を追跡する {#section-7251d88befd440b4b79520e33c5aa44a}

IDサービスは、訪問者がサイトを訪問したときにファーストパーティCookieとサードパーティCookieをブラウザーに書き込みます（ [cookieとエクスペリエンスプラットフォームIDサービス](../../introduction/cookies.md) を参照）。ファーストパーティ Cookie には、訪問者の一意の ID である MID が含まれます。サードパーティ Cookie には、ID サービスで MID を生成するために使用される別の ID が含まれます。ブラウザーでサードパーティ Cookie がブロックされている場合、ID サービスは以下のことができなくなります。

* サイト訪問者が別のドメインに移動したときに、その訪問者の一意の ID を再生成する。
* 同じ組織が所有する異なるドメインにわたって訪問者を追跡する。

この問題を解決するには、URLを実装 ` Visitor.appendVisitorIDsTo( *``*)`してください。これにより、ブラウザーがサードパーティ Cookie をブロックしても、ID サービスが複数ドメインにわたってサイト訪問者を適切に追跡できます。このプロパティは以下のように動作します。

* 訪問者が他のドメインを閲覧するとき、 ` Visitor.appendVisitorIDsTo( *`URL`*)` は元のドメインから宛先ドメインへのURLリダイレクトにクエリパラメーターとしてMIDを追加します。
* アドビに訪問者の ID のリクエストを送信するのではなく、宛先ドメインの ID サービスコードによって、URL から MID が抽出されます。このリクエストにはサードパーティ Cookie が含まれますが、このケースではサードパーティ Cookie を利用できません。
* 宛先ページの ID サービスコードは、MID で渡された値を使用して訪問者を追跡します。

詳しくは、コードサンプルを参照してください。

## 訪問者 ID コードサンプルを追加する {#section-62d55f7f986542b0b9238e483d50d7b0}

次の例は、URLの使用 ` Visitor.appendVisitorIDsTo( *`を開始するのに役立ち`*)`ます。設定が完了すると、JavaScript コードは以下の例のようになります。

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
   <th colname="col1" class="entry">  サポート対象 </th> 
   <th colname="col2" class="entry"> 詳しくは、 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>DTM</b> </p> </td> 
   <td colname="col2"> <p> <a href="https://helpx.adobe.com/dtm/kb/how-to-set-marketing-cloud-id-service-helper-function-in-adobe-d.html" format="https" scope="external"> DTM で appendVisitorIDTo 関数を設定する </a> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>SDK</b> </p> </td> 
   <td colname="col2"> 
    <ul id="ul_9D7933FF68EE4C71BAE999B3747F8398"> 
     <li id="li_9036C76AAECC4E639C23020C0C9F2AF8"> <a href="https://marketing.adobe.com/resources/help/en_US/mobile/android/mc_methods.html" format="https" scope="external"> Android ID サービスメソッド </a> </li> 
     <li id="li_E49D357905584674BFDFE348345B3849"> <a href="https://marketing.adobe.com/resources/help/en_US/mobile/ios/mc_methods.html" format="https" scope="external"> iOS ID サービスメソッド </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

