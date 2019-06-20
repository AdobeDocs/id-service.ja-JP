---
description: これらの手順は、Experience Cloud IDサービスを使用し、Dynamic Tag Management（DTM）を使用しないAnalyticsのお客様向けです。ただし、ID サービスの実装に DTM を使用することを強くお勧めします。DTM は、実装ワークフローを合理化し、適切なコード配置と優先順位付けを自動的に確認します。
keywords: ID サービス
seo-description: これらの手順は、Experience Cloud IDサービスを使用し、Dynamic Tag Management（DTM）を使用しないAnalyticsのお客様向けです。ただし、ID サービスの実装に DTM を使用することを強くお勧めします。DTM は、実装ワークフローを合理化し、適切なコード配置と優先順位付けを自動的に確認します。
seo-title: Experience Cloud ID サービスの Analytics への実装
title: Experience Cloud ID サービスの Analytics への実装
uuid: 7fbd6fa0-1713-4232-8680-500ED62709d5
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Experience Cloud ID サービスの Analytics への実装 {#implement-the-experience-cloud-id-service-for-analytics}

これらの手順は、Experience Cloud IDサービスを使用し、Dynamic Tag Management（DTM）を使用しないAnalyticsのお客様向けです。ただし、ID サービスの実装に DTM を使用することを強くお勧めします。DTM は、実装ワークフローを合理化し、適切なコード配置と優先順位付けを自動的に確認します。

>[!IMPORTANT]
>
>* [始める前に、要件を確認してください](../reference/requirements.md)。
>* このコードを本番環境に実装する前に、開発環境で設定してテストしてください。
>



Adobe Analytics用にIDサービスを実装するには、次の手順に従います。

1. [IDサービスコードのダウンロード](../implementation-guides/setup-analytics.md#section-ead9403a6b7e45b887f9ac959ef89f7f)
1. [IDサービスコードへのVisitor. getInstance関数の追加](../implementation-guides/setup-analytics.md#section-6053a6b7c16c466a9f9fdbf9cb9db3df)
1. [Visitor. getInstanceにExperience Cloud組織IDを追加します](../implementation-guides/setup-analytics.md#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e)
1. [Visitor. getInstanceにトラッキングサーバーを追加します](../implementation-guides/setup-analytics.md#section-70ec9ebff47940d8ab520be5ec4728c5)
1. [AppMeasurement. jsまたはs_ code. jsファイルの更新](../implementation-guides/setup-analytics.md#section-b53113aea1bd4de896e0e4e9a7edee19)
1. [ページへの訪問者APIコードの追加](../implementation-guides/setup-analytics.md#section-d46d6aa324c842f2931d901e38d6db1d)
1. [（オプション）猶予期間の設定](../implementation-guides/setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3)
1. [IDサービスコードのテストと導入](../implementation-guides/setup-analytics.md#section-e9c1764ac21a4ec5be1ff338c0e2e01b)

## Step 1: Download the ID Service code {#section-ead9403a6b7e45b887f9ac959ef89f7f}

The [!DNL ID Service] requires the `VisitorAPI.js` code library. このコードライブラリをダウンロードするには：

1. **[!UICONTROL 管理]** 者/ **[!UICONTROL コードマネージャー]** に移動します。
1. In [!DNL Code Manager], click either **[!UICONTROL JavaScript (New)]** or **[!UICONTROL JavaScript (Legacy)]**.

   圧縮されたコードライブラリがダウンロードされます。

1. コードファイルを解凍し、`VisitorAPI.js` ファイルを開きます。

## 手順 2：Add the Visitor.getInstance function to the ID Service Code {#section-6053a6b7c16c466a9f9fdbf9cb9db3df}

>[!IMPORTANT]
>
>* ID サービス API の過去のバージョンでは、この関数を別の場所に別の構文で配置する必要がありました。[version 1.4](../release-notes/notes-2015.md#section-f5c596f355b14da28f45c798df513572) より前のバージョンから移行する場合は、ここで説明する新しい場所と構文について注意してください。
>* すべて大文字で書かれたコードは、実際の値のプレースホルダーです。このテキストを組織 ID、トラッキングサーバー URL、またはその他の指定された値に置き換えます。
>



**パート 1：以下の Visitor.getInstance 関数をコピーします**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
}); 
```

**パート 2：VisitorAPI.js ファイルに関数コードを追加します**

`Visitor.getInstance` 関数をファイル末尾のコードブロックの後に配置します。編集後のファイルは以下のようになります。

```js
/* 
========== DO NOT ALTER ANYTHING BELOW THIS LINE ========== 
Version and copyright section 
*/ 
 
// Visitor API code library section 
 
// Put Visitor.getInstance at the end of the file, after the code library

var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
}); 
```

## Step 3: Add your Experience Cloud Organization ID to Visitor.getInstance {#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e}

`Visitor.getInstance` 関数で、組織ID `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` に置き換え [!DNL Experience Cloud] ます。組織 ID がわからない場合、[!DNL Experience Cloud] 管理ページで確認できます。[管理 - コアサービス](https://marketing.adobe.com/resources/help/en_US/mcloud/admin_getting_started.html)も参照してください。編集後の関数は、以下のサンプルのようになります。

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg", { ...`

>[!IMPORTANT]
>
>*組織ID内の文字の大文字小文字は* 変更しないでください。この ID は大文字小文字が区別され、割り当てられたとおりに使用する必要があります。

## Step 4: Add your tracking servers to Visitor.getInstance {#section-70ec9ebff47940d8ab520be5ec4728c5}

トラッキングサーバーは、[!DNL Analytics] データ収集に使用されます。

**パート 1：トラッキングサーバー URL の確認**

Check your `s_code.js` or `AppMeasurement.js` files to find the tracking server URLs. この URL に以下の変数を指定します。

* `s.trackingServer`
* `s.trackingServerSecure`

**パート 2：トラッキングサーバー変数の設定**

使用するトラッキングサーバー変数を判断するには：

1. 以下の判断マトリックスの質問に答えます。自分の答えに合う変数を使用します。
1. トラッキングサーバーのプレースホルダーをトラッキングサーバー URL に置き換えます。
1. 未使用のトラッキングサーバーおよび [!DNL Experience Cloud] サーバーの変数をコードから削除します。

![](assets/tracking-server-matrix.png)

>[!NOTE]
>
>When used, match the [!DNL Experience Cloud] server URLs to their corresponding tracking server URLs like this: &gt;
>* [!DNL Experience Cloud] server URL=トラッキングサーバーURL
>* [!DNL Experience Cloud] server secure URL=トラッキングサーバーセキュアURL
>



If you&#39;re not sure how to find your tracking server see the [FAQ](../faq-intro/faq.md) and [Correctly Populate the trackingServer and trackingServerSecure variables](https://helpx.adobe.com/analytics/kb/determining-data-center.html#).

## Step 5: Update your AppMeasurement.js or s_code.js file {#section-b53113aea1bd4de896e0e4e9a7edee19}

Add this function to your `AppMeasurement.js` or `s_code.js` file:

`s.visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");`

Place the code in the same section that contains configurations such as `linkInternalFilters`, `charSet`, `trackDownloads`, etc.

**（オプション、推奨）**カスタム prop の作成**

Set a custom prop in `AppMeasurement.js` or `s_code.js` to measure coverage. Add this custom prop to the `doPlugins` function of your `AppMeasurement.js` or `s_code.js` files:

```js
// prop1 is used as an example only. Choose any available prop. 
s.prop1 = (typeof(Visitor) != "undefined" ? "VisitorAPI Present" : "VisitorAPI Missing");
```

## Step 6: Add Visitor API code to the page {#section-d46d6aa324c842f2931d901e38d6db1d}

Place the `VisitorAPI.js` file within the `<head>` tags on each page. `VisitorAPI.js` ファイルをページに配置する際には、以下のようにします。

* Put it at the beginning of the `<head>` section to it appears before other solution tags.
* AppMeasurement およびその他の [!DNL Experience Cloud] ソリューションのコードより前に実行する必要があります。

テストと検証の後にこのコードを本番に移行します。

## Step 7: (Optional) Configure a grace period {#section-7bbb2f72c26e4abeb8881e18366797a3}

If any of these use cases apply to your situation, ask [Customer Care](https://helpx.adobe.com/marketing-cloud/contact-support.html) to set up a temporary [grace period](../reference/analytics-reference/grace-period.md). 猶予期間は最大 180 日間有効です。必要に応じて、猶予期間を更新できます。

**部分的実装**

ID サービスを使用するページと使用しないページが混在し、そのすべてのページが同じ [!DNL Analytics] レポートスイートで管理される場合は、猶予期間が必要です。この状況は、複数のドメインで管理されるグローバルなレポートスイートがある場合に一般的です。

同じレポートスイートで管理されるすべての Web ページに ID サービスを導入した後に、猶予期間を停止します。

**s_vi Cookie の要件**

新しい訪問者が ID サービスへの移行後に s_vi Cookie を使用する必要がある場合、猶予期間が必要です。この状況は、実装で s_vi Cookie を読み取って変数に保存している場合に一般的です。

実装で s_vi Cookie を読み取る代わりに MID を取得できるようになった後に、猶予期間を停止します。

[cookieとExperience Cloud IDサービス](../introduction/cookies.md)を参照してください。

クリックストリームデータフィードから内部システムにデータを送信していて、そのプロセスで `visid_high` 列と `visid_low` 列を使用している場合、猶予期間が必要です。

Discontinue the grace period after your data ingestion process can use the `post_visid_high` and `post_visid_low` columns.

[クリックストリームデータ列リファレンス](https://marketing.adobe.com/resources/help/en_US/sc/clickstream/datafeeds_reference.html)を参照してください。

**クリックストリームデータ収集**

## Step 8: Test and deploy ID Service code {#section-e9c1764ac21a4ec5be1ff338c0e2e01b}

次のようにテストおよびデプロイできます。

**テストと確認**

ID サービスの導入状況をテストするには、以下の項目を確認します。

* [AMCV cookie](../introduction/cookies.md)（ページがホストされているドメイン内）
* [!DNL Analytics] イメージリクエストの MID 値（[Adobe Debugger ツール](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html)を使用）

See, [Test and Verify the Experience Cloud ID Service](../implementation-guides/test-verify.md).

**コードの導入**

テストの合格後に、コードを導入します。

[手順 7](../implementation-guides/setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3) で猶予期間を有効にした場合：

* [!DNL Analytics] ID（AID）と MID がイメージリクエストに含まれていることを確認します。
* 停止条件が満たされたら、必ず猶予期間を無効にします。
