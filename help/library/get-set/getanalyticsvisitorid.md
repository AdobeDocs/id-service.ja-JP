---
description: Experience Cloud Identity Service が実装される前に s_vi Cookie に保存されていた従来の Analytics ID を返します（存在する場合）。訪問者に Analytics ID が割り当てられたことがない場合は、空の文字列を返します。
keywords: ID サービス
seo-description: Experience Cloud Identity Service が実装される前に s_vi Cookie に保存されていた従来の Analytics ID を返します（存在する場合）。訪問者に Analytics ID が割り当てられたことがない場合は、空の文字列を返します。
seo-title: getAnalyticsVisitorID
title: getAnalyticsVisitorID
uuid: 6bb8ddfc-9fc1-4105-b377-d9b4d247a0f8
translation-type: ht
source-git-commit: c4c0b791230422f17292b72fd45ba5689a60adae

---


# getAnalyticsVisitorID{#getanalyticsvisitorid}

Experience Cloud Identity Service が実装される前に s_vi Cookie に保存されていた従来の Analytics ID を返します（存在する場合）。訪問者に Analytics ID が割り当てられたことがない場合は、空の文字列を返します。

**構文** `var analyticsID = visitor.getAnalyticsVisitorID()`

この関数は、通常、訪問者 ID を読み取る必要があるカスタムソリューションで使用されます。標準の実装では使用されません。`getAnalyticsVisitorID` は、[!DNL Analytics] ID を読み取ってシステムまたはアプリケーションに送信するコールバック関数とも連携します。

**サンプルコード**

```js
//callback function 
var useAnalyticsVisitorID = function(id){ 
     //whatever your function does with the Experience Cloud ID 
}; 
 
//get Analytics ID and pass it to the function 
var analyticsID = visitor.getAnalyticsVisitorID(useAnalyticsVisitorID)
```

>[!TIP]
>
>[!DNL Analytics] ユーザーの場合は、さらに [!DNL Analytics] ID をチェックして独自の関数に送信します。例えば、hidden フォーム要素の訪問者 ID を、データ挿入 API を使用するサーバー側のアプリケーションに渡す場合に、両方の識別子が必要になります。その場合は、[!DNL Experience Cloud] と [!DNL Analytics] の訪問者 ID を取得して返してください。[getMarketingCloudVisitorID](../../library/get-set/getmcvid.md) を参照してください。

**「aid」パラメーターは従来の値です**

`aid` パラメーターは異なる 2 つの条件セット下で、クエリ文字列内で使用されます。

**例 1**

`aid` パラメーターは次の場合に、クエリ文字列内で使用されます。

* [!DNL Experience Cloud] ID サービスが正しくデプロイされている場合。
* サイトに訪問しているユーザーの [!DNL Analytics]s_vi Cookie[ に既に ](https://marketing.adobe.com/resources/help/ja_JP/whitepapers/cookies/cookies_analytics.html) ID が保存されている場合。

**例 2**

`aid` パラメーターは、組織が ID サービスを完全に導入する前の[猶予期間](../../reference/analytics-reference/grace-period.md)を使用している場合に、クエリ文字列内で使用されます。サイトに訪問しているユーザーが新規ユーザーであり、組織が猶予期間を使用していない場合、訪問者には [!DNL Experience Cloud]（`mid` ID）パラメーターが送信されます。

>[!MORELIKETHIS]
>
>* [Analytics の cookie](https://marketing.adobe.com/resources/help/ja_JP/whitepapers/cookies/cookies_analytics.html)

