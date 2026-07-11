---
description: この訪問者ID サービス関数を呼び出して、訪問者ID サービスがクライアントサイドのECID （MID）を生成したかどうかを判断します。 VisitorAPI.js バージョン 1.7.0 以降で利用できます。
keywords: 訪問者 ID サービス
title: isClientSideMarketingCloudVisitorID
exl-id: ed2672e7-da1a-4c02-9f4e-c14419ec9ec7
TQID: https://experienceleague.adobe.com/kQK7Lw-j33luPqTSzQKGuf8fMPuOEDoQBzesZa-bvVo
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 128
ht-degree: 32%

---

# isClientSideMarketingCloudVisitorID{#isclientsidemarketingcloudvisitorid}

この訪問者ID サービス関数を呼び出して、訪問者ID サービスがクライアントサイドのECID （MID）を生成したかどうかを判断します。 `VisitorAPI.js` バージョン 1.7.0以降で使用できます。

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
   <td colname="col2"> <p>訪問者ID サービスは、CX エンタープライズ サーバーからMIDを受信できなかったか、受信しませんでした。 ブラウザー（クライアント側）で、ローカルに MID を作成しました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> false</span> </p> </td> 
   <td colname="col2"> <p>訪問者ID サービスは、CX エンタープライズ サーバーからMIDを受信しました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> null</span> </p> </td> 
   <td colname="col2"> <p>訪問者ID サービスがCX エンタープライズ サーバーを呼び出しませんでした。 </p> </td> 
  </tr> 
 </tbody> 
</table>

