---
description: ID サービスが他のドメインに対する呼び出しをおこなえないようにするブール型のフラグ（オプション）。
keywords: クロスドメイントラッキング;ID サービス
title: disableThirdPartyCalls
exl-id: 1d5b4e80-1b2d-4401-9057-449a6abf5db5
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 100%

---

# disableThirdPartyCalls{#disablethirdpartycalls}

ID サービスが他のドメインに対する呼び出しをおこなえないようにするブール型のフラグ（オプション）。

**構文：** ` `disableThirdPartyCalls: true|false``（デフォルトは `false`。）

`disableThirdPartyCalls: true` の場合、この ID サービスは他のドメインの呼び出しをおこないません。

**目的**

この変数は、以下を必要とする顧客向けに設計されています。

* 顧客の安全な認証済みページから ID サービスが呼び出しを行うのを防ぐ。
* Experience Cloud ID（MID）を持つサイト訪問者。
* 適切に動作する他の Experience Cloud ソリューション。

**実装方法**

他の Experience Cloud ソリューションが MID に基づいているので、ID サービスは Adobe を呼び出してこの ID を返したり設定したりします。ID サービスが Web サイトの認証済みセクションから呼び出しをおこなわないようにする必要がある場合、最初に認証を求められないページからの呼び出しを必須にすることができます。サイト訪問者が MID を取得したら、サイトの認証済みセクションの ID サービスコードで `disableThirdPartyCalls= true` を設定できます。ここでは、すべてではないにせよ、ほとんどの顧客がサイトの安全な部分にアクセスするために認証ページに移動することを前提としています。

**コードサンプル**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCalls: true 
}); 
```
