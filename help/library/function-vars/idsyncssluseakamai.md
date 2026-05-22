---
description: 宛先の公開テンプレートで HTTPS 接続に Akamai を使用するかを指定します。
keywords: ID サービス
title: idSyncSSLUseAkamai
exl-id: 74c24eb5-bf3d-4e6b-ac7d-1a37d940d77f
TQID: https://experienceleague.adobe.com/bFdWlHB0fNXOYQ6qIg6kx7pku6iZlqhx13Yu-i3nm5E
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 40
ht-degree: 100%

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

