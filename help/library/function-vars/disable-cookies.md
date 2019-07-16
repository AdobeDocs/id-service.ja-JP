---
description: Experience Platform IDサービスがサードパーティのdemdex. net cookieを返さないようにするブール型のフラグ（オプション）。
keywords: ID サービス
seo-description: Experience Platform IDサービスがサードパーティのdemdex. net cookieを返さないようにするブール型のフラグ（オプション）。
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7ed5aa16-44ca-4702-878a-1a208ca95270
translation-type: tm+mt
source-git-commit: 484c52265d8e0b6f0e79cb21d09082fff730a44b

---


# disableThirdPartyCookies{#disablethirdpartycookies}

Experience Platform IDサービスがサードパーティのdemdex. net cookieを返さないようにするブール型のフラグ（オプション）。

>[!NOTE]
>
>この設定は従来 `idSyncDisable3rdPartySyncing` でしたが、2018 年 1 月 18 日の v3.0 リリースで `disableThirdPartyCookies` に名称変更されました。

**構文：**`disableThirdPartyCookies: true|false`（デフォルトは `false` です。）`VisitorAPI.js` v1.5.3 以降の場合。

When `disableThirdPartyCookies: true`, the ID service does not return the third-party, demdex.net cookie (see [Cookies and the Experience Platform Identity Service](../../introduction/cookies.md) ). サイトの訪問者のブラウザーにこの Cookie が既に設定されている場合、ID サービスが新しい Experience Cloud ID（MID）の作成や既存の ID の返却のためにこの Cookie を使用することはありません。代わりに、ID サービスは、ファーストパーティ Cookie に新しいランダムな MID を作成します。有効にすると、ID サービスを使用してデータを収集し、異なる Experience Cloud ソリューション間で共有できます。

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

