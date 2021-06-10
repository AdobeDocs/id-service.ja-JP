---
description: getInstance は、指定した Experience Cloud 組織 ID に対応する訪問者 ID オブジェクトを返します。このメソッドは、s.visitor を使用して AppMeasurement に提供される訪問者 ID オブジェクトを初期化するために必要です。
keywords: ID サービス
title: getInstance
exl-id: 4941cf51-a8d0-4796-a102-4cd13cd5574d
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 100%

---

# getInstance{#getinstance}

getInstance は、指定した Experience Cloud 組織 ID に対応する訪問者 ID オブジェクトを返します。このメソッドは、s.visitor を使用して AppMeasurement に提供される訪問者 ID オブジェクトを初期化するために必要です。

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
>訪問者関数を `var visitor = new Visitor` でインスタンス化&#x200B;*しないで*&#x200B;ください。ここに記載されている正しい関数呼び出しを使用してください。この警告は [!UICONTROL VisitorAPI.js] コードライブラリ v3.0 以降に適用されます。

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

`getInstance` により既存のインスタンスが見つからない場合は、新しいインスタンスが作成されて返されます。この動作は、[!DNL AppMeasurement] の [`s_gi()` 関数](https://docs.adobe.com/content/help/ja-JP/analytics/implementation/vars/functions/s-gi.html)と同様です。

**一般的な使用例**

[!DNL Experience Cloud] ID サービス API は各 [!DNL Adobe Experience Cloud] 組織 ID に対して作成されたすべてのインスタンスのリストを保持しています。ID サービス API を使用するアプリケーションがそのインスタンスへの参照を渡さない場合、新しいインスタンスを作成する代わりに `getInstance` を呼び出すことでそのインスタンスを見つけることができます。同じ Web ページまたはアプリケーションにおいて、異なる組織の複数のインスタンスもサポートされます。

このメソッドは、明確な `init` フェーズは持たないものの、複数の場所で ID サービス API を呼び出す必要があるアプリケーションで役立ちます。それらすべての場所で `getInstance` を呼び出すことができ、その最初の実行時にインスタンスが作成されます。その後の呼び出しでは既存のインスタンスが返されます。
