---
description: この ID サービス関数を呼び出して、ID サービスがクライアントサイドの Experience Cloud 訪問者 ID（MID）を生成したかどうかを判断します。 VisitorAPI.js バージョン 1.7.0 以降で利用できます。
keywords: ID サービス
title: isClientSideMarketingCloudVisitorID
exl-id: ed2672e7-da1a-4c02-9f4e-c14419ec9ec7
TQID: https://experienceleague.adobe.com/kQK7Lw-j33luPqTSzQKGuf8fMPuOEDoQBzesZa-bvVo
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 127
ht-degree: 100%

---

# isClientSideMarketingCloudVisitorID{#isclientsidemarketingcloudvisitorid}

この ID サービス関数を呼び出して、ID サービスがクライアントサイドの Experience Cloud 訪問者 ID（MID）を生成したかどうかを判断します。 VisitorAPI.js バージョン 1.7.0 以降で利用できます。

**構文**

`var *`variableName`* = visitor.isClientSideMarketingCloudVisitorID()`

この関数で返される応答の一覧と説明を次の表に示します。

<table id="table_5D08A5DD6FD04F94818B0E8B790D3136"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 応答 </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> true</span> </p> </td> 
   <td colname="col2"> <p>ID サービスは、<span class="keyword">Experience Cloud</span> サーバーから MID を受け取れなかったか、受け取っていません。 ブラウザー（クライアント側）で、ローカルに MID を作成しました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> false</span> </p> </td> 
   <td colname="col2"> <p>ID サービスは、<span class="keyword">Experience Cloud</span> サーバーから MID を受け取りました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> null</span> </p> </td> 
   <td colname="col2"> <p>ID サービスは、<span class="keyword">Experience Cloud</span> サーバーへの呼び出しをおこなっていません。 </p> </td> 
  </tr> 
 </tbody> 
</table>

