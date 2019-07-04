---
description: 宛先の公開テンプレートで HTTPS 接続に Akamai を使用するかを指定します。
keywords: ID サービス
seo-description: 宛先の公開テンプレートで HTTPS 接続に Akamai を使用するかを指定します。
seo-title: idSyncSSLUseAkamai
title: idSyncSSLUseAkamai
uuid: 501ccc37-c3ab-4454-bfcf-3e3c3e8b5ca3
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# idSyncSSLUseAkamai{#idsyncssluseakamai}

宛先の公開テンプレートで HTTPS 接続に Akamai を使用するかを指定します。

`idSyncSSLUseAkamai` 設定は、パートナーごとに有効化します。

**構文: ** `idSyncSSLUseAkamai: true`

**コードサンプル**

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
 
    //Set Akamai URL for ID sync container 
    idSyncSSLUseAkamai:true 
 
    ... 
});
```

