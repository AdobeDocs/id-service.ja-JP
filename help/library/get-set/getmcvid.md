---
description: getMarketingCloudVisitorID は、Experience Cloud 訪問者 ID を返します。
keywords: ID サービス
seo-description: getMarketingCloudVisitorID は、Experience Cloud 訪問者 ID を返します。
seo-title: getMarketingCloudVisitorID
title: getMarketingCloudVisitorID
uuid: 93e16220- b5b3-4d81-9189-30031bc15129
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# getMarketingCloudVisitorID{#getmarketingcloudvisitorid}

getMarketingCloudVisitorID は、Experience Cloud 訪問者 ID を返します。

**構文:**` var *`変数名`* = visitor.getMarketingCloudVisitorID()`

このメソッドは、通常、訪問者 ID を読み取る必要があるカスタムソリューションで使用されます。標準の実装では使用されません。`getMarketingCloudVisitorID` は、[!DNL Analytics] ID を読み取ってシステムまたはアプリケーションに送信するコールバック関数とも連携します。

```js
//callback function 
var useMarketingCloudID = function(id){ 
     //whatever your function does with the Experience Cloud ID 
}; 
 
//get the Experience Cloud ID and pass it to the function 
var mcID = visitor.getMarketingCloudVisitorID(useMarketingClouidID)
```

>[!TIP]
>
>お客様 [!DNL Analytics] の場合は、 [!DNL Analytics] IDをチェックして関数に送信します。例えば、hidden フォーム要素の訪問者 ID を、データ挿入 API を使用するサーバー側のアプリケーションに渡す場合に、両方の識別子が必要になります。この場合、訪問者IDと [!DNL Experience Cloud][!DNL Analytics] 訪問者IDを収集して返します。Analytics訪問者ID [の取得を参照](../../library/get-set/getanalyticsvisitorid.md)してください。

