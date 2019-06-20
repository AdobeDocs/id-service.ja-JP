---
description: ブラウザーは、クロスオリジンリソース共有（CORS）を使用して、現在のドメイン以外のドメインのリソースをリクエストします。Experience Cloud IDサービスは、これらのクライアント側のクロスオリジンリソースリクエストを有効にするCORS標準規格をサポートしています。古いブラウザーや CORS をサポートしていないブラウザー上では、JSONP に切り替わります。
keywords: ID サービス
seo-description: ブラウザーは、クロスオリジンリソース共有（CORS）を使用して、現在のドメイン以外のドメインのリソースをリクエストします。Experience Cloud IDサービスは、これらのクライアント側のクロスオリジンリソースリクエストを有効にするCORS標準規格をサポートしています。古いブラウザーや CORS をサポートしていないブラウザー上では、JSONP に切り替わります。
seo-title: Experience Cloud ID サービスでの CORS のサポート
title: Experience Cloud ID サービスでの CORS のサポート
uuid: e656b573-72a8-4312- a7d5-5cc3818f0a9e
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Experience Cloud ID サービスでの CORS のサポート {#cors-support-in-the-experience-cloud-id-service}

ブラウザーは、クロスオリジンリソース共有（CORS）を使用して、現在のドメイン以外のドメインのリソースをリクエストします。Experience Cloud IDサービスは、これらのクライアント側のクロスオリジンリソースリクエストを有効にするCORS標準規格をサポートしています。古いブラウザーや CORS をサポートしていないブラウザー上では、JSONP に切り替わります。

## 同一オリジンポリシーと ID サービスリクエストの問題 {#section-6608cf46d27143eeaeabacaa6aa14e8e}

同一オリジンポリシーは、Web ブラウザーによって実行されるセキュリティコントロールまたは制限です。このレベルで実行される場合、あるページから別のページに対しておこなわれたリソースのリクエストが許可されるかブロックされるかは、Web ブラウザー自体が判定します。リクエストが同一オリジンのリクエストかどうかを判定するために、ブラウザーは以下を比較します。

* Uniform Resource Identifier（URI）
* ホスト名（例：http://www.my-webpage-example.com）
* ポート番号（例：HTTP および HTTPS のリクエストの場合、ポート 80 および 440）

ブラウザーは、両方のページがこれらの特徴を共有している場合にリクエストの続行を許可し、そうでない場合はリソースリクエストをブロックします。

## 同一オリジンポリシーの問題を解決する CORS {#section-76c87ec3295d447bab220c84f138c235}

CORS は、異なるドメイン間でリソースをリクエストするための安全で効果的な方法を提供します。CORS 仕様には、リソースリクエストを送信、受信および評価するためにブラウザーが使用する HTTP ヘッダーのセットが含まれます。リソースリクエストの評価は、 *`preflight check`*. このチェックにより、ブラウザーとサーバーは、どのリクエストを許可またはブロックするかを判定します。プリフライトチェックは、リソースをリクエストするアプリ、API、スクリプトに対して透過的です。リソースリクエストで重要なのは、以下の 2 つのヘッダーです。

* `Origin`：リクエストのソースを識別するリクエストヘッダー。
* `Access-Control-Allow-Origin`：リクエストがリクエスト元と共有できるかどうかを示す応答ヘッダー。

これらのヘッダーがどのように動作するかを説明します。この例では、サイト www.finance-website.com に [!DNL Experience Cloud] ID サービスを実装した金融サービス会社があるとします。以下の表に、CORS リクエストおよび応答ヘッダーがリソースへのアクセスをチェックする方法を定義します。

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
   <td colname="col2"> <p>金融会社のページが読み込まれると、ブラウザーは <span class="codeph">dpm.demdex.net</span> に対してリクエストをおこないます。これは、ID サービスが使用するデータ収集サーバー（DCS）のドメインに対する呼び出しです。このクロスドメインリクエストには、以下のヘッダーが含まれます。 </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Origin:https://www.finance-website.com</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>応答</b> </p> </td> 
   <td colname="col2"> <p>DCS ドメインからの応答には、金融会社のサイトに必要なリソースへのアクセスを許可する以下のヘッダーが含まれます。 </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Access-Control-Allow-Origin: https://www.finance-website.com</span> </li> 
      <li> <span class="codeph"> Access-Control-Allow-Credentials: true</span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

[useCORSOnly](../library/function-vars/use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa)も参照してください。

## CORS を使用することのその他のメリット {#section-6f44f30694c44f95bf9854b8a2af8449}

以下の表に、ID サービスを使用する顧客が得られる CORS の利点の一部を説明します。

<table id="table_AEB51A263D454F90B66E8C8D0513CF79"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> メリット </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p><b>強化されたセキュリティ</b> </p> </td> 
   <td colname="col2"> <p>CORS は、<a href="https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest" format="https" scope="external">XMLHttpRequest</a> を使用して、データをリクエストおよび転送します。この方法は、JSONP リクエストよりも安全です。DCS からの応答に含まれている可能性のある、任意の JavaScript を実行する方法がないことを保証します。CORS XMLHttpRequest 応答ペイロードは、ID サービス JavaScript によって解析され、単純にコールバック関数で実行されることはありません。 </p> <p> <p>注意：Cookie を受け入れるために、<span class="codeph">XMLHttpRequest</span> オブジェクトの <span class="codeph">withCredentials</span> プロパティを <span class="codeph">true</span> に設定する必要があります。このプロパティは、Chrome、Firefox、Internet Explorer（v10 以降）、Opera および Safari でサポートされます。 </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><b>パフォーマンスの向上</b> </p> </td> 
   <td colname="col2"> <p>以下の理由により、CORS はパフォーマンスの向上に役立ちます。 </p> 
    <ul id="ul_EC3A178003A94D70883B914050D7C464"> 
     <li id="li_F8B44352BFBB46CDBD07AE40B9F2D0EC">ブラウザーは、リソースリクエストを管理します。リクエストの処理は、ID サービスに対して透過的です。 </li> 
     <li id="li_C63E43A4CAB84210AB6A39100E5864BE">非同期 JSONP リクエストとは異なり、ブラウザーは、CORS リクエストについて優先順位を下げたりキューに追加したりしません。 </li> 
     <li id="li_1A2A15F591B84D1BAED3CFAB391EEBEC">ID サービスは、許容的に応答します。これは、URL が <span class="codeph">Origin</span> として渡された場合に、ID サービスは必要なリソースに対するアクセスをページに付与することを意味します。 </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

