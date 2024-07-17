---
description: タイムアウト間隔をミリ秒単位で設定します。 他のソリューション（Analytics、Audience Manager、Target など）に ID サービスからの応答を待つ時間を伝えるために使用します。
keywords: ID サービス
title: loadTimeout
exl-id: 485264f4-ee24-4042-8be3-259e70462110
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 100%

---

# loadTimeout{#loadtimeout}

タイムアウト間隔をミリ秒単位で設定します。 他のソリューション（Analytics、Audience Manager、Target など）に ID サービスからの応答を待つ時間を伝えるために使用します。

**構文：** ` loadTimeout: *`間隔（ミリ秒）`*`

デフォルト値は 30,000 ミリ秒（30 秒）です。 デフォルト値を変更&#x200B;*しない*&#x200B;ことを強くお勧めします。

>[!NOTE]
>
>ID サービスの呼び出しは、ページ上にある他の、アドビ以外のコードに関連して、非同期です。その結果、タイムアウト間隔を増減しても、ページがコンテンツをレンダリングする速度は変わりません。 ただし、タイムアウト間隔が長いと、一般的なネットワーク監視ツールで測定されるページ読み込み時間に影響する可能性がありますが、レンダリング時間は影響を受けません。

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
