---
description: AMCV Cookie に「Secure」属性を追加するブール型フラグ（オプション）。
keywords: ID サービス
title: secureCookie
exl-id: ba281b1c-1112-4ed6-b4fd-b8f87cabc575
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 100%

---

# secureCookie{#securecookie}

AMCV Cookie に「Secure」属性を追加するブール型フラグ（オプション）。

この設定属性は、`visitorAPI` バージョン 3.3.0 で使用できます。

>[!NOTE]
>
>`SecureCookie` 設定は、セキュリティで保護されていないドメインで機能しません。その結果、セキュリティで保護されていないプロトコルを使用する訪問について MID 値が返されない可能性があります。`secureCookie` を `true` に設定する必要があるのは、すべてのページおよびサブドメインでセキュリティで保護されたプロトコルが常に使用されていることを確認できた場合のみです。

**構文：** `secureCookie: true | false`（デフォルト）

**コードサンプル**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE",{ 
 
        //Set secure cookie property 
        secureCookie: true 
 });
```
