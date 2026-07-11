---
description: 訪問者ID サービスがサードパーティのdemdex.net Cookieを返さないようにする、オプションのブール値フラグ。
keywords: 訪問者 ID サービス
title: disableThirdPartyCookies
exl-id: 19d12822-0e17-4a1c-8e9c-25a22e20a4a8
TQID: https://experienceleague.adobe.com/vx9q-Q1X0fraWPUmaBlx-bBFX-gvnAox03mpENTizHw
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 144
ht-degree: 16%

---

# disableThirdPartyCookies{#disablethirdpartycookies}

訪問者ID サービスがサードパーティのdemdex.net Cookieを返さないようにする、オプションのブール値フラグ。

>[!NOTE]
>
>この設定は従来 `idSyncDisable3rdPartySyncing` でしたが、2018 年 1 月 18 日（PT）の v3.0 リリースで `disableThirdPartyCookies` に名称変更されました。

**構文：** `disableThirdPartyCookies: true|false`（デフォルトは `false` です。） `VisitorAPI.js` v3.0.0以降の場合。

`disableThirdPartyCookies: true`の場合、訪問者ID サービスはサードパーティのdemdex.net Cookieを返しません（[Cookieと訪問者ID サービス ](../../introduction/cookies.md)を参照）。 サイト訪問者が既にこのCookieをブラウザーに持っている場合、訪問者ID サービスはそれを使用して新しいECIDを作成したり、既存のIDを返したりしません。 代わりに、訪問者ID サービスは、ファーストパーティ Cookieに新しいランダム MIDを作成します。 有効にすると、訪問者ID サービスを使用してデータを収集し、様々なCX エンタープライズソリューション間で共有できるようになります。

**コードサンプル**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCookies: true 
});
```

