---
description: これは、デフォルトで Analytics の識別子、ID サービス、データ収集オプトアウト、地域およびメタデータ「blob」コンテンツを返す非同期 API です。オプションの visitor.FIELDS 列挙を使用して、返される ID を制御することもできます。
keywords: ID サービス
title: getVisitorValues
exl-id: bd023e8d-a804-4205-989f-e1e58080b63c
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 100%

---

# getVisitorValues{#getvisitorvalues}

これは、デフォルトで Analytics の識別子、ID サービス、データ収集オプトアウト、地域およびメタデータ「blob」コンテンツを返す非同期 API です。オプションの visitor.FIELDS 列挙を使用して、返される ID を制御することもできます。

内容：

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-5aebe3907b2b46e997f45a1d1ed35c09" format="dita" scope="local">構文</a> </li> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-36a31683558742a5915db3a391e09f7b" format="dita" scope="local"> 使用例 1：デフォルトデータセットのリクエスト </a> </li> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-467b2f4e513344c89b7332b05f6f59f3" format="dita" scope="local"> 使用例 2：カスタムデータセットのリクエスト </a> </li> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-4c4c300167694c6fbff1d6c612f372b5" format="dita" scope="local"> レスポンスパラメーターの定義 </a> </li> 
</ul>

## 構文 {#section-5aebe3907b2b46e997f45a1d1ed35c09}

この関数は、次の構文を使用します（斜体は変数のプレースホルダーを表します）：` var *`values`* = visitor.getVisitorValues (callback, [visitor.FIELDS. *`ID type`*, visitor.FIELDS. *`ID type`*]);`

関数パラメーターの詳細は次のとおりです。

* ` *`callback`*` は、返される ID を受け取るコールバックコードを表します。
* *（オプション）* ` visitor.FIELDS. *`ID type`*` は、この関数で返す必要がある [ID 値](../../library/get-set/getvisitorvalues.md#section-4c4c300167694c6fbff1d6c612f372b5)を指定できる列挙です。

詳しくは、以下の使用例と定義を参照してください。

## ユースケース 1：デフォルトデータセットのリクエスト {#section-36a31683558742a5915db3a391e09f7b}

このコードは、標準データセットを返します。リクエストと応答は、次の例のようになります。

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{...}); 
   
//Add your callback to the GET method to return IDs and data. 
visitor.getVisitorValues(visitorIdsCallback);
```

デフォルトのサンプル応答では、デモ用に一部の値が短縮されています。

```js
//Formatted IDs in JSON response 
{ 
    MCMID: 'mid-1234', 
    MCOPTOUT: 'isoptedout-true', 
    MCAID: 'aid-1234', 
    MCAAMLH: 7, 
    MCAAMB: 'hgfe54236786oygj' 
}
```

## ユースケース 2：カスタムデータセットのリクエスト {#section-467b2f4e513344c89b7332b05f6f59f3}

このコードはオプションの配列を使用し、`visitor.FIELDS` 列挙を使用して特定の ID セットを返します。この場合、訪問者の Experience Cloud ID（MCID）と Analytics ID（MCAID）のみが必要です。リクエストと応答は、次の例のようになります。

```js
//Call the ID service 
var visitor = Visitor.getInstance("Insert Experience Cloud organization ID here", { ... });

// Add an optional array to specify which IDs you want to return. 
visitor.getVisitorValues(visitorIdsCallback, [visitor.FIELDS.MCMID, visitor.FIELDS.MCAID]);
```

カスタマイズされたレスポンスの例では、リクエストで指定された ID のみが返されます。

```js
//Formatted IDs in JSON response 
{ 
    MCMID: 'mid-1234', 
    MCAID: 'aid-4321' 
}
```

## レスポンスパラメーターの定義 {#section-4c4c300167694c6fbff1d6c612f372b5}

以下の表に、レスポンスパラメーターとその定義を示します。これらは `visitor.FIELDS` 列挙に含まれるすべての値でもあります。特定の変数に値がない場合、このメソッドは空の文字列を返すことに注意してください。

<table id="table_32D0FEEA76CE4F298EED4B8F5C644232"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 値 </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAAMB </span> </p> </td> 
   <td colname="col2"> <p>「blob」と呼ばれる、暗号化された <span class="keyword">Audience Manager</span> メタデータです。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAAMLH </span> </p> </td> 
   <td colname="col2"> <p>データ収集地域 ID です。これは、特定の ID サービスデータセンターの地理的場所を示す数値識別子です。 </p> <p><a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html?lang=ja" format="https" scope="external">DCS 地域 ID、場所、ホスト名</a>および<a href="../../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c" format="dita" scope="local"> getLocationHint</a> を参照してください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAID </span> </p> </td> 
   <td colname="col2"> <p>訪問者の <span class="keyword">Analytics</span> ID です。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCMID </span> </p> </td> 
   <td colname="col2"> <p>訪問者の Experience Cloud ID です。 </p> <p><a href="../../introduction/cookies.md" format="dita" scope="local">Cookie と Experience Cloud ID サービス</a>を参照してください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCOPTOUT </span> </p> </td> 
   <td colname="col2"> <p>訪問者がデータ収集をオプトアウトしたかを示すフラグです。 </p> <p>以下の値が含まれます。 </p> <p> 
     <ul id="ul_E82431DE12B449F8822499364B363798"> 
      <li id="li_2BAB7C15A38A408E8FC4B85E70B66E46"> <span class="codeph">'isoptedout-true'</span>：訪問者はデータ収集をオプトアウトしています。 </li> 
      <li id="li_BB80AE4CEBC44166BC04428B212FEF51"> <span class="codeph">'isoptedout-false'</span>：訪問者はデータ収集をオプトアウトしていません。 </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>
