---
description: このプロパティは ID 同期に使用するデータソースコンテナ ID を設定します。
keywords: ID サービス
seo-description: このプロパティは ID 同期に使用するデータソースコンテナ ID を設定します。
seo-title: idSyncContainerID
title: idSyncContainerID
uuid: e35dc48b-1aa1-41e3-91c1-ef1e9d2d8b90
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# idSyncContainerID{#idsynccontainerid}

このプロパティは ID 同期に使用するデータソースコンテナ ID を設定します。

内容：

<ul class="simplelist"> 
 <li> <a href="../../mcvid-library/mcvid-function-vars/mcvid-idsyncontainerid.md#section-b0c50732b1c84bed8616e82e8e83d58c" format="dita" scope="local"> 構文およびコードサンプル </a> </li> 
 <li> <a href="../../mcvid-library/mcvid-function-vars/mcvid-idsyncontainerid.md#section-6aed44fbe9d6401a8f912cb0d98339a7" format="dita" scope="local">コンテナの概要と用途</a> </li> 
 <li> <a href="../../mcvid-library/mcvid-function-vars/mcvid-idsyncontainerid.md#section-f283cb69c8de4348b5316cc4e02a3e9e" format="dita" scope="local"> DIL および VisitorAPI.js を使用する場合のコンテナ ID の設定 </a> </li> 
</ul>

## 構文およびコードサンプル {#section-b0c50732b1c84bed8616e82e8e83d58c}

**構文：** ` idSyncContainerID: *`コンテナ ID 値`*`

**コードサンプル：**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
   //Set container ID 
   idSyncContainerID:80 
});
```

## コンテナの概要と用途{#section-6aed44fbe9d6401a8f912cb0d98339a7}

**コンテナ**

コンテナは [!DNL Audience Manager] によって作成されるオブジェクトです。外部からはアクセスできませんが、コンテナには次のいずれかの条件に該当するすべてのデータソースがリストされます。

* ID 同期に使用可能だが未使用である。
* ID 同期に使用されている。

[!DNL Audience Manager] を使用していない場合でも、ドメイン内の他のページの他のデータソースと ID を交換している場合、アカウントにはこれらのコンテナがあります。これは、[!DNL Audience Manager] が ID 同期を可能にするテクノロジーとバックエンド機能を提供しているからです。

**使用例**

ID サービスコードにこの設定を追加する必要があるかどうかは、お客様の状況によって異なります。

<table id="table_48621F343C7F4760A75F6BCC2DB2DA20"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 条件 </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>不要</b> </p> </td> 
   <td colname="col2"> <p>以下の場合はこの設定を使用する必要がありません。 </p> <p> 
     <ul id="ul_4D6F794CD65C43D0BEFBA6F5DE420C2E"> 
      <li id="li_0F048A6AC7BE4450AFA1B20B1AC25808">ID サービスを <span class="keyword">Experience Cloud</span> ソリューションと組み合わせて使用しているが、他のデータソースとの ID 同期はおこなっていない。この場合、アカウントにはデフォルトのコンテナ（ID 0）があり、アクションは必要ありません。 </li> 
      <li id="li_5657D64D9406407D9B4DB7D8BE4F8EE4">すべてのデータソースが 1 つのコンテナに含まれている。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>必要</b> </p> </td> 
   <td colname="col2"> <p>以下のすべての条件に当てはまる場合は、この設定が必要になります。 </p> <p> 
     <ul id="ul_9AFD14FC5A2745F7BD7BE7B64545DA62"> 
      <li id="li_04F0EFBBD71B43608CAAA7E7409D33FE"><span class="keyword">Audience Manager</span> を使用していない。 </li> 
      <li id="li_4BFA6DC76CE9455EBBC337FD2FE820BF">コンテナによって編成されている他のデータソースと ID を同期する必要がある。 </li> 
      <li id="li_731DA5D1CBF244F8BEBE57C0E2EBA713">ドメイン内の他のページにある他のコンテナに含まれるデータソースと ID を同期する必要がある。 </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

## DIL および VisitorAPI.js を使用する場合のコンテナ ID の設定{#section-f283cb69c8de4348b5316cc4e02a3e9e}

同じページに [!DNL DIL]* および* VisitorAPI.js を導入している場合：

* ID 同期において、訪問者 ID サービスコードが DIL よりも優先されます。
* ID サービスコードでのみ、`idSyncContainerID` コンフィギュレーションを設定します。

