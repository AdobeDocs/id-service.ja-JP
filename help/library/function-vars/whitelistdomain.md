---
description: これらの設定により、iFrameに実装されたIDサービスコードの異なるインスタンスと親ページ上の異なるインスタンス間で通信が可能になります。 親ページやドメインを制御している場合と制御していない場合の2つの特定の使用例、および制御するドメインのiFrameにIDサービスコードを読み込んでいる場合の問題を解決できるように設計されています。 これらは、VisitorAPI.jsコードバージョン2.2以降で使用できます。
keywords: ID Service
seo-description: これらの設定により、iFrameに実装されたIDサービスコードの異なるインスタンスと親ページ上の異なるインスタンス間で通信が可能になります。 親ページやドメインを制御している場合と制御していない場合の2つの特定の使用例、および制御するドメインのiFrameにIDサービスコードを読み込んでいる場合の問題を解決できるように設計されています。 これらは、VisitorAPI.jsコードバージョン2.2以降で使用できます。
seo-title: whitelistParentDomain および whitelistIframeDomains
title: whitelistParentDomain および whitelistIframeDomains
uuid: 6b66a4d0-fea2-4d98-963e-0c4f4ab1efb6
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# whitelistParentDomain および whitelistIframeDomains{#whitelistparentdomain-and-whitelistiframedomains}

これらの設定により、iFrameに実装されたIDサービスコードの異なるインスタンスと親ページ上の異なるインスタンス間で通信が可能になります。 親ページやドメインを制御している場合と制御していない場合の2つの特定の使用例、および制御するドメインのiFrameにIDサービスコードを読み込んでいる場合の問題を解決できるように設計されています。 これらは、VisitorAPI.jsコードバージョン2.2以降で使用できます。

内容：

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-f645198bbaba4fba8961acb6e88d1470" format="dita" scope="local">構文</a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-09d0049fe88a473baa69d404c50bf8ae" format="dita" scope="local"> コードサンプル </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-fc2eeb93546b406fae3b102dbcd11de7" format="dita" scope="local"> 使用例 </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-2b1ce31fab034e1ca0f6b1c3cc57a6e2" format="dita" scope="local"> 設定の安全性とセキュリティ </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-30c6a9f4dcdc4265a1149260b97cc057" format="dita" scope="local"> サポートされる訪問者 API メソッド </a> </li> 
</ul>

## 構文{#section-f645198bbaba4fba8961acb6e88d1470}

このコードを使用する場合は、両方の設定要素が必要です。

<table id="table_237108A4D40F4AAC981D0060BA68F881"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 設定の構文 </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> whitelistParentDomain: "<span class="varname">親ページのドメイン名</span>" </span> </p> </td> 
   <td colname="col2"> <p>文字列として渡される単一のドメイン名を受け入れます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> whitelistIframeDomains: [ <span class="varname"> "iFrame ドメイン","iFrame ドメイン","iFrame ドメイン" </span>] </span> </p> </td> 
   <td colname="col2"> <p>配列として渡される 1 つ以上の iFrame ドメイン名を受け入れます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## コードサンプル {#section-09d0049fe88a473baa69d404c50bf8ae}

設定が完了すると、[!UICONTROL ID サービス]コードはこの例のようになります。

```js
//Instantiate Visitor 
var visitor = Visitor.getInstance("Insert Experience Cloud Organization ID here",{ 
 ... 
 //Add parent page domain name and iFrame domain names 
 whitelistParentDomain: "parentpageA.com", 
 whitelistIframeDomains: ["iFrameDomain1.com","iFrameDomain2.com"], 
 ... 
 } 
);
```

## 使用例 {#section-fc2eeb93546b406fae3b102dbcd11de7}

これらの設定は、ブラウザーがサードパーティcookieをブロックする場合、および次のいずれかの条件が適用される場合、IDサービスcookieを設定し、訪問者IDを割り当てる問題の解決に役立ちます。

* 親ページ/ドメインを制御していない。
* IDサービスコードは親ページにインストールされていませんが、iFrameに実装されています。

>[!TIP]
>
>また、 [ビデオハートビートを含むiFrameでビデオを提供する場合は、これらの設定を実装する必要がある場合があります](https://docs.adobe.com/content/help/ja-JP/media-analytics/using/media-overview.html)。 ビデオハートビートが正しく機能するには、IDサービスID(MID)が必要です。

**使用例1: このブラウザーはサードパーティCookieをブロックし、IDサービスはiFrameと親ページに実装されます**

<table id="table_B479AA96DBE64685A253A6DF98D81B31"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 使用例の要素 </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>条件</b> </p> </td> 
   <td colname="col2"> <p>この使用例には、次の条件が含まれます。 </p> <p> 
     <ul id="ul_DC748846585745B0AB74398D82BDA53A"> 
      <li id="li_6E04CF0B6A204B4D8856656B0C9EF2A5">会社Aは、ホームページにIDサービスを実装します。 </li> 
      <li id="li_B53AE0F0C69844E7B6C4D3464C57883B">会社Aは、iFrameでIDサービスをホームページに実装しています。 </li> 
      <li id="li_07E0A6D7BEB140E4B9FB6C7B9629B860">会社Aは親ページとiFrameを所有し、両方にIDサービスを実装しています。 </li> 
      <li id="li_76967BD69DDB40A8A9C915DADC58AC62">顧客が、サードパーティcookieをブロックするブラウザーに親ページを読み込みます。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>結果</b> </p> </td> 
   <td colname="col2"> <p>次の条件の場合、IDサービスは次の操作を行います。 </p> <p> 
     <ul id="ul_12356701501E40DFA57903494FFE58F7"> 
      <li id="li_B57EDF1B0762486F95FA6526C047390C">親ページで正しく機能します。 AMCV cookieをリクエストおよび設定し、サイト訪問者に一意のIDを割り当てます。 </li> 
      <li id="li_BA9F42C759E747EAAE14DD3FBB6130A5">iFrameでは機能しません。 これは、ブラウザーがiFrameをサードパーティドメインと見なし、IDサービスがAMCV cookieを設定できないためです。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>ソリューション</b> </p> </td> 
   <td colname="col2"> <p>これらのホワイトリスト設定を使用して、iFrame の ID サービス <span class="codeph">Visitor.getInstance</span> 関数を変更します。コードで親ドメインと子ドメインを指定します。 これらの設定により、iFrameのIDサービスコードは、訪問者IDの親ページにあるIDサービスコードを確認できます。 </p> <p>iFrame内のIDサービスコードが応答の親ページを受け取らない場合、これらの設定によってローカル訪問者IDが生成されます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**使用例2: 制御しない、またはIDサービスを使用しない親ページに埋め込まれたiFrameからIDをリクエストする**

<table id="table_1F21710F9D5F493BA6BA5974F2966DF4"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 使用例の要素 </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>条件</b> </p> </td> 
   <td colname="col2"> <p>この使用例には、次の条件が含まれます。 </p> <p> 
     <ul id="ul_356E8FB0B1D14F46A844FE5281967E28"> 
      <li id="li_1285D945361842268B46FB492A3B5AA5">会社AはIDサービスを使用しません。 </li> 
      <li id="li_880D6D473F8342FF9BB49FCE111FD61A">会社Aがページ上のiFrameを読み込みます。 このiFrameは会社Bが所有し、会社Aとは別のドメインに読み込まれます。 </li> 
      <li id="li_7988F0272B094FE0B398006AD4E6F81B">ブラウザーは、サードパーティCookieをブロックします。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>結果</b> </p> </td> 
   <td colname="col2"> <p>次の条件の場合、IDサービスは次の操作を行います。 </p> <p> 
     <ul id="ul_A92D90896E5A42C5804AC5CE83E8EB25"> 
      <li id="li_9734EA9C5D9D4F908DE783188C9E5530">iFrameでは機能しません。 これは、ブラウザーがiFrameをサードパーティドメインと見なし、IDサービスがAMCV cookieを設定できないためです。 </li> 
      <li id="li_3F4BE9048E774902A867D67E5A80674D">会社Aはこのサービスを使用していないため、親ページから訪問者IDを取得できません。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>ソリューション</b> </p> </td> 
   <td colname="col2"> <p>これらのホワイトリスト設定を使用して、iFrame の ID サービス <span class="codeph">Visitor.getInstance</span> 関数を変更します。コードで親ドメインと子ドメインを指定します。 これらの設定により、iFrameのIDサービスコードは、訪問者IDの親ページにあるIDサービスコードを確認できます。 </p> <p>iFrame内のIDサービスコードが応答の親ページを受け取らない場合、これらの設定によってローカル訪問者IDが生成されます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 設定の安全性とセキュリティ {#section-2b1ce31fab034e1ca0f6b1c3cc57a6e2}

以下の理由から、これらの設定は安全に実装できます。

* 親ドメインとiFrameドメインに実装されるIDサービスでは、同じ組織IDを使用する必要があります。 これらのホワイトリストの設定は、親の組織IDとiFrameの組織IDが異なる場合は機能しません。
* これらの設定は、コードで指定されたドメインおよびiFrameとのみ通信します。
* iFrameと親ページ間の通信は、特定の形式に従います。 親ページのIDサービスが、期待された形式で要求を受け取らない場合、この共有プロセスは失敗します。

## サポートされる訪問者 API メソッド {#section-30c6a9f4dcdc4265a1149260b97cc057}

これらのホワイトリストの設定を実装する場合、IDサービスは限られた一連のパブリックAPIメソッドをサポートします。 サポートされる方法は、前述の使用事例のシナリオによって異なります。

<table id="table_0FF9E529FD1C43A8A3B2B0D789C8E83C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 使用例 </th> 
   <th colname="col2" class="entry"> サポートされるメソッド </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>例 1</b> </p> </td> 
   <td colname="col2"> <p> 
     <ul id="ul_99FAC8608F4C4B39805EEAA6297DB771"> 
      <li id="li_B13F6C4119F44F17963794B1E2046B1F"> <span class="codeph"> getMarketingCloudID </span> </li> 
      <li id="li_9C1B5C00A17F467CAB7EFE5F0D040777"> <span class="codeph"> getAudienceManagerLocationHint </span> </li> 
      <li id="li_30D4608F4C3849659FCBA97D88A10F0C"> <span class="codeph"> getAudienceManagerBlob </span> </li> 
      <li id="li_BA359596C80147EEA89CABCE83F123CA"> <span class="codeph"> getSupplementalDataID </span> </li> 
      <li id="li_26774089B6854CD6A3216043B6EEA01B"> <span class="codeph"> getCustomerIDs </span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>例 2</b> </p> </td> 
   <td colname="col2"> <p> 
     <ul id="ul_CCAD7E362E7F4DAB9D5C3E166EEE6BDD"> 
      <li id="li_1F0B006BAD044ECBA5604625DE411E84"> <span class="codeph"> getSupplementalDataID </span> </li> 
      <li id="li_C6022223C8314B9C923202207C7472EA"> <span class="codeph"> getMarketingCloudVisitorID </span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

