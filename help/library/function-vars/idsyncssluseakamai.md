---
description: 宛先の公開テンプレートで HTTPS 接続に Akamai を使用するかを指定します。
keywords: ID サービス
seo-description: 宛先の公開テンプレートで HTTPS 接続に Akamai を使用するかを指定します。
seo-title: idSyncSSLUseAkamai
title: idSyncSSLUseAkamai
uuid: 501ccc37- c3ab-4454- bfcf-3e3c3e8b5ca3
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

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

