---
description: ID サービスの idSyncByURL 関数と idSyncByDataSource 関数を使用すると、Destination Publishing iFrame で ID 同期を手動で実装できます。これらは、VisitorAPI.js バージョン 1.10 以降で利用できます。
keywords: ID サービス
title: URL またはデータソースによる ID 同期
exl-id: a22e6b47-00ff-4b51-9958-ddeccc1e507e
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 100%

---

# URL またはデータソースによる ID 同期{#id-synchronization-by-url-or-data-source}

ID サービスの idSyncByURL 関数と idSyncByDataSource 関数を使用すると、Destination Publishing iFrame で ID 同期を手動で実装できます。これらは、VisitorAPI.js バージョン 1.10 以降で利用できます。

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
   <td colname="col2"> <p>カスタム ID 同期 URL を使用して、様々なデータパラメーターおよび <span class="keyword">Audience Manager</span> 間で同期。 </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> visitor.idSyncByDataSource(); </span> </p> </td> 
   <td colname="col2"> <p>既に DPID および DPUUID がわかっており、標準 ID 同期 URL 形式で <span class="keyword">Audience Manager</span> に送信したい場合。 </p> <p></p> </td> 
  </tr> 
 </tbody> 
</table>

**プロパティ**

次の表のリストと、両方の関数で使用できるプロパティの定義を示します。

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
   <td colname="col3"> <p>ユーザーに対するデータプロバイダーの一意の ID。 </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> minutesToLive </span> </td> 
   <td colname="col2"> 数値 </td> 
   <td colname="col3"> <p> <i>（オプション）</i> Cookie の有効期限を設定します。整数である必要があります。デフォルトは 20160 分（14 日）です。 </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> url </span> </td> 
   <td colname="col2"> 文字列 </td> 
   <td colname="col3"> <p>宛先 URL </p> </td> 
  </tr> 
 </tbody> 
</table>

**マクロ**

どちらの関数も次のマクロを受け付けます。

* `%TIMESTAMP%`：タイムスタンプを生成します（ミリ秒単位）。キャッシュバスティングに使用されます。
* `%DID%`：ユーザーの Audience Manager ID を挿入します。
* `%HTTP_PROTO%`：通信プロトコルを設定します（`http` または `https`）。

## サンプルコードと出力 {#section-0115615c37584a19a2ab11e917c4e7e9}

両方の関数は、成功した場合、`Successfully queued` を返します。そうでない場合、エラーメッセージを返します。

### visitor.idSyncByURL

**サンプルコード**

```javascript
   //Instatiate Visitor
    var visitor = Visitor.getInstance
    ("MARKETING-CLOUD-ORG-ID-HERE",{}); 
   // Fires url with macros replaced 
    visitor.idSyncByURL({ 
    dpid: '24', // must be a string 
    url: '//su.addthis.com/red/usync?pid=16&puid=%DID%&url=%HTTP_PROTO%://
    dpm.demdex.net/ibs:dpid=420&dpuuid={{uid}}', 
    minutesToLive: 20160 // optional, defaults to 20160 minutes (14 days) });
```

**サンプル出力**

```
http://su.addthis.com/red/usync?pid=16&puid=28777806459181003670799219185178493848&url=http%3A%2F%2Fdpm.demdex.net%2Fibs%3Adpid%3D420%26dpuuid%3D%7B%7Buid%7D%7D
```

### visitor.idSyncByDataSource

**サンプルコード**

```javascript
  //Instantiate Visitor
   var visitor = Visitor.getInstance
   ("MARKETING-CLOUD-ORG-ID-HERE",{}); 
  // Fires 'http:/https:' + '//dpm.demdex.net/ibs:dpid=&dpuuid='
   visitor.idSyncByDataSource({ 
     dpid: '24', // must be a string
     dp     minutesToLive: 20160 // optional, defaults to 20160 minutes (14 days) });
```

**サンプル出力**

```
http://dpm.demdex.net/ibs:dpid=24&dpuuid=98765
```

>[!MORELIKETHIS]
>
>* [DIL idSync](https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/dil-instance-methods.html?lang=ja#idsync)

