---
description: 訪問者ID サービスが他のドメインに対して呼び出しを行うことを防ぐ、オプションのブール値フラグ。
keywords: クロスドメイントラッキング；訪問者ID サービス
title: disableThirdPartyCalls
exl-id: 1d5b4e80-1b2d-4401-9057-449a6abf5db5
TQID: https://experienceleague.adobe.com/mv00QfToxSqeITADmY1LbihbtJNHf1zzQef9uKDu-dc
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 205
ht-degree: 24%

---

# disableThirdPartyCalls{#disablethirdpartycalls}

訪問者ID サービスが他のドメインに対して呼び出しを行うことを防ぐ、オプションのブール値フラグ。

**構文：** ` `disableThirdPartyCalls: true|false&grave;&grave;（デフォルトは `false`。）

`disableThirdPartyCalls: true`の場合、訪問者ID サービスは他のドメインへの呼び出しを行いません。

**目的**

この変数は、以下を必要とする顧客向けに設計されています。

* 訪問者ID サービスが安全な認証されたページから呼び出しを行わないようにします。
* サイト訪問者がECIDを持つ。
* その他のCX エンタープライズソリューションが適切に機能するように支援します。

**導入戦略**

他のCX Enterprise ソリューションはMIDに依存しているため、訪問者ID サービスはAdobeを呼び出して、このIDを返して設定します。 訪問者ID サービスによるweb サイトの認証済みセクションからの呼び出しを停止する必要がある場合は、最初に認証を必要としないページからの必要な呼び出しを実行します。 サイト訪問者にMIDが設定されたら、サイトの認証済みセクションで訪問者ID サービスコードに`disableThirdPartyCalls= true`を設定できます。 ここでは、すべてではないにせよ、ほとんどの顧客がサイトの安全な部分にアクセスするために認証ページに移動することを前提としています。

**コードサンプル**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCalls: true 
}); 
```

