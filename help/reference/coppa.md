---
description: 児童オンラインプライバシー保護法（COPPA）は、保護者の同意なしに13歳未満の児童から個人情報をオンラインで収集することを禁止しています。 COPPAを懸念するお客様は、ブラウザーのサードパーティドメインでCookieを設定できないように、オプションの変数を訪問者ID サービスコードに追加できます。
keywords: 訪問者 ID サービス
title: ADOBE Visitor ID サービスでのCOPPA サポート
exl-id: c7579f90-3011-4e26-b908-08907bf12ba2
TQID: https://experienceleague.adobe.com/szz7syrA2KSDasXTox02PTbxBy60tfFc80hHmsjXwc0
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: d3cdead0-685a-4489-9250-4bb709942f66id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 363
ht-degree: 36%

---

# ADOBE Visitor ID サービスでのCOPPA サポート {#coppa-support-in-the-experience-cloud-id-service}

児童オンラインプライバシー保護法（COPPA）は、保護者の同意なしに13歳未満の児童から個人情報をオンラインで収集することを禁止しています。 COPPAを懸念するお客様は、ブラウザーのサードパーティドメインでCookieを設定できないように、オプションの変数を訪問者ID サービスコードに追加できます。

>[!NOTE]
>
>バージョン 3.0.0 以降でサポートされています。

**Cookie とトラッキング**

Web ページが読み込まれると、訪問者ID サービスはAdobe Data Collection Server （DCS）を呼び出します。 DCS応答には、CX Enterprise Cookieとdemdex.net Cookieが含まれます。

* CX Enterprise Cookieは、ファーストパーティドメインで設定されます。 これは、異なるドメインをまたいで訪問者を追跡するために使用することはできません（ドメインが連携してアクセスを許可する場合を除く）。
* demdex.net Cookie は、サードパーティドメインに設定されます。 これには、異なるドメインをまたいで訪問者を追跡するために使用できる一意の識別子が含まれています。

**Cookie と COPPA への準拠**

子供向け（または主に子供向け）の web サイトで、異なるドメインをまたいで訪問者を追跡するサードパーティ Cookie は、COPPA の保護者同意要件をトリガーします。 内部 Web サイト分析で COPPA をより簡単に遵守するには、以下のように `disableThirdPartyCookies:true` 関数に `Visitor.getInstance` 変数を追加します。

```js
//Call the Visitor ID Service 
var visitor = Visitor.getInstance("insert marketing cloud ID here", { 
 
    //Set disableThirdPartyCookies configuration param 
    disableThirdPartyCookies: true 
 
    ... 
});
```

`true` に設定した場合、DCS が demdex.net サードパーティ Cookie を返す処理が `disableThirdPartyCookies` オブジェクトによって停止されます。 サイト訪問者が既にこのCookieをブラウザーに持っている場合、訪問者ID サービスはそれを使用して新しいECIDを作成したり、既存のIDを返したりしません。 代わりに、訪問者ID サービスは、ファーストパーティ Cookieに新しいランダム IDを作成します。 有効にすると、訪問者ID サービスを使用してデータを収集し、COPPAによって許可される他の内部操作を含む、さまざまなCX エンタープライズ ソリューション間で共有できるようになります。

>[!MORELIKETHIS]
>
>* [アドビプライバシーセンター](http://www.adobe.com/jp/privacy.html)
>* [COPPA とは](http://www.consumer.ftc.gov/articles/0031-protecting-your-childs-privacy-online#whatis)

