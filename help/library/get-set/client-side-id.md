---
description: この ID サービス関数を呼び出して、ID サービスがクライアント側で Experience Cloud 訪問者 ID（MID）を生成したかどうかを判定します。VisitorAPI.js バージョン 1.7.0 以降で利用できます。
keywords: ID サービス
seo-description: この ID サービス関数を呼び出して、ID サービスがクライアント側で Experience Cloud 訪問者 ID（MID）を生成したかどうかを判定します。VisitorAPI.js バージョン 1.7.0 以降で利用できます。
seo-title: isClientSideMarketingCloudVisitorID
title: isClientSideMarketingCloudVisitorID
uuid: 1c39ac60-1d2b-4ed4- a2ea-30d680e61e10
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# isClientSideMarketingCloudVisitorID{#isclientsidemarketingcloudvisitorid}

この ID サービス関数を呼び出して、ID サービスがクライアント側で Experience Cloud 訪問者 ID（MID）を生成したかどうかを判定します。VisitorAPI.js バージョン 1.7.0 以降で利用できます。

**構文**

`var *`variableName`* = visitor.isClientSideMarketingCloudVisitorID()`

以下の表に、この関数で返される応答とその説明を示します。

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
   <td colname="col2"> <p>ID サービスは、<span class="keyword">Experience Cloud</span> サーバーから MID を受け取れなかったか、受け取っていません。ブラウザー（クライアント側）で、ローカルに MID を作成しました。 </p> </td> 
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

