---
description: これらの ID サービス関数を呼び出して、Experience Cloud Identity Service、Analytics または Audience Manager ID リクエストのタイムアウトステータスを判定します。 VisitorAPI.js バージョン 1.7.0 以降で利用できます。
keywords: ID サービス
title: callTimeOut メソッド
exl-id: ff3a2c5e-a0a8-4257-b538-0e4ce454b4e8
TQID: https://experienceleague.adobe.com/DIis78iaPQ7qpawlKwWCwReXbh5Mt0K8J3w-5KYdhmg
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 127
ht-degree: 100%

---

# callTimeOut メソッド{#calltimeout-methods}

これらの ID サービス関数を呼び出して、Experience Cloud Identity Service、Analytics または Audience Manager ID リクエストのタイムアウトステータスを判定します。 VisitorAPI.js バージョン 1.7.0 以降で利用できます。

## タイムアウトの関数 {#section-e08228ef5f9b45c9a84139bbb763164a}

<table id="table_B3ACE584B3224D838070D32A8462EF28"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> ソリューションまたはサービス </th> 
   <th colname="col2" class="entry"> 関数の構文 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Experience Cloud ID サービス </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variableName</span> = visitor.MCIDCallTimedOut()</span> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="keyword"> Analytics</span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variableName</span> = visitor.AnalyticsIDCallTimedOut()</span> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="keyword"> Audience Manager</span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variableName</span> = visitor.AAMIDCallTimedOut()</span> </p> </td> 
  </tr> 
 </tbody> 
</table>

## 関数の応答 {#section-ff73aaca58b74e10a0953c49a3387160}

<table id="table_5D08A5DD6FD04F94818B0E8B790D3136"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 応答 </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> TRUE</span> </p> </td> 
   <td colname="col2"> <p>ID サービスはリクエストを送信し、リクエストがタイムアウトになった。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> FALSE</span> </p> </td> 
   <td colname="col2"> <p>ID サービスはリクエストを送信し、サーバーから成功した応答を受け取った。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> NULL</span> </p> </td> 
   <td colname="col2"> <p>ID サービスはリクエストを送信しなかった。 </p> </td> 
  </tr> 
 </tbody> 
</table>

