---
description: これらの手順は、Experience Cloud ID サービスを使用し、Dynamic Tag Management（DTM）を使用しない Analytics および Audience Manager のお客様向けです。ただし、ID サービスの実装に DTM を使用することを強くお勧めします。DTM は、実装ワークフローを合理化し、適切なコード配置と優先順位付けを自動的に確認します。
keywords: ID サービス
seo-description: これらの手順は、Experience Cloud ID サービスを使用し、Dynamic Tag Management（DTM）を使用しない Analytics および Audience Manager のお客様向けです。ただし、ID サービスの実装に DTM を使用することを強くお勧めします。DTM は、実装ワークフローを合理化し、適切なコード配置と優先順位付けを自動的に確認します。
seo-title: Experience Cloud ID サービスの Analytics および Audience Manager への実装
title: Experience Cloud ID サービスの Analytics および Audience Manager への実装
uuid: d46050ae-87de-46cc-911b- d6346c7fd511
translation-type: tm+mt
source-git-commit: 4dc668afd37cd1d6f9104adb1b102f1dd4c5746e

---


# Experience Cloud ID サービスの Analytics および Audience Manager への実装{#implement-the-experience-cloud-id-service-for-analytics-and-audience-manager}

これらの手順は、Experience Cloud ID サービスを使用し、Dynamic Tag Management（DTM）を使用しない Analytics および Audience Manager のお客様向けです。ただし、ID サービスの実装に DTM を使用することを強くお勧めします。DTM は、実装ワークフローを合理化し、適切なコード配置と優先順位付けを自動的に確認します。

>[!IMPORTANT]
>
>* [始める前に、要件を確認してください](../mcvid-reference/mcvid-requirements.md)。
>* この手順には、AppMeasurement が必要です。s_code を使用するお客様は、この手順を完了できません。
>* このコードを本番環境に実装する前に、開発環境で設定してテストしてください。
>



## 手順1:サーバー側転送の計画 {#section-880797cc992d4755b29cada7b831f1fc}

ここで説明する手順に加えて、[!DNL Analytics] および [!DNL Audience Manager] を使用するお客様は、サーバー側転送に移行する必要があります。サーバー側転送を使用すると、DIL（Audience Manager のデータ収集コード）を削除して、[Audience Management モジュール](https://marketing.adobe.com/resources/help/en_US/aam/c_profiles_audiences.html)に置き換えることができます。詳しくは、[サーバー側転送のドキュメント](https://marketing.adobe.com/resources/help/en_US/analytics/audiences/ssf.html)を参照してください。

サーバー側転送への移行には、計画と調整が必要です。この手順には、サイトコードに対する外部の変更と、アカウントをプロビジョニングするためにアドビが取る必要のある内部手順が関係します。実際、これらの移行手順の多くは、並行しておこない、同時にリリースする必要があります。実装パスは、このイベントの順番に従う必要があります。

1. [!DNL Analytics] と [!DNL Audience Manager] の連絡先を使用して、ID サービスおよびサーバー側転送の移行を計画します。この計画で重要な部分である、トラッキングサーバーを選択します。

1. プロビジョニングを取得 [!DNL Profiles & Audiences]します。開始するには、[統合およびプロビジョニングサイト](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=X8SVES)のフォームを完成させます。

1. IDサービスと [!DNL Audience Management Module] 同時にIDサービスを実装します。適切に動作させるには [!DNL Audience Management Module] 、（サーバー側転送）とIDサービスを同じページのセットに対してリリースする必要があります。

## 手順2:IDサービスコードのダウンロード {#section-0780126cf43e4ad9b6fc5fe17bb3ef86}

ID サービスでは、`VisitorAPI.js` コードライブラリが必要です。このコードライブラリをダウンロードするには：

1. **[!UICONTROL 管理]** 者/ **[!UICONTROL コードマネージャー]** に移動します。

1. In Code Manager, click either **[!UICONTROL JavaScrpt (New)]** or **[!UICONTROL JavaScript (Legacy)]**. 圧縮されたコードライブラリがダウンロードされます。

1. コードファイルを解凍し、`VisitorAPI.js` ファイルを開きます。

## 手順3:IDサービスコードにVisitor. getInstance関数を追加します {#section-9e30838b4d0741658a7a492153c49f27}

>[!IMPORTANT]
>
>* ID サービス API の過去のバージョンでは、この関数を別の場所に別の構文で配置する必要がありました。[version 1.4](../mcvid-release-notes/mcvid-notes-2015.md#section-f5c596f355b14da28f45c798df513572) より前のバージョンから移行する場合は、ここで説明する新しい場所と構文について注意してください。
>* すべて大文字で書かれたコードは、実際の値のプレースホルダーです。このテキストを組織 ID、トラッキングサーバー URL、またはその他の指定された値に置き換えます。
>



**パート 1：以下の Visitor.getInstance 関数をコピーします**

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

**パート 2：Visitor API.js ファイルに関数コードを追加します**

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

## 手順4:Visitor. getInstanceにExperience Cloud組織IDを追加します {#section-e2947313492546789b0c3b2fc3e897d8}

`Visitor.getInstance` 関数で、Experience Cloud組織ID `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` に置き換えます。組織 ID がわからない場合、Experience Cloud 管理ページで確認できます。編集後の関数は、以下のサンプルのようになります。

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg", { ...`

>[!IMPORTANT]
>
>*組織ID内の文字の大文字小文字は* 変更しないでください。この ID は大文字小文字が区別され、割り当てられたとおりに使用する必要があります。

## 手順5:Visitor. getInstanceにトラッキングサーバーを追加します {#section-0dfc52096ac2427f86045aab9a0e0dfc}

Analytics は、データ収集にトラッキングサーバーを使用します。

**パート 1：トラッキングサーバー URL の確認**

トラッキング `s_code.js` サーバーURLを確認するには `AppMeasurement.js` 、またはファイルを確認してください。この URL に以下の変数を指定します。

* `s.trackingServer`
* `s.trackingServerSecure`

**パート 2：トラッキングサーバー変数の設定**

使用するトラッキングサーバー変数を判断するには：

1. 以下の判断マトリックスの質問に答えます。自分の答えに合う変数を使用します。
1. トラッキングサーバーのプレースホルダーをトラッキングサーバー URL に置き換えます。
1. 未使用のトラッキングサーバーおよび Experience Cloud サーバーの変数をコードから削除します。

![](assets/tracking-server-matrix.png)

>[!NOTE]
>
>使用する場合、Experience CloudサーバーのURLは、次のような対応するトラッキングサーバーURLに一致します。

* Experience Cloud サーバー URL = トラッキングサーバー URL
* Experience Cloud サーバーセキュア URL = トラッキングサーバーセキュア URL

トラッキングサーバーの見つけ方が分からない場合は、[FAQ](../mcvid-faq-intro/mcvid-faq.md) および [trackingServer 変数と trackingServerSecure 変数の適切な設定](https://helpx.adobe.com/analytics/kb/determining-data-center.html#)を参照してください。

## 手順6:AppMeasurement. jsファイルの更新 {#section-5517e94a09bc44dfb492ebca14b43048}

この手順 [!DNL AppMeasurement]は必須です。s_code を使用している場合、続行できません。

以下に示す `Visitor.getInstance` 関数を `AppMeasurement.js` ファイルに追加します。次のような設定を含むセクションに配置 `linkInternalFilters``charSet``trackDownloads`します。

`s.visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");`

>[!IMPORTANT]
>
>この時点で [!DNL Audience Manager] 、DILコードを削除して、Audience Managementモジュールに置き換える必要があります。手順については、[サーバー側転送の実装](https://marketing.adobe.com/resources/help/en_US/reference/ssf.html)を参照してください。

****（オプション、推奨）カスタム prop の作成**

有効範囲を測定するために `AppMeasurement.js` にカスタム prop を設定します。このカスタム prop を `doPlugins` ファイルの `AppMeasurement.js` 関数に追加します。

```js
// prop1 is used as an example only. Choose any available prop. 
s.prop1 = (typeof(Visitor) != "undefined" ? "VisitorAPI Present" : "VisitorAPI Missing");
```

## 手順7:ページへの訪問者APIコードの追加 {#section-c2bd096a3e484872a72967b6468d3673}

各ページのタグ内に ` [!DNL VisitorAPI.js]` ファイル `<head>` を配置します。`VisitorAPI.js` ファイルをページに配置する際には、以下のようにします。

* 他のソリューションタグの前に `<head>` セクションの先頭に配置します。
* AppMeasurement およびその他の [!DNL Experience Cloud] ソリューションのコードより前に実行する必要があります。

## 手順8:（オプション）猶予期間の設定 {#section-aceacdb7d5794f25ac6ff46f82e148e1}

これらの使用例のいずれかが状況に該当する場合は、 [カスタマーケア](https://helpx.adobe.com/marketing-cloud/contact-support.html) に問い合わせて一時 [的な猶予期間](../mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md)を設定してください。猶予期間は最大 180 日間有効です。必要に応じて、猶予期間を更新できます。

**部分的実装**

ID サービスを使用するページと使用しないページが混在し、そのすべてのページが同じ Analytics レポートスイートで管理される場合は、猶予期間が必要です。この状況は、複数のドメインで管理されるグローバルなレポートスイートがある場合に一般的です。

同じレポートスイートで管理されるすべての Web ページに ID サービスを導入した後に、猶予期間を停止します。

**s_vi Cookie の要件**

新しい訪問者が ID サービスへの移行後に s_vi Cookie を使用する必要がある場合、猶予期間が必要です。この状況は、実装で s_vi Cookie を読み取って変数に保存している場合に一般的です。

実装で s_vi Cookie を読み取る代わりに MID を取得できるようになった後に、猶予期間を停止します。

[cookieとExperience Cloud IDサービス](../mcvid-introduction/mcvid-cookies.md)も参照してください。

**クリックストリームデータの統合**

クリックストリームデータフィードから内部システムにデータを送信していて、そのプロセスで `visid_high` 列と `visid_low` 列を使用している場合、猶予期間が必要です。

データ収集プロセスでおよび `post_visid_high``post_visid_low` 列を使用できるようになった後、猶予期間を停止します。

[クリックストリームデータ列リファレンス](https://marketing.adobe.com/resources/help/en_US/sc/clickstream/datafeeds_reference.html)も参照してください。

## 手順9:IDサービスコードのテストと導入 {#section-f857542bfc70496dbb9f318d6b3ae110}

次のようにテストおよびデプロイできます。

**テストと確認**

ID サービスの実装状況をテストするには、以下の項目を確認します。

* [AMCV Cookie](../mcvid-introduction/mcvid-cookies.md)（ページがホストされているドメイン内）
* Analytics イメージリクエストの MID 値（[Adobe Debugger](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html) を使用）
* Experience Cloud IDサービスの [テストと検証](../mcvid-implementation-guides/mcvid-test-verify.md)も参照してください。

サーバー側転送を検証するには、[サーバー側転送の実装の確認方法](https://marketing.adobe.com/resources/help/en_US/reference/ssf-verify.html)を参照してください。

**導入**

テストの合格後に、コードを導入します。

猶予期間を有効にしている場合：

* Analytics ID（AID）と MID がイメージリクエストに含まれていることを確認します。
* 停止条件が満たされたら、必ず猶予期間を無効にします。

