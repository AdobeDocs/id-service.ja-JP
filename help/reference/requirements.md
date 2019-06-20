---
description: この節では、Experience Cloud IDサービスに必要な適切なソリューション、サービスおよびコードバージョンを使用していることを確認してください。
keywords: ID サービス
seo-description: この節では、Experience Cloud IDサービスに必要な適切なソリューション、サービスおよびコードバージョンを使用していることを確認してください。
seo-title: Experience Cloud ID サービスの要件
title: Experience Cloud ID サービスの要件
uuid: 608b1082-6e9e-4101- b6cb-60027950109b
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Experience Cloud ID サービスの要件 {#requirements-for-the-experience-cloud-id-service}

この節では、Experience Cloud IDサービスに必要な適切なソリューション、サービスおよびコードバージョンを使用していることを確認してください。

## 実装の成功とサポートを確実にする要件 {#section-15e54a9e9ad2443cb9dc950b4a78f1f1}

成功した、サポートされた実装は、コード要件を満たし（または上回り）、[!DNL Adobe] ヘルプに記載された説明に従っています。サポートされない実装は、予期せぬ結果を生み出し、カスタマーケアおよびアドビのエンジニアリングチームが ID サービスの問題をトラブルシューティングまたは解決するための努力を支援するのを妨げます。

<table id="table_2216C44AA66248DCAA13BF64BDF2D88A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 実装タイプ </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445" format="dita" scope="local"> 標準</a> </p> </td> 
   <td colname="col2"> <p>Dynamic Tag Management（DTM）を使用した標準実装の場合、以下をおこなう必要があります。 </p> 
    <ul id="ul_59CDE179566844B494F3068FF6333809"> 
     <li id="li_CCCB6AFC08EE405F94C42216D3CE50AC"> ページの <span class="codeph">&lt;head&gt;</span> セクションに埋め込みヘッドコードを配置する。 </li> 
     <li id="li_13962F2CB1764091A84863BE499675A2"><span class="codeph">&lt;/body&gt;</span> 終了タグの前に、埋め込みフッターコードを配置する。 </li> 
    </ul> <p>標準実装は、以下の場合にはサポートされません。 </p> 
    <ul id="ul_3B62559317ED4C7AA548C3B8DBA281F7"> 
     <li id="li_1F16C6D412944197BEA56BC24730782C"> これらの DTM 埋め込みコードのいずれかをマークアップまたはページコードの他の場所に配置する。 </li> 
     <li id="li_05615C01F3A947BBBD41046E68377224"> 非同期メソッド、呼び出し／コールバックメソッド、ラッパーを使用して、DTM コードを付加、追加または読み込む。 </li> 
     <li id="li_B2137DFF627B473FA876580449026D2B">同じページに埋め込みコードの複数のインスタンスを含める。 </li> 
    </ul> <p><a href="https://marketing.adobe.com/resources/help/en_US/dtm/?f=deployment.html" format="https" scope="external">埋め込みコードとホスティングオプション</a>も参照してください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <a href="../implementation-guides/implementation-guides.md#section-2c4f2db1f9704315a7cccab6d2e07113" format="dita" scope="local"> 非標準的な実装 </a> </p> </td> 
   <td colname="col2"> <p>非標準、または手動の実装の場合、ID サービスをこのガイドの手順で説明するとおりに設定する必要があります。前述の DTM ガイドラインのように、不適切なコード配置および読み込みによって、サポートされない実装が作成されます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## Experience Cloud の要件：組織 ID {#section-a02f537129a64ffbb690d5738d360c26}

ID サービスを使用するには、会社で [!DNL Experience Cloud] を有効にして、組織 ID を持つ必要があります。会社の [!DNL Experience Cloud] ステータスが不明であり、組織 ID を探す必要がある場合は、以下のリストを確認してください。

>[!IMPORTANT]
>
>組織IDでは大文字と小文字が区別され、指定したとおりに使用する必要があります。

<table id="table_6C74B676EB094C568D2439FDCC9A7830"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Experience Cloud のステータス </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>有効</b> </p> </td> 
   <td colname="col2"> <p>会社が <span class="keyword">Experience Cloud</span> を有効にしているものの、組織 ID がない場合は、<a href="https://marketing.adobe.com/resources/help/en_US/mcloud/organizations.html" format="https" scope="external">組織 ID</a> を確認してください（<i>組織 ID を見つける</i>セクションまで下にスクロールしてください）。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>不明</b> </p> </td> 
   <td colname="col2"> <p> 会社の <span class="keyword">Experience Cloud</span> のステータスが不明である場合は、会社のアドビアカウントの管理者に、会社のメンバーが Adobe ID を使用して <a href="https://marketing.adobe.com" format="https" scope="external">marketing.adobe.com</a> にログインできるかどうかを問い合わせてください。ログインできる場合は有効であり、管理者が組織 ID を参照できる状態にあります。この ID を探す方法については、<a href="https://marketing.adobe.com/resources/help/en_US/mcloud/?f=admin_getting_started" format="https" scope="external">Experience Cloud 管理</a>の「管理ページ」の節を参照してください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>無効</b> </p> </td> 
   <td colname="col2"> <p> 会社が Experience Cloud を有効にしていない場合は、はじめに、<a href="https://marketing.adobe.com/resources/help/en_US/mcloud/?f=core_services.html" format="https" scope="external">コアサービス - ソリューションを有効にする方法</a>を参照してください。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## Analytics の要件：地域別データ収集（RDC）{#section-7d04bb013bc84a25bae3b148bc0ca25f}

すべてのトラッキングサーバーはRDCに変換されているので、Analyticsトラッキングサーバーを変更する必要はありません。[詳細情報...](https://docs.adobe.com/content/help/en/analytics/admin/data-collection/regional-data-collection/regional-data-collection.html)

## コードライブラリとバージョンの要件 {#section-ad7542a4317d430fa79fc6b095beb84d}

以降では、[!DNL Experience Cloud] ID サービスを使用する際に必要となる最小コードバージョンについて示します。

>[!TIP]
>
>必要最小限ではなく最新のコードバージョンを使用することをお勧めします。

**JavaScript**

<table id="table_8E773F76DBCB4797A0C117080CA8707C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Experience Cloud ソリューション </th> 
   <th colname="col3" class="entry"> コードライブラリ </th> 
   <th colname="col4" class="entry"> バージョンの要件 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b><span class="keyword"></span>  Experience Cloud ID サービス</b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> VisitorAPI.js</span> </p> </td> 
   <td colname="col4"> <p>2.0 以降 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1" morerows="2"> <p> <b> <span class="keyword"> Analytics </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> AppMeasurement.js</span> </p> <p><a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=appmeasure_mjs.html" format="https" scope="external">JavaScript 版 AppMeasurement</a> を参照してください。 </p> </td> 
   <td colname="col4"> <p>1.6.4 以降。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> s_code.js</span> </p> </td> 
   <td colname="col4"> <p>H.27 </p> <p> <p>注意：<span class="keyword"> Analytics</span> s_code バージョン H.27 は、ID サービスバージョン 1.6.0 のリリースからサポートされなくなりました。コードを AppMeasurement の最新バージョンにアップグレードしてください。 </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p>ビデオハートビート </p> <p><a href="https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/hbvideo/index.html" format="https" scope="external">JavaScript 向けビデオハートビート 2.x</a> を参照してください。 </p> </td> 
   <td colname="col4"> <p>2.0 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b> <span class="keyword"> Audience Manager </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> dil.js</span> </p> <p> <a href="https://marketing.adobe.com/resources/help/en_US/aam/?f=c_dil.html" format="https" scope="external">データ統合ライブラリ</a>（DIL）を参照してください。 </p> </td> 
   <td colname="col4"> <p>5.0 </p> <p> 
     <draft-comment>
       4.9から更新 
     </draft-comment> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1" morerows="1"> <p> <b><span class="keyword">Target </span></b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> mbox.js</span> </p> <p><a href="https://marketing.adobe.com/resources/help/en_US/target/ov/?f=c_mbox_technical.html" format="https" scope="external">mbox コード</a>を参照してください。 </p> </td> 
   <td colname="col4"> <p>61 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> at.js</span> </p> <p><a href="https://marketing.adobe.com/resources/help/en_US/target/ov2/c_target-atjs-implementation.html" format="https" scope="external">at.js 実装</a>を参照してください。 </p> </td> 
   <td colname="col4"> <p>0.9.1 </p> </td> 
  </tr> 
 </tbody> 
</table>

## Android および iOS 向け SDK 要件 {#section-73b2446fba8e463888642c7d7dfd94f1}

少なくとも、ID サービスには、以下に示す SDK バージョンが必要です。

* Android: 4.11.0
* iOS：4.11.0

>[!TIP]
>
>必要最小限ではなく最新のコードバージョンを使用することをお勧めします。

ID サービスに関して、SDK コードが有効になっている必要があります。[Adobe Mobile Services](https://mobilemarketing.adobe.com/) アカウントから、各アプリ用の最新 SDK コードを有効にして、ダウンロードします。関連トピック:

* [SDK 訪問者 ID サービスの設定](https://marketing.adobe.com/resources/help/en_US/mobile/t_config_visitor.html)
* [Android SDK のメソッド](https://marketing.adobe.com/resources/help/en_US/mobile/android/c_marketing_cloud.html)
* [iOS SDK のメソッド](https://marketing.adobe.com/resources/help/en_US/mobile/ios/marketing_cloud.html)

>[!MORE_ LIKE_ THIS]
>
>* [コードライブラリ](../library/library.md#concept-ff27497375644a898d47984aefb21c97)

