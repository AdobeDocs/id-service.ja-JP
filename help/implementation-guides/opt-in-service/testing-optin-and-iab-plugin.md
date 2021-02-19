---
description: Web サイトでオプトインを有効にしたら、検証方法を使用して、ブラウザーの開発者ツールでサービスが期待どおりに動作しているかどうかをテストします。
seo-description: Web サイトでオプトインを有効にしたら、検証方法を使用して、ブラウザーの開発者ツールでサービスが期待どおりに動作しているかどうかをテストします。
seo-title: オプトインサービスの検証
title: オプトインサービスの検証
uuid: 1743360a-d757-4e50-8697-0fa92b302cbc
translation-type: tm+mt
source-git-commit: 0c300aa92991c0dec2ccdeeb34f9d886dcac7671
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 27%

---


# オプトインサービスの検証{#validating-opt-in-service}

Web サイトでオプトインを有効にしたら、検証方法を使用して、ブラウザーの開発者ツールでサービスが期待どおりに動作しているかどうかをテストします。

## 使用例 1：オプトインを有効にする {#section-c8fe1ee3711b420c8186c7057abbecb3}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true 
});
```

![](assets/use_case_1_1.png)

ページを読み込む前に、キャッシュとCookieをクリアします。

Chromeで、Webページを右クリックし、「Inspect」を選択します。 上のスクリーンショットのように、「*Network*」タブを選択して、ブラウザーからの要求を表示します。

上の例では、次のAdobeJSタグがページにインストールされています。ECID、AAM、Analytics、ターゲット。

**オプトインが期待どおりに動作していることを証明する方法：**

Adobeサーバーへのリクエストは表示されません。

* demdex.net/id
* demdex.net/event
* omtrdc.net/b/ss
* omtrdc.net/m2
* everesttech.net

>[!NOTE]
>
>`http://dpm.demdex.net/optOutStatus` の呼び出しが表示される場合があります。これは、訪問者のオプトアウトステータスを取得するために使用される読み取り専用のエンドポイントです。このエンドポイントでは、サードパーティCookieが作成されず、ページから情報が収集されません。

Adobeタグによって作成されたCookieは表示されません。(AMCV_{{YOUR_ORG_ID}}、mbox、demdex、s_cc、s_sq、everest_g_v2、everest_session_v2)

Chromeで、「*アプリケーション*」タブに移動し、「*ストレージ*」の下の「*Cookies*」セクションを展開し、Webサイトのドメイン名を選択します。

![](assets/use_case_1_2.png)

## 使用例2:オプトインとストレージを有効にする{#section-bd28326f52474fa09a2addca23ccdc0f}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isOptInStorageEnabled: true 
});
```

使用事例2の唯一の違いは、*新しいcookie*&#x200B;が表示され、訪問者が提供するオプトイン権限が含まれることです。**adobeujs-optin**

## 使用例3:オプトインと事前承認のAdobe Analyticsを有効にする{#section-257fe582b425496cbf986d0ec12d3692}

```
var preApproveAnalytics = {}; 
preApproveAnalytics[adobe.OptInCategories.ANALYTICS] = true;

Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    preOptInApprovals: preApproveAnalytics 
});
```

Adobe Analyticsは事前にオプトインが承認されているので、「ネットワーク」タブにトラッキングサーバーへのリクエストが表示されます。

![](assets/use_case_3_1.png)

「アプリケーション」タブにAnalytics cookieが表示されます。

![](assets/use_case_3_2.png)

## 使用例4:オプトインとIABを有効にする{#section-64331998954d4892960dcecd744a6d88}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isIabContext: true 
});
```

**ページで現在のIABの同意を表示する方法：**

開発者ツールを開き、「*コンソール*」タブを選択します。 次のコードスニペットを貼り付け、Enterキーを押します。

```
<codeblock>
  __cmp("getVendorConsents", null, function (vendorConsents) { 
     console.log("Vendor Consent:", vendorConsents); }) 
</codeblock>  
  
```

以下は、目的1、2、5が承認され、Audience ManagerベンダーIDが承認された場合の出力例です。

* demdex.net/id:この呼び出しが存在する場合、ECIDがdemdex.netからIDをリクエストしたことを証明します
* demdex.net/event:この呼び出しが存在する場合、DILのデータ収集呼び出しが期待どおりに動作していることが証明されます。
* demdex.net/dest5.html:この呼び出しが存在する場合、ID同期がトリガーされていることを証明します。

![](assets/use_case_4_1.png)

次のいずれかが無効な場合、Adobeサーバーへのリクエストは表示されず、Adobecookieも表示されません。

* 目的1、2、または5は承認されません。
* Audience ManagerベンダーIDが承認されていません。