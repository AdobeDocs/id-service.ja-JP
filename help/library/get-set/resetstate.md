---
description: この機能は、単一ページのサイト／画面またはアプリでの ID の使用に関連する問題を解決するために、主に A4T のお客様向けに設計されています。
keywords: ID サービス
title: resetState
exl-id: 8e8cb299-bb89-4bc1-8841-3091ce0cbd81
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 100%

---

# resetState{#resetstate}

この機能は、単一ページのサイト／画面またはアプリでの ID の使用に関連する問題を解決するために、主に A4T のお客様向けに設計されています。

## ユースケース {#section-840b88a5cdb042488b340cad5d7b22a5}

ID サービスを利用している A4T のお客様の場合、以下をおこなう必要があるときには `visitor.resetState()` 関数を使用することが推奨されます。

* リダイレクトを使用して、補助的なデータ ID（SDID）またはその他の任意の ID を 1 つのページまたは画面から別のページに渡す。 通常、この関数がなければ、ID サービスはこの ID を渡しません。
* Ajax 呼び出しを通じてページまたはアプリの特定のセクションのみを更新するコードを使用し、それらのアクションを追跡する必要がある。 例えば、オブジェクトをクリックすると、特別なセクションのみが読み込まれたり変更されたりするページがあるとします。 この場合、ID サービスは、ページが再読み込みされない限り、別の ID をリクエストできません。 しかし、`visitor.resetState()` を使用すると、この条件でも新しい ID をリクエストできます。

以下のコードサンプルを参照してください。

## 構文 {#section-9e63503e178f4be28ac850abf44d6d91}

**構文：** ` visitor.resetState( *`state`*);`

## コードサンプル {#section-d75b211bb4ea473887eb284de2ad838b}

ID サービスの実装によって、この関数の使用方法が変わります。 例については、以下の表を参照してください。

**サーバー側実装**

サーバー側実装は、[!DNL Analytics]、[!DNL Target]、および ID サービスのサーバーおよびクライアント側実装を使用する A4T のお客様向けです。この方法で ID サービスを設定した場合は、ページに `visitor.resetState()` を追加するだけでかまいません。ID サービスの呼び出しにより自動的に新しい ID とサーバーの状態が返されます。

**非標準的な実装**（ID を渡す場合）

ID サービスを[非標準的な実装](../../implementation-guides/implementation-guides.md#section-2c4f2db1f9704315a7cccab6d2e07113)で設定した場合、`visitor.resetState()` と共に渡す SDID（またはその他の ID）を保持するための可変オブジェクトを設定する必要があります。以下に示すように、これには[組織 ID](../../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26) と、渡す ID が含まれます。コードは、以下の例のようになります。

```js
//Instantiate server state variable 
var serverState = { 
     "Insert Experience Cloud organization ID here": { 
          //Specify the SDID or other ID 
          supplementalDataIDCurrent: "1234", 
          supplementalDataIDCurrentConsumed: { 
               "payload:top-center": false 
          } 
     } 
}; 
 
//Instantiate ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here", { 
     ... 
}); 
 
//Reset server state to pass the SDID 
visitor.resetState(serverState);
```

**非標準的な実装**（ID を渡さない場合）

この場合は、`visitor.resetState()` を使用して新しい ID を生成できます。これは、単一ページアプリで、ユーザーがページを更新せずに新しい画面に移動して新しい ID が必要になる場合に役に立ちます。

```js
 
//Instantiate ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here", { 
     ... 
}); 
 
//Request a supplemental Data ID for consumer1 and consumer2: 
var sdid1 = visitor.getSupplementalDataID("consumer1"); // sdid1: 1234 
var sdid2 = visitor.getSupplementalDataID("consumer2"); // sdid2: 1234 
 
//User navigates to a new screen in a single-page app, without refreshing the page. 
//To reset the Supplemental Data ID internal, call resetState without passing any parameters. 
//This way we will not be recycling the `1234` ID anymore. Instead Visitor will generate a new supplemental Data ID going forward. 
visitor.resetState(); 
 
//Request a supplemental Data ID for consumer3 and consumer4: 
var sdid1 = visitor.getSupplementalDataID("consumer3"); // sdid1: 5678 
 
var sdid2 = visitor.getSupplementalDataID("consumer4"); // sdid2: 5678
```

**Dynamic Tag Manager（DTM）**

現在、`visitor.resetState()` を DTM で使用するための設定方法はありません。
