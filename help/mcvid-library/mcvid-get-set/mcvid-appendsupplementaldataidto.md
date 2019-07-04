---
description: このヘルパーメソッドを使用すると、Supplemental Data ID（SDID）をクエリ文字列パラメーターとしてリダイレクト URL に追加できます。これは、A4T を使用する場合と、あるページから別のページへ移動する際に SDID を維持し、それらの訪問を結合する必要がある場合に便利です。この機能を使用するには、ソースドメインと宛先ドメインで同じ組織 ID を使用して ID サービスを実装する必要があります。
keywords: ID サービス
seo-description: このヘルパーメソッドを使用すると、Supplemental Data ID（SDID）をクエリ文字列パラメーターとしてリダイレクト URL に追加できます。これは、A4T を使用する場合と、あるページから別のページへ移動する際に SDID を維持し、それらの訪問を結合する必要がある場合に便利です。この機能を使用するには、ソースドメインと宛先ドメインで同じ組織 ID を使用して ID サービスを実装する必要があります。
seo-title: appendSupplementalDataIDTo
title: appendSupplementalDataIDTo
uuid: f3504d82-8da3-4971-818b-3df57df4ec2d
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# appendSupplementalDataIDTo{#appendsupplementaldataidto}

このヘルパーメソッドを使用すると、Supplemental Data ID（SDID）をクエリ文字列パラメーターとしてリダイレクト URL に追加できます。これは、A4T を使用する場合と、あるページから別のページへ移動する際に SDID を維持し、それらの訪問を結合する必要がある場合に便利です。この機能を使用するには、ソースドメインと宛先ドメインで同じ組織 ID を使用して ID サービスを実装する必要があります。

内容：

<ul class="simplelist"> 
 <li> <a href="../../mcvid-library/mcvid-get-set/mcvid-appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> 構文およびコードサンプル </a> </li> 
 <li> <a href="../../mcvid-library/mcvid-get-set/mcvid-appendsupplementaldataidto.md#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4" format="dita" scope="local"> サンプル出力 </a> </li> 
 <li> <a href="../../mcvid-library/mcvid-get-set/mcvid-appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> 構文およびコードサンプル </a> </li> 
 <li> <a href="../../mcvid-library/mcvid-get-set/mcvid-appendsupplementaldataidto.md#section-99946715cefa4acc95200b093db5297e" format="dita" scope="local"> sdidParamExpiry を使用した SDID タイムアウトの変更 </a> </li> 
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

## サンプル出力{#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4}

以下に示すように、URL リダイレクトでは、訪問者の SDID、組織 ID、UNIX タイムスタンプが受信ページへの呼び出しに含まれます。

<ul class="simplelist"> 
 <li> <span class="codeph"> www.domain.com/pageB?adobe_mc_sdid=SDID=123|MCORGID=123456789@AdobeOrg|TS=1498569322 </span> </li> 
</ul>

## sdidParamExpiry を使用した SDID タイムアウトの変更 {#section-99946715cefa4acc95200b093db5297e}

[sdidParamExpiry](../../mcvid-library/mcvid-function-vars/mcvid-sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458) 設定を使用すると、`appendSupplementalDataIDTo` ヘルパー関数を使用して、あるページから別のページに SDID を渡す際に、デフォルトの ID の有効期限を変更できます。デフォルトでは、受信ページの ID サービスコードは参照元ページによって送信された URL から SDID を 30 秒以内に取得します。受信ページの ID サービスコードが 30 秒以内に SDID を取得できない場合は新しい SDID を要求します。この機能は主に、あるページから別のページに SDID を渡す必要があり、このタイムアウト間隔を制御する必要がある A4T のユーザーを対象としています。

デフォルトの SDID タイムアウトを変更したい場合は、次の構文を使用して `sdidParamExpiry` を `Visitor.getInstance` 関数に追加します。

**構文：** ` sdidParamExpiry: *`時間（秒単位）`*`

**コードサンプル**

設定が完了すると、ID サービスコードはこのサンプルのようになります。このサンプルでは SDID タイムアウトを 15 秒に設定しています。

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

