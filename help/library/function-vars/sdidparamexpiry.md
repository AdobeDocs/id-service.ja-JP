---
description: この設定では、appendSupplementalDataIDTo ヘルパー関数を使用して、あるページから別のページにデフォルトの補助的なデータ ID（SDID）を渡す場合、その ID の有効間隔を上書きできます。 デフォルトでは、受信側ページの ID サービスコードで、参照元ページから送信された URL から SDID を取得するのに 30 秒かかります。 受信側ページの ID サービスコードが 30 秒以内に SDID を取得できない場合は、新しい SDID をリクエストします。 この機能は、あるページから別のページに SDID を渡す必要があり、このタイムアウト間隔を制御する必要がある A4T ユーザーを主に対象としています。
keywords: ID サービス
title: sdidParamExpiry
exl-id: 5458ffa5-03d1-4c52-907d-c50fe00ce35d
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 100%

---

# sdidParamExpiry{#sdidparamexpiry}

この設定では、appendSupplementalDataIDTo ヘルパー関数を使用して、あるページから別のページにデフォルトの補助的なデータ ID（SDID）を渡す場合、その ID の有効間隔を上書きできます。 デフォルトでは、受信側ページの ID サービスコードで、参照元ページから送信された URL から SDID を取得するのに 30 秒かかります。 受信側ページの ID サービスコードが 30 秒以内に SDID を取得できない場合は、新しい SDID をリクエストします。 この機能は、あるページから別のページに SDID を渡す必要があり、このタイムアウト間隔を制御する必要がある A4T ユーザーを主に対象としています。

**SDID タイムアウトの上書き**

デフォルトの SDID タイムアウトを変更したい場合は、次の構文を使用して `sdidParamExpiry` を `Visitor.getInstance` 関数に追加します。

**構文：** ` sdidParamExpiry: *`時間（秒単位）`*`

**コードサンプル**

設定する場合、ID サービスコードは次のサンプルのようになります。 このサンプルでは、SDID タイムアウトを 15 秒に設定しています。 この設定は、[appendSupplementalDataIDTo](../../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d) ヘルパーメソッドと連携します。

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
