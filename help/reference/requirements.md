---
description: ここでは、Experience Cloud Identity Service に必要な適切なソリューション、サービス、コードバージョンを使用していることを確認します。
keywords: ID サービス
title: Experience Cloud Identity Service の要件
exl-id: ebeac4c7-b36c-4a4e-9378-351fac5baf53
source-git-commit: 159b37e360b586bbada13e34793009e3067de668
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 100%

---

# Experience Cloud Identity Service の要件 {#requirements-for-the-experience-cloud-id-service}

ここでは、Experience Cloud Identity Service に必要な適切なソリューション、サービス、コードバージョンを使用していることを確認します。

## 実装の成功とサポートを確実にする要件 {#section-15e54a9e9ad2443cb9dc950b4a78f1f1}

成功した、サポートされた実装は、コード要件を満たし（または上回り）、[!DNL Adobe] ヘルプに記載された説明に従っています。サポートされない実装は、予期せぬ結果を生み出し、カスタマーケアおよびアドビのエンジニアリングチームが ID サービスの問題をトラブルシューティングまたは解決するための努力を支援するのを妨げます。

### 標準実装

標準実装について詳しくは、[Experience Platform タグ](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=ja)を参照してください。

### 非標準実装

非標準、または手動の実装の場合、ID サービスをこのガイドの手順で説明するとおりに設定する必要があります。前述の DTM ガイドラインのように、不適切なコード配置および読み込みによって、サポートされない実装が作成されます。

## Experience Cloud の要件：組織 ID {#section-a02f537129a64ffbb690d5738d360c26}

ID サービスを使用するには、会社で [!DNL Experience Cloud] を有効にして、組織 ID を持つ必要があります。会社の [!DNL Experience Cloud] ステータスが不明であり、組織 ID を探す必要がある場合は、以下のリストを確認してください。

>[!IMPORTANT]
>
>組織 ID は大文字小文字が区別され、割り当てられたとおりに使用する必要があります。

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
   <td colname="col2"> <p>会社が <span class="keyword">Experience Cloud</span> を有効にしているものの、組織 ID がない場合は、<a href="https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html?lang=ja" format="https" scope="external">組織 ID</a> を確認してください（<i>組織 ID を見つける</i>セクションまで下にスクロールしてください）。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>不明</b> </p> </td> 
   <td colname="col2"> <p> 会社の <span class="keyword">Experience Cloud</span> のステータスが不明である場合は、会社のアドビアカウントの管理者に、会社のメンバーが Adobe ID を使用して <a href="https://experiencecloud.adobe.com" format="https" scope="external">marketing.adobe.com</a> にログインできるかどうかを問い合わせてください。ログインできる場合は有効であり、管理者が組織 ID を参照できる状態にあります。この ID を探す方法については、<a href="https://experienceleague.adobe.com/docs/core-services/interface/experience-cloud.html?lang=ja" format="https" scope="external">Experience Cloud 管理</a>の「管理ページ」の節を参照してください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>無効</b> </p> </td> 
   <td colname="col2"> <p> 会社が Experience Cloud を有効にしていない場合は、はじめに、<a href="https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html?lang=ja" format="https" scope="external">コアサービス - ソリューションを有効にする方法</a>を参照してください。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## Analytics の要件：地域別データ収集（RDC）  {#section-7d04bb013bc84a25bae3b148bc0ca25f}

すべてのトラッキングサーバーは RDC に変換されているので、Analyticsトラッキングサーバーを変更する必要はありません。[詳細情報...](https://experienceleague.adobe.com/docs/analytics/technotes/rdc/regional-data-collection.html?lang=ja)

## コードライブラリとバージョンの要件 {#section-ad7542a4317d430fa79fc6b095beb84d}

以降では、[!DNL Experience Cloud] ID サービスを使用する際に必要となる最小コードバージョンについて示します。

>[!TIP]
>
>必要最小限ではなく、最新のコードバージョンを使用することをお勧めします。

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
   <td colname="col1"> <p> <b> <span class="keyword"> Experience Cloud</span> ID サービス</b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> VisitorAPI.js</span> </p> </td> 
   <td colname="col4"> <p>2.0 以降 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1" morerows="2"> <p> <b> <span class="keyword"> Analytics </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> AppMeasurement.js</span> </p> <p><a href="https://experienceleague.adobe.com/docs/analytics/implementation/js/overview.html?lang=ja" format="https" scope="external">JavaScript 版 AppMeasurement</a> を参照してください。 </p> </td> 
   <td colname="col4"> <p>1.6.4 以降。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> s_code.js</span> </p> </td> 
   <td colname="col4"> <p>H.27 </p> <p> <p>注意：<span class="keyword"> Analytics</span> s_code バージョン H.27 は、ID サービスバージョン 1.6.0 のリリースからサポートされなくなりました。コードを AppMeasurement の最新バージョンにアップグレードしてください。 </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p>ビデオハートビート </p> <p><a href="https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=ja" format="https" scope="external">JavaScript 向けビデオハートビート 2.x</a> を参照してください。 </p> </td> 
   <td colname="col4"> <p>2.0 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b> <span class="keyword"> Audience Manager </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> dil.js</span> </p> <p> <a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/dil-overview.html?lang=ja" format="https" scope="external">データ統合ライブラリ</a>（DIL）を参照してください。 </p> </td> 
   <td colname="col4"> <p>5.0 </p></td> 
  </tr> 
  <tr> 
   <td colname="col1" morerows="1"> <p> <b> <span class="keyword">Target </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> mbox.js</span> </p> <p><a href="https://experienceleague.adobe.com/docs/target/using/implement-target/client-side/mbox-implement/mbox-technical.html?lang=ja" format="https" scope="external">mbox コード</a>を参照してください。 </p> </td> 
   <td colname="col4"> <p>61 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> at.js</span> </p> <p><a href="https://experienceleague.adobe.com/docs/target/using/implement-target/client-side/at-js/how-atjs-works.html?lang=ja" format="https" scope="external">at.js 実装</a>を参照してください。 </p> </td> 
   <td colname="col4"> <p>0.9.1 </p> </td> 
  </tr> 
 </tbody> 
</table>

## Android および iOS 向け SDK 要件 {#section-73b2446fba8e463888642c7d7dfd94f1}

少なくとも、ID サービスには、以下に示す SDK バージョンが必要です。

* Android：4.11.0
* iOS：4.11.0

>[!TIP]
>
>必要最小限ではなく、最新のコードバージョンを使用することをお勧めします。

ID サービスに関して、SDK コードが有効になっている必要があります。[Adobe Mobile Services](https://mobilemarketing.adobe.com/) アカウントから、各アプリ用の最新 SDK コードを有効にして、ダウンロードします。関連トピック:

* [SDK 訪問者 ID サービスの設定](https://experienceleague.adobe.com/docs/mobile-services/using/manage-app-settings-ug/configuring-app/t-config-visitor.html?lang=ja)
* [Android SDK のメソッド](https://experienceleague.adobe.com/docs/mobile-services/android/experience-cloud-android/c-marketing-cloud.html?lang=ja)
* [iOS SDK のメソッド](https://experienceleague.adobe.com/docs/mobile-services/ios/exp-cloud-ios/marketing-cloud.html?lang=ja)

>[!MORELIKETHIS]
>
>* [コードライブラリ](../library/library.md#concept-ff27497375644a898d47984aefb21c97)

