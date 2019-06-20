---
description: Experience Cloud IDサービスがサードパーティのdemdex. net cookieを返さないようにするブール型のフラグ（オプション）。
keywords: ID サービス
seo-description: Experience Cloud IDサービスがサードパーティのdemdex. net cookieを返さないようにするブール型のフラグ（オプション）。
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7ed5aa16-44ca-4702-878a-1a208ca95270
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# disableThirdPartyCookies{#disablethirdpartycookies}

Experience Cloud IDサービスがサードパーティのdemdex. net cookieを返さないようにするブール型のフラグ（オプション）。

>[!NOTE]
>
>This configuration was `idSyncDisable3rdPartySyncing` and renamed to `disableThirdPartyCookies` in the January 18, 2018 release of v3.0.

**構文:**`disableThirdPartyCookies: true|false` （デフォルトは `false`、です）。`VisitorAPI.js` v1.5.3以降の場合。

When `disableThirdPartyCookies: true`, the ID service does not return the third-party, demdex.net cookie (see [Cookies and the Experience Cloud ID Service](../../introduction/cookies.md) ). サイトの訪問者のブラウザーにこの Cookie が既に設定されている場合、ID サービスが新しい Experience Cloud ID（MID）の作成や既存の ID の返却のためにこの Cookie を使用することはありません。代わりに、ID サービスは、ファーストパーティ Cookie に新しいランダムな MID を作成します。有効にすると、ID サービスを使用してデータを収集し、異なる Experience Cloud ソリューション間で共有できます。

**コードサンプル**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCookies: true 
});
```

