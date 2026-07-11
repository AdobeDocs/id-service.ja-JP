---
description: この実装により、お客様は、JavaScriptまたはSDK コードを受け入れたり操作したりできないデバイスでVisitor ID サービスを使用できます。 これには、ゲーム機やスマート TV など、インターネットに接続可能な機器が含まれます。 構文、コードサンプル、定義については、この節を参照してください。
keywords: 訪問者 ID サービス
title: Adobe Visitor ID Serviceとのネイティブ統合
exl-id: 29565b74-5fe7-41f7-b278-6a90559faab9
TQID: https://experienceleague.adobe.com/f5Tp-XaNY-KIpHXExT4hFwNt7FQqh6y4iaaWmIHEhAI
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 690
ht-degree: 71%

---

# Adobe Visitor ID Serviceとのネイティブ統合 {#direct-integration-with-the-experience-cloud-id-service}

この実装により、お客様は、JavaScriptまたはSDK コードを受け入れたり操作したりできないデバイスでVisitor ID サービスを使用できます。 これには、ゲーム機やスマート TV など、インターネットに接続可能な機器が含まれます。 構文、コードサンプル、定義については、この節を参照してください。

## 構文 {#section-a4754afec5ad40b6be00d6f1011d68bb}

`VisitorAPI.js`またはSDK コードライブラリを使用できないデバイスは、訪問者ID サービスで使用されるデータ収集サーバー（DCS）に直接呼び出しを行うことができます。 これをおこなうには `dpm.demdex.net` を呼び出し、次の形式のリクエストを使用します。 *斜体*&#x200B;の部分には実際の情報が入ります。

![](assets/directSyntax.png)

この構文の例において、`d_` という接頭辞は呼び出し内のキーと値のペアがシステムレベルの変数であることを示します。 訪問者ID サービスにはかなりの数の`d_` パラメーターを渡すことができますが、上記のコードに示すように、キーと値のペアに集中してください。 他の変数について詳しくは、[DCS API 呼び出しでサポートされる属性](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-keys.html?lang=ja)を参照してください。

訪問者ID サービスは、HTTP呼び出しとHTTPS呼び出しをサポートしています。 セキュアなページからデータを渡す際には HTTPS を使用してください。

## リクエストのサンプル {#section-26302b8851704888b6f8e6b2071bcdb0}

リクエストは以下のサンプルのようになります。 長い変数は短縮されています。

![](assets/directExample.png)

## レスポンスのサンプル {#section-89bc103b3e9e4a8b98e74c32897b1200}

訪問者ID サービスは、次に示すように、JSON オブジェクト内のデータを返します。 レスポンスは異なる場合があります。

```js
{
     "d_mid":"12345",
     "dcs_region":"6",
     "id_sync_ttl":"604800",
     "d_blob":"wxyz5432"
}
```

## リクエストパラメーターおよびレスポンスパラメーターの定義 {#section-4a9912b545364dc4acad4f1ea5ec641d}

**リクエストパラメーター**

<table id="table_C8FFA89AB74E4E31A6926CDE5CD54217"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> パラメーター </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> dpm.demdex.net</span> </p> </td> 
   <td colname="col2"> <p><span class="keyword">アドビ</span>が管理する従来のドメインです。 <a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=ja" format="https" scope="external">Demdex ドメインの呼び出しについて</a>を参照してください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_mid</span> </p> </td> 
   <td colname="col2"> <p>ECIDです。 <a href="../introduction/cookies.md" format="dita" scope="local"> Cookieと訪問者ID サービス </a>を参照してください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_orgid</span> </p> </td> 
   <td colname="col2"> <p>IMS組織ID。 このIDを見つける際のヘルプについては、「訪問者ID サービスの<a href="../reference/requirements.md" format="dita" scope="local">要件</a>」を参照してください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_cid</span> </p> </td> 
   <td colname="col2"> <p>データプロバイダーID （DPID）、一意のユーザーID （DPUUID）、および<a href="../reference/authenticated-state.md" format="dita" scope="local">認証済み状態ID</a>を訪問者ID サービスに渡すオプションのパラメーター。 コードサンプルで示すように、DPID と DPUUID の間は非表示の制御文字 <span class="codeph">%01</span> で区切ります。 </p> <p> <b>DPID および DPUUID</b> </p> <p><span class="codeph">d_cid</span> パラメーターでは、関連する DPID と DPUUID の各組み合わせを同じ <span class="codeph">d_cid</span> パラメーターに割り当てます。 これにより、複数の ID セットを単一のリクエストで設定できます。 また、DPID、DPUUID、および任意の認証フラグの間は非表示の制御文字 <span class="codeph">%01</span> で区切ります。 以下の例では、プロバイダー ID とユーザー ID が<b>太字</b>のテキストで強調されています。 </p> 
    <ul id="ul_2E19D837296B40E9ACD096495CF711C5"> 
     <li id="li_5B94B057654440B99B989BA60E4ED053">構文：<span class="codeph">...d_cid=DPID%01DPUUID%01認証状態...</span> </li> 
     <li id="li_B07833EF51D54F088574B7B7F9FB841A">例：<span class="codeph">...d_cid=123%01456%011...</span> </li> 
    </ul> <p> <b>認証状態</b> </p> <p>これは <span class="codeph">d_cid</span> パラメーターのオプションの ID です。 整数で表され、以下に示す認証状態によってユーザーを識別します。 </p> 
    <ul id="ul_E2B36922B11C4AA2A9016B6E2DC9EDAA"> 
     <li id="li_31C018E3F9514B938C73EF40C436715F"> <span class="codeph">0</span>（不明） </li> 
     <li id="li_1F125C3879324C2F8EF4613C0ECB5F02"> <span class="codeph">1</span>（認証済み） </li> 
     <li id="li_EF6792D0115D407485079D5D7480D965"> <span class="codeph">2</span>（ログアウト済み） </li> 
    </ul> <p>認証状態を指定するには、ユーザー ID（UUID）変数の後にこのフラグを設定します。 また、UUID と任意の認証フラグの間は非表示の制御文字 <span class="codeph">%01</span> で区切ります。 以下の例では、認証 ID が<b>太字</b>のテキストで強調されています。 </p> <p>構文：<span class="codeph">...d_cid=DPID%01DPUUID%01認証状態</span> </p> <p>例： </p> 
    <ul id="ul_4C1054CE860A4D9C8DD85C2A8020C47F"> 
     <li id="li_AD4000BF3E0146C0BD37B1EC513EC314">不明：<span class="codeph">...d_cid=123%01456%010...</span> </li> 
     <li id="li_B037D424AADA4D41BF29381A9602AE61">認証済み：<span class="codeph">...d_cid=123%01456%011...</span> </li> 
     <li id="li_0410FCB9E60D4DD08E7898D814E1C3C9">ログアウト済み：<span class="codeph">...d_cid=123%01456%012...</span> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> dcs_region</span> </p> </td> 
   <td colname="col2"> <p>訪問者ID サービスは、地理的に分散され、負荷分散されたシステムです。 呼び出しを処理するデータセンターの地域は ID で識別されます。 <a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html?lang=ja" format="https" scope="external">DCS 地域 ID、場所、ホスト名</a>を参照してください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_cb</span> </p> </td> 
   <td colname="col2"> <p> <i>（オプション）</i>リクエスト本文で JavaScript 関数を実行できるようにするコールバックパラメーターです。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_blob</span> </p> </td> 
   <td colname="col2"> <p>暗号化された JavaScript メタデータのチャンクです。 サイズ制限により blob は 512 バイト以下に制限されています。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_ver</span> </p> </td> 
   <td colname="col2"> <p>必須。 API バージョン番号を設定します。 この設定は <span class="codeph">d_ver=2</span> のままにしてください。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**レスポンスパラメーター**

一部のレスポンスパラメーターはリクエストの一部であり、上の節で定義されています。

<table id="table_58D0E8876DDC4A81B1F24F845E87EC18"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> パラメーター </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> id_sync_ttl</span> </p> </td> 
   <td colname="col2"> <p>再同期の間隔（秒数）。 デフォルトの間隔は、604,800 秒（7 日間）です。 </p> </td> 
  </tr> 
 </tbody> 
</table>

