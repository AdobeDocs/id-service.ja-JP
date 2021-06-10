---
description: Experience Cloud Identity Service をデプロイする前に、このサービスが複数のドメインでの訪問者トラッキングに与える影響と、異なる方法や JavaScript ファイルによってデータを収集する場合の潜在的な問題について理解する必要があります。
keywords: ID サービス
title: Experience Cloud Identity Service 移行の判断ポイント
exl-id: f2802db2-c95f-476f-8c60-f45e8312253c
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 100%

---

# Experience Cloud Identity Service 移行の判断ポイント

Experience Cloud Identity Service をデプロイする前に、このサービスが複数のドメインでの訪問者トラッキングに与える影響と、異なる方法や JavaScript ファイルによってデータを収集する場合の潜在的な問題について理解する必要があります。

この節に示す質問に答えながら、必要な移行手順について判断してください。

## データ収集 CNAME がありますか。

多くの環境では、ID サービスに移行する際に、データ収集 CNAME の使用を停止することができます。

<table id="table_13F7C1E3D64D4F86B0149C9D3B54AADD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> データ収集方法 </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>CNAME がある </p> </td> 
   <td colname="col2"> <p>次の質問を確認して、データ収集 CNAME の使用を停止する必要があるかどうかを判断します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>CNAME がない </p> </td> 
   <td colname="col2"> <p>「<a href="../../reference/analytics-reference/migration-decisions.md#section-34dabde7780e4a339f134c0ca7768961" format="dita" scope="local">データ収集 CNAME がない場合、データ収集サーバーは *.2o7.net または *.sc.omtrdc.net のどちらですか。</a>」の質問に進みます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## データ収集 CNAME がある場合、複数のドメインがありますか。

データを&#x200B;*同じレポートスイート*&#x200B;に送信する複数のドメインがある場合、CNAME によるデータ収集をお勧めします。この方法により、複数のドメインで訪問者を追跡できます。単一のドメインでデータを収集している場合は、データ収集 CNAME を維持する必要はありません。

<table id="table_D132BCA243E54657AEC930559343FDD3"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> データの収集元 </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>複数のドメイン </p> </td> 
   <td colname="col2"> <p>複数のドメインで訪問者を追跡しており、顧客が他のドメインを訪問する前にメインエントリサイトを最初に訪問してそこで顧客を識別する場合は、データ収集 CNAME を引き続き使用する必要があります。<!--See <a href="../../reference/analytics-reference/cname.md#concept-4df91f8a30ad4ec7a01eb943d579cc9d" format="dita" scope="local"> Data Collection CNAMES and Cross Domain Tracking</a> for a detailed explanation.--> </p> <p>ID サービスを使用して CNAME を設定するには、<span class="codeph">visitor.marketingCloudServer</span> と <span class="codeph">visitor.marketingCloudServerSecure</span> の 2 つの追加のトラッキングサーバーパラメーターを指定する必要があることに注意してください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>単一のドメイン </p> </td> 
   <td colname="col2"> <p>単一のドメインを使用する場合は、データ収集 CNAME の管理を終了したい場合に、その使用を停止できます。ただし、CNAME が機能している場合には、変更する必要はありません。 </p> <p>CNAME を削除する場合： </p> 
    <ul id="ul_12CDECEFC7BB41A18895B507CAA42315"> 
     <li id="li_32E2CD3E58454E20A642BADE507AE86E">新しいトラッキングサーバーが <a href="https://docs.adobe.com/content/help/ja-JP/analytics/technotes/rdc/regional-data-collection.html" format="https" scope="external">RDC に準拠している</a>ことを確認します。 </li> 
     <li id="li_865BB6DAA3594EBBAB688E73C8343762"><span class="keyword">Experience Cloud</span> ID サービスに移行する数ヶ月前に、CNAME から RDC トラッキングサーバーに移行します。 </li> 
     <li id="li_284A015177554C848C8648DC5BBAA365"> <i></i><span class="codeph">*.2o7.net</span> トラッキングサーバーは使用しないでください。 </li> 
     <li id="li_B1ABF03DC46C42059F61542CDE0FE5A1">訪問者の移行の設定方法については、<a href="https://helpx.adobe.com/jp/marketing-cloud/contact-support.html" format="https" scope="external">カスタマーケア</a>にお問い合わせください。この設定により、訪問者を一貫性のある方法でカウントすることができます。 </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## 複数の Analytics JavaScript ファイルがありますか。または、Flash アプリケーションやビデオを追跡していますか。

サイトに、*同じレポートスイート*&#x200B;にデータを送信する複数の Analytics JavaScript ファイル、または Flash アプリケーションやビデオがある場合は、[!DNL Experience Cloud] ID サービスの展開中も訪問者が引き続き Analytics ID で識別されるように、猶予期間を設定する必要があります。

<table id="table_8A4EA063AF4345B69BC98537E2E702BA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> データ収集方法 </th> 
   <th colname="col2" class="entry"> 必要なアクション </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> 
    <ul id="ul_910DD99E074E49C6907F86426EFA5BF2"> 
     <li id="li_4366CC8EB7A54A959568E3761ABBBF23">複数の Analytics JavaScript ファイル </li> 
     <li id="li_B8A8132019EA48088E4F37E36F153D76">その他のデータ収集方法 </li> 
    </ul> </td> 
   <td colname="col2"> <p>各 JavaScript ファイルおよび他のデータ収集ライブラリに訪問者 ID サービスを展開できるように、訪問者 ID サービス猶予期間を設定する必要があります。<a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local">ID サービスの猶予期間</a>を参照してください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>単一の Analytics JavaScript ファイル </p> </td> 
   <td colname="col2"> <p>猶予期間を設定することなく、訪問者 ID サービスを使用するように単一の JavaScript ファイルを更新できます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## サポートされていないデータ収集方法を使用していますか。

リンクを追跡する方法を更新するか、Silverlight から移行しなければならない場合があります。

<table id="table_A72AEB92F48345DD83F136B9989F4EF9"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> データ収集方法 </th> 
   <th colname="col2" class="entry"> 必要なアクション </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>JavaScript、Flash </p> </td> 
   <td colname="col2"> <p>なし。<span class="keyword">Experience Cloud</span> ID サービスは、これらのデータ収集方法をサポートしています。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Silverlight </p> </td> 
   <td colname="col2"> <p>訪問者が Silverlight コンテンツと、<span class="keyword">Experience Cloud</span> ID サービスを使用するその他のサイトセクションにアクセスできる場合は、Silverlight から移行する必要があります。ID サービスは Silverlight をサポートしていません。 </p> <p> Silverlight ベースのビデオプレーヤーを追跡している場合は、代わりに使用できる JavaScript API がベンダーから提供されている可能性があります。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>ハードコーディングされた画像タグ </p> </td> 
   <td colname="col2"> <p>JavaScript を使用するようにハードコーディングされたリンクを更新します。 </p> </td> 
  </tr> 
 </tbody> 
</table>
