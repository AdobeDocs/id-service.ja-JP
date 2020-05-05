---
description: これらの手順は、Experience Cloud Identity Service を使用し、Dynamic Tag Management（DTM）を使用しない Analytics および Audience Manager のお客様向けです。ただし、IDサービスの実装にはDTMを使用することを強くお勧めします。 DTMは、実装ワークフローを合理化し、適切なコード配置と順序付けを自動的に確認します。
keywords: ID Service
seo-description: これらの手順は、Experience Cloud Identity Service を使用し、Dynamic Tag Management（DTM）を使用しない Analytics および Audience Manager のお客様向けです。ただし、IDサービスの実装にはDTMを使用することを強くお勧めします。 DTMは、実装ワークフローを合理化し、適切なコード配置と順序付けを自動的に確認します。
seo-title: Experience Cloud Identity Service の Analytics および Audience Manager への実装
title: Experience Cloud Identity Service の Analytics および Audience Manager への実装
uuid: d46050ae-87de-46cc-911b-d6346c7fd511
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# Experience Cloud Identity Service の Analytics および Audience Manager への実装{#implement-the-experience-cloud-id-service-for-analytics-and-audience-manager}

これらの手順は、Experience Cloud Identity Service を使用し、Dynamic Tag Management（DTM）を使用しない Analytics および Audience Manager のお客様向けです。ただし、IDサービスの実装にはDTMを使用することを強くお勧めします。 DTMは、実装ワークフローを合理化し、適切なコード配置と順序付けを自動的に確認します。

>[!IMPORTANT]
>
>* [始める前に、要件を確認してください](../reference/requirements.md)。
>* この手順にはAppMeasurementが必要です。 s_codeを使用するお客様は、この手順を完了できません。
>* このコードを本番環境に実装する前に、開発環境で設定してテストしてください。
>



## 手順 1：サーバー側転送の計画 {#section-880797cc992d4755b29cada7b831f1fc}

ここで説明する手順に加えて、[!DNL Analytics] および [!DNL Audience Manager] を使用するお客様は、サーバー側転送に移行する必要があります。サーバー側転送を使用すると、DIL(オーディエンスマネージャーのデータ収集コード)を削除し、 [オーディエンス管理モジュール](https://docs.adobe.com/content/help/en/audience-manager/user-guide/implementation-integration-guides/integration-other-solutions/audience-management-module.html)(DIL)に置き換えることができます。 See the [server-side forwarding documentation](https://docs.adobe.com/content/help/ja-JP/analytics/admin/admin-tools/server-side-forwarding/ssf.html) for more information.

サーバー側転送への移行には、計画と調整が必要です。 このプロセスには、サイトコードに対する外部の変更と、アカウントのプロビジョニングにアドビが行う必要のある内部手順が含まれます。 実際、これらの移行手順の多くは、並行して実行され、同時にリリースされる必要があります。 導入パスは、次のイベントのシーケンスに従う必要があります。

1. [!DNL Analytics] と [!DNL Audience Manager] の連絡先を使用して、ID サービスおよびサーバー側転送の移行を計画します。この計画で重要な部分である、トラッキングサーバーを選択します。

1. Complete the form on the [integrations and provisioning site](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=X8SVES) to get started.

1. ID サービスと [!DNL Audience Management Module] を同時に実装します。適切に動作させるには、[!DNL Audience Management Module]（サーバー側転送）および ID サービスがページの同じセットに同時にリリースされる必要があります。

## 手順 2：ID サービスコードのダウンロード {#section-0780126cf43e4ad9b6fc5fe17bb3ef86}

ID サービスでは、`VisitorAPI.js` コードライブラリが必要です。このコードライブラリをダウンロードするには：

1. **[!UICONTROL 管理者]** / **[!UICONTROL コードマネージャーに移動します]**。

1. コードマネージャーで、「**[!UICONTROL JavaScript (新規)]**」または「**[!UICONTROL JavaScript (レガシー)]**」をクリックします。圧縮されたコードライブラリがダウンロードされます。

1. コードファイルを解凍し、`VisitorAPI.js` ファイルを開きます。

## 手順 3：ID サービスコードへの Visitor.getInstance 関数の追加 {#section-9e30838b4d0741658a7a492153c49f27}

>[!IMPORTANT]
>
>* 以前のバージョンのIDサービスAPIでは、この関数を別の場所に別の構文で配置する必要がありました。 バージョン1.4より前のバージョンから移行する場合は、 [ここで説明する新しい場所と構文に注意してください](../release-notes/notes-2015.md#section-f5c596f355b14da28f45c798df513572)。
>* すべて大文字のコードは、実際の値のプレースホルダです。 このテキストを組織ID、トラッキングサーバーURL、またはその他の指定された値に置き換えます。
>



**パート1: 以下の訪問者.getInstance関数をコピーします**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
}); 
```

**パート2: 関数追加コードを訪問者API.jsファイルに**

`Visitor.getInstance` 関数をファイル末尾のコードブロックの後に配置します。編集後のファイルは以下のようになります。

```js
/* 
========== DO NOT ALTER ANYTHING BELOW THIS LINE ========== 
Version and copyright section 
*/ 
 
// Visitor API code library section 
 
// Put Visitor.getInstance at the end of the file, after the code library 
 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
}); 
```

## 手順 4：Visitor.getInstance への Experience Cloud 組織 ID の追加 {#section-e2947313492546789b0c3b2fc3e897d8}

`Visitor.getInstance` 関数の `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` を Experience Cloud 組織 ID に置き換えます。組織IDがわからない場合は、Experience Cloud管理ページで確認できます。 編集後の関数は、以下のサンプルのようになります。

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg", { ...`

>[!IMPORTANT]
>
>組織 ID の大文字小文字を変更&#x200B;*しない*&#x200B;でください。この ID は大文字小文字が区別され、割り当てられたとおりに使用する必要があります。

## 手順 5：Visitor.getInstance へのトラッキングサーバーの追加 {#section-0dfc52096ac2427f86045aab9a0e0dfc}

Analyticsでは、データ収集にトラッキングサーバーを使用します。

**パート 1：トラッキングサーバー URL の確認**

`s_code.js` ファイルまたは `AppMeasurement.js` ファイルでトラッキングサーバー URL を確認します。この URL に以下の変数を指定します。

* `s.trackingServer`
* `s.trackingServerSecure`

**パート2: トラッキングサーバー変数の設定**

使用するトラッキングサーバー変数を決定するには：

1. 以下の判断マトリックスの質問に答えます。 回答に対応する変数を使用します。
1. トラッキングサーバーのプレースホルダーをトラッキングサーバーのURLに置き換えます。
1. 未使用のトラッキングサーバー変数とExperience Cloudサーバー変数をコードから削除します。

![](assets/tracking-server-matrix.png)

>[!NOTE]
>
>使用されている場合は、以下のように Experience Cloud サーバーの URL をトラッキングサーバーの URL に対応させます。

* Experience CloudサーバーURL =トラッキングサーバーURL
* Experience CloudサーバーセキュアURL =トラッキングサーバーセキュアURL

トラッキングサーバーの見つけ方が分からない場合は、[FAQ](../faq-intro/faq.md) と [trackingServer および trackingServerSecure 変数の適切な設定](https://helpx.adobe.com/jp/analytics/kb/determining-data-center.html#)を参照してください。

## 手順 6：AppMeasurement.js ファイルの更新 {#section-5517e94a09bc44dfb492ebca14b43048}

This step requires [!UICONTROL AppMeasurement]. s_code を使用している場合、続行できません。

以下に示す `Visitor.getInstance` 関数を `AppMeasurement.js` ファイルに追加します。`linkInternalFilters`、`charSet`、`trackDownloads` などの設定を含むセクションに配置します。

`s.visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");`

>[!IMPORTANT]
>
>この時点で、[!DNL Audience Manager] DIL コードを削除して、Audience Management モジュールに置き換える必要があります。手順については、「サーバー側転送の [実装](https://docs.adobe.com/content/help/ja-JP/analytics/admin/admin-tools/server-side-forwarding/ssf.html) 」を参照してください。

***（オプション、推奨）*カスタム prop の作成&#x200B;****

有効範囲を測定するために `AppMeasurement.js` にカスタム prop を設定します。このカスタム prop を `doPlugins` ファイルの `AppMeasurement.js` 関数に追加します。

```js
// prop1 is used as an example only. Choose any available prop. 
s.prop1 = (typeof(Visitor) != "undefined" ? "VisitorAPI Present" : "VisitorAPI Missing");
```

## 手順 7：ページへの訪問者 API コードの追加 {#section-c2bd096a3e484872a72967b6468d3673}

` [!UICONTROL VisitorAPI.js]` ファイルを各ページの `<head>` タグ内に配置します。`VisitorAPI.js` ファイルをページに配置する際には、以下のようにします。

* タグは `<head>` セクションの先頭に配置して、他のソリューションタグより先に表示させます。
* AppMeasurement およびその他の [!DNL Experience Cloud] ソリューションのコードより前に実行する必要があります。

## 手順 8：（オプション）猶予期間の設定 {#section-aceacdb7d5794f25ac6ff46f82e148e1}

If any of these use cases apply to your situation, ask [Customer Care](https://helpx.adobe.com/jp/marketing-cloud/contact-support.html) to set up a temporary [grace period](../reference/analytics-reference/grace-period.md). 猶予期間は180日間まで有効です。 必要に応じて、猶予期間を更新できます。

**部分的実装**

IDサービスを使用するページと使用しないページがあり、それらのページがすべて同じAnalyticsレポートスイートにレポートされる場合は、猶予期間が必要です。 これは、複数のドメインでレポートするグローバルレポートスイートがある場合に一般的です。

同じレポートスイートで管理されるすべての Web ページに ID サービスをデプロイした後に、猶予期間を停止します。

**s_vi cookieの要件**

IDサービスへの移行後に新しい訪問者がs_vi cookieを持つ必要がある場合は、猶予期間が必要です。 これは、実装がs_vi cookieを読み取って変数に保存する場合に一般的です。

実装がs_vi cookieを読み取る代わりにMIDを取り込めるようになった後に、猶予期間を停止します。

詳しくは、[Cookie と Experience Cloud Identity Service](../introduction/cookies.md) を参照してください。

**クリックストリームデータの統合**

クリックストリームデータフィードから内部システムにデータを送信していて、そのプロセスで `visid_high` 列と `visid_low` 列を使用している場合、猶予期間が必要です。

データ収集プロセスで `post_visid_high` 列と `post_visid_low` 列を使用できるようになった後で、猶予期間を停止します。

クリックストリーム [データ列リファレンスも参照](https://docs.adobe.com/content/help/ja-JP/analytics/export/analytics-data-feed/data-feed-overview.html)。

## 手順 9：ID サービスコードのテストとデプロイ {#section-f857542bfc70496dbb9f318d6b3ae110}

次のようにテストおよびデプロイできます。

**テストと検証**

ID サービスの実装状況をテストするには、以下の項目を確認します。

* [AMCV Cookie](../introduction/cookies.md)（ページがホストされているドメイン内）
* AnalyticsイメージリクエストのMID値( [Adobe Debuggerを使用](https://docs.adobe.com/content/help/en/analytics/implementation/validate/debugger.html))。
* 詳しくは、[Experience Cloud Identity Service のテストと検証](../implementation-guides/test-verify.md)を参照してください。

サーバー側転送を検証するには、 [How to Verify Your Server-Side Forwarding Implementation](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/server-side-forwarding/ssf-verify.html)（サーバー側転送の実装を検証する方法）を参照してください。

**デプロイ**

テストの合格後に、コードをデプロイします。

猶予期間を有効にした場合：

* Analytics ID(AID)とMIDがイメージリクエストに含まれていることを確認します。
* 停止条件が満たされたら、必ず猶予期間を無効にします。

