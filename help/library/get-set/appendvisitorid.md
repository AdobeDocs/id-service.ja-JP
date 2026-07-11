---
description: この関数を使用すると、ブラウザーでサードパーティ Cookie がブロックされている場合でも、複数のドメインにまたがって訪問者の ECID を共有できます。 この関数を使用するには、訪問者ID サービスを実装し、ソースドメインと宛先ドメインを所有している必要があります。 VisitorAPI.js バージョン 1.7.0 以降で利用できます。
keywords: 訪問者 ID サービス
title: appendVisitorIDsTo（クロスドメイントラッキング）
exl-id: 3e4f4e2c-e658-4124-bd0e-59c63127bdde
TQID: https://experienceleague.adobe.com/F4rWmYj6NidX861-qU8KI9RRbdwNdzP0x4CZUxPZfYw
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 432
ht-degree: 61%

---

# appendVisitorIDsTo（クロスドメイントラッキング）{#appendvisitoridsto-cross-domain-tracking}

>[!TIP]
>
>ECID が最初に（または以前に）拒否された場合、クロスドメイントラッキングは意図したとおりに機能しません。 同意が「いいえ」に設定された時点での ID であったことを考慮し、URL を介して渡された既存の ID や、以前に Cookie に存在していた既存の ID はチェックされません。

この関数を使用すると、ブラウザーでサードパーティ Cookie がブロックされている場合でも、複数のドメインにまたがって訪問者の ECID を共有できます。 この関数を使用するには、訪問者ID サービスを実装し、ソースドメインと宛先ドメインを所有している必要があります。 `VisitorAPI.js` バージョン 1.7.0以降で使用できます。

内容：

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-7251d88befd440b4b79520e33c5aa44a" format="dita" scope="local"> ブラウザーでサードパーティ Cookie がブロックされている場合の複数のドメインをまたいだ訪問者の追跡 </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-62d55f7f986542b0b9238e483d50d7b0" format="dita" scope="local"> 訪問者 ID コードサンプルの追加 </a> </li> 
 </a> </li> 
</ul>

## ブラウザーでサードパーティの Cookie がブロックされている場合に複数のドメインをまたいだ訪問者を追跡する {#section-7251d88befd440b4b79520e33c5aa44a}

訪問者ID サービスは、ユーザーがサイトにアクセスしたときに、ファーストパーティおよびサードパーティのCookieをブラウザーに書き込みます（[Cookieと訪問者ID サービス &#x200B;](../../introduction/cookies.md)を参照）。 ファーストパーティ Cookie には、訪問者の一意の ID である MID が含まれます。 サードパーティ Cookieには、訪問者ID サービスがMIDを生成するために使用する別のIDが含まれています。 ブラウザーがこのサードパーティ Cookieをブロックすると、訪問者ID サービスは次のことができません。

* サイト訪問者が別のドメインに移動したときに、その訪問者の一意の ID を再生成する。
* 同じ組織が所有する異なるドメインにわたって訪問者を追跡する。

この問題を解決するには、`Visitor.appendVisitorIDsTo( *`url`*)` を実装します。 このプロパティを使用すると、ブラウザーがサードパーティ Cookieをブロックしている場合でも、訪問者ID サービスが複数のドメインのサイト訪問者を追跡できます。 このプロパティは以下のように動作します。

* 訪問者が同じ組織の他のドメインを参照すると、`Visitor.appendVisitorIDsTo( *`url`*)` によって、元のドメインから宛先ドメインへの URL リダイレクトのクエリパラメーターとして MID が追加されます。
* 宛先ドメインの訪問者ID サービスコードは、その訪問者のIDのリクエストをAdobeに送信する代わりに、URLからMIDを抽出します。 このリクエストにはサードパーティ Cookie が含まれますが、この場合、サードパーティ Cookie を利用できません。
* 宛先ページの訪問者ID サービスコードは、渡されたMIDを使用して訪問者を追跡します。

詳しくは、コードサンプルを参照してください。

## 訪問者 ID コードサンプルの追加 {#section-62d55f7f986542b0b9238e483d50d7b0}

次のコード例では、`appendVisitorIDsTo` 関数の基本を学ぶことができます。

>[!TIP]
>
>このコードは、Adobe Analytics 拡張機能の一部であるカスタムコードエディターや、[AppMeasurement.js](https://experienceleague.adobe.com/docs/analytics/implementation/js/overview.html?lang=ja) の上部に配置できます。

```js
var adbeDomains = ["marketo.com", "figma.com", "workfront.com"];
var visitor = Visitor.getInstance("9E1005A551ED61CA0A490D45@AdobeOrg", {
  trackingServer: "sstats.adobe.com",
  trackingServerSecure: "sstats.adobe.com",
  marketingCloudServer: "sstats.adobe.com",
  marketingCloudServerSecure: "sstats.adobe.com"
});
adbeDomains.forEach(function(domain) {
  var domainRegex = RegExp(domain);
  if (!domainRegex.test(location.hostname)) {
    hrefSelector = '[href*="' + domain + '"]';
    document.querySelectorAll(hrefSelector).forEach(function(href) {
      href.addEventListener('mousedown', function(event) {
        var destinationURLWithVisitorIDs = visitor.appendVisitorIDsTo(event.currentTarget.href)
        event.currentTarget.href = destinationURLWithVisitorIDs.replace(/MCAID%3D.*%7CMCORGID/, 'MCAID%3D%7CMCORGID');
      });
    });
  }
});
```

<!-- 
>[!IMPORTANT]
>
>In order for the values passed in the URL via appendVisitorsIDsTo to be picked up, the [ovewriteCrossDomainMCIDAndAID](../function-vars/overwrite-visitor-id.md) variable must be set to true.

The following example can help you get started with `Visitor.appendVisitorIDsTo( *`url`*)`. When implemented properly, your JavaScript code could look similar to the following example.

```js
//Code on Domain A 
var destinationURL = "www.destination.com"; 
 
//Call the Visitor ID Service 
var visitor = Visitor.getInstance(...); 
 
//Append visitor IDs to the destination URL 
var destinationURLWithVisitorIDs = visitor.appendVisitorIDsTo(destinationURL); 
     //Result of appendVisitorIDsTo includes destination URL, ECID (MCMID), and Analytics ID (MCAID) 
     "www.destination.com?adobe_mc=MCMID=1234|MCAID=5678"
//Redirect to the destination
``` 
-->

<!--
## SDK Support {#section-168e313df6054af0a7e27b9fa0d69640}

<table id="table_6E7152B4FD2B4C4D8C9477C68204C4FF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Support for </th> 
   <th colname="col2" class="entry"> See </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>SDK</b> </p> </td> 
   <td colname="col2"> 
    <ul id="ul_9D7933FF68EE4C71BAE999B3747F8398"> 
     <li id="li_9036C76AAECC4E639C23020C0C9F2AF8"> <a href="https://experienceleague.adobe.com/docs/mobile-services/android/experience-cloud-android/mc-methods.html?lang=ja" format="https" scope="external"> Android Visitor ID Service Methods </a> </li> 
     <li id="li_E49D357905584674BFDFE348345B3849"> <a href="https://experienceleague.adobe.com/docs/mobile-services/ios/exp-cloud-ios/mc-methods.html?lang=ja" format="https" scope="external"> iOS Visitor ID Service Methods </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table> 
-->

