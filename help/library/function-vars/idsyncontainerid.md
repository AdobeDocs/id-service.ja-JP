---
description: このプロパティは ID 同期に使用するデータソースコンテナ ID を設定します。
keywords: 訪問者 ID サービス
title: idSyncContainerID
exl-id: 6c4cd41b-902b-4872-8c3f-475a834b76f4
TQID: https://experienceleague.adobe.com/bDW5Z4LKbLW2igmRsJ-QxajnBj8KyvoTypUjUekElj4
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 328
ht-degree: 60%

---

# idSyncContainerID{#idsynccontainerid}

このプロパティは ID 同期に使用するデータソースコンテナ ID を設定します。

内容：

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-b0c50732b1c84bed8616e82e8e83d58c" format="dita" scope="local"> 構文およびコードサンプル </a> </li> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-6aed44fbe9d6401a8f912cb0d98339a7" format="dita" scope="local">コンテナの概要と用途</a> </li> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-f283cb69c8de4348b5316cc4e02a3e9e" format="dita" scope="local"> DIL および VisitorAPI.js を使用する場合のコンテナ ID の設定 </a> </li> 
</ul>

## 構文およびコードサンプル {#section-b0c50732b1c84bed8616e82e8e83d58c}

**構文：** `idSyncContainerID: *`コンテナ ID 値`*`

**コードサンプル:**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   ... 
   //Set container ID 
   idSyncContainerID:80 
});
```

## コンテナの概要と用途 {#section-6aed44fbe9d6401a8f912cb0d98339a7}

**コンテナ**

コンテナは、Audience Managerによって作成されたオブジェクトです。 外部からはアクセスできませんが、これらのコンテナには、次のようなすべてのデータソースがリストされます。

* ユーザーからは使用できるが、ID 同期には使用されない。
* ID 同期に使用されている。

Audience Managerを利用していない場合でも、ドメイン全体のさまざまなページで異なるデータソースとIDを交換している場合、アカウントには次のコンテナが割り当てられます。 これは、Audience Managerが、IDの同期を可能にするテクノロジーとバックエンド機能を提供するからです。

**使用例**

状況に応じて、この設定を訪問者ID サービスコードに追加する必要がある場合とない場合があります。

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
      <li id="li_0F048A6AC7BE4450AFA1B20B1AC25808">任意のCX Enterprise ソリューションで訪問者ID サービスを使用し、他のデータソースとのID同期を実行しません。 この場合、アカウントには ID 0 のデフォルトのコンテナがあり、アクションは不要です。 </li> 
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

## DILおよび`VisitorAPI.js`を使用する場合のコンテナ IDの設定 {#section-f283cb69c8de4348b5316cc4e02a3e9e}

[!UICONTROL DIL] *と* `VisitorAPI.js`を同じページにデプロイした場合：

* 訪問者ID サービスコードは、ID同期ではDILよりも優先されます。
* 訪問者ID サービスコードでのみ`idSyncContainerID`設定を設定します。

