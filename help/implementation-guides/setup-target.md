---
description: これらの手順は、Experience Cloud Identity Service を使用し、Dynamic Tag Management（DTM）を使用しない Target のお客様向けです。ただし、IDサービスの実装にはDTMを使用することを強くお勧めします。 DTMは、実装ワークフローを合理化し、適切なコード配置と順序付けを自動的に確認します。
keywords: ID Service
seo-description: これらの手順は、Experience Cloud Identity Service を使用し、Dynamic Tag Management（DTM）を使用しない Target のお客様向けです。ただし、IDサービスの実装にはDTMを使用することを強くお勧めします。 DTMは、実装ワークフローを合理化し、適切なコード配置と順序付けを自動的に確認します。
seo-title: Experience Cloud Identity Service の Target への実装
title: Experience Cloud Identity Service の Target への実装
uuid: cb3581fa-4c4b-43aa-bb8e-8db85a6a1ef2
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# Experience Cloud Identity Service の Target への実装{#implement-the-experience-cloud-id-service-for-target}

これらの手順は、Experience Cloud Identity Service を使用し、Dynamic Tag Management（DTM）を使用しない Target のお客様向けです。ただし、IDサービスの実装にはDTMを使用することを強くお勧めします。 DTMは、実装ワークフローを合理化し、適切なコード配置と順序付けを自動的に確認します。

>[!IMPORTANT]
>
>* [始める前に、要件を確認してください](../reference/requirements.md)。
>* このコードを本番環境に実装する前に、開発環境で設定してテストしてください。
>



## 手順 1：ID サービスコードの入手 {#section-b32ba0548aa546a79dd38be59832a53e}

[!UICONTROL ID サービス]では、`VisitorAPI.js` コードライブラリが必要です。このコードを取得するには、 [カスタマーケアにお問い合わせください](https://helpx.adobe.com/jp/marketing-cloud/contact-support.html) 。

## 手順 2：ID サービスコードへの Visitor.getInstance 関数の追加 {#section-287ef2958e9f43858fe9d630ae519e22}

**パート1: 以下の訪問者.getInstance関数をコピーします**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE"); 
```

**パート2: 関数追加コードをVisitorAPI.jsファイルに**

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

`Visitor.getInstance` 関数の `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` を [!DNL Experience Cloud] 組織 ID に置き換えます。組織 ID がわからない場合、[!DNL Experience Cloud] 管理ページで確認できます。「 [管理 — コアサービス](https://docs.adobe.com/content/help/ja-JP/core-services/interface/manage-users-and-products/admin-getting-started.html)」も参照してください。 編集後の関数は、以下のサンプルのようになります。

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>組織 ID の大文字小文字を変更&#x200B;*しない*&#x200B;でください。この ID は大文字小文字が区別され、割り当てられたとおりに使用する必要があります。

## 手順 4：ページへの訪問者 API コードの追加 {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

サイトの `VisitorAPI.js` タグ内の、`<head>` ファイルを参照している箇所の前に `mbox.js` ファイルをデプロイします。最初の [!DNL Experience Cloud] ネットワークの呼び出しが生成される前に [!DNL Target] ID サービスを実行する必要があります。テストと検証の後にこのコードを本番に移行します。

## 手順 5：ID サービスコードのテストとデプロイ {#section-e81ee439bb8a4c2abea43d76f3112e9c}

次のようにテストおよびデプロイできます。

**テストと検証**

IDサービスの導入状況をテストするには：

* ページがホストされているドメイン内のAMCV cookieを確認します。
* `mboxMCGVID` が [!DNL Target] のリクエストに存在し、[!DNL Experience Cloud] ID（MID）が含まれていることを確認します。

AMCV Cookie と MID について詳しくは、[Cookie と Experience Cloud Identity Service](../introduction/cookies.md) を参照してください。

**デプロイ**

テストの合格後に、コードをデプロイします。
