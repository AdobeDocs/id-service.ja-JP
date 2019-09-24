---
description: Experience Cloud Identity Service がサードパーティの demdex.net Cookie を返さないようにするブール型フラグです（オプション）。
keywords: ID サービス
seo-description: Experience Cloud Identity Service がサードパーティの demdex.net Cookie を返さないようにするブール型フラグです（オプション）。
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7ed5aa16-44ca-4702-878a-1a208ca95270
translation-type: tm+mt
source-git-commit: 584b6240c3e0286111689499ca5df5d98aa9fab2

---


# disableThirdPartyCookies{#disablethirdpartycookies}

Experience Cloud Identity Service がサードパーティの demdex.net Cookie を返さないようにするブール型フラグです（オプション）。

>[!NOTE]
>
>この設定は従来 `idSyncDisable3rdPartySyncing` でしたが、2018 年 1 月 18 日の v3.0 リリースで `disableThirdPartyCookies` に名称変更されました。

**構文：**`disableThirdPartyCookies: true|false`（デフォルトは `false` です。）`VisitorAPI.js` v3.0.0 以降の場合。

`disableThirdPartyCookies: true` のとき、ID サービスはサードパーティである demdex.net の Cookie（[Cookie と Experience Cloud Identity Service ](../../introduction/cookies.md)を参照）を返しません。サイトの訪問者のブラウザーにこの Cookie が既に設定されている場合、ID サービスが新しい Experience Cloud ID（MID）の作成や既存の ID の返却のためにこの Cookie を使用することはありません。代わりに、ID サービスは、ファーストパーティ Cookie に新しいランダムな MID を作成します。有効にすると、ID サービスを使用してデータを収集し、異なる Experience Cloud ソリューション間で共有できます。

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

