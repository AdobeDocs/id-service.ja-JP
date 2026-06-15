---
description: Experience Cloud ID サービスがサードパーティの demdex.net Cookie を返さないようにするブール型フラグです（オプション）。
keywords: ID サービス
title: disableThirdPartyCookies
exl-id: 19d12822-0e17-4a1c-8e9c-25a22e20a4a8
TQID: https://experienceleague.adobe.com/vx9q-Q1X0fraWPUmaBlx-bBFX-gvnAox03mpENTizHw
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 145
ht-degree: 97%

---

# disableThirdPartyCookies{#disablethirdpartycookies}

Experience Cloud ID サービスがサードパーティの demdex.net Cookie を返さないようにするブール型フラグです（オプション）。

>[!NOTE]
>
>この設定は従来 `idSyncDisable3rdPartySyncing` でしたが、2018 年 1 月 18 日（PT）の v3.0 リリースで `disableThirdPartyCookies` に名称変更されました。

**構文：** `disableThirdPartyCookies: true|false`（デフォルトは `false` です。） `VisitorAPI.js` v3.0.0以降の場合。

`disableThirdPartyCookies: true` のとき、ID サービスはサードパーティである demdex.net の Cookie（[Cookie と Experience Cloud Identity Service ](../../introduction/cookies.md)を参照）を返しません。 サイト訪問者が既にブラウザーにこの cookie を持っている場合、ID サービスはそれを使用して新しい Experience Cloud ID（MID）を作成したり、既存の ID を返したりすることはありません。 代わりに、ID サービスはファーストパーティ Cookie に新しいランダムな MID を作成します。 有効にすると、ID サービスを使用してデータを収集し、異なる Experience Cloud ソリューション間で共有できます。

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

