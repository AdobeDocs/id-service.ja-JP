---
description: 次の説明は、Experience Cloud ID サービスを使用し、データ収集タグを使用しない Analytics のお客様を対象としています。ただし、タグを使用して ID サービスを実装することを強くお勧めします。タグは、実装ワークフローを効率化し、適切なコードの配置とシーケンスを自動的に保証します。
keywords: ID サービス
title: Experience Cloud Identity Service の Analytics への実装
exl-id: c0271e49-32e5-49ee-bb11-548751ccafad
source-git-commit: 792fb5d5192843f345577a99b6179fb6d95fedc0
workflow-type: ht
source-wordcount: '1007'
ht-degree: 100%

---

# Experience Cloud Identity Service の Analytics への実装 {#implement-the-experience-cloud-id-service-for-analytics}

次の説明は、Experience Cloud ID サービスを使用し、[データ収集タグ](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=ja)を使用しない Analytics のお客様を対象としています。ただし、タグを使用して ID サービスを実装することを強くお勧めします。タグは、実装ワークフローを効率化し、適切なコードの配置とシーケンスを自動的に保証します。

>[!IMPORTANT]
>
>* [始める前に、要件を確認してください](../reference/requirements.md)。
>* このコードを本番環境に実装する前に、開発環境で設定してテストしてください。

次の手順に従い、Adobe Analytics 用 ID サービスを実装します。

1. [ID サービスコードのダウンロード](../implementation-guides/setup-analytics.md#section-ead9403a6b7e45b887f9ac959ef89f7f)
1. [ID サービスコードへの Visitor.getInstance 関数の追加](../implementation-guides/setup-analytics.md#section-6053a6b7c16c466a9f9fdbf9cb9db3df)
1. [Visitor.getInstance への Experience Cloud 組織 ID の追加](../implementation-guides/setup-analytics.md#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e)
1. [Visitor.getInstance へのトラッキングサーバーの追加](../implementation-guides/setup-analytics.md#section-70ec9ebff47940d8ab520be5ec4728c5)
1. [AppMeasurement.js または s_code.js ファイルの更新](../implementation-guides/setup-analytics.md#section-b53113aea1bd4de896e0e4e9a7edee19)
1. [ページへの訪問者 API コードの追加](../implementation-guides/setup-analytics.md#section-d46d6aa324c842f2931d901e38d6db1d)
1. [（オプション）猶予期間の設定](../implementation-guides/setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3)
1. [ID サービスコードのテストとデプロイ](../implementation-guides/setup-analytics.md#section-e9c1764ac21a4ec5be1ff338c0e2e01b)

## 手順 1：ID サービスコードのダウンロード {#section-ead9403a6b7e45b887f9ac959ef89f7f}

[!UICONTROL ID サービス]では、`VisitorAPI.js` コードライブラリが必要です。このコードライブラリをダウンロードするには：

1. **[!UICONTROL 管理]**／**[!UICONTROL Code Manager]** に移動します。
1. [!UICONTROL Code Manager] で、「**[!UICONTROL JavaScript (新規)]**」または「**[!UICONTROL JavaScript (レガシー)]**」をクリックします。

   圧縮されたコードライブラリがダウンロードされます。

1. コードファイルを解凍し、`VisitorAPI.js` ファイルを開きます。

## 手順 2：ID サービスコードへの Visitor.getInstance 関数の追加 {#section-6053a6b7c16c466a9f9fdbf9cb9db3df}

>[!IMPORTANT]
>
>* 以前のバージョンの ID サービス API では、この関数を別の場所に別の構文で配置する必要がありました。[バージョン 1.4](../release-notes/notes-2015.md#section-f5c596f355b14da28f45c798df513572) より前のバージョンから移行する場合は、ここで説明する新しい場所と構文について注意してください。
>* すべて大文字で書かれたコードは、実際の値用のプレースホルダーです。このテキストを組織 ID、トラッキングサーバー URL、またはその他の指定された値に置き換えます。

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

## 手順 3：Visitor.getInstance への Experience Cloud 組織 ID の追加 {#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e}

`Visitor.getInstance` 関数の `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` を [!DNL Experience Cloud] 組織 ID に置き換えます。組織 ID がわからない場合、[!DNL Experience Cloud] 管理ページで確認できます。[管理 - コアサービス](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/admin-getting-started.html?lang=ja)も参照してください。編集後の関数は、以下のサンプルのようになります。

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg", { ...`

>[!IMPORTANT]
>
>組織 ID の大文字小文字を変更&#x200B;*しない*&#x200B;でください。この ID は大文字小文字が区別され、割り当てられたとおりに使用する必要があります。

## 手順 4：Visitor.getInstance へのトラッキングサーバーの追加 {#section-70ec9ebff47940d8ab520be5ec4728c5}

トラッキングサーバーは、[!DNL Analytics] データ収集に使用されます。

**パート 1：トラッキングサーバー URL の確認**

`s_code.js` ファイルまたは `AppMeasurement.js` ファイルでトラッキングサーバー URL を確認します。この URL に以下の変数を指定します。

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
>使用されている場合は、以下のように [!DNL Experience Cloud] サーバーの URL をトラッキングサーバーの URL に対応させます。
>
>* [!DNL Experience Cloud] サーバー URL = トラッキングサーバー URL
>* [!DNL Experience Cloud] サーバーセキュア URL = トラッキングサーバーセキュア URL

トラッキングサーバーの見つけ方がわからない場合は、[FAQ](../faq-intro/faq.md) と [trackingServer および trackingServerSecure 変数の適切な設定](https://helpx.adobe.com/jp/analytics/kb/determining-data-center.html#)を参照してください。

## 手順 5：AppMeasurement.js または s_code.js ファイルの更新 {#section-b53113aea1bd4de896e0e4e9a7edee19}

`AppMeasurement.js` または `s_code.js` ファイルにこの関数を追加します。

`s.visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");`

`linkInternalFilters`、`charSet`、`trackDownloads` などの設定を含むセクションにこのコードを配置します。

***（オプション、推奨）* カスタム prop の作成。**

有効範囲を測定するために `AppMeasurement.js` または `s_code.js` にカスタム prop を設定します。このカスタム prop を `doPlugins` ファイルまたは `AppMeasurement.js` ファイルの `s_code.js` 関数に追加します。

```js
// prop1 is used as an example only. Choose any available prop. 
s.prop1 = (typeof(Visitor) != "undefined" ? "VisitorAPI Present" : "VisitorAPI Missing");
```

## 手順 6：ページへの Visitor API コードの追加 {#section-d46d6aa324c842f2931d901e38d6db1d}

`VisitorAPI.js` ファイルを各ページの `<head>` タグ内に配置します。`VisitorAPI.js` ファイルをページに配置する際には、以下のようにします。

* タグは `<head>` セクションの先頭に配置して、他のソリューションタグより先に表示させます。
* AppMeasurement およびその他の [!DNL Experience Cloud] ソリューションのコードより前に実行する必要があります。

テストと検証の後にこのコードを本番に移行します。

## 手順 7：（オプション）猶予期間の設定 {#section-7bbb2f72c26e4abeb8881e18366797a3}

これらの使用例のいずれかがお客様の状況に当てはまる場合は、[カスタマーケア](https://helpx.adobe.com/jp/marketing-cloud/contact-support.html)までお問い合わせいただき、一時的な[猶予期間](../reference/analytics-reference/grace-period.md)を設定するよう依頼してください。猶予期間は最大 180 日です。必要に応じて、猶予期間を更新できます。

**部分的実装**

ID サービスを使用するページと使用しないページが混在し、そのすべてのページが同じ [!DNL Analytics] レポートスイートで管理される場合は、猶予期間が必要です。この状況は、複数のドメインで管理されるグローバルなレポートスイートがある場合に一般的です。

同じレポートスイートで管理されるすべての Web ページに ID サービスをデプロイした後に、猶予期間を停止します。

**s_vi Cookie の要件**

新しい訪問者が ID サービスへの移行後に s_vi Cookie を使用する必要がある場合、猶予期間が必要です。この状況は、実装で s_vi Cookie を読み取って変数に保存している場合に一般的です。

実装で s_vi Cookie を読み取る代わりに MID を取得できるようになった後に、猶予期間を停止します。

[Cookie と Experience Cloud Identity Service](../introduction/cookies.md) を参照してください。

クリックストリームデータフィードから内部システムにデータを送信していて、そのプロセスで `visid_high` 列と `visid_low` 列を使用している場合、猶予期間が必要です。

データ収集プロセスで `post_visid_high` 列と `post_visid_low` 列を使用できるようになった後で、猶予期間を停止します。

[クリックストリームデータ列リファレンス](https://experienceleague.adobe.com/docs/analytics/export/analytics-data-feed/data-feed-overview.html?lang=ja)を参照してください。

**クリックストリームデータの取り込み**

## 手順 8：ID サービスコードのテストとデプロイ {#section-e9c1764ac21a4ec5be1ff338c0e2e01b}

次のようにテストおよびデプロイできます。

**テストと検証**

ID サービスの実装状況をテストするには、以下の項目を確認します。

* [AMCV cookie](../introduction/cookies.md)（ページがホストされているドメイン内）
* [!DNL Analytics] イメージリクエストの MID 値（[Adobe Debugger ツール](https://experienceleague.adobe.com/docs/analytics/implementation/validate/debugger.html?lang=ja)を使用）

詳しくは、[Experience Cloud Identity Service のテストと検証](../implementation-guides/test-verify.md)を参照してください。

**コードのデプロイ**

テストの合格後に、コードをデプロイします。

[手順 7](../implementation-guides/setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3) で猶予期間を有効にした場合：

* [!DNL Analytics] ID（AID）と MID がイメージリクエストに含まれていることを確認します。
* 停止条件が満たされたら、必ず猶予期間を無効にします。
