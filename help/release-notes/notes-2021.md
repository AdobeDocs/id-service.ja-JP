---
description: 訪問者ID サービスの機能リリース、更新、変更。
keywords: 訪問者 ID サービス
title: 2021年リリースノート
exl-id: 56bffb6f-a4fc-40df-8bb2-17e43772fe60
TQID: https://experienceleague.adobe.com/AB8VuYn9X41P9REJ8C215GzBRtH66lb35i-q1PNbZfU
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 110
ht-degree: 59%

---

# Adobe Visitor ID サービスのリリースノート - 2021

訪問者ID サービスの機能リリース、更新、変更。

## Visitor 5.3.0

Visitor 5.3.0 のリリースには、次の更新が含まれています。

* ローカル ECID を生成するようにアルゴリズムを更新しました。
* プライバシー cookie の `Secure` および `SameSite` フラグを使用した最新のオプトイン。
* ページが子 iFrame に読み込まれる際の Firefox ブラウザーの問題に対するパッチ修正。

## Visitor 5.2.0

Visitor 5.2.0 のリリースには、次の更新が含まれています。

* このバージョンでは、訪問者ID サービスからECIDを受信したときに呼び出されるイベント `onReceiveEcid`が導入されます。 次に例を示します。

```js
visitorInstance.onReceiveEcid(callback(ecid){
 console.log(ecid)
})
```

