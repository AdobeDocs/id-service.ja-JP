---
description: Web サイトでオプトインを有効にしたら、検証方法を使用して、ブラウザーの開発者ツールでサービスが期待どおりに動作しているかどうかをテストします。
title: オプトインサービスの検証
exl-id: f0bcb32a-ccad-40a4-b031-2584e4136ace
TQID: https://experienceleague.adobe.com/hODkrRE20lKjVoLJ769h27EinOy58m8KbdOmThtpUgM
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 451
ht-degree: 97%

---

# オプトインサービスの検証{#validating-opt-in-service}

Web サイトでオプトインを有効にしたら、検証方法を使用して、ブラウザーの開発者ツールでサービスが期待どおりに動作しているかどうかをテストします。

## ユースケース 1：オプトインを有効にする {#section-c8fe1ee3711b420c8186c7057abbecb3}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true 
});
```

![](assets/use_case_1_1.png)

ページを読み込む前に、キャッシュと Cookie をクリアします。

Chrome で web ページを右クリックし、「検証」を選択します。 上のスクリーンショットのように、「*ネットワーク*」タブを選択して、ブラウザーからのリクエストを表示します。

上の例では、アドビ JS タグ ECID、AAM、Analytics、Target がページにインストールされています。

**オプトインが期待どおりに動作していることを証明する方法：**

アドビサーバーへのリクエストは表示されません。

* demdex.net/id
* demdex.net/event
* omtrdc.net/b/ss
* omtrdc.net/m2
* everesttech.net

>[!NOTE]
>
>`http://dpm.demdex.net/optOutStatus` の呼び出しが表示される場合があります。これは、訪問者のオプトアウトステータスを取得するために使用される読み取り専用のエンドポイントです。 最終的に、このエンドポイントでは、サードパーティの Cookie が作成されることはなく、ページから情報が収集されることもありません。

Adobe タグによって作成されたCookieは表示されません：（`AMCV_{{YOUR_ORG_ID}}`、`mbox`、`demdex`、`s_cc`、`s_sq`、`everest_g_v2`、`everest_session_v2`）

Chromeで、「*Application*」タブに移動し、「*Storage*」の下の「*Cookies*」セクションを展開し、web サイトのドメイン名を選択します。

![](assets/use_case_1_2.png)

## ユースケース 2：オプトインとストレージを有効にする {#section-bd28326f52474fa09a2addca23ccdc0f}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isOptInStorageEnabled: true 
});
```

ユースケース 2 の唯一の違いは、訪問者から提供されるオプトイン権限を含む&#x200B;*新しい Cookie*（**adobeujs-optin**）が表示されることです。

## ユースケース 3：オプトインを有効にし Adobe Analytics を事前承認する {#section-257fe582b425496cbf986d0ec12d3692}

```
var preApproveAnalytics = {}; 
preApproveAnalytics[adobe.OptInCategories.ANALYTICS] = true;

Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    preOptInApprovals: preApproveAnalytics 
});
```

Adobe Analytics は事前にオプトインが承認されているので、「Network」タブにトラッキングサーバーへのリクエストが表示されます。

![](assets/use_case_3_1.png)

また、「Application」タブに Analytics Cookie が表示されます。

![](assets/use_case_3_2.png)

## ユースケース 4：オプトインと IAB を有効にする {#section-64331998954d4892960dcecd744a6d88}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isIabContext: true 
});
```

**ページでの現在の IAB 同意を表示する方法：**

デベロッパーツールを開き、「*Console*」タブを選択します。 次のコードスニペットを貼り付け、Enter キーを押します。

```
<codeblock>
  __cmp("getVendorConsents", null, function (vendorConsents) { 
     console.log("Vendor Consent:", vendorConsents); }) 
</codeblock>  
  
```

目的 1、2、5 が承認され、Audience Manager ベンダー ID が承認された場合の出力例を次に示します。

* demdex.net/id：この呼び出しが存在する場合は、ECID が demdex.net から ID をリクエストしたことの証明になります
* demdex.net/event：この呼び出しが存在する場合は、DIL のデータ収集呼び出しが正常に動作していることの証明になります。
* demdex.net/dest5.html：この呼び出しが存在する場合は、ID 同期がトリガーされていることの証明になります。

![](assets/use_case_4_1.png)

次のいずれかの場合、アドビサーバーへのリクエストは表示されず、アドビ Cookie も表示されません。

* 目的 1、2、5 のいずれかが承認されていない。
* Audience Manager ベンダー ID が承認されていない。

