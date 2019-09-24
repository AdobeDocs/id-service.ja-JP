---
description: setCustomerIDs は、顧客 ID とその認証状態を定義する 1 つ以上のキーと値のペアを設定します。
keywords: ID サービス
seo-description: setCustomerIDs は、顧客 ID とその認証状態を定義する 1 つ以上のキーと値のペアを設定します。
seo-title: setCustomerIDs
title: setCustomerIDs
uuid: 4f960f98-cec2-4db6-84ea-0259e2128ea2
translation-type: tm+mt
source-git-commit: 21fb12b817b7c8cd34e6022ca6c188229228d1df

---


# setCustomerIDs{#setcustomerids}

setCustomerIDs は、顧客 ID とその認証状態を定義する 1 つ以上のキーと値のペアを設定します。

**構文：** `visitor.setCustomerIDs()`

以下のコードサンプルのように、1 つの ID または複数の ID を設定できます。その他の詳細および例については、[顧客 ID と認証状態](../../reference/authenticated-state.md)を参照してください。

```js
// Single ID with a single authentication state 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    } 
}); 
 
//Multiple IDs with a single authentication state 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":"550e8400-e29b-41d4-a716-446655440000" 
});
```

