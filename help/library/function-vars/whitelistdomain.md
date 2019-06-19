---
description: これらの設定を使用すると、iFrame と親ページに実装されている ID サービスコードのインスタンスが互いに通信できるようになります。これらの設定は、自社が管理しているドメインの iFrame に ID サービスコードを読み込む場合の 2 つの具体的な使用例（親ページまたはドメインを制御できる場合とできない場合）に関わる問題の解決に役立つように設計されています。これらは、VisitorAPI.js コードバージョン 2.2 以降で利用できます。
keywords: ID サービス
seo-description: これらの設定を使用すると、iFrame と親ページに実装されている ID サービスコードのインスタンスが互いに通信できるようになります。これらの設定は、自社が管理しているドメインの iFrame に ID サービスコードを読み込む場合の 2 つの具体的な使用例（親ページまたはドメインを制御できる場合とできない場合）に関わる問題の解決に役立つように設計されています。これらは、VisitorAPI.js コードバージョン 2.2 以降で利用できます。
seo-title: whitelistParentDomain および whitelistIframeDomains
title: whitelistParentDomain および whitelistIframeDomains
uuid: 6b66a4d0- fea2-4d98-963e-0c4f4ab1efb6
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# whitelistParentDomain および whitelistIframeDomains{#whitelistparentdomain-and-whitelistiframedomains}

これらの設定を使用すると、iFrame と親ページに実装されている ID サービスコードのインスタンスが互いに通信できるようになります。これらの設定は、自社が管理しているドメインの iFrame に ID サービスコードを読み込む場合の 2 つの具体的な使用例（親ページまたはドメインを制御できる場合とできない場合）に関わる問題の解決に役立つように設計されています。これらは、VisitorAPI.js コードバージョン 2.2 以降で利用できます。

内容：

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-f645198bbaba4fba8961acb6e88d1470" format="dita" scope="local">構文</a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-09d0049fe88a473baa69d404c50bf8ae" format="dita" scope="local"> コードサンプル </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-fc2eeb93546b406fae3b102dbcd11de7" format="dita" scope="local"> ユースケース </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-2b1ce31fab034e1ca0f6b1c3cc57a6e2" format="dita" scope="local"> 設定の安全性とセキュリティ </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-30c6a9f4dcdc4265a1149260b97cc057" format="dita" scope="local"> サポートされる訪問者 API メソッド </a> </li> 
</ul>

## 構文{#section-f645198bbaba4fba8961acb6e88d1470}

このコードを使用する際には、どちらの設定要素も必要です。

<table id="table_237108A4D40F4AAC981D0060BA68F881"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 設定の構文 </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> ホワイトListParentDomain:「 <span class="varname"> 親ページのドメイン名 </span>」 </span> </p> </td> 
   <td colname="col2"> <p>文字列として渡される単一のドメイン名を受け入れます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> WhiteListFrameDomains:[ <span class="varname"> "iFrame domain"，"iFrame domain"，"iFrame domain" </span>] </span> </p> </td> 
   <td colname="col2"> <p>配列として渡される iFrame ドメイン名を受け入れます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## コードサンプル {#section-09d0049fe88a473baa69d404c50bf8ae}

設定 [!DNL ID service] したコードは、この例のようになります。

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

## ユースケース {#section-fc2eeb93546b406fae3b102dbcd11de7}

これらの設定は、ブラウザーがサードパーティ Cookie をブロックし、以下のいずれかの条件に該当する場合に発生する、ID サービス Cookie 設定と訪問者 ID 割り当ての問題の解決に役立ちます。

* 親ページまたはドメインを自社で管理していない。
* ID サービスコードが親ページにインストールされていないが、iFrame には実装されている。

>[!TIP]
>
>ビデオハートビートを使用 [してiFrameでビデオを提供するときに、これらの設定を実装すること](https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/hbvideo/)もできます。ビデオハートビートを正しく動作させるには ID サービスの ID（MID）が必要です。

**使用例 1：ブラウザーがサードパーティ Cookie をブロックし、ID サービスが iFrame および親ページに実装されている**

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
   <td colname="col2"> <p>この使用例には以下の条件が含まれます。 </p> <p> 
     <ul id="ul_DC748846585745B0AB74398D82BDA53A"> 
      <li id="li_6E04CF0B6A204B4D8856656B0C9EF2A5">A 社が自社のホームページに ID サービスを実装する。 </li> 
      <li id="li_B53AE0F0C69844E7B6C4D3464C57883B">A 社が自社のホームページの iFrame の ID サービスを実装する。 </li> 
      <li id="li_07E0A6D7BEB140E4B9FB6C7B9629B860">A 社が親ページおよび iFrame を所有し、両方に ID サービスを実装済みである。 </li> 
      <li id="li_76967BD69DDB40A8A9C915DADC58AC62">顧客がサードパーティ Cookie をブロックするブラウザーで親ページを読み込む。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>結果</b> </p> </td> 
   <td colname="col2"> <p>これらの条件に当てはまる場合、ID サービスの動作は以下のようになります。 </p> <p> 
     <ul id="ul_12356701501E40DFA57903494FFE58F7"> 
      <li id="li_B57EDF1B0762486F95FA6526C047390C">親ページでは正しく動作します。AMCV Cookie を要求して設定し、サイト訪問者に一意の ID を割り当てます。 </li> 
      <li id="li_BA9F42C759E747EAAE14DD3FBB6130A5">iFrame では動作しません。これは、ブラウザーが iFrame をサードパーティドメインとみなして、ID サービスによる AMCV Cookie の設定を禁止するためです。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>ソリューション</b> </p> </td> 
   <td colname="col2"> <p>これらのホワイトリスト設定を使用して、iFrame の ID サービス <span class="codeph">Visitor.getInstance</span> 関数を変更します。コードの親ドメインおよび子ドメインを指定します。これらの設定により、iFrame の ID サービスコードが親ページの ID サービスコードをチェックして訪問者 ID を確認できるようになります。 </p> <p>iFrame の ID サービスコードが親ページの応答を受信しない場合、これらの設定によってローカルの訪問者 ID が生成されます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**ユースケース 2：自社で管理していない iFrame、または ID サービスを使用していない親ページに埋め込まれた iFrame から ID をリクエストする**

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
   <td colname="col2"> <p>この使用例には以下の条件が含まれます。 </p> <p> 
     <ul id="ul_356E8FB0B1D14F46A844FE5281967E28"> 
      <li id="li_1285D945361842268B46FB492A3B5AA5">A 社は ID サービスを利用しない。 </li> 
      <li id="li_880D6D473F8342FF9BB49FCE111FD61A">A 社がページ上の iFrame を読み込む。この iFrame は B 社が所有し、A 社とは別のドメインで読み込まれる。 </li> 
      <li id="li_7988F0272B094FE0B398006AD4E6F81B">ブラウザーはサードパーティ Cookie をブロックする。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>結果</b> </p> </td> 
   <td colname="col2"> <p>これらの条件に当てはまる場合、ID サービスの動作は以下のようになります。 </p> <p> 
     <ul id="ul_A92D90896E5A42C5804AC5CE83E8EB25"> 
      <li id="li_9734EA9C5D9D4F908DE783188C9E5530">iFrame では動作しません。これは、ブラウザーが iFrame をサードパーティドメインとみなして、ID サービスによる AMCV Cookie の設定を禁止するためです。 </li> 
      <li id="li_3F4BE9048E774902A867D67E5A80674D">A 社はこのサービスを利用していないので、親ページから訪問者 ID を取得できません。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>ソリューション</b> </p> </td> 
   <td colname="col2"> <p>これらのホワイトリスト設定を使用して、iFrame の ID サービス <span class="codeph">Visitor.getInstance</span> 関数を変更します。コードの親ドメインおよび子ドメインを指定します。これらの設定により、iFrame の ID サービスコードが親ページの ID サービスコードをチェックして訪問者 ID を確認できるようになります。 </p> <p>iFrame の ID サービスコードが親ページの応答を受信しない場合、これらの設定によってローカルの訪問者 ID が生成されます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 設定の安全性とセキュリティ {#section-2b1ce31fab034e1ca0f6b1c3cc57a6e2}

これらの設定は、以下の理由により安全に実装できます。

* ID サービスは親ドメインに実装され、iFrame ドメインは同じ組織 ID を使用する必要があります。親または iFrame の組織 ID が異なる場合、これらのホワイトリスト設定は無効です。
* これらの設定はコードで指定されているドメインおよび iFrame とのみ通信をおこないます。
* iFrame と親ページの間の通信は、特定のフォーマットに従います。親ページの ID サービスが想定されているフォーマットでリクエストを受信しない場合、この共有プロセスは失敗します。

## サポートされる訪問者 API メソッド {#section-30c6a9f4dcdc4265a1149260b97cc057}

これらのホワイトリスト設定を実装する際に ID サービスでサポートされる公開 API メソッドは限定されています。サポートされるメソッドは、上記の使用例シナリオによって異なります。

<table id="table_0FF9E529FD1C43A8A3B2B0D789C8E83C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 使用例 </th> 
   <th colname="col2" class="entry"> サポートされるメソッド </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>使用例 1</b> </p> </td> 
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

