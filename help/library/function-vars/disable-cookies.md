---
description: Experience Cloud ID サービスがサードパーティの demdex.net Cookie を返さないようにするブール型フラグです（オプション）。
keywords: ID サービス
title: disableThirdPartyCookies
exl-id: 19d12822-0e17-4a1c-8e9c-25a22e20a4a8
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 100%

---

# disableThirdPartyCookies{#disablethirdpartycookies}

Experience Cloud ID サービスがサードパーティの demdex.net Cookie を返さないようにするブール型フラグです（オプション）。

>[!NOTE]
>
>この設定は従来 `idSyncDisable3rdPartySyncing` でしたが、2018 年 1 月 18 日（PT）の v3.0 リリースで `disableThirdPartyCookies` に名称変更されました。

**構文：** `disableThirdPartyCookies: true|false`（デフォルトは `false` です。）`VisitorAPI.js` v3.0.0 以降の場合。

`disableThirdPartyCookies: true` のとき、ID サービスはサードパーティである demdex.net の Cookie（[Cookie と Experience Cloud Identity Service ](../../introduction/cookies.md)を参照）を返しません。サイト訪問者が既にブラウザーにこの cookie を持っている場合、ID サービスはそれを使用して新しい Experience Cloud ID（MID）を作成したり、既存の ID を返したりすることはありません。 代わりに、ID サービスはファーストパーティ Cookie に新しいランダムな MID を作成します。 有効にすると、ID サービスを使用してデータを収集し、異なる Experience Cloud ソリューション間で共有できます。

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
