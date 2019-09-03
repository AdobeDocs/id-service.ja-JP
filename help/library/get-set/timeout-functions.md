---
description: これらの ID サービス関数を呼び出して、Experience Cloud Identity Service、Analytics または Audience Manager ID リクエストのタイムアウトステータスを判定します。VisitorAPI.js バージョン 1.7.0 以降で利用できます。
keywords: ID サービス
seo-description: これらの ID サービス関数を呼び出して、Experience Cloud Identity Service、Analytics または Audience Manager ID リクエストのタイムアウトステータスを判定します。VisitorAPI.js バージョン 1.7.0 以降で利用できます。
seo-title: callTimeOut メソッド
title: callTimeOut メソッド
uuid: e5047498-11db-4945-b356-c92b7d447573
translation-type: ht
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# callTimeOut メソッド{#calltimeout-methods}

これらの ID サービス関数を呼び出して、Experience Cloud Identity Service、Analytics または Audience Manager ID リクエストのタイムアウトステータスを判定します。VisitorAPI.js バージョン 1.7.0 以降で利用できます。

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
   <td colname="col1"> <p>Experience Cloud Identity Service </p> </td> 
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

