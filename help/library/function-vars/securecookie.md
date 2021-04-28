---
description: AMCV Cookie に「Secure」属性を追加するブール型フラグ（オプション）。
keywords: ID サービス
seo-description: AMCV Cookie に「Secure」属性を追加するブール型フラグ（オプション）。
seo-title: secureCookie
title: secureCookie
uuid: 995d19f6-9c9d-4493-9c9c-545b0b5696b0
exl-id: ba281b1c-1112-4ed6-b4fd-b8f87cabc575
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '105'
ht-degree: 100%

---

# secureCookie {#securecookie}

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
