---
description: この関数を使用すると、ブラウザーでサードパーティ Cookie がブロックされている場合でも、複数のドメインにまたがって訪問者の Experience Cloud ID を共有できます。この関数を使用するには、ID サービスを実装し、ソースドメインおよび宛先ドメインを所有している必要があります。VisitorAPI.js バージョン 1.7.0 以降で利用できます。
keywords: ID サービス
title: appendVisitorIDsTo（クロスドメイントラッキング）
exl-id: 3e4f4e2c-e658-4124-bd0e-59c63127bdde
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 100%

---

# appendVisitorIDsTo（クロスドメイントラッキング） {#appendvisitoridsto-cross-domain-tracking}

この関数を使用すると、ブラウザーでサードパーティ Cookie がブロックされている場合でも、複数のドメインにまたがって訪問者の Experience Cloud ID を共有できます。この関数を使用するには、ID サービスを実装し、ソースドメインおよび宛先ドメインを所有している必要があります。VisitorAPI.js バージョン 1.7.0 以降で利用できます。

内容：

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-7251d88befd440b4b79520e33c5aa44a" format="dita" scope="local"> ブラウザーでサードパーティ Cookie がブロックされている場合の複数のドメインをまたいだ訪問者の追跡 </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-62d55f7f986542b0b9238e483d50d7b0" format="dita" scope="local"> 訪問者 ID コードサンプルの追加 </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-168e313df6054af0a7e27b9fa0d69640" format="dita" scope="local"> Dynamic Tag Management（DTM）および SDK のサポート </a> </li> 
</ul>

## ブラウザーでサードパーティ Cookie がブロックされている場合の複数のドメインをまたいだ訪問者の追跡 {#section-7251d88befd440b4b79520e33c5aa44a}

ID サービスは、ユーザーがサイトを訪問したときにファーストパーティ Cookie とサードパーティ Cookie をブラウザーに書き込みます（[Cookie と Experience Cloud Identity Service ](../../introduction/cookies.md)を参照）。ファーストパーティ Cookie には、訪問者の一意の ID である MID が含まれます。サードパーティ Cookie には、ID サービスで MID を生成するために使用される別の ID が含まれます。ブラウザーでサードパーティ Cookie がブロックされている場合、ID サービスは以下のことができなくなります。

* サイト訪問者が別のドメインに移動したときに、その訪問者の一意の ID を再生成する。
* 同じ組織が所有する異なるドメインにわたって訪問者を追跡する。

この問題を解決するには、` Visitor.appendVisitorIDsTo( *`url`*)` を実装します。これにより、ブラウザーがサードパーティ Cookie をブロックしても、ID サービスが複数ドメインにわたってサイト訪問者を適切に追跡できます。このプロパティは以下のように動作します。

* 訪問者が同じ組織の他のドメインを参照すると、` Visitor.appendVisitorIDsTo( *`url`*)` によって、元のドメインから宛先ドメインへの URL リダイレクトのクエリパラメーターとして MID が追加されます。
* アドビに訪問者の ID のリクエストを送信するのではなく、宛先ドメインの ID サービスコードによって、URL から MID が抽出されます。このリクエストにはサードパーティ Cookie が含まれますが、この場合、サードパーティ Cookie を利用できません。
* 宛先ページの ID サービスコードは、MID で渡された値を使用して訪問者を追跡します。

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
     "www.destination.com?adobe_mc=MCMID=1234|MCAID=5678"
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
     <li id="li_9036C76AAECC4E639C23020C0C9F2AF8"> <a href="https://docs.adobe.com/content/help/ja-JP/mobile-services/android/experience-cloud-android/mc-methods.html" format="https" scope="external"> Android ID サービスメソッド </a> </li> 
     <li id="li_E49D357905584674BFDFE348345B3849"> <a href="https://docs.adobe.com/content/help/ja-JP/mobile-services/ios/exp-cloud-ios/mc-methods.html" format="https" scope="external"> iOS ID サービスメソッド </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
