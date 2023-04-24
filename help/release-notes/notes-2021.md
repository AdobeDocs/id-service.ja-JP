---
description: Experience Cloud Identity Service の機能リリース、更新、変更点です。
keywords: ID サービス
title: 2021年リリースノート
source-git-commit: dce2c0036f697507381d0763c2f6a9538155681c
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 27%

---

# Experience CloudID サービスリリースノート — 2021 年

Experience Cloud ID サービスの機能リリース、更新、変更点です。

## 訪問者 5.3.0

Visitor 5.3.0 のリリースには、次の更新が含まれています。

* ローカル ECID を生成するようにアルゴリズムを更新しました。
* での最新のオプトイン `Secure` および `SameSite` プライバシー cookie のフラグ。
* ページが子 iFrame に読み込まれる際の Firefox ブラウザーの問題に対するパッチ修正。

## 訪問者 5.2.0

訪問者 5.2.0 のリリースには、次の更新が含まれています。

* このバージョンでは、イベントを導入します `onRecieveEcid`:ECID が ID サービスから受け取られると呼び出されます。 以下に例を示します。

```js
visitorInstance.onRecieveEcid(callback(ecid){
 console.log(ecid)
})
```
