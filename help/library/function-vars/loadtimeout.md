---
description: タイムアウト間隔をミリ秒単位で設定します。 他のソリューション(分析、Audience Manager、ターゲットなど)を伝えるために使用 IDサービスからの応答を待機する時間。
keywords: ID Service
seo-description: タイムアウト間隔をミリ秒単位で設定します。 他のソリューション(分析、Audience Manager、ターゲットなど)を伝えるために使用 IDサービスからの応答を待機する時間。
seo-title: loadTimeout
title: loadTimeout
uuid: f627e044-bd73-49a4-8a90-6d19aa566751
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 14%

---


# loadTimeout{#loadtimeout}

タイムアウト間隔をミリ秒単位で設定します。 他のソリューション(分析、Audience Manager、ターゲットなど)を伝えるために使用 IDサービスからの応答を待機する時間。

**構文：** ` loadTimeout: *`間隔（ミリ秒）`*`

デフォルト値は30,000ミリ秒（30秒）です。 デフォルト値は変更しないこ *とを強くお勧めします* 。

>[!NOTE]
>
>ID サービスの呼び出しは、ページ上にある他の、アドビ以外のコードに関連して、非同期です。その結果、タイムアウト間隔を増減しても、ページでコンテンツがレンダリングされる速度は変わりません。 ただし、長いタイムアウト間隔は、一般的なネットワーク監視ツールによって測定されるページ読み込み時間に影響を与える可能性がありますが、レンダリング時間は影響を受けません。

**コードサンプル**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example sets the timeout to 10,000 milliseconds (10 seconds). 
   loadTimeout:10000 
});
```

