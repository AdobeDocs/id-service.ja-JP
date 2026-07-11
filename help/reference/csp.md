---
description: コンテンツセキュリティポリシー（CSP）は、Web ページに読み込まれるリソースのタイプをブラウザーで制御できるようにするために HTTP ヘッダーで使用されるセキュリティ機能です。 Visitor ID サービスを使用しており、信頼できるドメインからリソースを受け入れるために許可リストを使用する厳格なCSPを使用している場合は、この節を参照してください。 ここに記載されているアドビドメインを CSP 許可リストに追加する必要があります。
keywords: 訪問者 ID サービス
title: コンテンツセキュリティポリシーとAdobe Visitor ID サービス
exl-id: e35c6809-764e-4c3e-9139-88bb92e82338
TQID: https://experienceleague.adobe.com/UX0RWE7v912XEHJCJE49yt1sy13t1P0I0I79gG9Z7m8
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 527
ht-degree: 70%

---

# コンテンツセキュリティポリシーとAdobe Visitor ID サービス {#content-security-policies-and-the-experience-cloud-id-service}

コンテンツセキュリティポリシー（CSP）は、Web ページに読み込まれるリソースのタイプをブラウザーで制御できるようにするために HTTP ヘッダーで使用されるセキュリティ機能です。 Visitor ID サービスを使用しており、信頼できるドメインからリソースを受け入れるために許可リストを使用する厳格なCSPを使用している場合は、この節を参照してください。 ここに記載されているアドビドメインを CSP 許可リストに追加する必要があります。

## CSP レビュー {#section-5fde5c00a678455c914b8307a8caab82}

CSP は HTTP ヘッダー `Content-Security-Policy` を使用してブラウザーが許可したりページに読み込んだりするリソースのタイプを制御します。 CSP を適用すると以下の問題を防ぐことができます。

* ソースが不明、または許可リストに含まれていない JavaScript ファイルの読み込み。
* クロスサイトスクリプティング（XXS）攻撃。
* データインジェクション攻撃。
* サイト改ざん攻撃。
* マルウェアの配布。

CSP の使用は一般的であり、よく理解されています。 このドキュメントの目的は CSP について詳しく説明することではありません（詳しくは、後にある関連情報リンクを参照してください）。 重要なのは、厳格なセキュリティポリシーを適用する必要がある場合に、CSP に追加する必要があるアドビのドメイン名を理解することです。 これらのドメインを追加すると、サイトにアクセスする訪問者ブラウザーが、使用するCX エンタープライズリソースに対して重要な呼び出しを行うことができます。

## 許可リストに加える用CX Enterprise Domains {#section-30693e9a96834edfbf04de9e698cf2aa}

使用するリスト CX Enterprise ソリューションまたはサービスごとに、これらのドメイン名またはURLをCSPに追加します。

<table id="table_EC9FC999A62D4B7A830CE73B0AB9EF3C">
 <thead>
  <tr>
   <th colname="col1" class="entry">CX エンタープライズソリューション/サービス</th>
   <th colname="col2" class="entry">説明</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1">
    <p><b>AppMeasurement</b></p>
   </td>
   <td colname="col2">
    <p>CSP に以下を追加します。</p>
    <ul id="ul_7522AE83A03A4115A84DF5B32D6DD79B">
     <li id="li_AB1EC161FB154BEDA1BEFE76C8A38A90"><span class="codeph">*.2o7.net</span></li>
     <li id="li_4B12A283716746949201528CD6AF529E"><span class="codeph">*.omtrdc.net</span></li>
    </ul>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>ターゲット</b></p>
   </td>
   <td colname="col2">
    <p>CSP に <span class="codeph">*.tt.omtrdc.net</span> を追加します。</p>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Visitor ID ServiceとAudience Manager</b></p>
   </td>
   <td colname="col2">
    <p>CSP を変更し、以下のドメインを含めます。</p>
    <ul>
     <li>connect-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
     <li>img-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
     <li>script-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
     <li>frame-src 'self' <code>https://*.demdex.net;</code></li>
     <li>タグを使用する場合は、<code>https://assets.adobedtm.com</code>をドメインのリストに追加する必要もあります。</li>
    </ul>
    <p><span class="codeph">demdex.net</span> ドメインへの呼び出しは、<a href="../introduction/cookies.md" format="dita" scope="local">Cookieと訪問者ID サービス </a>の生成およびID同期に使用されます。 詳しくは、<a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=ja" format="https" scope="external">Demdex ドメインの呼び出しについて</a>も参照してください。</p>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Activity Map プラグイン</b></p>
   </td>
   <td colname="col2">
    <p>CSP に *.adobe.com を追加します。 **メモ**：2020 年 1 月より前に Activity Map をインストールした場合、ブラウザーには「*.omniture.com」への初期リクエストが表示されますが、「*.adobe.com」にリダイレクトされます。</p>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Advertising Analytics</b></p>
   </td>
   <td colname="col2">
    <p>クエリ文字列パラメーターを制限する場合は、次のパラメーターを許可リストに加えます。</p>
    <ul>
     <li><code>s_kwcid</code> （<code>!</code> を使用）</li>
     <li><code>ef_id</code> （<code>:</code> を使用）</li>
    </ul>
    <p>URL 内の <code>!</code> 文字をブロックする場合は、その文字も許可リストに加えます。</p>
    <p>Advertising Analytics では <code>s_kwcid</code> のみを使用しますが、Advertising 検索、Social、Commerce、Advertising DSPでも <code>ef_id</code> を使用します。</p>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Adobe Advertising</b></p>
   </td>
   <td colname="col2">
    <p>CSP に次のドメインを追加します：</p>
    <ul>
     <li><code>.everestjs.net</code></li>
     <li><code>.everesttech.net</code></li>
    </ul>
   </td>
  </tr>
 </tbody>
</table>

>[!MORELIKETHIS]
>
>* [コンテンツセキュリティポリシーリファレンス](https://content-security-policy.com/)
>* [MDN：コンテンツセキュリティポリシー](https://developer.mozilla.org/ja/docs/Web/HTTP/CSP)
>* [Wikipedia：コンテンツセキュリティポリシー](https://en.wikipedia.org/wiki/Content_Security_Policy)

