---
description: このプロパティは ID 同期に使用するデータソースコンテナ ID を設定します。
keywords: ID サービス
seo-description: このプロパティは ID 同期に使用するデータソースコンテナ ID を設定します。
seo-title: idSyncContainerID
title: idSyncContainerID
uuid: e35dc48b-1aa1-41e3-91c1-ef1e9d2d8b90
exl-id: 6c4cd41b-902b-4872-8c3f-475a834b76f4
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '336'
ht-degree: 100%

---

# idSyncContainerID {#idsynccontainerid}

このプロパティは ID 同期に使用するデータソースコンテナ ID を設定します。

内容：

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-b0c50732b1c84bed8616e82e8e83d58c" format="dita" scope="local"> 構文およびコードサンプル </a> </li> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-6aed44fbe9d6401a8f912cb0d98339a7" format="dita" scope="local">コンテナの概要と用途</a> </li> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-f283cb69c8de4348b5316cc4e02a3e9e" format="dita" scope="local"> DIL および VisitorAPI.js を使用する場合のコンテナ ID の設定 </a> </li> 
</ul>

## 構文およびコードサンプル {#section-b0c50732b1c84bed8616e82e8e83d58c}

**構文：** ` idSyncContainerID: *`コンテナ ID 値`*`

**コードサンプル:**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
   //Set container ID 
   idSyncContainerID:80 
});
```

## コンテナの概要と用途 {#section-6aed44fbe9d6401a8f912cb0d98339a7}

**コンテナ**

コンテナは [!DNL Audience Manager] によって作成されるオブジェクトです。外部からはアクセスできませんが、これらのコンテナには、次のようなすべてのデータソースがリストされます。

* ユーザーからは使用できるが、ID 同期には使用されない。
* ID 同期に使用されている。

[!DNL Audience Manager] を使用していない場合でも、ドメイン内の他のページの他のデータソースと ID を交換している場合、アカウントにはこれらのコンテナがあります。これは、[!DNL Audience Manager] が ID 同期を可能にするテクノロジーとバックエンド機能を提供しているからです。

**使用例**

ID サービスコードにこの設定を追加する必要があるかどうかは、状況次第です。

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
   <td colname="col2"> <p>次の場合は、この設定を使用する必要はありません。 </p> <p> 
     <ul id="ul_4D6F794CD65C43D0BEFBA6F5DE420C2E"> 
      <li id="li_0F048A6AC7BE4450AFA1B20B1AC25808">ID サービスを <span class="keyword">Experience Cloud</span> ソリューションと組み合わせて使用しているが、他のデータソースとの ID 同期はおこなっていない。この場合、アカウントには ID 0 のデフォルトのコンテナがあり、アクションは不要です。 </li> 
      <li id="li_5657D64D9406407D9B4DB7D8BE4F8EE4">すべてのデータソースが 1 つのコンテナに格納されている。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>必要</b> </p> </td> 
   <td colname="col2"> <p>次の条件のすべてに当てはまる場合は、この設定を使用する必要があります。 </p> <p> 
     <ul id="ul_9AFD14FC5A2745F7BD7BE7B64545DA62"> 
      <li id="li_04F0EFBBD71B43608CAAA7E7409D33FE"><span class="keyword">Audience Manager</span> を使用していない。 </li> 
      <li id="li_4BFA6DC76CE9455EBBC337FD2FE820BF">ID を、コンテナ別に整理された他のデータソースと同期する必要がある。 </li> 
      <li id="li_731DA5D1CBF244F8BEBE57C0E2EBA713">ドメイン全体の異なるページ上にある異なるコンテナ内のデータソースと ID を同期する必要がある。 </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

## DIL および VisitorAPI.js を使用する場合のコンテナ ID の設定 {#section-f283cb69c8de4348b5316cc4e02a3e9e}

[!UICONTROL DIL ]* と* VisitorAPI.js を同じページにデプロイした場合：

* ID 同期において、訪問者 ID サービスコードが DIL よりも優先されます。
* ID サービスコードでのみ、`idSyncContainerID` コンフィギュレーションを設定します。
