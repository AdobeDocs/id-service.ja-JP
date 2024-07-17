---
description: Experience Cloud ID サービスの機能リリース、更新、変更点です。
keywords: ID サービス
title: 2021年リリースノート
exl-id: 56bffb6f-a4fc-40df-8bb2-17e43772fe60
source-git-commit: 52956b38c59f60507aaf236b152ce41fc1229d14
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 100%

---

# Experience Cloud ID サービスリリースノート - 2021

Experience Cloud ID サービスの機能リリース、更新、変更点です。

## Visitor 5.3.0

Visitor 5.3.0 のリリースには、次の更新が含まれています。

* ローカル ECID を生成するようにアルゴリズムを更新しました。
* プライバシー cookie の `Secure` および `SameSite` フラグを使用した最新のオプトイン。
* ページが子 iFrame に読み込まれる際の Firefox ブラウザーの問題に対するパッチ修正。

## Visitor 5.2.0

Visitor 5.2.0 のリリースには、次の更新が含まれています。

* このバージョンでは、ID サービスから ECID を受信した際に呼び出されるイベント `onReceiveEcid` が導入されています。以下に例を示します。

```js
visitorInstance.onReceiveEcid(callback(ecid){
 console.log(ecid)
})
```
