---
description: これらの手順は、Experience Platform IDサービスを使用し、Dynamic Tag Management（DTM）を使用しないTargetのお客様向けです。ただし、ID サービスの実装に DTM を使用することを強くお勧めします。DTM は、実装ワークフローを合理化し、適切なコード配置と優先順位付けを自動的に確認します。
keywords: ID サービス
seo-description: これらの手順は、Experience Platform IDサービスを使用し、Dynamic Tag Management（DTM）を使用しないTargetのお客様向けです。ただし、ID サービスの実装に DTM を使用することを強くお勧めします。DTM は、実装ワークフローを合理化し、適切なコード配置と優先順位付けを自動的に確認します。
seo-title: Target向けExperience Platform IDサービスの実装
title: Target向けExperience Platform IDサービスの実装
uuid: cb3581fa-4c4b-43aa- bb8e-8db85a6a1ef2
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Target向けExperience Platform IDサービスの実装{#implement-the-experience-cloud-id-service-for-target}

これらの手順は、Experience Platform IDサービスを使用し、Dynamic Tag Management（DTM）を使用しないTargetのお客様向けです。ただし、ID サービスの実装に DTM を使用することを強くお勧めします。DTM は、実装ワークフローを合理化し、適切なコード配置と優先順位付けを自動的に確認します。

>[!IMPORTANT]
>
>* [始める前に、要件を確認してください](../reference/requirements.md)。
>* このコードを本番環境に実装する前に、開発環境で設定してテストしてください。
>



## 手順1:IDサービスコードの取得 {#section-b32ba0548aa546a79dd38be59832a53e}

コードライブラリが [!DNL ID Service]`VisitorAPI.js` 必要です。このコードを入手するには、[カスタマーケア](https://helpx.adobe.com/marketing-cloud/contact-support.html)にお問い合わせください。

## 手順2:IDサービスコードにVisitor. getInstance関数を追加します {#section-287ef2958e9f43858fe9d630ae519e22}

**パート 1：以下の Visitor.getInstance 関数をコピーします**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE"); 
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
 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");
```

## 手順3:Visitor. getInstanceにExperience Cloud組織IDを追加します {#section-522b1877be9243c39b222859b821f0ce}

`Visitor.getInstance` 関数で、組織ID `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` に置き換え [!DNL Experience Cloud] ます。組織 ID がわからない場合、[!DNL Experience Cloud] 管理ページで確認できます。[管理 - コアサービス](https://marketing.adobe.com/resources/help/en_US/mcloud/admin_getting_started.html)も参照してください。編集後の関数は、以下のサンプルのようになります。

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*組織ID内の文字の大文字小文字は* 変更しないでください。この ID は大文字小文字が区別され、割り当てられたとおりに使用する必要があります。

## 手順4:ページへの訪問者APIコードの追加 {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

ファイルを `VisitorAPI.js` 参照する前に `<head>` 、タグ内のサイトにファイルをデプロイ `mbox.js` します。ID [!DNL Experience Cloud] サービスは、最初 [!DNL Target] のネットワーク呼び出しが生成される前に実行する必要があります。テストと検証の後にこのコードを本番に移行します。

## 手順5:IDサービスコードのテストと導入 {#section-e81ee439bb8a4c2abea43d76f3112e9c}

次のようにテストおよびデプロイできます。

**テストと確認**

ID サービスの実装状況をテストするには：

* ページがホストされているドメインの AMCV Cookie を確認します。
* 検証には検証が `mboxMCGVID` 表示され、 [!DNL Target][!DNL Experience Cloud] ID（MID）が含まれていることが確認されます。

AMCV cookieとMIDについて詳しくは [、cookieとエクスペリエンスプラットフォームIDサービス](../introduction/cookies.md) を参照してください。

**導入**

テストの合格後に、コードを導入します。
