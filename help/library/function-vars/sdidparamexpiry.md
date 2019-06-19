---
description: この設定を使用すると、appendSupplementalDataIDTo ヘルパー関数を使用して追加データ ID（SDID）をあるページから別のページに渡す際に、デフォルトの ID の有効期限を変更できます。デフォルトでは、受信ページの ID サービスコードは参照元ページによって送信された URL から SDID を 30 秒以内に取得します。受信ページの ID サービスコードが 30 秒以内に SDID を取得できない場合は新しい SDID を要求します。この機能は主に、あるページから別のページに SDID を渡す必要があり、このタイムアウト間隔を制御する必要がある A4T のユーザーを対象としています。
keywords: ID サービス
seo-description: この設定を使用すると、appendSupplementalDataIDTo ヘルパー関数を使用して追加データ ID（SDID）をあるページから別のページに渡す際に、デフォルトの ID の有効期限を変更できます。デフォルトでは、受信ページの ID サービスコードは参照元ページによって送信された URL から SDID を 30 秒以内に取得します。受信ページの ID サービスコードが 30 秒以内に SDID を取得できない場合は新しい SDID を要求します。この機能は主に、あるページから別のページに SDID を渡す必要があり、このタイムアウト間隔を制御する必要がある A4T のユーザーを対象としています。
seo-title: sdidParamExpiry
title: sdidParamExpiry
uuid: cdaf7e2d- b196-4c70-936d-8a98191cbb85
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# sdidParamExpiry{#sdidparamexpiry}

この設定を使用すると、appendSupplementalDataIDTo ヘルパー関数を使用して追加データ ID（SDID）をあるページから別のページに渡す際に、デフォルトの ID の有効期限を変更できます。デフォルトでは、受信ページの ID サービスコードは参照元ページによって送信された URL から SDID を 30 秒以内に取得します。受信ページの ID サービスコードが 30 秒以内に SDID を取得できない場合は新しい SDID を要求します。この機能は主に、あるページから別のページに SDID を渡す必要があり、このタイムアウト間隔を制御する必要がある A4T のユーザーを対象としています。

**SDID タイムアウトの変更**

デフォルトの SDID タイムアウトを変更したい場合は、次の構文を使用して `sdidParamExpiry` を `Visitor.getInstance` 関数に追加します。

**構文:**` sdidParamExpiry: *`秒単位の時間`*`

**コードサンプル**

設定が完了すると、ID サービスコードはこのサンプルのようになります。このサンプルでは SDID タイムアウトを 15 秒に設定しています。この設定は、[appendSupplementalDataIDTo](../../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d) ヘルパーメソッドで使用できます。

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

