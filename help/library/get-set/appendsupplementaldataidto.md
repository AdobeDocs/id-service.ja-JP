---
description: このヘルパーメソッドを使用すると、補助的なデータ ID（SDID）をクエリ文字列パラメーターとしてリダイレクト URL に追加できます。 これは、A4T の使用時に、SDID をあるページから別のページへと保持し、それらの個別の訪問を結合する必要がある場合に便利です。 この関数を使用するには、ソースドメインと宛先ドメインに同じ組織 ID を持つ ID サービスを実装しておく必要があります。
keywords: ID サービス
title: appendSupplementalDataIDTo
exl-id: 7f0e7fca-4551-4165-a12b-c7e5514d6818
source-git-commit: 5710539b45a81394061cd4af2ef3edc27b49092e
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 100%

---

# appendSupplementalDataIDTo {#appendsupplementaldataidto}

このヘルパーメソッドを使用すると、補助的なデータ ID（SDID）をクエリ文字列パラメーターとしてリダイレクト URL に追加できます。 これは、A4T の使用時に、SDID をあるページから別のページへと保持し、それらの個別の訪問を結合する必要がある場合に便利です。 この関数を使用するには、ソースドメインと宛先ドメインに同じ組織 ID を持つ ID サービスを実装しておく必要があります。

内容：

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> 構文およびコードサンプル </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4" format="dita" scope="local"> サンプル出力 </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> 構文およびコードサンプル </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-99946715cefa4acc95200b093db5297e" format="dita" scope="local"> sdidParamExpiry を使用した SDID タイムアウトの変更 </a> </li> 
</ul>

## 構文およびコードサンプル {#section-cbb0b2f73bcc418386796c24c01b2365}

**構文：** ` appendSupplementalDataIDTo( *`URL`*, *`SDID`*)`

**コードサンプル**

```js
var visitor = Visitor.getInstance("Insert Experience Cloud organization ID here"); 

//Get current supplemental data id
var theCurrentSDID = visitor._supplementalDataIDCurrent ? visitor._supplementalDataIDCurrent : "";

//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, theCurrentSDID));
```

## サンプル出力 {#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4}

以下に示すように、URL リダイレクトでは、訪問者の SDID、組織 ID、UNIX タイムスタンプが受信ページへの呼び出しに含まれます。

<ul class="simplelist"> 
 <li> <span class="codeph"> www.domain.com/pageB?adobe_mc_sdid=SDID=7996F0B028999505-13DA591039D6226|MCORGID=123456789@AdobeOrg|TS=1498569322 </span> </li> 
</ul>

## sdidParamExpiry を使用した SDID タイムアウトの変更 {#section-99946715cefa4acc95200b093db5297e}

[sdidParamExpiry](../../library/function-vars/sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458) 設定を使用すると、`appendSupplementalDataIDTo` ヘルパー関数を使用して、あるページから別のページに SDID を渡す際に、デフォルトの ID の有効期限を変更できます。デフォルトでは、受信側ページの ID サービスコードで、参照元ページから送信された URL から SDID を取得するのに 30 秒かかります。 受信側ページの ID サービスコードが 30 秒以内に SDID を取得できない場合は、新しい SDID をリクエストします。 この機能は、あるページから別のページに SDID を渡す必要があり、このタイムアウト間隔を制御する必要がある A4T ユーザーを主に対象としています。

デフォルトの SDID タイムアウトを変更したい場合は、次の構文を使用して `sdidParamExpiry` を `Visitor.getInstance` 関数に追加します。

**構文：** ` sdidParamExpiry: *`時間（秒単位）`*`

**コードサンプル**

設定すると、ID サービスコードは次のサンプルのようになります。 このサンプルでは、SDID タイムアウトを 15 秒に設定しています。

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
   //Change the default SDID timeout to 15 seconds 
   sdidParamExpiry: 15 
}); 
 
//Get current supplemental data id
var theCurrentSDID = visitor._supplementalDataIDCurrent ? visitor._supplementalDataIDCurrent : "";

//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, theCurrentSDID)); 
```
