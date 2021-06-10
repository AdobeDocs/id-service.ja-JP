---
description: getMarketingCloudVisitorID は、Experience Cloud 訪問者 ID を返します。
keywords: ID サービス
title: getMarketingCloudVisitorID
exl-id: bd81cc0b-0511-492d-beb8-8ba2fe5d4323
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '117'
ht-degree: 100%

---

# getMarketingCloudVisitorID{#getmarketingcloudvisitorid}

getMarketingCloudVisitorID は、Experience Cloud 訪問者 ID を返します。

**構文：** ` var *`変数名`* = visitor.getMarketingCloudVisitorID()`

この方法は通常、訪問者 ID の読み取りを必要とするカスタムソリューションで使用されます。 標準の実装では使用されません。`getMarketingCloudVisitorID` は、[!DNL Analytics] ID を読み取ってシステムまたはアプリケーションに送信するコールバック関数とも連携します。

```js
//callback function 
var useMarketingCloudID = function(id){ 
     //whatever your function does with the Experience Cloud ID 
}; 
 
//get the Experience Cloud ID and pass it to the function 
var mcID = visitor.getMarketingCloudVisitorID(useMarketingCloudID)
```

>[!TIP]
>
>[!DNL Analytics] ユーザーの場合は、さらに [!DNL Analytics] ID をチェックして独自の関数に送信します。例えば、hidden フォーム要素の訪問者 ID を、データ挿入 API を使用するサーバー側のアプリケーションに渡す場合に、両方の識別子が必要になります。その場合は、[!DNL Experience Cloud] と [!DNL Analytics] の訪問者 ID を取得して返してください。[Analytics 訪問者 ID の取得](../../library/get-set/getanalyticsvisitorid.md)を参照してください。
