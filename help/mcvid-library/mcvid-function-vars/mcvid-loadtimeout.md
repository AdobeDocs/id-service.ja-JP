---
description: タイムアウトの間隔をミリ秒単位で設定します。他のソリューション（Analytics、Audience Manager、Target など）にID サービスからの応答までの待ち時間を通知するために使用されます。
keywords: ID サービス
seo-description: タイムアウトの間隔をミリ秒単位で設定します。他のソリューション（Analytics、Audience Manager、Target など）にID サービスからの応答までの待ち時間を通知するために使用されます。
seo-title: loadTimeout
title: loadTimeout
uuid: f627e044- bd73-49a4-8a90-6d19aa566751
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# loadTimeout{#loadtimeout}

タイムアウトの間隔をミリ秒単位で設定します。他のソリューション（Analytics、Audience Manager、Target など）にID サービスからの応答までの待ち時間を通知するために使用されます。

**構文:**` loadTimeout: *`ミリ秒単位の間隔`*`

デフォルト値は、30,000 ミリ秒（30 秒）です。デフォルト値を変更*しない*ことを強くお勧めします。

>[!NOTE]
>
>IDサービスへの呼び出しは、ページ上の他のAdobe以外のコードと関連して非同期的に行われます。そのため、タイムアウト間隔を調整しても、ページにコンテンツがレンダリングされる速さは変わりません。ただし、長いタイムアウト間隔を設定すると、一般的なネットワーク監視ツールによって測定されるページ読み込み時間が影響を受ける可能性はあります。それでも、レンダリングの時間は影響を受けません。

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

