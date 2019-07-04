---
description: getMarketingCloudVisitorID は、Experience Cloud 訪問者 ID を返します。
keywords: ID サービス
seo-description: getMarketingCloudVisitorID は、Experience Cloud 訪問者 ID を返します。
seo-title: getMarketingCloudVisitorID
title: getMarketingCloudVisitorID
uuid: 93e16220-b5b3-4d81-9189-30031bc15129
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# getMarketingCloudVisitorID{#getmarketingcloudvisitorid}

getMarketingCloudVisitorID は、Experience Cloud 訪問者 ID を返します。

**構文：** ` var *`変数名`* = visitor.getMarketingCloudVisitorID()`

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
>[!DNL Analytics] ユーザーの場合は、さらに [!DNL Analytics] ID をチェックして独自の関数に送信します。例えば、hidden フォーム要素の訪問者 ID を、データ挿入 API を使用するサーバー側のアプリケーションに渡す場合に、両方の識別子が必要になります。その場合は、[!DNL Experience Cloud] と [!DNL Analytics] の訪問者 ID を取得して返してください。[Analytics 訪問者 ID の取得](../../mcvid-library/mcvid-get-set/mcvid-getanalyticsvisitorid.md)を参照してください。

