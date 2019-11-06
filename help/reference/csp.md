---
description: コンテンツセキュリティポリシー（CSP）は、Web ページに読み込まれるリソースのタイプをブラウザーで制御できるようにするために HTTP ヘッダーで使用されるセキュリティ機能です。ID サービスを使用していて、信頼されているドメインからのリソースを許可するホワイトリストを用いる厳格な CSP がある場合は、このセクションを確認してください。ここに記載されているアドビドメインを CSP ホワイトリストに追加する必要があります。
keywords: ID サービス
seo-description: コンテンツセキュリティポリシー（CSP）は、Web ページに読み込まれるリソースのタイプをブラウザーで制御できるようにするために HTTP ヘッダーで使用されるセキュリティ機能です。ID サービスを使用していて、信頼されているドメインからのリソースを許可するホワイトリストを用いる厳格な CSP がある場合は、このセクションを確認してください。ここに記載されているアドビドメインを CSP ホワイトリストに追加する必要があります。
seo-title: コンテンツセキュリティポリシーおよび Experience Cloud Identity Service
title: コンテンツセキュリティポリシーおよび Experience Cloud Identity Service
uuid: 7399edf3-01c1-4730-834e-e2dd2c5791ff
translation-type: ht
source-git-commit: c4c0b791230422f17292b72fd45ba5689a60adae

---


# コンテンツセキュリティポリシーおよび Experience Cloud Identity Service {#content-security-policies-and-the-experience-cloud-id-service}

コンテンツセキュリティポリシー（CSP）は、Web ページに読み込まれるリソースのタイプをブラウザーで制御できるようにするために HTTP ヘッダーで使用されるセキュリティ機能です。ID サービスを使用していて、信頼されているドメインからのリソースを許可するホワイトリストを用いる厳格な CSP がある場合は、このセクションを確認してください。ここに記載されているアドビドメインを CSP ホワイトリストに追加する必要があります。

## CSP レビュー{#section-5fde5c00a678455c914b8307a8caab82}

CSP は HTTP ヘッダー `Content-Security-Policy` を使用してブラウザーが許可したりページに読み込んだりするリソースのタイプを制御します。CSP を適用すると以下の問題を防ぐことができます。

* ソースが不明な JavaScript ファイルや、ホワイトリストに含まれていない JavaScript ファイルの読み込み。
* クロスサイトスクリプティング攻撃。
* データ注入攻撃。
* サイト改編攻撃。
* マルウェアの配布。

CSP の使用は一般的であり、よく理解されています。このドキュメントの目的は CSP について詳しく説明することではありません（詳しくは、後にある関連情報リンクを参照してください）。重要なのは、厳格なセキュリティポリシーを適用する必要がある場合に、CSP に追加する必要があるアドビのドメイン名を理解することです。これらのドメインを追加することで、お客様のサイトにアクセスした訪問者のブラウザーが、使用する Experience Cloud リソースに対する重要な呼び出しをおこなえるようになります。

## ホワイトリストに追加する必要がある Experience Cloud ドメイン {#section-30693e9a96834edfbf04de9e698cf2aa}

現在使用している Experience Cloud ソリューションまたはサービスごとに、これらのドメイン名または URL を CSP に追加してください。

<table id="table_EC9FC999A62D4B7A830CE73B0AB9EF3C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Experience Cloud ソリューションまたはサービス </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>AppMeasurement</b> </p> </td> 
   <td colname="col2"> <p>CSP に以下を追加します。 </p> <p> 
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
   <td colname="col1"> <p> <b>訪問者 ID サービス</b> </p> </td> 
   <td colname="col2"> <p>CSP に <span class="codeph">*.demdex.net</span> を追加します。 </p> <p><span class="codeph"> demdex.net</span> ドメインの呼び出しは、<a href="../introduction/cookies.md" format="dita" scope="local">Cookies および Experience Cloud Identity Service</a> の生成と、ID 同期用に使用されます。<a href="https://docs.adobe.com/content/help/ja-JP/audience-manager/user-guide/reference/demdex-calls.translate.html" format="https" scope="external">Demdex ドメインの呼び出しについて</a>も参照してください。 </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!MORELIKETHIS]
>
>* [コンテンツセキュリティポリシーリファレンス](https://content-security-policy.com/)
>* [MDN：コンテンツセキュリティポリシー](https://developer.mozilla.org/ja/docs/Web/HTTP/CSP)
>* [Wikipedia：コンテンツセキュリティポリシー](https://ja.wikipedia.org/wiki/Content_Security_Policy)

