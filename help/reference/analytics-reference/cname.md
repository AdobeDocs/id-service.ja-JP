---
description: 'null'
keywords: order of operations;ID Service
seo-description: 'null'
seo-title: データ収集 CNAME およびクロスドメイントラッキング
title: データ収集 CNAME およびクロスドメイントラッキング
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: 588c4b29ebd3cccea4f2ab032f69a4b6c6e97f2a

---


# データ収集とID{#data-collection-and-identity}

Analyticsでは、訪問者をID付けする方法が3つあります。

- 訪問者IDサ [ービスの使用](https://docs.adobe.com/content/help/en/id-service/using/home.md)
- 従来のAnalytics [訪問者IDの使用](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/unique-visitors/visid-overview.md)
- 独自のIDを提供する

## Using the Visitor ID Service{#using-the-visitor-id-service}

訪問者IDサービスは、訪問者を識別するための推奨される方法です。 2つのコンポーネントに基づいています

- ファーストパーティID — 自社のWebサイトへの訪問者の測定に使用できるファーストパーティID。 このIDは、最初のパーティIDに格納され、クライアント側のcookieとサーバー側のcookie（CNAME付き）の両方に格納されます。
- サードパーティID（オプション） — demdex.netに保存される別のサードパーティIDで、複数のドメイン（example.comやexample.netなど）での訪問者の測定に使用できます。

Analyticsは常にファーストパーティIDを使用し、サードパーティIDが有効で、各サイトのファーストパーティIDが同じである場合、 ただし、サードパーティIDが設定によって無効になっている場合や、ブラウザーがサードパーティcookieをブロックしている場合は、2つのサイトのトラフィックを相互に関連付ける方法はありません。

## 従来のAnalyticsドメイン

訪問者IDサービスが導入される前、数年前には、多くのお客様がネイティブの分析ドメインを使用してID cookieを設定していました。 これには、 `omtrdc.net`または `2o7.net` CNAMEドメインが含まれます。 `omtrdc.net`、およ `2o7.net` び場合によっては、CNAMEのドメインがサードパーティCookieの保存に使用されます。 この方法で設定されたcookieは、常に1人の顧客に限定され、顧客が複数の会社でデータを組み合わせることができなくなりました。 サードパーティのCNAMEDドメイン（フレンドリーサードパーティドメインとも呼ばれる）は、顧客が所有するサイト(例：com、example.co.jp)でユーザーを追跡する場合にのみ使用します。 この方法は、より堅牢でプライバシーに対応した訪問者IDサービスを可能にするために廃止されています。 お客様は、可能な限り早急に、ドメインごとにCNAMEを持つ訪問者IDサービスに移行する必要があります。

## 自分のIDの入力

顧客がアドビの識別システムを完全にバイパスして、カスタム訪問者IDを指定することで独自の識別システムを実 [装できる](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/unique-visitors/visid-custom.md)。 このルートを選択した場合は、注意が必要な点がいくつかあります。

- オプトアウトおよび適切なプライバシーコントロールを実装する必要があります。
- そのIDはAnalyticsにのみ適用されます
- そのIDを保持する必要があります。

## データ収集CNAMES

アドビでは、訪問者IDサービスと併せてCNAMEを使用することをお勧めします。 これにより、ファーストパーティ訪問者IDがHTTP cookieを使用して保持され、cookieの耐久性が向上します。

## オプトアウト

アドビでは、アドビのシステムとオプトアウトシグナルを共有するAPIを提供しており、ユーザーが追跡をオプトアウトする方法を提供できます。 詳しい説明は、オプトアウトとオプト [インを参照](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/data-collection/opt-out.md)[してください](https://docs.adobe.com/content/help/en/id-service/using/implementation-guides/opt-in-service/optin-overview.md)

## Experience Cloud Identity Service で CNAME サポートを有効にする {#section-25d4feb686d944e3a877d7aad8dbdf9a}

データ収集サーバーのCNAMEサ [ポートは、CNAMEの設定と、Experience Cloud](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-first-party.md) Identity Serviceで変数を設定し、AppMeasurementで設定することで有効 `visitor.marketingCloudServerSecure``s.trackingServerSecure` になります。
