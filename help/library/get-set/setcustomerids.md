---
description: setCustomerIDs は、顧客 ID とその認証状態を定義する 1 つ以上のキーと値のペアを設定します。
keywords: ID サービス
title: setCustomerIDs
exl-id: 8fc549d3-2a6f-4214-bb0d-3e0bc1501ce2
TQID: https://experienceleague.adobe.com/PY-2KQSxqIV1xygQwSduPuq-YeYt5tY-UMGh4sRSZNM
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 62
ht-degree: 100%

---

# setCustomerIDs{#setcustomerids}

setCustomerIDs は、顧客 ID とその認証状態を定義する 1 つ以上のキーと値のペアを設定します。

**構文：** `visitor.setCustomerIDs()`

以下のコードサンプルのように、1 つの ID または複数の ID を設定できます。 その他の詳細および例については、[顧客 ID と認証状態](../../reference/authenticated-state.md)を参照してください。

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

