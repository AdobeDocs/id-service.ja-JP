---
description: Analytics での ID　サービス利用の特徴、機能、問題に関するよくある質問です。
keywords: ID サービス
seo-description: Analytics での ID サービス利用の特徴、機能、問題に関するよくある質問です。
seo-title: Analytics と ID サービスに関する FAQ
title: Analytics と ID サービスに関する FAQ
uuid: 35ed79a9- eccc-4b54-8451-606f091c73b7
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Analytics と ID サービスに関する FAQ{#analytics-and-id-service-faqs}

Analytics での ID サービス利用の特徴、機能、問題に関するよくある質問です。

## トラッキングサーバー {#section-9a2ad7842e364c869e1650480d17f8ef}

**トラッキングサーバーの情報を見つけるにはどうすればよいですか。**

適切に設定された AppMeasurement コードにはトラッキングサーバーの情報が含まれています。

しかし、お客様側で Analytics の AppMeasurement ファイルが複数のファイルに分割されている場合があります。例えば、1 つ目のファイルに設定変数を入れ、2 つ目のファイルをプラグインで使用し、3 つ目のファイルに AppMeasurement コードを入れるお客様がいます。このような方法は推奨されません。

トラッキングサーバーの情報が見つからない場合は、Analytics のインスタンスが正しく設定されない可能性があります。トラッキングサーバーの情報が見つからない場合は[カスタマーケア](https://helpx.adobe.com/marketing-cloud/contact-support.html)にお問い合わせください。

**ID サービスを使用していて、トラッキングサーバーを変更すると、どうなりますか。**

ID サービスで既に識別されているユーザーの場合、何も変更されません。ID サービスに移行しておらず、Analytics Cookie を使用して識別されている従来の訪問者は、複数回カウントされます。影響を受けるユーザー数は、ID サービスがアクティブである時間の長さに応じて変わります。例えば、サイトに再訪するユーザーが移行されているので、ID サービスが 1 週間アクティブである実装は、ID サービスが 6 ヶ月アクティブである実装よりも多くの従来のユーザーを抱えている可能性があります。

## 実装と設定 {#section-6028f55d5b514ae6a631c6a79f42fb89}

**訪問者をドメイン間で追跡する場合は、CNAME を設定する必要がありますか。**

メインのエントリサイトがあり、顧客が他のドメインを訪問する前にメインのエントリサイトで顧客の識別ができる場合には、CNAME を使用することで、サードパーティ Cookie を受け入れないブラウザー（Safari など）でもクロスドメイントラッキングをおこなうことができます。

サードパーティ Cookie を受け入れるブラウザーでは、訪問者 ID の取得をリクエストしたときに、[demdex.net ドメイン](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html)に Cookie が設定されます。ID サービスはこの Cookie を使用することで、同じ組織 ID を使用するように設定されているすべてのドメインで、同じ Experience Cloud 訪問者 ID を返すことができます。サードパーティ Cookie を受け入れないブラウザーでは、各ドメインに対して新しい Experience Cloud 訪問者 ID が割り当てられます。

CNAME を設定しても、訪問者がメインのエントリサイトを最初に訪問しないと、サードパーティ Cookie を受け入れないブラウザーでは、セカンダリサイトとメインサイトで訪問者が別々に識別されます。

**Analytics リクエストに Experience Cloud ID（MID）パラメーターがない理由を教えてください。**

ID サービスが正しく情報を返しているにもかかわらず `MID` パラメーターがない場合は、サポートされているバージョンの AppMeasurement にアップグレードしていることを確認してください。

**サイトで H コードおよび JavaScript 版 AppMeasurement と共に ID サービスを使用できますか。**

はい。両方のファイルが同じ VisitorAPI.js ファイルを参照していれば、H コードと JavaScript 版 AppMeasurement の両方をサイトで使用できます。

ただし、H コードは、visitorAPI.js コードバージョン 1.6 以降ではサポートされません。visitorAPI.js v 1.6（またはそれ以降）にアップグレードする場合、H コードを使用し続けることはできません。

**猶予期間とはどのようなもので、どのように設定すればよいですか。**

詳しくは、[IDサービスの猶予期間](../mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md) と [カスタマーケア](https://helpx.adobe.com/marketing-cloud/contact-support.html)にお問い合わせください。

**ID サービスを使用するためにリアルタイムデータ収集（RDC）に移行しなければならない理由を教えてください。**

RDC は、全体的なパフォーマンスのメリットがあり、アドビのエッジノードのグローバルネットワークを利用する将来の新機能に備えるために必要です。[Analytics の要件：地域別データ収集（RDC）](../mcvid-reference/mcvid-requirements.md#section-7d04bb013bc84a25bae3b148bc0ca25f)を参照してください。

## レポート {#section-123cd55a32e54a45a23beb140becfa8f}

**Analytics を ID サービスと組み合わせて使用する場合に生じる可能性がある不整合について教えてください。**

ID サービスの使用時に不整合が生じる一般的な原因を以下に示します。

* 従来の s_vi Cookie を継続して使用している。これはデータ収集の不整合につながります。
* 訪問者が調査からポップアップに移動したときに二重にカウントされている。

## Cookie {#section-b7d5384fbedd47b09e1030211c39a3d1}

**ID サービスが AMCV Cookie を設定できない場合、Analytics ではどのようなことが起こりますか。**

この問題が新規訪問者の Analytics データに影響するシナリオとしては次の 3 つが考えられます。

1. AMCV Cookie が設定される前に（30 秒のタイムアウト期間内に）エンドユーザーがページを離れた。

   読み込み完了前に訪問者がページを離れた場合、Analytics ヒットは送信されません。この場合、Analytics はデータを受信できず、ページが早期に閉じられたためにデータが失われたものとみなします。さまざまな地方を対象にアドビが実施したテストによると、このシナリオに相当するトラフィックは平均で全トラフィックの 1 ％未満であることがわかっています。このシナリオは、MCIDサービスが存在しなくても常に発生することが重要です。これは、ページの下部にAnalyticsデータ収集コードを含めることのアーティファクトです。

1. 接続が遅すぎるか、ブラウザーの読み込みが遅すぎるために、30 秒のタイムアウト期間内にエンドユーザーに ID サービスまたは Analytics の ID が割り当てられない。

   この場合は、ID サービスも Analytics ID も設定されず、訪問者にはクライアント側の ID が割り当てられます。この場合も Analytics データは収集できますが、次のページで Analytics ID が設定されるまで、訪問者のプロファイルは中断されます。また、クライアント側 ID は、Audience Manager または Analytics に格納されている既存の訪問者プロファイルと一致しません。2 つのドメインが同じレポートスイートに送信されている場合、クライアント側 ID は 2 人の別々の訪問者として Analytics に表示されます。

1. 30 秒のタイムアウト期間内に ID サービスの ID がエンドユーザーに割り当てられていないが、標準の Analytics トラッキング ID は割り当てられ、猶予期間は無効になっている。

   シナリオ 3 はシナリオ 2 と同じ結果になり、クライアント側 ID が使用されます。

>[!TIP]
>
>デフォルト設定でVisitorAPI. jsおよびAppMeasurement. jsに最新のアップデートを使用すると、上記の3つのシナリオにおいて、重大な影響や顕著な影響を回避する必要があります。

>[!MORE_ LIKE_ THIS]
>
>* [カスタマーケア](https://helpx.adobe.com/marketing-cloud/contact-support.html)

