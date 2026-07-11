---
description: getInstanceは、指定されたIMS組織IDの訪問者ID オブジェクトを返します。 このメソッドは、s.visitor を使用して AppMeasurement に提供される訪問者 ID オブジェクトを初期化するために必要です。
keywords: 訪問者 ID サービス
title: getInstance
exl-id: 4941cf51-a8d0-4796-a102-4cd13cd5574d
TQID: https://experienceleague.adobe.com/XtjVkeuXAke6g-K8DNmq5kT6aUszrj6W0k9UM2NBBIA
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: c2be0313-b3ae-45e0-b454-d20bf54b23f2
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 230
ht-degree: 55%

---

# getInstance{#getinstance}

getInstanceは、指定されたIMS組織IDの訪問者ID オブジェクトを返します。 このメソッドは、s.visitor を使用して AppMeasurement に提供される訪問者 ID オブジェクトを初期化するために必要です。

**構文**

**JavaScript**

```js
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE", { 
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
>訪問者関数を `var visitor = new Visitor` でインスタンス化&#x200B;*しないで*&#x200B;ください。 ここに記載されている正しい関数呼び出しを使用してください。 この警告は `VisitorAPI.js` コードライブラリ v3.0 以降に適用されます。

**ActionScript／Flash**

```js
import com.adobe.mc.Visitor; 
... 
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
});
```

`getInstance` により既存のインスタンスが見つからない場合は、新しいインスタンスが作成されて返されます。 これは、AppMeasurementの[`s_gi()`関数](https://experienceleague.adobe.com/docs/analytics/implementation/vars/functions/s-gi.html?lang=ja)に似ています。

**一般的な使用例**

訪問者ID サービス APIは、各IMS組織IDに対して作成されたすべてのインスタンスのリストを保持します。 訪問者ID サービス APIを使用するアプリケーションがインスタンスへの参照を渡さない場合は、新しいインスタンスを作成する代わりに`getInstance`を呼び出すことでそのインスタンスを見つけることができます。 同じ Web ページまたはアプリケーションにおいて、異なる組織の複数のインスタンスもサポートされます。

これは、`init` フェーズが明確でないが、複数の場所で訪問者ID サービス APIを呼び出す必要があるアプリケーションに役立ちます。 それらすべての場所で `getInstance` を呼び出すことができ、その最初の実行時にインスタンスが作成されます。 その後の呼び出しでは既存のインスタンスが返されます。

