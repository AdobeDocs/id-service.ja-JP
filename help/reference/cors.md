---
description: ブラウザーは、クロスオリジンリソース共有（CORS）を使用して、現在のドメイン以外のドメインのリソースをリクエストします。Experience Cloud Identity Service は、これらのクライアント側のクロスオリジンリソースリクエストを可能にする CORS 標準規格をサポートしています。古いブラウザーや CORS をサポートしていないブラウザー上では、JSONP リクエストに切り替わります。
keywords: ID Service
seo-description: ブラウザーは、クロスオリジンリソース共有（CORS）を使用して、現在のドメイン以外のドメインのリソースをリクエストします。Experience Cloud Identity Service は、これらのクライアント側のクロスオリジンリソースリクエストを可能にする CORS 標準規格をサポートしています。古いブラウザーや CORS をサポートしていないブラウザー上では、JSONP リクエストに切り替わります。
seo-title: Experience Cloud Identity Service での CORS のサポート
title: Experience Cloud Identity Service での CORS のサポート
uuid: e656b573-72a8-4312-a7d5-5cc3818f0a9e
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 46%

---


# Experience Cloud Identity Service での CORS のサポート {#cors-support-in-the-experience-cloud-id-service}

ブラウザーは、クロスオリジンリソース共有（CORS）を使用して、現在のドメイン以外のドメインのリソースをリクエストします。Experience Cloud Identity Service は、これらのクライアント側のクロスオリジンリソースリクエストを可能にする CORS 標準規格をサポートしています。古いブラウザーや CORS をサポートしていないブラウザー上では、JSONP リクエストに切り替わります。

## 同一オリジンポリシーと ID サービスリクエストの問題 {#section-6608cf46d27143eeaeabacaa6aa14e8e}

同じ接触チャネルポリシーとは、Webブラウザーによって適用されるセキュリティ制御または制限です。 このレベルで適用される場合、Webブラウザー自体は、あるページから別のページに対して行われたリソースのリクエストを許可するかブロックするかを決定します。 リクエストが同じ接触チャネルのリクエストであるかどうかを判断するために、ブラウザーは次を比較します。

* Uniform Resource Identifier(URI)
* ホスト名(例：http://www.my-webpage-example.com)
* ポート番号（例：HTTPおよびHTTPS要求の場合はポート80および440）

両方のページがこれらの特性を共有している場合、ブラウザーはリクエストの成功を許可し、共有していない場合はリソースリクエストをブロックします。

## 同じ接触チャネルポリシーの問題を解決するCORS {#section-76c87ec3295d447bab220c84f138c235}

CORSは、異なるドメイン間でリソースをリクエストするための安全で効果的な方法を提供します。 CORS仕様には、リソースリクエストの送信、受信および評価にブラウザーが使用するHTTPヘッダーのセットが含まれています。 リソースリクエストの評価は、「」と呼ばれ *`preflight check`*&#x200B;ます。 このチェックにより、ブラウザーとサーバーは、どのリクエストを許可またはブロックするかを決定できます。 プリフライトチェックは、リソースをリクエストするアプリ、API、スクリプトに対して透過的です。 リソースリクエストプロセスで重要な2つのヘッダーは、次のとおりです。

* `Origin`：リクエストのソースを識別するリクエストヘッダー。
* `Access-Control-Allow-Origin`：リクエストがリクエスト元と共有できるかどうかを示す応答ヘッダー。

これらのヘッダーがどのように動作するかを説明します。この例では、サイト www.finance-website.com に [!DNL Experience Cloud] ID サービスを実装した金融サービス会社があるとします。次の表に、CORSリクエストおよび応答ヘッダーがリソースへのアクセスをチェックする方法を定義します。

<table id="table_B004ACF52B5A4D33B1DCF7EA77BE4E6D"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> アクション </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>リクエスト</b> </p> </td> 
   <td colname="col2"> <p>金融会社のページが読み込まれると、ブラウザーは <span class="codeph">dpm.demdex.net</span> に対してリクエストをおこないます。これは、IDサービスが使用するデータ収集サーバー(DCS)のドメインへの呼び出しです。 このクロスドメインリクエストには、次のヘッダーが含まれます。 </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Origin: https://www.finance-website.com</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>応答</b>  </p> </td> 
   <td colname="col2"> <p>DCSドメインからの応答には、金融会社のサイトに必要なリソースへのアクセスを与える以下のヘッダーが含まれます。 </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Access-Control-Allow-Origin: https://www.finance-website.com</span> </li> 
      <li> <span class="codeph"> Access-Control-Allow-Credentials: true</span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

[useCORSOnly](../library/function-vars/use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa) も参照してください。

## CORS を使用することのその他のメリット {#section-6f44f30694c44f95bf9854b8a2af8449}

次の表に、IDサービスを使用する顧客にとってCORSがもたらす利点の一部を示します。

<table id="table_AEB51A263D454F90B66E8C8D0513CF79"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> メリット </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p><b>セキュリティの向上</b> </p> </td> 
   <td colname="col2"> <p>CORSは、XMLHttpRequest <a href="https://developer.mozilla.org/ja/docs/Web/API/XMLHttpRequest" format="https" scope="external"> を使用してデータをリクエストおよび転送します</a> 。 この方法は、JSONPリクエストよりも安全です。 DCSからの応答に含まれている可能性のある、任意のJavaScriptを実行する方法がないことを保証します。 CORS XMLHttpRequest応答ペイロードは、IDサービスJavaScriptによって解析され、単純にコールバック関数で実行されるわけではありません。 </p> <p> <p>注意：Cookie を受け入れるために、<span class="codeph">XMLHttpRequest</span> オブジェクトの <span class="codeph">withCredentials</span> プロパティを <span class="codeph">true</span> に設定する必要があります。このプロパティは、Chrome、Firefox、Internet Explorer（v10以降）、OperaおよびSafariでサポートされます。 </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><b>パフォーマンスの向上</b> </p> </td> 
   <td colname="col2"> <p>次の理由で、CORSはパフォーマンスの向上に役立ちます。 </p> 
    <ul id="ul_EC3A178003A94D70883B914050D7C464"> 
     <li id="li_F8B44352BFBB46CDBD07AE40B9F2D0EC">ブラウザーは、リソースリクエストを管理します。 要求プロセスは、IDサービスに対して透過的です。 </li> 
     <li id="li_C63E43A4CAB84210AB6A39100E5864BE">非同期JSONPリクエストとは異なり、ブラウザーはCORSリクエストの優先順位を下げたりキューに登録したりしません。 </li> 
     <li id="li_1A2A15F591B84D1BAED3CFAB391EEBEC">IDサービスは、許容的に応答します。 これは、URL が <span class="codeph">Origin</span> として渡された場合に、ID サービスは必要なリソースに対するアクセスをページに付与することを意味します。 </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

