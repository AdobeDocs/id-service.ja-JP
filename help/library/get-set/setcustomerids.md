---
description: setCustomerIDs は、顧客 ID とその認証状態を定義する 1 つ以上のキーと値のペアを設定します。
keywords: ID サービス
title: setCustomerIDs
exl-id: 8fc549d3-2a6f-4214-bb0d-3e0bc1501ce2
source-git-commit: e185c7d2b7582b52adbe9b525be7868ab8bfa374
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

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

