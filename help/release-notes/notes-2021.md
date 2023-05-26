---
description: Experience Cloud Identity Service の機能リリース、更新、変更点です。
keywords: ID サービス
title: 2021年リリースノート
exl-id: f0bbb100-49a9-4bba-8cee-5f40bec87984
source-git-commit: fcd3e8b65bb84e94eabac7ffec6a34f4cf75ec3d
workflow-type: tm+mt
source-wordcount: '103'
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

* このバージョンでは、ID サービスから ECID を受信した際に呼び出されるイベント `onRecieveEcid` が導入されています。以下に例を示します。

```js
visitorInstance.onRecieveEcid(callback(ecid){
 console.log(ecid)
})
```
