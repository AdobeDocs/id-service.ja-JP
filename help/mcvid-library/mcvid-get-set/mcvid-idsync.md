---
description: ID サービスの関数、idSyncByURL と idSyncByDataSource を使用すると、ターゲットパブリッシング iFrame で ID 同期を手動で実装できます。これらは、VisitorAPI.js バージョン 1.10 以降で利用できます。
keywords: ID サービス
seo-description: ID サービスの関数、idSyncByURL と idSyncByDataSource を使用すると、ターゲットパブリッシング iFrame で ID 同期を手動で実装できます。これらは、VisitorAPI.js バージョン 1.10 以降で利用できます。
seo-title: URL またはデータソースによる ID 同期
title: URL またはデータソースによる ID 同期
uuid: ff83d910-8375-4295-9f2a- e14c15eee09a
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# URL またはデータソースによる ID 同期{#id-synchronization-by-url-or-data-source}

ID サービスの関数、idSyncByURL と idSyncByDataSource を使用すると、ターゲットパブリッシング iFrame で ID 同期を手動で実装できます。これらは、VisitorAPI.js バージョン 1.10 以降で利用できます。

内容：

<ul class="simplelist"> 
 <li> <a href="../../mcvid-library/mcvid-get-set/mcvid-idsync.md#section-90ac61617482463aaf4c57009b830332" format="dita" scope="local"> 構文、プロパティおよびマクロ </a> </li> 
 <li> <a href="../../mcvid-library/mcvid-get-set/mcvid-idsync.md#section-0115615c37584a19a2ab11e917c4e7e9" format="dita" scope="local"> サンプルコードと出力 </a> </li> 
</ul>

## 構文、プロパティおよびマクロ {#section-90ac61617482463aaf4c57009b830332}

**構文**

<table id="table_ADC7501511914805A6A6B24B2DFEBA51"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> コード </th> 
   <th colname="col2" class="entry"> ユーザー ID の同期 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> visitor.idSyncByURL(); </span> </p> </td> 
   <td colname="col2"> <p>カスタム ID 同期 URL を使用して、様々なデータパラメーターおよび <span class="keyword">Audience Manager</span> 間で同期。 </p> <p> 
     <draft-comment>
       複数のデータパートナーと Audience Manager の間で実行されます。例えば、パートナー x がこれを使用してユーザー ID をパートナー y と同期し、Audience Manager に送信します。 
     </draft-comment> </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> visitor.idSyncByDataSource(); </span> </p> </td> 
   <td colname="col2"> <p>既に DPID および DPUUID がわかっており、標準 ID 同期 URL 形式で <span class="keyword">Audience Manager</span> に送信したい場合。 </p> <p> 
     <draft-comment>
       ユーザー ID が既に判明していて、それを Audience Manager に送信する場合に使用します。 
     </draft-comment> </p> </td> 
  </tr> 
 </tbody> 
</table>

**プロパティ**

以下の表に、両方の関数で利用可能なプロパティのリストと定義を示します。

<table id="table_5343BE784E694C67B09A0A8878CF8001"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 名前 </th> 
   <th colname="col2" class="entry"> タイプ </th> 
   <th colname="col3" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> dpid </span> </td> 
   <td colname="col2"> 文字列 </td> 
   <td colname="col3"> <p>Audience Manager によって割り当てられたデータプロバイダー ID。 </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> dpuuid </span> </td> 
   <td colname="col2"> 文字列 </td> 
   <td colname="col3"> <p>ユーザーに関するデータプロバイダーの一意の ID。 </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> minutesToLive </span> </td> 
   <td colname="col2"> 数値 </td> 
   <td colname="col3"> <p> <i>（オプション）</i> Cookie の有効期限を設定します。整数である必要があります。デフォルトは、20,160 分（14 日）です。 </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> url </span> </td> 
   <td colname="col2"> 文字列 </td> 
   <td colname="col3"> <p>リンク先 URL。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**マクロ**

両方の関数は、以下のマクロを受け付けます。

* ** `%TIMESTAMP%`:**タイムスタンプを生成します（ミリ秒単位）。キャッシュバスティングに使用されます。
* ** `%DID%`:**ユーザーのAudience Manager IDを挿入します。
* ** `%HTTP_PROTO%`:**通信プロトコル（ `http` また `https`は）を設定します。

## サンプルコードと出力 {#section-0115615c37584a19a2ab11e917c4e7e9}

両方の関数が成功した場合に返さ `Successfully queued` れます。そうでない場合、エラーメッセージを返します。

**visitor.idSyncByURL**

<table id="table_56AD8291DF9445C69CC2BF50435E1626"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> サンプルコード </th> 
   <th colname="col2" class="entry"> サンプル出力 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <code class="syntax javascript"> //Instatiate訪問者
var visitor= Visitor. getInstance（"MARKETING- CLOUD- ORG- ID"，{}）;{}）;

    //&amp; amp;nbsp;amp&amp; amp;nbsp;url&amp; amp;nbsp;with&amp; amp;nbsp;マクロ&amp; amp;nbsp;replaceVisitor
    . idSyncByURL（{
    &amp; amp;nbsp;dpid:&amp; amp;nbsp;24&#39;amp; amp;nbsp;//&amp; amp;nbsp;must&amp; amp;nbsp;amp&amp; amp;nbsp;1amp（&amp; amp）;nbsp;文字列
    amp;nbsp;url:&amp; amp;nbsp;&#39;//su.addthis.com/red/usync?pid=16&amp;amp;puid=%DID%&amp;amp;url=%HTTP_PROTO%%3A%2F%2Fdpm.demdex.net%2Fibs%3Adpid%3D420%26dpuuid%3D%7B%7Buid%7D%7D&#39;,&amp;nbsp;minutesToLive:&amp;nbsp;20160&amp;nbsp;//&amp;nbsp;optional,&amp;nbsp;defaults&amp;nbsp;to&amp;nbsp;20160&amp;nbsp;minutes&amp;nbsp;(14&amp;nbsp;days)&amp;nbsp
    ;
    }）;&lt;/code&gt;&lt;/p&gt;&lt;/td&gt;
<td colname="col2"> <p> <span class="codeph"> http://su.addthis.com/red/usync?pid=16&amp;puid=28777806459181003670799219185178493848&amp;url=http%3A%2F%2Fdpm.demdex.net%2Fibs%3Adpid%3D420%26dpuuid%3D%7B%7Buid%7D%7D </span> </p> </td> 
  </tr> 
 </tbody> 
</table>

**visitor.idSyncByDataSource**

<table id="table_90D61A7E715D47238AAFF2808B33C2F0"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> サンプルコード </th> 
   <th colname="col2" class="entry"> サンプル出力 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <code class="syntax javascript"> //Instantiate訪問者
var visitor= Visitor. getInstance（"MARKETING- CLOUD- ORG- ID"，{}）;{}）;

    //&amp; amp;nbsp;amp&amp; amp;nbsp;&#39;http:/https:&#39;&amp;nbsp;+&amp;nbsp;&#39;//dpm.demdex.net/ibs:dpid=&amp;lt;dpid&amp;gt;&amp;amp;dpuuid=&amp;lt;dpuuid&amp;gt;&#39;visitor.idSyncByDataSource(
    {
    &amp; amp;nbsp;dpid:&amp; amp;nbsp;24&#39;amp; amp;nbsp;//&amp; amp;nbsp;must&amp; amp;nbsp;amp&amp; amp;nbsp;1amp（&amp; amp）;nbsp;文字列
    amp;nbsp;dpuuid:&amp; amp;nbsp;98765&#39;，&amp; amp;nbsp;//&amp; amp;nbsp;must&amp; amp;nbsp;amp&amp; amp;nbsp;1amp（&amp; amp）;nbsp;文字列
    amp;nbsp;minutesToLive:&amp; amp;nbsp;20160&amp; amp;nbsp;//&amp; amp;nbsp;オプション、amp;nbsp;default&amp; amp;nbsp;宛先（&amp; amp）;nbsp;20160&amp; amp;nbsp;minutes&amp; amp;nbsp;（14&amp; amp;nbsp;days）&amp; amp;nbsp;
    }）;&lt;/code&gt;&lt;/p&gt;&lt;/td&gt;
<td colname="col2"> <p> <span class="codeph"> http://dpm.demdex.net/ibs:dpid=24&amp;dpuuid=98765 </span> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!MORE_ LIKE_ THIS]
>
>* [DIL idSync](https://marketing.adobe.com/resources/help/en_US/aam/r_dil_idsync.html)

