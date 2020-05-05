---
description: 'null'
keywords: order of operations;ID Service
seo-description: 'null'
seo-title: データ収集 CNAME およびクロスドメイントラッキング
title: データ収集 CNAME およびクロスドメイントラッキング
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# データ収集 CNAME およびクロスドメイントラッキング {#data-collection-cnames-and-cross-domain-tracking}

顧客が他のドメインを訪問する前に識別できるメインエントリサイトがある場合、CNAMEは、サードパーティcookieを受け入れないブラウザー（Safariなど）でクロスドメイントラッキングを有効にできます。

サードパーティcookieを受け入れるブラウザーでは、訪問者IDのリクエスト時に、データ収集サーバーによってcookieが設定されます。 このcookieを使用すると、訪問者IDサービスは、同じExperience Cloud組織IDを使用して設定されているすべてのドメインで、同じExperience Cloud訪問者IDを返すことができます。

サードパーティcookieを拒否するブラウザーでは、各ドメインに新しいExperience Cloud訪問者IDが割り当てられます。

demdex.net cookieを使用すると、訪問者IDサービスは、Analyticsのs_vi cookieと同じレベルのクロスドメイントラッキングを提供できます。このcookieは一部のブラウザーで受け入れられ、ドメイン間で使用されますが、他のブラウザーでは拒否されます。

## Data Collection CNAMEs {#section-48fd186d376a48079769d12c4bd9f317}

When the Analytics cookie was set by the data collection server, many customers have configured data collection server CNAME records as part of a [first-party cookie implementation](https://docs.adobe.com/content/help/ja-JP/core-services/interface/ec-cookies/cookies-first-party.html) to avoid issues with browsers that reject third-party cookies. このプロセスでは、データ収集サーバードメインがWebサイトのドメインと一致するように設定され、訪問者ID cookieがファーストパーティcookieとして設定されます。

訪問者IDサービスはJavaScriptを使用して現在のWebサイトのドメインに訪問者cookieを直接設定するので、この設定はファーストパーティcookieの設定に必要なくなりました。

単一の Web プロパティ（単一のドメイン）を持つお客様は、データ収集 CNAME を廃止し、代わりにデフォルトのデータ収集ホスト名を使用できます（`omtrdc.net` または `2o7.net`）。

ただし、データ収集にCNAMEを使用すると、サードパーティcookieを受け入れないブラウザーで、メインのランディングドメインと他のドメインの間の訪問者を追跡できるという利点もあります。 複数のWebプロパティ（複数のドメイン）を持つお客様は、データ収集CNAMEを維持するメリットがある場合があります。 次の節では、クロスドメイン訪問者トラッキングのしくみを説明します。

## CNAME によるクロスドメイントラッキングのしくみ {#section-78925af798e24917b9abed79de290ad9}

Apple Safari などのブラウザーではファーストパーティ Cookie をサードパーティのコンテキストで使用できるしくみがあるため、CNAME を利用して、同じトラッキングサーバーを使用するプライマリドメインとその他のドメインとにまたがって顧客を追跡できます。

例えば、プライマリサイトが `mymainsite.com` にあるとします。CNAME レコードを設定して、セキュリティで保護されたデータ収集サーバー `smetrics.mymainsite.com` を参照します。

ユーザーが `mymainsite.com` を訪問すると、データ収集サーバーによって ID サービス Cookie が設定されます。これが可能であるのは、データ収集サーバーのドメインと Web サイトのドメインが一致しているからです。このような Cookie の使用方法を、「*ファーストパーティコンテキスト*」または単に「*ファーストパーティ Cookie*」と呼びます。

同じデータ収集サーバーを他のサイトでも使用し（例えば、`myothersiteB.com` と `myothersiteA.com` など）、訪問者が後でそのようなサイトを訪問する場合、`mymainsite.com` の訪問時に設定された Cookie がデータ収集サーバーへの HTTPS リクエストに含まれて送信されます（ブラウザーは Cookie が対応しているドメインが現在の Web サイトのドメインと一致していなくても、そのすべての Cookie をすべての HTTPS リクエストでそのドメインに送信することに注意してください）。このような Cookie の使用方法を、*サードパーティコンテキスト*&#x200B;または単に&#x200B;*サードパーティ Cookie* と呼びます。これにより、同じ訪問者 ID を他のドメインでも使用することができます。ブラウザーは、サードパーティのコンテキストの Cookie をファーストパーティ Cookie とは異なる方法で処理します。

*注意：Safari は、設定に関わらず、サードパーティコンテキストのすべての Cookie をブロックします。*

このことから、訪問者を複数のドメインで識別するには、ユーザーが共通して訪問するドメインを収集ドメインにする必要があります。データ収集ドメインとして使用できる&#x200B;*共通の*&#x200B;ドメインがない場合は、クロスドメイントラッキングのためにデータ収集ドメインの CNAME を保持するメリットはありません。訪問者がメインエントリサイトを最初に訪問しない場合は、セカンダリサイトとメインサイトで訪問者が異なる訪問者として識別されます。

## Experience Cloud Identity Service で CNAME サポートを有効にする {#section-25d4feb686d944e3a877d7aad8dbdf9a}

データ収集サーバーの CNAME のサポートは、`visitor.marketingCloudServerSecure` 変数を設定することで有効になります。
