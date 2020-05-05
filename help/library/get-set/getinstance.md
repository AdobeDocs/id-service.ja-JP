---
description: getInstanceは、指定されたExperience Cloud組織IDの訪問者IDオブジェクトを返します。 これは、s.訪問者を使用してAppMeasurementに提供される訪問者IDオブジェクトを初期化するために必要です。
keywords: ID Service
seo-description: getInstanceは、指定されたExperience Cloud組織IDの訪問者IDオブジェクトを返します。 これは、s.訪問者を使用してAppMeasurementに提供される訪問者IDオブジェクトを初期化するために必要です。
seo-title: getInstance
title: getInstance
uuid: 259b88a6-e3d0-4aab-b935-566099bdab98
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# getInstance{#getinstance}

getInstanceは、指定されたExperience Cloud組織IDの訪問者IDオブジェクトを返します。 これは、s.訪問者を使用してAppMeasurementに提供される訪問者IDオブジェクトを初期化するために必要です。

**構文**

**JavaScript**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
});
```

>[!CAUTION]
>
>訪問者関数を `var visitor = new Visitor` でインスタンス化&#x200B;*しないで*&#x200B;ください。ここに記載されている正しい関数呼び出しを使用してください。Applies to [!UICONTROL VisitorAPI.js] code library v3.0 or higher.

**ActionScript／Flash**

```js
import com.adobe.mc.Visitor; 
... 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
});
```

`getInstance` により既存のインスタンスが見つからない場合は、新しいインスタンスが作成されて返されます。これは、の [ 関数と似 `s_gi()` てい ](https://docs.adobe.com/content/help/en/analytics/implementation/vars/functions/s-gi.html)[!DNL AppMeasurement]ます。

**一般的な使用例**

[!DNL Experience Cloud] ID サービス API は各 [!DNL Adobe Experience Cloud] 組織 ID に対して作成されたすべてのインスタンスのリストを保持しています。ID サービス API を使用するアプリケーションがそのインスタンスへの参照を渡さない場合、新しいインスタンスを作成する代わりに `getInstance` を呼び出すことでそのインスタンスを見つけることができます。同じ Web ページまたはアプリケーションにおいて、異なる組織の複数のインスタンスもサポートされます。

このメソッドは、明確な `init` フェーズは持たないものの、複数の場所で ID サービス API を呼び出す必要があるアプリケーションで役立ちます。それらすべての場所で `getInstance` を呼び出すことができ、その最初の実行時にインスタンスが作成されます。その後の呼び出しでは既存のインスタンスが返されます。
