---
description: ブラウザーは、クロスオリジンリソース共有（CORS）を使用して、現在のドメイン以外のドメインのリソースをリクエストします。Experience Cloud Identity Service は、これらのクライアント側のクロスオリジンリソースリクエストを可能にする CORS 標準規格をサポートしています。古いブラウザーや CORS をサポートしていないブラウザー上では、JSONP リクエストに切り替わります。
keywords: ID サービス
seo-description: ブラウザーは、クロスオリジンリソース共有（CORS）を使用して、現在のドメイン以外のドメインのリソースをリクエストします。Experience Cloud Identity Service は、これらのクライアント側のクロスオリジンリソースリクエストを可能にする CORS 標準規格をサポートしています。古いブラウザーや CORS をサポートしていないブラウザー上では、JSONP リクエストに切り替わります。
seo-title: Experience Cloud Identity Service での CORS のサポート
title: Experience Cloud Identity Service での CORS のサポート
uuid: e656b573-72a8-4312-a7d5-5cc3818f0a9e
exl-id: 0e8ffe85-8d1f-42a0-aae3-a2b3b28c7bce
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '674'
ht-degree: 100%

---

# Experience Cloud Identity Service での CORS のサポート {#cors-support-in-the-experience-cloud-id-service}

ブラウザーは、クロスオリジンリソース共有（CORS）を使用して、現在のドメイン以外のドメインのリソースをリクエストします。Experience Cloud Identity Service は、これらのクライアント側のクロスオリジンリソースリクエストを可能にする CORS 標準規格をサポートしています。古いブラウザーや CORS をサポートしていないブラウザー上では、JSONP リクエストに切り替わります。

## 同一オリジンポリシーと ID サービスリクエストの問題 {#section-6608cf46d27143eeaeabacaa6aa14e8e}

同一生成元ポリシー（同一オリジンポリシー）は、web ブラウザーによって適用されるセキュリティ制御または制限です。 このレベルで適用されると、あるページから別のページへのリソースのリクエストを許可するかブロックするかを web ブラウザー自体が決定します。 リクエストが同一生成元（オリジン）のリクエストであるかどうかを判断するために、ブラウザーは以下を比較します。

* ユニフォームリソース識別子（URI）
* ホスト名（例：http://www.my-webpage-example.com）
* ポート番号（例：HTTP および HTTPS リクエストの場合はポート 80 および 440）

ブラウザーは、両方のページがこれらの特性を共有している場合はリクエストを成功させ、共有していない場合はリソースリクエストをブロックします。

## CORS で同一生成元ポリシーの問題を解決 {#section-76c87ec3295d447bab220c84f138c235}

CORS は、異なるドメインをまたいでリソースをリクエストするための安全で効果的な方法を提供します。 CORS 仕様には、ブラウザーがリソースリクエストの送信、受信、評価に使用する一連の HTTP ヘッダーが含まれています。 リソースリクエストの評価は&#x200B;*`preflight check`*&#x200B;と呼ばれます。 このチェックにより、ブラウザーとサーバーは、どのリクエストを許可またはブロックするかを決定できます。 プリフライトチェックは、リソースをリクエストするアプリ、API、スクリプトに対して透過的です 。 リソースリクエストの処理で重要なヘッダーは次の 2 つです。

* `Origin`：リクエストのソースを識別するリクエストヘッダー。
* `Access-Control-Allow-Origin`：リクエストがリクエスト元と共有できるかどうかを示す応答ヘッダー。

これらのヘッダーがどのように動作するかを説明します。この例では、サイト www.finance-website.com に [!DNL Experience Cloud] ID サービスを実装した金融サービス会社があるとします。CORS リクエストヘッダーおよび応答ヘッダーでリソースへのアクセスをチェックする方法を次の表に示します。

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
   <td colname="col2"> <p>金融会社のページが読み込まれると、ブラウザーは <span class="codeph">dpm.demdex.net</span> に対してリクエストをおこないます。これは、ID サービスで使用するデータ収集サーバー（DCS）のドメインへの呼び出しです。 このクロスドメインリクエストには、次のヘッダーが含まれます。 </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Origin: https://www.finance-website.com</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>応答</b> </p> </td> 
   <td colname="col2"> <p>DCS ドメインからの応答には、必要なリソースへのアクセスを金融会社のサイトに提供する以下のヘッダーが含まれます。 </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Access-Control-Allow-Origin: https://www.finance-website.com</span> </li> 
      <li> <span class="codeph"> Access-Control-Allow-Credentials: true</span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

[useCORSOnly](../library/function-vars/use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa) も参照してください。

## CORS を使用することのその他のメリット {#section-6f44f30694c44f95bf9854b8a2af8449}

ID サービスを使用する顧客にとっての CORS の利点をいくつか次の表に示します。

<table id="table_AEB51A263D454F90B66E8C8D0513CF79"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 利点 </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p><b>セキュリティの向上</b> </p> </td> 
   <td colname="col2"> <p>CORS では、<a href="https://developer.mozilla.org/ja/docs/Web/API/XMLHttpRequest" format="https" scope="external">XMLHttpRequest</a> を使用して、データをリクエストおよび転送します。 このメソッドは、JSONP リクエストよりも安全です。 これにより、DCS からの応答に含まれている可能性のある任意の JavaScript を実行できなくなります。 CORS XMLHttpRequest 応答ペイロードは、ID サービス JavaScript によって解析され、コールバック関数で単純に実行されることはなくなります。 </p> <p> <p>注意：Cookie を受け入れるために、<span class="codeph">XMLHttpRequest</span> オブジェクトの <span class="codeph">withCredentials</span> プロパティを <span class="codeph">true</span> に設定する必要があります。このプロパティは、Chrome、Firefox、Internet Explorer（v10 以降）、Opera および Safari でサポートされています。 </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><b>パフォーマンスの向上</b> </p> </td> 
   <td colname="col2"> <p>次の理由で、CORS はパフォーマンスの向上に役立ちます。 </p> 
    <ul id="ul_EC3A178003A94D70883B914050D7C464"> 
     <li id="li_F8B44352BFBB46CDBD07AE40B9F2D0EC">ブラウザーがリソースリクエストを管理します。 リクエストプロセスは ID サービスに対して透過的です。 </li> 
     <li id="li_C63E43A4CAB84210AB6A39100E5864BE">非同期 JSONP リクエストとは異なり、ブラウザーが CORS リクエストの優先順位を下げたりキューに入れたりしません。 </li> 
     <li id="li_1A2A15F591B84D1BAED3CFAB391EEBEC">ID サービスが寛容に応答します。 これは、URL が <span class="codeph">Origin</span> として渡された場合に、ID サービスは必要なリソースに対するアクセスをページに付与することを意味します。 </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
