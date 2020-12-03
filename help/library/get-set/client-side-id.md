---
description: このIDサービス関数を呼び出して、IDサービスがクライアント側のExperience Cloud訪問者ID(MID)を生成したかどうかを判断します。 VisitorAPI.js バージョン 1.7.0 以降で利用できます。
keywords: ID Service
seo-description: このIDサービス関数を呼び出して、IDサービスがクライアント側のExperience Cloud訪問者ID(MID)を生成したかどうかを判断します。 VisitorAPI.js バージョン 1.7.0 以降で利用できます。
seo-title: isClientSideMarketingCloudVisitorID
title: isClientSideMarketingCloudVisitorID
uuid: 1c39ac60-1d2b-4ed4-a2ea-30d680e61e10
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 52%

---


# isClientSideMarketingCloudVisitorID{#isclientsidemarketingcloudvisitorid}

このIDサービス関数を呼び出して、IDサービスがクライアント側のExperience Cloud訪問者ID(MID)を生成したかどうかを判断します。 VisitorAPI.js バージョン 1.7.0 以降で利用できます。

**構文**

`var *`variableName`* = visitor.isClientSideMarketingCloudVisitorID()`

次の表のリストと、この関数が返す応答について説明します。

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

