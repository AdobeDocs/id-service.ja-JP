---
description: 児童オンラインプライバシー保護法（COPPA）では、証明可能な親の同意なく 13 歳未満の子供からの個人情報をオンラインで取得することを禁止しています。COPPA を遵守するために、オプションの変数を Experience Cloud Identity Service コードに追加して、ブラウザーのサードパーティドメインに Cookie を設定できなくすることができます。
keywords: ID Service
seo-description: 児童オンラインプライバシー保護法（COPPA）では、証明可能な親の同意なく 13 歳未満の子供からの個人情報をオンラインで取得することを禁止しています。COPPA を遵守するために、オプションの変数を Experience Cloud Identity Service コードに追加して、ブラウザーのサードパーティドメインに Cookie を設定できなくすることができます。
seo-title: Experience Cloud Identity Service での COPPA のサポート
title: Experience Cloud Identity Service での COPPA のサポート
uuid: 621b5ebd-92e7-4635-be85-8d7e36589fcb
translation-type: tm+mt
source-git-commit: c4c0b791230422f17292b72fd45ba5689a60adae
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 77%

---


# Experience Cloud Identity Service での COPPA のサポート {#coppa-support-in-the-experience-cloud-id-service}

児童オンラインプライバシー保護法（COPPA）では、証明可能な親の同意なく 13 歳未満の子供からの個人情報をオンラインで取得することを禁止しています。COPPA を遵守するために、オプションの変数を Experience Cloud Identity Service コードに追加して、ブラウザーのサードパーティドメインに Cookie を設定できなくすることができます。

>[!NOTE]
>
>バージョン 3.0.0 以降でサポートされています。

**Cookie とトラッキング**

Web ページを読み込む際に、[!DNL Experience Cloud] ID サービスが [!DNL Adobe] データ収集サーバー（DCS）を呼び出します。DCSの応答には、Experience Cloudcookieとdemdex.net cookieが含まれます。

* Experience CloudCookieはファーストパーティドメインに設定されます。 異なるドメイン間で訪問者を追跡する場合は、それらのドメインが連携してアクセスを許可する場合を除き、このメソッドを使用することはできません。
* demdex.net cookieは、サードパーティドメインに設定されます。 このIDには、異なるドメイン間で訪問者を追跡するために使用できる一意の識別子が含まれます。

**CookieとCOPPAの準拠**

子供を対象とする（または主に子供向けの）Webサイトに関して異なるドメイン間で訪問者を追跡するサードパーティCookieによって、COPPAの親の同意が求められます。 内部 Web サイト分析で COPPA をより簡単に遵守するには、以下のように `disableThirdPartyCookies:true` 関数に `Visitor.getInstance` 変数を追加します。

```js
//Call the ID service 
var visitor = Visitor.getInstance("insert marketing cloud ID here", { 
 
    //Set disableThirdPartyCookies configuration param 
    disableThirdPartyCookies: true 
 
    ... 
});
```

`true` に設定した場合、DCS が demdex.net サードパーティ Cookie を返す処理が `disableThirdPartyCookies` オブジェクトによって停止されます。サイトの訪問者のブラウザーにこの Cookie が既に設定されている場合、ID サービスが新しい [!DNL Experience Cloud] ID の作成や既存 ID の返却のためにこの Cookie を使用することはありません。[!DNL Experience Cloud] ID サービスは、ファーストパーティ Cookie に新しいランダムな ID を作成します。一度有効にすれば、COPPA によって許可されているその他の内部操作を含め、ID サービスによってデータを収集して、異なる [!DNL Experience Cloud] ソリューション間でそのデータを共有することができます。

>[!MORELIKETHIS]
>
>* [アドビプライバシーセンター](http://www.adobe.com/jp/privacy.html)
>* [COPPA とは](http://www.consumer.ftc.gov/articles/0031-protecting-your-childs-privacy-online#whatis)

