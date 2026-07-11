---
description: これらの手順は、訪問者ID サービスを使用し、タグを使用しないTargetのお客様向けです。 ただし、タグを使用して訪問者ID サービスを実装することを強くお勧めします。 タグは、実装ワークフローを効率化し、適切なコードの配置とシーケンスを自動的に保証します。
keywords: 訪問者 ID サービス
title: Target用Adobe Visitor ID サービスの実装
exl-id: 7a387e98-c8fc-4904-942a-be5e527eada2
TQID: https://experienceleague.adobe.com/1994Y39yotvpJkcYazVnG0w-GupHiZZipnLWSTbgle8
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 430
ht-degree: 47%

---

# Target用Adobe Visitor ID サービスの実装{#implement-the-experience-cloud-id-service-for-target}

この手順は、訪問者ID サービスを使用し、[&#x200B; タグ &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=ja)を使用しないTargetのお客様向けです。 ただし、タグを使用して訪問者ID サービスを実装することを強くお勧めします。 タグは、実装ワークフローを効率化し、適切なコードの配置とシーケンスを自動的に保証します。

>[!IMPORTANT]
>
>* [始める前に、要件を確認してください](../reference/requirements.md)。
>* このコードを本番環境に実装する前に、開発環境で設定してテストしてください。

## 手順1：訪問者ID サービスコードの取得 {#section-b32ba0548aa546a79dd38be59832a53e}

訪問者ID サービスには、`VisitorAPI.js` コードライブラリが必要です。 このコードを入手するには、[カスタマーケア](https://helpx.adobe.com/jp/marketing-cloud/contact-support.html)にお問い合わせください。

## 手順2：訪問者ID サービスコードにVisitor.getInstance関数を追加する {#section-287ef2958e9f43858fe9d630ae519e22}

**パート 1：以下の Visitor.getInstance 関数をコピーします**

```js
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE"); 
```

**パート 2: `VisitorAPI.js` ファイルに関数コードを追加**

`Visitor.getInstance` 関数をファイル末尾のコードブロックの後に配置します。 編集後のファイルは以下のようになります。

```js
/* 
========== DO NOT ALTER ANYTHING BELOW THIS LINE ========== 
Version and copyright section 
*/ 
 
// Visitor API code library section 
 
// Put Visitor.getInstance at the end of the file, after the code library 
 
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE");
```

## ステップ 3: Visitor.getInstanceにIMS組織IDを追加する {#section-522b1877be9243c39b222859b821f0ce}

`Visitor.getInstance`関数で、`INSERT-IMS-ORG-ID-HERE`をIMS組織IDに置き換えます。 IMS組織IDがわからない場合は、CX Enterprise管理ページで確認できます。 [管理 - コアサービス](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/admin-getting-started.html?lang=ja)も参照してください。 編集後の関数は、以下のサンプルのようになります。

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*IMS組織IDの文字の大文字と小文字を変更しないでください。* この ID は大文字小文字が区別され、割り当てられたとおりに使用する必要があります。

## 手順 4：ページへの Visitor API コードの追加 {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

サイトの `VisitorAPI.js` タグ内の、`<head>` ファイルを参照している箇所の前に `mbox.js` ファイルをデプロイします。 訪問者ID サービスは、最初のTarget ネットワーク呼び出しが生成される前に実行する必要があります。 テストと検証の後にこのコードを本番に移行します。

## 手順5：訪問者ID サービスコードのテストとデプロイ {#section-e81ee439bb8a4c2abea43d76f3112e9c}

次のようにテストおよびデプロイできます。

**テストと検証**

訪問者ID サービス実装をテストするには：

* ページがホストされているドメインの AMCV Cookie を確認します。
* Target リクエストに`mboxMCGVID`が表示され、ECIDが含まれていることを確認します。

AMCV CookieとMIDについて詳しくは、[Cookieと訪問者ID サービス &#x200B;](../introduction/cookies.md)を参照してください。

**デプロイ**

テストの合格後に、コードをデプロイします。

