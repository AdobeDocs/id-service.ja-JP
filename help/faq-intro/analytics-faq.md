---
description: Analytics での Experience Cloud Identity Service 利用の特徴、機能、問題に関するよくある質問です。
keywords: Experience Cloud Identity Service
title: Analytics と Identity Service に関する FAQ
exl-id: 98aeca0d-41a2-4b18-b307-19a6de816e38
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '972'
ht-degree: 100%

---

# Analytics と Identity Service に関する FAQ {#analytics-and-id-service-faqs}

Analytics での Identity Service 利用の特徴、機能、問題に関するよくある質問です。

## トラッキングサーバー {#section-9a2ad7842e364c869e1650480d17f8ef}

**トラッキングサーバーの情報を見つけるにはどうすればよいですか。**

適切に設定された AppMeasurement コードにはトラッキングサーバーの情報が含まれています。

しかし、お客様側で Analytics の AppMeasurement ファイルが複数のファイルに分割されている場合があります。例えば、1 つ目のファイルに設定変数を入れ、2 つ目のファイルをプラグインで使用し、3 つ目のファイルに AppMeasurement コードを入れるお客様がいます。このような方法は推奨されません。

トラッキングサーバーの情報が見つからない場合は、Analytics のインスタンスが正しく設定されない可能性があります。トラッキングサーバーの情報が見つからない場合は[カスタマーケア](https://helpx.adobe.com/jp/marketing-cloud/contact-support.html)にお問い合わせください。

**Identity Service を使用していて、トラッキングサーバーを変更すると、どうなりますか。**

Identity Service で既に識別されているユーザーの場合、何も変更されません。Identity Service に移行しておらず、Analytics cookie を使用して識別されている従来の訪問者は、複数回カウントされます。影響を受けるユーザー数は、Identity Service がアクティブである時間の長さに応じて変わります。例えば、サイトに再訪するユーザーが移行されているので、Identity Service が 1 週間アクティブである実装は、Identity Service が 6 ヶ月アクティブである実装よりも多くの従来のユーザーを抱えている可能性があります。

## 実装と設定 {#section-6028f55d5b514ae6a631c6a79f42fb89}

**訪問者をドメイン間で追跡する場合は、CNAME を設定する必要がありますか。**

メインのエントリサイトがあり、顧客が他のドメインを訪問する前にメインのエントリサイトで顧客の識別ができる場合には、CNAME を使用することで、サードパーティ Cookie を受け入れないブラウザー（Safari など）でもクロスドメイントラッキングをおこなうことができます。

サードパーティ Cookie を受け入れるブラウザーでは、訪問者 ID の取得をリクエストしたときに、[demdex.net ドメイン](https://docs.adobe.com/content/help/ja-JP/audience-manager/user-guide/reference/demdex-calls.html)に Cookie が設定されます。Identity Service はこの Cookie を使用することで、同じ組織 ID を使用するように設定されているすべてのドメインで、同じ Experience Cloud 訪問者 ID を返すことができます。サードパーティ Cookie を受け入れないブラウザーでは、各ドメインに対して新しい Experience Cloud 訪問者 ID が割り当てられます。

CNAME を設定しても、訪問者がメインのエントリサイトを最初に訪問しないと、サードパーティ Cookie を受け入れないブラウザーでは、セカンダリサイトとメインサイトで訪問者が別々に識別されます。

**Analytics リクエストに Experience Cloud ID（MID）パラメーターがない理由を教えてください。**

Identity Service が正しく情報を返しているにもかかわらず `MID` パラメーターがない場合は、サポートされているバージョンの AppMeasurement にアップグレードしていることを確認してください。

**サイトで H コードおよび JavaScript 版 AppMeasurement と共に Identity Service を使用できますか。**

はい。両方のファイルが同じ VisitorAPI.js ファイルを参照していれば、H コードと JavaScript 版 AppMeasurement の両方をサイトで使用できます。

ただし、H コードは、visitorAPI.js コードバージョン 1.6 以降ではサポートされません。visitorAPI.js v 1.6（またはそれ以降）にアップグレードする場合、H コードを使用し続けることはできません。

**猶予期間とはどのようなもので、どのように設定すればよいですか。**

[ID サービスの猶予期間](../reference/analytics-reference/grace-period.md)を参照し、[カスタマーケア](https://helpx.adobe.com/marketing-cloud/contact-support.html)にお問合せください。

**Identity Service を使用するためにリアルタイムデータ収集（RDC）に移行しなければならない理由を教えてください。**

RDC は、全体的なパフォーマンスのメリットがあり、アドビのエッジノードのグローバルネットワークを利用する将来の新機能に備えるために必要です。[Analytics の要件：地域別データ収集（RDC）](../reference/requirements.md#section-7d04bb013bc84a25bae3b148bc0ca25f)を参照してください。

## レポート {#section-123cd55a32e54a45a23beb140becfa8f}

**Analytics を Identity Service と組み合わせて使用する場合に生じる可能性がある不整合について教えてください。**

Identity Service の使用時に不整合が生じる一般的な原因を以下に示します。

* 従来の s_vi Cookie を継続して使用している。これはデータ収集の不整合につながります。
* 訪問者が調査からポップアップに移動したときに二重にカウントされている。

## Cookie {#section-b7d5384fbedd47b09e1030211c39a3d1}

**Identity Service が AMCV Cookie を設定できない場合、Analytics ではどのようなことが起こりますか。**

この問題が新規訪問者の Analytics データに影響するシナリオとしては次の 3 つが考えられます。

1. AMCV Cookie が設定される前に（30 秒のタイムアウト期間内に）エンドユーザーがページを離れた。

   読み込み完了前に訪問者がページを離れた場合、Analytics ヒットは送信されません。この場合、Analytics はデータを受信できず、ページが早期に閉じられたためにデータが失われたものとみなします。さまざまな地方を対象にアドビが実施したテストによると、このシナリオに相当するトラフィックは平均で全トラフィックの 1 ％未満であることがわかっています。このシナリオは Identity Service が存在しない場合でも発生することに注意してください。これはページ下部に Analytics データ収集コードが含まれていることの結果です。

1. 接続が遅すぎるか、ブラウザーの読み込みが遅すぎるために、30 秒のタイムアウト期間内にエンドユーザーに Identity Service または Analytics の ID が割り当てられない。

   この場合は、Identity Service も Analytics ID も設定されず、訪問者にはクライアント側の ID が割り当てられます。この場合も Analytics データは収集できますが、次のページで Analytics ID が設定されるまで、訪問者のプロファイルは中断されます。また、クライアント側 ID は、Audience Manager または Analytics に格納されている既存の訪問者プロファイルと一致しません。2 つのドメインが同じレポートスイートに送信されている場合、クライアント側 ID は 2 人の別々の訪問者として Analytics に表示されます。

1. 30 秒のタイムアウト期間内に Identity Service の ID がエンドユーザーに割り当てられていないが、標準の Analytics トラッキング ID は割り当てられ、猶予期間は無効になっている。

   シナリオ 3 はシナリオ 2 と同じ結果になり、クライアント側 ID が使用されます。

>[!TIP]
>
>上記 3 つのシナリオが発生する可能性はきわめて低いですが、VisitorAPI.js および AppMeasurement.js の最新アップデートをデフォルト設定で使用すると、これらのシナリオによる重大な影響や目立つ影響を避けることができます。

>[!MORELIKETHIS]
>
>* [カスタマーケア](https://helpx.adobe.com/marketing-cloud/contact-support.html)

