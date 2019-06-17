---
description: Experience Cloud ID サービスがサードパーティの demdex.net Cookie を返さないようにするブール型フラグ（オプション）。
keywords: ID サービス
seo-description: Experience Cloud ID サービスがサードパーティの demdex.net Cookie を返さないようにするブール型フラグ（オプション）。
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7ed5aa16-44ca-4702-878a-1a208ca95270
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# disableThirdPartyCookies{#disablethirdpartycookies}

Experience Cloud ID サービスがサードパーティの demdex.net Cookie を返さないようにするブール型フラグ（オプション）。

>[!NOTE]
>
>この設定は、 `idSyncDisable3rdPartySyncing` v3.0の2018年1月18日リリースで変更 `disableThirdPartyCookies` され、名前が変更されました。

**構文:**`disableThirdPartyCookies: true|false` （デフォルトは `false`、です）。`VisitorAPI.js` v1.5.3以降の場合。

この場合 `disableThirdPartyCookies: true`、IDサービスはサードパーティのdemdex. net cookieを返しません（ [cookieとExperience Cloud IDサービスを参照してください](../../mcvid-introduction/mcvid-cookies.md) ）。サイトの訪問者のブラウザーにこの Cookie が既に設定されている場合、ID サービスが新しい Experience Cloud ID（MID）の作成や既存の ID の返却のためにこの Cookie を使用することはありません。代わりに、ID サービスは、ファーストパーティ Cookie に新しいランダムな MID を作成します。有効にすると、ID サービスを使用してデータを収集し、異なる Experience Cloud ソリューション間で共有できます。

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

