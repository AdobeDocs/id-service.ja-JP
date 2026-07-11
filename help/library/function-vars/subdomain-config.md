---
description: 訪問者ID サービスの呼び出しで使用されるデフォルトのドメイン名を、次の設定を使用して独自のサブドメイン名に変更します。
keywords: 訪問者 ID サービス
title: audienceManagerServer および audienceManagerServerSecure
exl-id: b740eb5c-ac4e-46f4-ba7c-1080d8d9292d
TQID: https://experienceleague.adobe.com/a5KVErDX4putY8d9vGf-uAwswNzE0Maf-JEyfmQxhbg
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 234
ht-degree: 44%

---

# audienceManagerServer および audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

訪問者ID サービスの呼び出しで使用されるデフォルトのドメイン名を、次の設定を使用して独自のサブドメイン名に変更します。

**構文：**

* `audienceManagerServer: " *`サブドメイン名`*.demdex.net"`
* `audienceManagerServerSecure: " *`サブドメイン名`*.demdex.net"`

**目的**

通常、訪問者ID サービスは`dpm.demdex.net`にAdobeへの呼び出しを行います。 この宛先への呼び出しは、あまりに一般的で、サードパーティのように見えるため、好まれない場合があります。 訪問者ID サービス呼び出しを1st パーティ呼び出しのように見せるには、以下に示すように、これらの設定を使用してAudience Manager サブドメイン名を`demdex.net`に追加します。 `dpm.demdex.net` 呼び出しについて詳しくは、[Demdex ドメインの呼び出しについて](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=ja)を参照してください。

**要件**

これらの設定では、以下を使用する必要があります。

* 会社のAudience Manager サブドメイン名。 この名前はコンサルタントに確認するか、コンサルタントから取得してください。
* IMS組織IDに関連付けられたサブドメイン名。
* 同じサブドメイン名を持つ&#x200B;*両方の*&#x200B;設定パラメーター。

**コードサンプル**

この例では、`dpm.demdex.net` への呼び出しに法務上の懸念を抱くメディアエンターテインメント企業があるとします。 Audience Managerでは、レコードのサブドメイン名はMusic1です。 次のコードサンプルは、この顧客固有のサブドメイン名を使用してVisitor ID Service データ呼び出しをブランディングする方法を示しています。

```
//Instantiate Visitor 
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE",{ 
     ... 
     //Configure Visitor ID Service call 
     audienceManagerServer: "Music1.demdex.net", 
     audienceManagerServerSecure: "Music1.demdex.net" 
     } 
);
```

