---
description: これらの設定を使用して、Experience Cloud Identity Service への呼び出しに使用されるデフォルトのドメイン名を、独自のサブドメイン名に変更します。
keywords: ID Service
seo-description: これらの設定を使用して、Experience Cloud Identity Service への呼び出しに使用されるデフォルトのドメイン名を、独自のサブドメイン名に変更します。
seo-title: audienceManagerServer および audienceManagerServerSecure
title: audienceManagerServer および audienceManagerServerSecure
uuid: e21cacbf-5151-4d34-b0f7-9e90275f4c7c
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 100%

---


# audienceManagerServer および audienceManagerServerSecure {#audiencemanagerserver-and-audiencemanagerserversecure}

これらの設定を使用して、Experience Cloud Identity Service への呼び出しに使用されるデフォルトのドメイン名を、独自のサブドメイン名に変更します。

**構文：**

* ` audienceManagerServer: " *`サブドメイン名`*.demdex.net"`
* ` audienceManagerServerSecure: " *`サブドメイン名`*.demdex.net"`

**目的**

通常、[!DNL Experience Cloud] ID サービスは [!DNL Adobe] への呼び出しを `dpm.demdex.net` でおこないます。この宛先への呼び出しは、あまりに一般的で、サードパーティのように見えるため、好まれない場合があります。ID サービスをよりファーストパーティらしく見せるためには、これらの設定を使用して、以下のように [!DNL Audience Manager] サブドメイン名を `demdex.net` に追加します。`dpm.demdex.net` 呼び出しについて詳しくは、[Demdex ドメインの呼び出しについて](https://docs.adobe.com/content/help/ja-JP/audience-manager/user-guide/reference/demdex-calls.html)を参照してください。

**要件**

これらの設定では、以下を使用する必要があります。

* 会社で登録している [!DNL Audience Manager] サブドメイン名。この名前はコンサルタントに確認するか、コンサルタントから取得してください。
* [!UICONTROL 組織 ID] に関連付けられているサブドメイン名。
* 同じサブドメイン名を持つ&#x200B;*両方の*&#x200B;設定パラメーター。

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

