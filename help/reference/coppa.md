---
description: 児童オンラインプライバシー保護法（COPPA）では、証明可能な親の同意なく 13 歳未満の子供からの個人情報をオンラインで取得することを禁止しています。COPPA を遵守するために、オプションの変数を Experience Cloud Identity Service コードに追加して、ブラウザーのサードパーティドメインに Cookie を設定できなくすることができます。
keywords: ID サービス
seo-description: 児童オンラインプライバシー保護法（COPPA）では、証明可能な親の同意なく 13 歳未満の子供からの個人情報をオンラインで取得することを禁止しています。COPPA を遵守するために、オプションの変数を Experience Cloud Identity Service コードに追加して、ブラウザーのサードパーティドメインに Cookie を設定できなくすることができます。
seo-title: Experience Cloud Identity Service での COPPA のサポート
title: Experience Cloud Identity Service での COPPA のサポート
uuid: 621b5ebd-92e7-4635-be85-8d7e36589fcb
exl-id: c7579f90-3011-4e26-b908-08907bf12ba2
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '403'
ht-degree: 100%

---

# Experience Cloud Identity Service での COPPA のサポート {#coppa-support-in-the-experience-cloud-id-service}

児童オンラインプライバシー保護法（COPPA）では、証明可能な親の同意なく 13 歳未満の子供からの個人情報をオンラインで取得することを禁止しています。COPPA を遵守するために、オプションの変数を Experience Cloud Identity Service コードに追加して、ブラウザーのサードパーティドメインに Cookie を設定できなくすることができます。

>[!NOTE]
>
>バージョン 3.0.0 以降でサポートされています。

**Cookie とトラッキング**

Web ページを読み込む際に、[!DNL Experience Cloud] ID サービスが [!DNL Adobe] データ収集サーバー（DCS）を呼び出します。DCS の応答には、Experience Cloud Cookieと demdex.net Cookie が含まれています。

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

`true` に設定した場合、DCS が demdex.net サードパーティ Cookie を返す処理が `disableThirdPartyCookies` オブジェクトによって停止されます。サイトの訪問者のブラウザーにこの Cookie が既に設定されている場合、ID サービスが新しい [!DNL Experience Cloud] ID の作成や既存 ID の返却のためにこの Cookie を使用することはありません。[!DNL Experience Cloud] ID サービスは、ファーストパーティ Cookie に新しいランダムな ID を作成します。一度有効にすれば、COPPA によって許可されているその他の内部操作を含め、ID サービスによってデータを収集して、異なる [!DNL Experience Cloud] ソリューション間でそのデータを共有することができます。

>[!MORELIKETHIS]
>
>* [アドビプライバシーセンター](http://www.adobe.com/jp/privacy.html)
>* [COPPA とは](http://www.consumer.ftc.gov/articles/0031-protecting-your-childs-privacy-online#whatis)

