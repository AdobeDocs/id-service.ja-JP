---
description: ID サービスから Adobe Experience Cloud Device Co-op にデータを送信するかどうかを指定する任意のブール型設定です。
keywords: ID Service
seo-description: ID サービスから Adobe Experience Cloud Device Co-op にデータを送信するかどうかを指定する任意のブール型設定です。
seo-title: isCoopSafe
title: isCoopSafe
uuid: 4dfa1f35-0a88-48d1-9484-d88cb53ad461
translation-type: ht
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: ht
source-wordcount: '604'
ht-degree: 100%

---


# isCoopSafe {#iscoopsafe}

ID サービスから Adobe Experience Cloud Device Co-op にデータを送信するかどうかを指定する任意のブール型設定です。

内容：

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-4883eda6beb8437182bcc82bb58fae41" format="dita" scope="local"> 要件 </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-d18af2b903f248e18ae8108aaf0a8ebb" format="dita" scope="local"> 使用例 </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-952f56724a2b4d349340e26fbaf33ddd" format="dita" scope="local"> 構文およびコードサンプル </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-fcd441933506493faefaa6b51f194a17" format="dita" scope="local"> イベント呼び出し POST パラメーター </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-9281c39c8b6249d7864100b5cbca7dc6" format="dita" scope="local"> インスタンス化後の API </a> </li> 
</ul>

## 要件 {#section-4883eda6beb8437182bcc82bb58fae41}

`isCoopSafe` を使用するには、以下の要件を満たす必要があります。

* バージョン 2.4 以降の ID サービスコードを使用する。
* [Experience Cloud Device Co-op](https://docs.adobe.com/content/help/ja-JP/device-co-op/using/about/overview.html) に参加する。Co-op への参加を検討している場合は、このドキュメントをよく読み、デバイスグラフの作成にデータがどのように使用されるかに関する懸念に `isCoopSafe` で対処できるかどうかを確認する必要があります。

* [!DNL Adobe]コンサルタントに依頼して、Device Co-op アカウントにホワイトリストまたはブラックリストのフラグを設定する。これらのフラグをセルフサービスで有効にする方法はありません。

## 使用例 {#section-d18af2b903f248e18ae8108aaf0a8ebb}

`isCoopSafe` は、Device Co-op に既に参加しているお客様や、参加を検討しているお客様によるデータ収集に関連した 2 つのユースケースの解決に役立ちます。これらのユースケースは、サイト訪問者のデータが Device Co-op にどのように渡され、デバイスグラフの作成にどのように役立てられるかということに関連しています。これらのユースケースで `isCoopSafe` がデータをどのようにブロックまたは送信するかを次の表で説明します。

<table id="table_A24C63D2A21F47EDBAC8FA5E7BE888D8"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 使用例 </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>認証済み訪問者</b> </p> </td> 
   <td colname="col2"> <p><span class="codeph">isCoopSafe</span> を ID サービスコードに追加して、使用規約同意書に同意した（または同意していない）認証済み訪問者のデータを Device Co-op がデバイスグラフの作成にどのように使用するかを管理します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>サードパーティサイトの DIL</b> </p> </td> 
   <td colname="col2"> <p><span class="codeph">isCoopSafe</span> を ID サービスコードに追加して、以下の場合にサードパーティサイトで使用します。 </p> <p> 
     <ul id="ul_C27BB26510314834A2A7CD99D46DA4AC"> 
      <li id="li_4E6AE574F18646F09C0CF4553EEA1A9E">認証済み訪問者が使用規約同意書に同意したかどうかを確認できない。 </li> 
      <li id="li_26D0561BF32B4278B0A6B5082C17FED8">Device Co-op によるデバイスグラフの作成でデータがどのように利用されるかを管理する必要がある。 </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

## 構文およびコードサンプル {#section-952f56724a2b4d349340e26fbaf33ddd}

**構文：** `isCoopSafe: true | false`

Device Co-op で顧客データを利用するか利用しないかをブール型オプションで指定します。

* `isCoopSafe: true`：モバイル SDK または Web サイトが収集した訪問者データをデバイスグラフの作成に利用&#x200B;*できます*。

* `isCoopSafe: false`：モバイル SDK または Web サイトが収集した訪問者データをデバイスグラフの作成に利用&#x200B;*できません*。

**コードサンプル**

ID サービスコードをインスタンス化する際には、次のように設定します。

```js
var visitor = Visitor.getInstance("Insert Experience Cloud organization ID here",{ 
     ... 
     isCoopSafe: true 
});
```

## イベント呼び出し POST パラメーター {#section-fcd441933506493faefaa6b51f194a17}

設定したフラグ（`true` または `false`）に応じて、ID サービスは `isCoopSafe` をこれらの POST パラメーターに変換し、イベント呼び出しで [!DNL Adobe] に送信します。

* `d_coop_safe=1`
* `d_coop_unsafe=1`

POST パラメーターは、ユーザーデータをデバイスグラフに含めてもよいかどうかを [!DNL Experience Cloud] Device Co-op に通知します。次の表で `isCoopSafe` のブール型フラグとイベント呼び出し時に渡される POST パラメーターの関係について説明します。`isCoopSafe` を使用しない場合、イベント呼び出しにおいて、これらのいずれも渡されません。

<table id="table_0A544534CA904F4D9836A34B8C1EACBB"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 設定ステータス </th> 
   <th colname="col2" class="entry"> POST パラメーター </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe: true </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> d_coop_safe=1 </span> </p> <p>Device Co-op は訪問者データをデバイスグラフの作成に利用できます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe: false </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> d_coop_unsafe=1 </span> </p> <p>Device Co-op は訪問者データをデバイスグラフの作成に利用できません。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## インスタンス化後の API {#section-9281c39c8b6249d7864100b5cbca7dc6}

これらの API を使用すると `isCoopSafe` のステータスを変更できます。これらを使用すると、ページが更新されない場合にサイトやシングルページアプリで訪問者のインスタンス化後またはログイン後のステータスを変更できます。例えば、ユーザーがサイトやアプリで認証をおこない、後で Device Co-op によるデータ利用を許可する使用規約ポリシーに同意した場合に、これらの API を呼び出す必要があります。

<table id="table_BAA96B1F82BE48C3A61A1AF1367BA45C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> API </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> visitor.setAsCoopSafe(); </span> </p> </td> 
   <td colname="col2"> <p>後続のすべてのイベント呼び出しで POST パラメーター <span class="codeph">d_coop_safe=1</span> を設定します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> visitor.setAsCoopUnsafe(); </span> </p> </td> 
   <td colname="col2"> <p>後続のすべてのイベント呼び出しで POST パラメーター <span class="codeph">d_coop_unsafe=1</span> を設定します。 </p> </td> 
  </tr> 
 </tbody> 
</table>

<!--
Wiki page https://wiki.corp.adobe.com/x/RCfFTg
-->

>[!MORELIKETHIS]
>
>* [DIL isCoopSafe](https://docs.adobe.com/content/help/ja-JP/audience-manager/user-guide/dil-api/class-level-dil-methods/dil-coopsafe.html)

