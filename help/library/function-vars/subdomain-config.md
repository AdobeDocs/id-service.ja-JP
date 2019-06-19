---
description: Experience Platform IDサービスへの呼び出しで使用されるデフォルトのドメイン名を、これらの設定を使用して独自のサブドメイン名に変更します。
keywords: ID サービス
seo-description: Experience Platform IDサービスへの呼び出しで使用されるデフォルトのドメイン名を、これらの設定を使用して独自のサブドメイン名に変更します。
seo-title: audienceManagerServer および audienceManagerServerSecure
title: audienceManagerServer および audienceManagerServerSecure
uuid: e21cacf-5151-4d34- b0f7-9e90275f4c7c
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# audienceManagerServer および audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

Experience Platform IDサービスへの呼び出しで使用されるデフォルトのドメイン名を、これらの設定を使用して独自のサブドメイン名に変更します。

**構文：**

* ` audienceManagerServer: " *`サブドメイン名`*.demdex.net"`
* ` audienceManagerServerSecure: " *`サブドメイン名`*.demdex.net"`

**目的**

通常、 [!DNL Experience Cloud] IDサービスは [!DNL Adobe] 、呼び出し `dpm.demdex.net`をおこないます。この宛先への呼び出しは、あまりに一般的で、サードパーティのように見えるため、好まれない場合があります。ID サービスをよりファーストパーティらしく見せるためには、これらの設定を使用して、以下のように [!DNL Audience Manager] サブドメイン名を `demdex.net` に追加します。`dpm.demdex.net` 呼び出しについて詳しくは、[Demdex ドメインの呼び出しについて](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html)を参照してください。

**要件**

これらの設定では、以下を使用する必要があります。

* 会社のレコードの [!DNL Audience Manager] サブドメイン名。この名前はコンサルタントに確認するか、コンサルタントから取得してください。
* に関連付けられているサブドメイン名 [!DNL Organization ID]。
* 同じサブドメイン名を持つ*両方の*設定パラメーター。

**コードサンプル**

この例では、`dpm.demdex.net` への呼び出しに法務上の懸念を抱くメディアエンターテインメント企業があるとします。[!DNL Audience Manager] で登録されているこの会社のサブドメイン名は Music1 です。以下のコードサンプルは、ID サービスデータ呼び出しをこの顧客固有のサブドメイン名でブランディングする方法を示します。

```
//Instantiate Visitor 
var visitor = Visitor.getInstance("Insert Experience Cloud Organization ID here",{ 
     ... 
     //Configure ID service call 
     audienceManagerServer: "Music1.demdex.net", 
     audienceManagerServerSecure: "Music1.demdex.net" 
     } 
);
```

