---
description: AMCV Cookie に「Secure」属性を追加するブール型フラグ（オプション）。
keywords: ID サービス
seo-description: AMCV Cookie に「Secure」属性を追加するブール型フラグ（オプション）。
seo-title: secureCookie
title: secureCookie
uuid: 995d19f6-9c9d-4493-9c9c-545b0b5696b0
translation-type: ht
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

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

