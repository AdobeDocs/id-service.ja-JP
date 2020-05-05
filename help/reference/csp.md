---
description: コンテンツセキュリティポリシー(CSP)は、Webページに読み込まれるリソースの種類をブラウザーで制御できるHTTPヘッダーおよびセキュリティ機能です。 このセクションは、IDサービスを使用し、ホワイトリストを使用して信頼されたドメインのリソースを受け入れる厳密なCSPがある場合に確認します。 ここに示すAdobeドメインをCSPホワイトリストに追加する必要があります。
keywords: ID Service
seo-description: コンテンツセキュリティポリシー(CSP)は、Webページに読み込まれるリソースの種類をブラウザーで制御できるHTTPヘッダーおよびセキュリティ機能です。 このセクションは、IDサービスを使用し、ホワイトリストを使用して信頼されたドメインのリソースを受け入れる厳密なCSPがある場合に確認します。 ここに示すAdobeドメインをCSPホワイトリストに追加する必要があります。
seo-title: コンテンツセキュリティポリシーおよび Experience Cloud Identity Service
title: コンテンツセキュリティポリシーおよび Experience Cloud Identity Service
uuid: 7399edf3-01c1-4730-834e-e2dd2c5791ff
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# コンテンツセキュリティポリシーおよび Experience Cloud Identity Service {#content-security-policies-and-the-experience-cloud-id-service}

コンテンツセキュリティポリシー(CSP)は、Webページに読み込まれるリソースの種類をブラウザーで制御できるHTTPヘッダーおよびセキュリティ機能です。 このセクションは、IDサービスを使用し、ホワイトリストを使用して信頼されたドメインのリソースを受け入れる厳密なCSPがある場合に確認します。 ここに示すAdobeドメインをCSPホワイトリストに追加する必要があります。

## CSPの確認 {#section-5fde5c00a678455c914b8307a8caab82}

CSP は HTTP ヘッダー `Content-Security-Policy` を使用してブラウザーが許可したりページに読み込んだりするリソースのタイプを制御します。CSPを適用すると、次の防止に役立ちます。

* ソースが不明またはホワイトリストに含まれていない場合に、JavaScriptファイルが読み込まれない。
* クロスサイトスクリプティング（XXS）攻撃。
* データ挿入攻撃。
* サイトデファクセメント攻撃。
* マルウェアの配布。

CSPの使用は一般的でよく理解されています。 CSPの詳細を説明するのは、このドキュメントの目的ではありません（詳細については、以下の関連情報のリンクを参照してください）。 重要なのは、CSPを使用し、セキュリティポリシーが厳しい場合、CSPに追加する必要のあるAdobeドメイン名を理解することです。 これらのドメインを追加すると、サイトにアクセスする訪問者ブラウザーから、使用するExperience Cloudリソースに対する重要な呼び出しを行うことができます。

## ホワイトリストに追加する必要がある Experience Cloud ドメイン {#section-30693e9a96834edfbf04de9e698cf2aa}

使用する各リストExperience Cloudソリュ追加ーションまたはサービスのCSPへのドメイン名またはURLです。

<table id="table_EC9FC999A62D4B7A830CE73B0AB9EF3C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Experience Cloudソリューションまたはサービス </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>AppMeasurement</b> </p> </td> 
   <td colname="col2"> <p>CSPを変更して次を含めます： </p> <p> 
     <ul id="ul_7522AE83A03A4115A84DF5B32D6DD79B"> 
      <li id="li_AB1EC161FB154BEDA1BEFE76C8A38A90"> <span class="codeph"> *.2o7.net</span> </li> 
      <li id="li_4B12A283716746949201528CD6AF529E"> <span class="codeph"> *.omtrdc.net</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Target</b> </p> </td> 
   <td colname="col2"> <p>CSP に <span class="codeph">*.tt.omtrdc.net</span> を追加します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Experience Cloud ID サービスと Audience Manager</b> </p> </td> 
   <td colname="col2"> <p>CSP を変更し、以下のドメインを含めます。</p> 
   <p><ul>
   <li>connect-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>img-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>script-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>frame-src 'self' <code>https://*.demdex.net;</code></li>
   <li>Adobe Launch を使用してタグをデプロイする場合は、ドメインのリストに <code>https://assets.adobedtm.com</code> も追加する必要があります。</li></ul></p> <p><span class="codeph">demdex.net</span> ドメインの呼び出しは、<a href="../introduction/cookies.md" format="dita" scope="local">Cookies および Experience Cloud Identity Service</a> の生成と、ID 同期用に使用されます。<a href="https://docs.adobe.com/content/help/ja-JP/audience-manager/user-guide/reference/demdex-calls.html" format="https" scope="external">Demdex ドメインの呼び出しについて</a>も参照してください。 </p> </td> </tr> 
 <tr>
 <td colname="col1"> <p> <b>Activity Map プラグイン</b> </p> </td> 
 <td colname="col2"> <p>CSP に *.adobe.com を追加します。**メモ**：2020 年 1 月より前に Activity Map をインストールした場合、ブラウザーには「*.omniture.com」への初期リクエストが表示されますが、「*.adobe.com」にリダイレクトされます。 </p></td> 
 </tr>
 </tbody> 
</table>

>[!MORELIKETHIS]
>* [コンテンツセキュリティポリシーリファレンス](https://content-security-policy.com/)
>* [MDN：コンテンツセキュリティポリシー](https://developer.mozilla.org/ja/docs/Web/HTTP/CSP)
>* [Wikipedia：コンテンツセキュリティポリシー](https://en.wikipedia.org/wiki/Content_Security_Policy)

