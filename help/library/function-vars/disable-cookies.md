---
description: Experience Cloud Identity Service がサードパーティの demdex.net Cookie を返さないようにするブール型フラグです（オプション）。
keywords: ID サービス
seo-description: Experience Cloud Identity Service がサードパーティの demdex.net Cookie を返さないようにするブール型フラグです（オプション）。
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7ed5aa16-44ca-4702-878a-1a208ca95270
translation-type: tm+mt
source-git-commit: 584b6240c3e0286111689499ca5df5d98aa9fab2
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 61%

---


# disableThirdPartyCookies{#disablethirdpartycookies}

Experience Cloud Identity Service がサードパーティの demdex.net Cookie を返さないようにするブール型フラグです（オプション）。

>[!NOTE]
>
>この設定は従来 `idSyncDisable3rdPartySyncing` でしたが、2018 年 1 月 18 日の v3.0 リリースで `disableThirdPartyCookies` に名称変更されました。

**構文：**`disableThirdPartyCookies: true|false`（デフォルトは `false` です。）`VisitorAPI.js` v3.0.0 以降の場合。

`disableThirdPartyCookies: true` のとき、ID サービスはサードパーティである demdex.net の Cookie（[Cookie と Experience Cloud Identity Service ](../../introduction/cookies.md)を参照）を返しません。サイト訪問者のブラウザーにこのcookieが既に設定されている場合、IDサービスは、そのcookieを使用して新しいExperience CloudID(MID)を作成したり、既存のIDを返したりしません。 代わりに、IDサービスは、ファーストパーティcookieに新しいランダムなMIDを作成します。 有効にすると、IDサービスを使用してデータを収集し、異なるExperience Cloudソリューション間で共有できます。

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

