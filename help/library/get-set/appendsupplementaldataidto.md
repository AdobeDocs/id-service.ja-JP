---
description: このヘルパーメソッドを使用すると、Supplemental Data ID(SDID)をクエリ文字列パラメーターとしてリダイレクトURLに追加できます。 これは、A4Tを使用する場合に便利です。ページ間でSDIDを保持し、それらの個別の訪問を結合する必要がある場合に便利です。 この関数を使用するには、ソースドメインと宛先ドメインに同じ組織IDを持つIDサービスを実装している必要があります。
keywords: ID サービス
seo-description: このヘルパーメソッドを使用すると、Supplemental Data ID(SDID)をクエリ文字列パラメーターとしてリダイレクトURLに追加できます。 これは、A4Tを使用する場合に便利です。ページ間でSDIDを保持し、それらの個別の訪問を結合する必要がある場合に便利です。 この関数を使用するには、ソースドメインと宛先ドメインに同じ組織IDを持つIDサービスを実装している必要があります。
seo-title: appendSupplementalDataIDTo
title: appendSupplementalDataIDTo
uuid: f3504d82-8da3-4971-818b-3df57df4ec2d
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 28%

---


# appendSupplementalDataIDTo{#appendsupplementaldataidto}

このヘルパーメソッドを使用すると、Supplemental Data ID(SDID)をクエリ文字列パラメーターとしてリダイレクトURLに追加できます。 これは、A4Tを使用する場合に便利です。ページ間でSDIDを保持し、それらの個別の訪問を結合する必要がある場合に便利です。 この関数を使用するには、ソースドメインと宛先ドメインに同じ組織IDを持つIDサービスを実装している必要があります。

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
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
}); 
 
//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, "67987653465787219");
```

## サンプル出力 {#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4}

以下に示すように、URL リダイレクトでは、訪問者の SDID、組織 ID、UNIX タイムスタンプが受信ページへの呼び出しに含まれます。

<ul class="simplelist"> 
 <li> <span class="codeph"> www.domain.com/pageB?adobe_mc_sdid=SDID=123|MCORGID=123456789@AdobeOrg|TS=1498569322 </span> </li> 
</ul>

## sdidParamExpiry を使用した SDID タイムアウトの変更 {#section-99946715cefa4acc95200b093db5297e}

[sdidParamExpiry](../../library/function-vars/sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458) 設定を使用すると、`appendSupplementalDataIDTo` ヘルパー関数を使用して、あるページから別のページに SDID を渡す際に、デフォルトの ID の有効期限を変更できます。デフォルトでは、受信側ページのIDサービスコードは、参照元ページから送信されたURLからSDIDを取得するために30秒かかります。 受信ページのIDサービスコードが30秒以内にSDIDを取得できない場合は、新しいSDIDを要求します。 この機能は主に、あるページから別のページにSDIDを渡す必要があり、このタイムアウト間隔を制御する必要があるA4Tのお客様向けです。

デフォルトの SDID タイムアウトを変更したい場合は、次の構文を使用して `sdidParamExpiry` を `Visitor.getInstance` 関数に追加します。

**構文：** ` sdidParamExpiry: *`時間（秒単位）`*`

**コードサンプル**

設定したIDサービスコードは、次の例のようになります。 次の例では、SDIDタイムアウトを15秒に設定します。

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

