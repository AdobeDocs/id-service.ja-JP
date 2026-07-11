---
description: この節を確認して、訪問者ID サービスで必要な適切なソリューション、サービス、コードバージョンを使用していることを確認します。
keywords: 訪問者 ID サービス
title: Adobe Visitor ID サービスの要件
exl-id: ebeac4c7-b36c-4a4e-9378-351fac5baf53
TQID: https://experienceleague.adobe.com/yOoLEIKihVSpDLeZsplTZzg-toOENKlBzsQt2G2YcKk
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: c2be0313-b3ae-45e0-b454-d20bf54b23f2id: d3cdead0-685a-4489-9250-4bb709942f66id: df401a2a-327d-468c-a5e4-b7b7ccd071a0id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 727
ht-degree: 39%

---

# Adobe Visitor ID サービスの要件 {#requirements-for-the-experience-cloud-id-service}

この節を確認して、訪問者ID サービスで必要な適切なソリューション、サービス、コードバージョンを使用していることを確認します。

## 実装の成功とサポートを確実にする要件 {#section-15e54a9e9ad2443cb9dc950b4a78f1f1}

サポートされている実装が成功した場合は、コード要件を満たし、Adobe ヘルプに記載されている手順に従います。 サポートされていない実装では、予期しない結果が生じるため、カスタマーケアおよび当社のエンジニアリングチームは、訪問者ID サービスに関する問題のトラブルシューティングや解決を支援できません。

### 標準実装

標準実装については、Adobe Experience Platform Data Collectionの[tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=ja)を参照してください。

### 非標準実装

非標準または手動の実装の場合は、このガイドの手順に従って訪問者ID サービスを設定する必要があります。 上記の標準実装ガイドラインと同様に、コードの配置と読み込みが不適切な場合、サポートされていない実装が作成されます。

## CX エンタープライズ要件：IMS組織ID {#section-a02f537129a64ffbb690d5738d360c26}

訪問者ID サービスを使用するには、お客様の会社がCX エンタープライズを有効にし、IMS組織IDを持っている必要があります。 自社のCX Enterpriseのステータスが不明で、IMS組織IDを見つける必要がある場合は、次のリストを確認してください。

>[!IMPORTANT]
>
>IMS組織IDは大文字と小文字が区別され、指定されたとおりに正確に使用する必要があります。

<table id="table_6C74B676EB094C568D2439FDCC9A7830"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> CX エンタープライズステータス </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>有効</b> </p> </td> 
   <td colname="col2"> <p>会社がCX Enterpriseに対して有効になっていても、IMS組織IDがない場合は、<a href="https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html?lang=ja" format="https" scope="external">組織ID</a>を参照してください（セクション <i>組織IDを検索</i>までスクロールします）。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>不明</b> </p> </td> 
   <td colname="col2"> <p> 自社のCX Enterprise ステータスがわからない場合は、自社のメンバーがAdobe IDを使用して<a href="https://experiencecloud.adobe.com" format="https" scope="external"> marketing.adobe.com</a>でログインできるかどうかを、Adobe アカウントを管理している人に尋ねます。 可能な場合は、有効になり、管理者はIMS組織IDを表示できます。 IMS組織IDを見つけるには、<a href="https://experienceleague.adobe.com/docs/core-services/interface/experience-cloud.html?lang=ja" format="https" scope="external"> CX Enterprise Administration</a>の「管理ページ」の節を参照してください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>無効</b> </p> </td> 
   <td colname="col2"> <p> お客様の会社がCX Enterpriseに対して有効になっていない場合は、「<a href="https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html?lang=ja" format="https" scope="external"> Core Services - Enabling Your Solutions</a>」を参照して開始してください。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## Analytics の要件：地域別データ収集（RDC） {#section-7d04bb013bc84a25bae3b148bc0ca25f}

すべてのトラッキングサーバーは RDC に変換されているので、Analyticsトラッキングサーバーを変更する必要はありません。 [詳細情報...](https://experienceleague.adobe.com/docs/analytics/technotes/rdc/regional-data-collection.html?lang=ja)

## コードライブラリとバージョンの要件 {#section-ad7542a4317d430fa79fc6b095beb84d}

次の節では、訪問者ID サービスの使用に必要な最小コードバージョンを示します。

>[!TIP]
>
>必要最小限ではなく、最新のコードバージョンを使用することをお勧めします。

**JavaScript**

<table id="table_8E773F76DBCB4797A0C117080CA8707C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> CX エンタープライズソリューション </th> 
   <th colname="col3" class="entry"> コードライブラリ </th> 
   <th colname="col4" class="entry"> バージョンの要件 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>訪問者ID サービス </b> </p> </td> 
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
   <td colname="col4"> <p>H.27 </p> <p> <p>注：<span class="keyword"> Analytics</span> s_code バージョン H.27は、Visitor ID Service バージョン 1.6.0のリリースではサポートされなくなりました。 コードを最新バージョンのAppMeasurementにアップグレードします。 </p> </p> </td> 
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
   <td colname="col3"> <p> <span class="codeph"> mbox.js</span> </p> <p><a href="https://experienceleague.adobe.com/en/docs/target-dev/developer/client-side/at-js-implementation/at-js/overview" format="https" scope="external">mbox コード</a>を参照してください。 </p> </td> 
   <td colname="col4"> <p>61 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> at.js</span> </p> <p><a href="https://experienceleague.adobe.com/en/docs/target-dev/developer/client-side/at-js-implementation/at-js/how-atjs-works" format="https" scope="external">at.js 実装</a>を参照してください。 </p> </td> 
   <td colname="col4"> <p>0.9.1 </p> </td> 
  </tr> 
 </tbody> 
</table>

## Android および iOS 向け SDK 要件 {#section-73b2446fba8e463888642c7d7dfd94f1}

少なくとも、Visitor ID サービスには、以下に示すSDK バージョンが必要です。

* Android：4.11.0
* iOS：4.11.0

>[!TIP]
>
>必要最小限ではなく、最新のコードバージョンを使用することをお勧めします。

Visitor ID サービスに対してSDK コードを有効にする必要があります。 [Adobe Mobile Services](https://mobilemarketing.adobe.com/) アカウントから、各アプリ用の最新 SDK コードを有効にして、ダウンロードします。 関連トピック:

* [SDK 訪問者 ID サービスの設定](https://experienceleague.adobe.com/docs/mobile-services/using/manage-app-settings-ug/configuring-app/t-config-visitor.html?lang=ja)
* [Android SDK のメソッド](https://experienceleague.adobe.com/docs/mobile-services/android/experience-cloud-android/c-marketing-cloud.html?lang=ja)
* [iOS SKD メソッド](https://experienceleague.adobe.com/docs/mobile-services/ios/exp-cloud-ios/marketing-cloud.html?lang=ja)

>[!MORELIKETHIS]
>
>* [コードライブラリ](../library/library.md#concept-ff27497375644a898d47984aefb21c97)
