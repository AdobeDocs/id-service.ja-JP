---
description: 宛先の公開テンプレートで HTTPS 接続に Akamai を使用するかを指定します。
keywords: ID サービス
title: idSyncSSLUseAkamai
exl-id: 74c24eb5-bf3d-4e6b-ac7d-1a37d940d77f
source-git-commit: e185c7d2b7582b52adbe9b525be7868ab8bfa374
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# idSyncSSLUseAkamai{#idsyncssluseakamai}

宛先の公開テンプレートで HTTPS 接続に Akamai を使用するかを指定します。

`idSyncSSLUseAkamai` 設定は、パートナーごとに有効化します。

**構文：** `idSyncSSLUseAkamai: true`

**コードサンプル**

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
 
    //Set Akamai URL for ID sync container 
    idSyncSSLUseAkamai:true 
 
    ... 
});
```

