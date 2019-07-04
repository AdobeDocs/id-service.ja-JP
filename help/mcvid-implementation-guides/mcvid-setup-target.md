---
description: これらの手順は、Experience Cloud ID サービスを使用し、Dynamic Tag Management（DTM）を使用しない Target のお客様向けです。ただし、ID サービスの実装に DTM を使用することを強くお勧めします。DTM は、実装ワークフローを合理化し、適切なコード配置と優先順位付けを自動的に確認します。
keywords: ID サービス
seo-description: これらの手順は、Experience Cloud ID サービスを使用し、Dynamic Tag Management（DTM）を使用しない Target のお客様向けです。ただし、ID サービスの実装に DTM を使用することを強くお勧めします。DTM は、実装ワークフローを合理化し、適切なコード配置と優先順位付けを自動的に確認します。
seo-title: Experience Cloud ID サービスの Target への実装
title: Experience Cloud ID サービスの Target への実装
uuid: cb3581fa-4c4b-43aa-bb8e-8db85a6a1ef2
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Experience Cloud ID サービスの Target への実装{#implement-the-experience-cloud-id-service-for-target}

これらの手順は、Experience Cloud ID サービスを使用し、Dynamic Tag Management（DTM）を使用しない Target のお客様向けです。ただし、ID サービスの実装に DTM を使用することを強くお勧めします。DTM は、実装ワークフローを合理化し、適切なコード配置と優先順位付けを自動的に確認します。

>[!IMPORTANT]
>
>* [始める前に、要件を確認してください](../mcvid-reference/mcvid-requirements.md)。
>* このコードを本番環境に実装する前に、開発環境で設定してテストしてください。
>



## 手順 1：ID サービスコードの入手 {#section-b32ba0548aa546a79dd38be59832a53e}

[!DNL ID Service] には`VisitorAPI.js` コードライブラリが必要です。このコードを入手するには、[カスタマーケア](https://helpx.adobe.com/jp/marketing-cloud/contact-support.html)にお問い合わせください。

## 手順 2：ID サービスコードへの Visitor.getInstance 関数の追加 {#section-287ef2958e9f43858fe9d630ae519e22}

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

## 手順 3：Visitor.getInstance への Experience Cloud 組織 ID の追加 {#section-522b1877be9243c39b222859b821f0ce}

`Visitor.getInstance` 関数の `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` を [!DNL Experience Cloud] 組織 ID に置き換えます。組織 ID がわからない場合、[!DNL Experience Cloud] 管理ページで確認できます。また、[管理 - コアサービス](https://marketing.adobe.com/resources/help/ja_JP/mcloud/admin_getting_started.html)も参照してください。編集後の関数は、以下のサンプルのようになります。

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>組織 ID の大文字小文字を変更*しない*でください。この ID は大文字小文字が区別され、割り当てられたとおりに使用する必要があります。

## 手順 4：ページへの訪問者 API コードの追加 {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

サイトの `VisitorAPI.js` タグ内の、`<head>` ファイルを参照している箇所の前に `mbox.js` ファイルを導入します。最初の [!DNL Experience Cloud] ネットワークの呼び出しが生成される前に [!DNL Target] ID サービスを実行する必要があります。テストと検証の後にこのコードを本番に移行します。

## 手順 5：ID サービスコードのテストとデプロイ {#section-e81ee439bb8a4c2abea43d76f3112e9c}

次のようにテストおよびデプロイできます。

**テストと検証**

ID サービスの実装状況をテストするには：

* ページがホストされているドメインの AMCV Cookie を確認します。
* `mboxMCGVID` が [!DNL Target] のリクエストに存在し、[!DNL Experience Cloud] ID（MID）が含まれていることを確認します。

AMCV Cookie と MID について詳しくは、[Cookie と Experience Cloud ID サービス](../mcvid-introduction/mcvid-cookies.md)を参照してください。

**導入**

テストの合格後に、コードを導入します。
