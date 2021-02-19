---
description: この設定では、appendSupplementalDataIDToヘルパー関数を使用して、ページ間でそのIDを渡す場合に、デフォルトのSupplemental Data ID(SDID)の有効期限間隔を上書きできます。 デフォルトでは、受信側ページのIDサービスコードは、参照元ページから送信されたURLからSDIDを取得するために30秒かかります。 受信ページのIDサービスコードが30秒以内にSDIDを取得できない場合は、新しいSDIDを要求します。 この機能は主に、あるページから別のページにSDIDを渡す必要があり、このタイムアウト間隔を制御する必要があるA4Tのお客様向けです。
keywords: ID サービス
seo-description: この設定では、appendSupplementalDataIDToヘルパー関数を使用して、ページ間でそのIDを渡す場合に、デフォルトのSupplemental Data ID(SDID)の有効期限間隔を上書きできます。 デフォルトでは、受信側ページのIDサービスコードは、参照元ページから送信されたURLからSDIDを取得するために30秒かかります。 受信ページのIDサービスコードが30秒以内にSDIDを取得できない場合は、新しいSDIDを要求します。 この機能は主に、あるページから別のページにSDIDを渡す必要があり、このタイムアウト間隔を制御する必要があるA4Tのお客様向けです。
seo-title: sdidParamExpiry
title: sdidParamExpiry
uuid: cdaf7e2d-b196-4c70-936d-8a98191cbb85
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 7%

---


# sdidParamExpiry{#sdidparamexpiry}

この設定では、appendSupplementalDataIDToヘルパー関数を使用して、ページ間でそのIDを渡す場合に、デフォルトのSupplemental Data ID(SDID)の有効期限間隔を上書きできます。 デフォルトでは、受信側ページのIDサービスコードは、参照元ページから送信されたURLからSDIDを取得するために30秒かかります。 受信ページのIDサービスコードが30秒以内にSDIDを取得できない場合は、新しいSDIDを要求します。 この機能は主に、あるページから別のページにSDIDを渡す必要があり、このタイムアウト間隔を制御する必要があるA4Tのお客様向けです。

**SDIDタイムアウトの上書き**

デフォルトの SDID タイムアウトを変更したい場合は、次の構文を使用して `sdidParamExpiry` を `Visitor.getInstance` 関数に追加します。

**構文：** ` sdidParamExpiry: *`時間（秒単位）`*`

**コードサンプル**

設定したIDサービスコードは、このサンプルのようになります。 次の例では、SDIDタイムアウトを15秒に設定します。 この設定は、[appendSupplementalDataIDTo](../../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d)ヘルパーメソッドと連携します。

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
   //Change the default SDID timeout to 15 seconds 
   sdidParamExpiry: 15 
}); 
 
//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, "67987653465787219"); 
```

