---
description: タイムアウト間隔をミリ秒単位で設定します。 他のソリューション（Analytics、Audience Manager、Targetなど）の情報を伝えるために使用 訪問者ID サービスからの応答を待つ時間。
keywords: 訪問者 ID サービス
title: loadTimeout
exl-id: 485264f4-ee24-4042-8be3-259e70462110
TQID: https://experienceleague.adobe.com/w0-c0ROMsYRLqlHQuBfSAdardHnMfaJ8oTLf1xwL9QQ
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 147
ht-degree: 56%

---

# loadTimeout{#loadtimeout}

タイムアウト間隔をミリ秒単位で設定します。 他のソリューション（Analytics、Audience Manager、Targetなど）の情報を伝えるために使用 訪問者ID サービスからの応答を待つ時間。

**構文：** `loadTimeout: *`間隔（ミリ秒）`*`

デフォルト値は 30,000 ミリ秒（30 秒）です。 デフォルト値を変更&#x200B;*しない*&#x200B;ことを強くお勧めします。

>[!NOTE]
>
>Visitor ID サービスへの呼び出しは、ページ上の他のAdobe以外のコードに関連して非同期になります。 その結果、タイムアウト間隔を増減しても、ページがコンテンツをレンダリングする速度は変わりません。 ただし、タイムアウト間隔が長いと、一般的なネットワークモニタリングツールで測定されるページ読み込み時間に影響する可能性がありますが、レンダリング時間は影響を受けません。

**コードサンプル**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example sets the timeout to 10,000 milliseconds (10 seconds). 
   loadTimeout:10000 
});
```

