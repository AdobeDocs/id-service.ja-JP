---
description: このヘルパーメソッドを使用すると、補助的なデータ ID（SDID）をクエリ文字列パラメーターとしてリダイレクト URL に追加できます。 これは、A4T の使用時に、SDID をあるページから別のページへと保持し、それらの個別の訪問を結合する必要がある場合に便利です。 この関数を使用するには、ソースおよび宛先ドメインに対して、同じIMS組織IDで訪問者ID サービスを実装している必要があります。
keywords: 訪問者 ID サービス
title: appendSupplementalDataIDTo
exl-id: 7f0e7fca-4551-4165-a12b-c7e5514d6818
TQID: https://experienceleague.adobe.com/oR2LCiVk5N-Xnt3wTOKMt7UYFXzwEGFwJpKoz-ikzh8
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 354
ht-degree: 61%

---

# appendSupplementalDataIDTo{#appendsupplementaldataidto}

このヘルパーメソッドを使用すると、補助的なデータ ID（SDID）をクエリ文字列パラメーターとしてリダイレクト URL に追加できます。 これは、A4T の使用時に、SDID をあるページから別のページへと保持し、それらの個別の訪問を結合する必要がある場合に便利です。 この関数を使用するには、ソースおよび宛先ドメインに対して、同じIMS組織IDで訪問者ID サービスを実装している必要があります。

内容：

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> 構文およびコードサンプル </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4" format="dita" scope="local"> サンプル出力 </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> 構文およびコードサンプル </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-99946715cefa4acc95200b093db5297e" format="dita" scope="local"> sdidParamExpiry を使用した SDID タイムアウトの変更 </a> </li> 
</ul>

## 構文およびコードサンプル {#section-cbb0b2f73bcc418386796c24c01b2365}

**構文：** `appendSupplementalDataIDTo( *`URL`*, *`SDID`*)`

**コードサンプル**

```js
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE"); 

//Get current supplemental data id
var theCurrentSDID = visitor._supplementalDataIDCurrent ? visitor._supplementalDataIDCurrent : "";

//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, theCurrentSDID));
```

## サンプル出力 {#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4}

以下に示すように、URL リダイレクトには、訪問者のSDID、IMS組織ID、および受信ページへの呼び出しのUNIX タイムスタンプが含まれます。

<ul class="simplelist"> 
 <li> <span class="codeph"> www.domain.com/pageB?adobe_mc_sdid=SDID=7996F0B028999505-13DA591039D6226|MCORGID=123456789@AdobeOrg|TS=1498569322 </span> </li> 
</ul>

## sdidParamExpiry を使用した SDID タイムアウトの変更 {#section-99946715cefa4acc95200b093db5297e}

[sdidParamExpiry](../../library/function-vars/sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458) 設定を使用すると、`appendSupplementalDataIDTo` ヘルパー関数を使用して、あるページから別のページに SDID を渡す際に、デフォルトの ID の有効期限を変更できます。 デフォルトでは、受信ページの訪問者ID サービスコードは、参照ページから送信されたURLからSDIDを取得するのに30秒かかります。 受信ページの訪問者ID サービスコードが30秒以内にSDIDを取得できない場合、新しいSDIDをリクエストします。 この機能は、あるページから別のページに SDID を渡す必要があり、このタイムアウト間隔を制御する必要がある A4T ユーザーを主に対象としています。

デフォルトの SDID タイムアウトを変更したい場合は、次の構文を使用して `sdidParamExpiry` を `Visitor.getInstance` 関数に追加します。

**構文：** `sdidParamExpiry: *`時間（秒単位）`*`

**コードサンプル**

訪問者ID サービスのコードを設定すると、このサンプルと同様に表示される場合があります。 このサンプルでは、SDID タイムアウトを 15 秒に設定しています。

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
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

