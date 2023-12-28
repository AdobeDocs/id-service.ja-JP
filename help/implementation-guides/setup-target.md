---
description: 次の説明は、Experience Cloud ID サービスを使用し、データ収集タグを使用しない Target のお客様を対象としています。ただし、タグを使用して ID サービスを実装することを強くお勧めします。タグは、実装ワークフローを効率化し、適切なコードの配置とシーケンスを自動的に保証します。
keywords: ID サービス
title: Experience Cloud Identity Service の Target への実装
exl-id: 7a387e98-c8fc-4904-942a-be5e527eada2
source-git-commit: 792fb5d5192843f345577a99b6179fb6d95fedc0
workflow-type: ht
source-wordcount: '398'
ht-degree: 100%

---

# Experience Cloud Identity Service の Target への実装{#implement-the-experience-cloud-id-service-for-target}

次の説明は、Experience Cloud ID サービスを使用し、[データ収集タグ](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=ja)を使用しない Target のお客様を対象としています。ただし、タグを使用して ID サービスを実装することを強くお勧めします。タグは、実装ワークフローを効率化し、適切なコードの配置とシーケンスを自動的に保証します。

>[!IMPORTANT]
>
>* [始める前に、要件を確認してください](../reference/requirements.md)。
>* このコードを本番環境に実装する前に、開発環境で設定してテストしてください。

## 手順 1：ID サービスコードの入手 {#section-b32ba0548aa546a79dd38be59832a53e}

[!UICONTROL ID サービス]では、`VisitorAPI.js` コードライブラリが必要です。このコードを入手するには、[カスタマーケア](https://helpx.adobe.com/jp/marketing-cloud/contact-support.html)にお問い合わせください。

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

`Visitor.getInstance` 関数の `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` を [!DNL Experience Cloud] 組織 ID に置き換えます。組織 ID がわからない場合、[!DNL Experience Cloud] 管理ページで確認できます。[管理 - コアサービス](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/admin-getting-started.html?lang=ja)も参照してください。編集後の関数は、以下のサンプルのようになります。

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>組織 ID の大文字小文字を変更&#x200B;*しない*&#x200B;でください。この ID は大文字小文字が区別され、割り当てられたとおりに使用する必要があります。

## 手順 4：ページへの Visitor API コードの追加 {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

サイトの `VisitorAPI.js` タグ内の、`<head>` ファイルを参照している箇所の前に `mbox.js` ファイルをデプロイします。最初の [!DNL Experience Cloud] ネットワークの呼び出しが生成される前に [!DNL Target] ID サービスを実行する必要があります。テストと検証の後にこのコードを本番に移行します。

## 手順 5：ID サービスコードのテストとデプロイ {#section-e81ee439bb8a4c2abea43d76f3112e9c}

次のようにテストおよびデプロイできます。

**テストと検証**

ID サービスの実装状況をテストするには：

* ページがホストされているドメインの AMCV Cookie を確認します。
* `mboxMCGVID` が [!DNL Target] のリクエストに存在し、[!DNL Experience Cloud] ID（MID）が含まれていることを確認します。

AMCV Cookie と MID について詳しくは、[Cookie と Experience Cloud Identity Service](../introduction/cookies.md) を参照してください。

**デプロイ**

テストの合格後に、コードをデプロイします。
