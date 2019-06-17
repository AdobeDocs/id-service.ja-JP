---
description: getInstance は、指定した Experience Cloud 組織 ID に対応する訪問者 ID オブジェクトを返します。このメソッドは、s.visitor を使用して AppMeasurement に提供される訪問者 ID オブジェクトを初期化するために必要です。
keywords: ID サービス
seo-description: getInstance は、指定した Experience Cloud 組織 ID に対応する訪問者 ID オブジェクトを返します。このメソッドは、s.visitor を使用して AppMeasurement に提供される訪問者 ID オブジェクトを初期化するために必要です。
seo-title: getInstance
title: getInstance
uuid: 259b88a6- e3d0-4aab- b935-566099bdab98
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

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
>*訪問者関数* をインスタンス化しない `var visitor = new Visitor`でください。ここに記載されている正しい関数呼び出しを使用してください。この警告は [!DNL VisitorAPI.js] コードライブラリ v3.0 以降に適用されます。

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

`getInstance` により既存のインスタンスが見つからない場合は、新しいインスタンスが作成されて返されます。これは、の [`s_gi()` 関数 ](https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=function_s_gi.html) と同様 [!DNL AppMeasurement]です。

**一般的な使用例**

[!DNL Experience Cloud] IDサービスAPIは、組織IDごと [!DNL Adobe Experience Cloud] に作成されたすべてのインスタンスのリストを保持します。ID サービス API を使用するアプリケーションがそのインスタンスへの参照を渡さない場合、新しいインスタンスを作成する代わりに `getInstance` を呼び出すことでそのインスタンスを見つけることができます。同じ Web ページまたはアプリケーションにおいて、異なる組織の複数のインスタンスもサポートされます。

これは明確 `init` なフェーズを持たないアプリケーションで役立ちますが、複数の場所でIDサービスAPIを呼び出す必要があります。それらすべての場所で `getInstance` を呼び出すことができ、その最初の実行時にインスタンスが作成されます。その後の呼び出しでは既存のインスタンスが返されます。
