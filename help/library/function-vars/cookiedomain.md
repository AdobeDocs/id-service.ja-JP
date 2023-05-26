---
description: URL の末尾 2 つのパートのいずれかが 3 文字以上から成るマルチパートのトップレベルドメインの場合に必須です。
keywords: ID サービス
title: cookieDomain
exl-id: 280416ad-372a-4a59-a938-0f49c0ce300f
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '56'
ht-degree: 100%

---

# cookieDomain{#cookiedomain}

URL の末尾 2 つのパートのいずれかが 3 文字以上から成るマルチパートのトップレベルドメインの場合に必須です。

**構文：** ` cookieDomain: " *`URL`*"`（`www` プレフィクスは不要。）

**使用例**

* 必須：`www.example.com.uk`
* 不要：`www.example.co.uk`

**コードサンプル**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   cookieDomain:"example.com.uk" 
});
```
