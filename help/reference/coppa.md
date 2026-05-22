---
description: 児童オンラインプライバシー保護法（COPPA）は、保護者の同意なしに13歳未満の児童から個人情報をオンラインで収集することを禁止しています。 COPPA を遵守するために、オプションの変数を Experience Cloud ID サービスコードに追加して、ブラウザーのサードパーティドメインに Cookie を設定できなくすることができます。
keywords: ID サービス
title: Experience Cloud ID サービスでの COPPA のサポート
exl-id: c7579f90-3011-4e26-b908-08907bf12ba2
TQID: https://experienceleague.adobe.com/szz7syrA2KSDasXTox02PTbxBy60tfFc80hHmsjXwc0
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: d3cdead0-685a-4489-9250-4bb709942f66id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 357
ht-degree: 86%

---

# Experience Cloud ID サービスでの COPPA のサポート {#coppa-support-in-the-experience-cloud-id-service}

児童オンラインプライバシー保護法（COPPA）は、保護者の同意なしに13歳未満の児童から個人情報をオンラインで収集することを禁止しています。 COPPA を遵守するために、オプションの変数を Experience Cloud ID サービスコードに追加して、ブラウザーのサードパーティドメインに Cookie を設定できなくすることができます。

>[!NOTE]
>
>バージョン 3.0.0 以降でサポートされています。

**Cookie とトラッキング**

Web ページを読み込む際に、[!DNL Experience Cloud] ID サービスが [!DNL Adobe] データ収集サーバー（DCS）を呼び出します。 DCS の応答には、Experience Cloud Cookieと demdex.net Cookie が含まれています。

* Experience Cloud Cookie はファーストパーティドメインに設定されます。 これは、異なるドメインをまたいで訪問者を追跡するために使用することはできません（ドメインが連携してアクセスを許可する場合を除く）。
* demdex.net Cookie は、サードパーティドメインに設定されます。 これには、異なるドメインをまたいで訪問者を追跡するために使用できる一意の識別子が含まれています。

**Cookie と COPPA への準拠**

子供向け（または主に子供向け）の web サイトで、異なるドメインをまたいで訪問者を追跡するサードパーティ Cookie は、COPPA の保護者同意要件をトリガーします。 内部 Web サイト分析で COPPA をより簡単に遵守するには、以下のように `disableThirdPartyCookies:true` 関数に `Visitor.getInstance` 変数を追加します。

```js
//Call the ID service 
var visitor = Visitor.getInstance("insert marketing cloud ID here", { 
 
    //Set disableThirdPartyCookies configuration param 
    disableThirdPartyCookies: true 
 
    ... 
});
```

`true` に設定した場合、DCS が demdex.net サードパーティ Cookie を返す処理が `disableThirdPartyCookies` オブジェクトによって停止されます。 サイトの訪問者のブラウザーにこの Cookie が既に設定されている場合、ID サービスが新しい [!DNL Experience Cloud] ID の作成や既存 ID の返却のためにこの Cookie を使用することはありません。 [!DNL Experience Cloud] ID サービスは、ファーストパーティ Cookie に新しいランダムな ID を作成します。 一度有効にすれば、COPPA によって許可されているその他の内部操作を含め、ID サービスによってデータを収集して、異なる [!DNL Experience Cloud] ソリューション間でそのデータを共有することができます。

>[!MORELIKETHIS]
>
>* [アドビプライバシーセンター](http://www.adobe.com/jp/privacy.html)
>* [COPPA とは](http://www.consumer.ftc.gov/articles/0031-protecting-your-childs-privacy-online#whatis)

