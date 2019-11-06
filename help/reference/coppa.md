---
description: 児童オンラインプライバシー保護法（COPPA）では、証明可能な親の同意なく 13 歳未満の子供からの個人情報をオンラインで取得することを禁止しています。COPPA を遵守するために、オプションの変数を Experience Cloud Identity Service コードに追加して、ブラウザーのサードパーティドメインに Cookie を設定できなくすることができます。
keywords: ID サービス
seo-description: 児童オンラインプライバシー保護法（COPPA）では、証明可能な親の同意なく 13 歳未満の子供からの個人情報をオンラインで取得することを禁止しています。COPPA を遵守するために、オプションの変数を Experience Cloud Identity Service コードに追加して、ブラウザーのサードパーティドメインに Cookie を設定できなくすることができます。
seo-title: Experience Cloud Identity Service での COPPA のサポート
title: Experience Cloud Identity Service での COPPA のサポート
uuid: 621b5ebd-92e7-4635-be85-8d7e36589fcb
translation-type: ht
source-git-commit: c4c0b791230422f17292b72fd45ba5689a60adae

---


# Experience Cloud Identity Service での COPPA のサポート {#coppa-support-in-the-experience-cloud-id-service}

児童オンラインプライバシー保護法（COPPA）では、証明可能な親の同意なく 13 歳未満の子供からの個人情報をオンラインで取得することを禁止しています。COPPA を遵守するために、オプションの変数を Experience Cloud Identity Service コードに追加して、ブラウザーのサードパーティドメインに Cookie を設定できなくすることができます。

>[!NOTE]
>
>バージョン 3.0.0 以降でサポートされています。

**Cookie とトラッキング**

Web ページを読み込む際に、[!DNL Experience Cloud] ID サービスが [!DNL Adobe] データ収集サーバー（DCS）を呼び出します。DCS の応答には Experience Cloud Cookie と demdex.net Cookie が含まれます。

* Experience Cloud Cookie はファーストパーティドメインに設定されます。異なるドメインが連動してアクセスを許可していない限り、この Cookie を使用して異なるドメインで訪問者を追跡することはできません。
* demdex.net Cookie は、サードパーティドメインに設定されます。この Cookie には、訪問者を異なるドメインで追跡するために使用できる一意の識別子が含まれます。

**Cookie と COPPA の遵守**

子供を対象とした（または主に子供向けの）Web サイトに、異なるドメインで訪問者を追跡するサードパーティ Cookie がある場合、COPPA により親の同意が求められます。内部 Web サイト分析で COPPA をより簡単に遵守するには、以下のように `disableThirdPartyCookies:true` 関数に `Visitor.getInstance` 変数を追加します。

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

