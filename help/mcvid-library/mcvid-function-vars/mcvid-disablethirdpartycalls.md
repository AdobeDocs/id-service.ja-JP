---
description: ID サービスが他のドメインに対する呼び出しをおこなえないようにするブール型のフラグ（オプション）。
keywords: クロスドメイントラッキング;ID サービス
seo-description: ID サービスが他のドメインに対する呼び出しをおこなえないようにするブール型のフラグ（オプション）。
seo-title: disableThirdPartyCalls
title: disableThirdPartyCalls
uuid: e92ce1f5-67a4-476c-9d04-41d4e96b1592
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# disableThirdPartyCalls{#disablethirdpartycalls}

ID サービスが他のドメインに対する呼び出しをおこなえないようにするブール型のフラグ（オプション）。

**構文：** ` `disableThirdPartyCalls: true|false``（デフォルトは `false`。）

`disableThirdPartyCalls: true` の場合、この ID サービスは他のドメインの呼び出しをおこないません。

**目的**

この変数は、以下を必要とするお客様向けに設計されています。

* ID サービスが認証済みの安全なページから呼び出しをおこなうのを防ぐ。
* サイト訪問者に Experience Cloud ID（MID）を持たせる。
* その他の Experience Cloud ソリューションを適切に動作させる。

**実装方法**

他の Experience Cloud ソリューションが MID を使用しているので、ID サービスは、この ID を返して設定するために Adobe を呼び出します。ID サービスが Web サイトの認証済みセクションから呼び出しをおこなわないようにする必要がある場合、最初に認証を求められないページからの呼び出しを必須にすることができます。サイト訪問者が MID を取得したら、サイトの認証済みセクションの ID サービスコードで `disableThirdPartyCalls= true` を設定できます。ここでは、すべてではないにせよ、ほとんどの顧客が、サイトの安全な部分へのアクセス権を取得する前に認証ページに移動することを想定しています。

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

