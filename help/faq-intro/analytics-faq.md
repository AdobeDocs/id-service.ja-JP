---
description: Analytics での Experience Cloud Identity Service 利用の特徴、機能、問題に関するよくある質問です。
keywords: Experience Cloud Identity Service
seo-description: Analytics での Identity Service 利用の特徴、機能、問題に関するよくある質問です。
seo-title: Analytics と Identity Service に関する FAQ
title: Analytics と Identity Service に関する FAQ
uuid: 35ed79a9-eccc-4b54-8451-606f091c73b7
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# Analytics と Identity Service に関する FAQ{#analytics-and-id-service-faqs}

Analytics での Identity Service 利用の特徴、機能、問題に関するよくある質問です。

## トラッキングサーバー {#section-9a2ad7842e364c869e1650480d17f8ef}

**自分のトラッキングサーバー情報を見つける方法**

適切に設定されたすべてのAppMeasurementコードには、トラッキングサーバー情報が含まれます。

ただし、場合によっては、Analytics AppMeasurementファイルが別々のファイルに分割されることがあります。 例えば、あるファイルに設定変数を入れ、プラグイン用の2つ目のファイルを使用してから、3つ目のファイルにAppMeasurementコードを入れる場合があります。 これは推奨されません。

トラッキングサーバー情報が見つからない場合は、Analyticsインスタンスが正しく設定されていない可能性があります。 トラッキングサーバーの情報が見つからない場合は、 [カスタマーケアにお問い合わせください](https://helpx.adobe.com/jp/marketing-cloud/contact-support.html) 。

**Identity Service を使用していて、トラッキングサーバーを変更すると、どうなりますか。**

Identity Service で既に識別されているユーザーの場合、何も変更されません。Identity Service に移行しておらず、Analytics cookie を使用して識別されている従来の訪問者は、複数回カウントされます。影響を受けるユーザー数は、Identity Service がアクティブである時間の長さに応じて変わります。例えば、サイトに再訪するユーザーが移行されているので、Identity Service が 1 週間アクティブである実装は、Identity Service が 6 ヶ月アクティブである実装よりも多くの従来のユーザーを抱えている可能性があります。

## 実装と設定 {#section-6028f55d5b514ae6a631c6a79f42fb89}

**ドメイン間で訪問者を追跡するためにCNAMEを設定する必要がありますか。**

顧客が他のドメインを訪問する前に識別できるメインエントリサイトがある場合、CNAMEは、サードパーティcookieを受け入れないブラウザー（Safariなど）でクロスドメイントラッキングを有効にできます。

サードパーティcookieを受け入れるブラウザーでは、訪問者IDの取得をリクエストする際に、 [demdex.netドメインにcookieが設定されます](https://docs.adobe.com/content/help/ja-JP/audience-manager/user-guide/reference/demdex-calls.html) 。 Identity Service はこの Cookie を使用することで、同じ組織 ID を使用するように設定されているすべてのドメインで、同じ Experience Cloud 訪問者 ID を返すことができます。サードパーティcookieを拒否するブラウザーでは、各ドメインに新しいExperience Cloud訪問者IDが割り当てられます。

CNAMEを設定した場合でも、メインエントリサイトを最初に訪問しないと、サードパーティcookieを受け入れないブラウザーでは、セカンダリサイトとメインサイトで訪問者が異なって識別されます。

**AnalyticsリクエストにExperience Cloud ID(MID)パラメーターがないのはなぜですか。**

Identity Service が正しく情報を返しているにもかかわらず `MID` パラメーターがない場合は、サポートされているバージョンの AppMeasurement にアップグレードしていることを確認してください。

**サイトで H コードおよび JavaScript 版 AppMeasurement と共に Identity Service を使用できますか。**

はい。両方のファイルが同じVisitorAPI.jsファイルを参照している限り、HコードとJavaScript版AppMeasurementの両方をサイトで使用できます。

ただし、HコードはvisitorAPI.jsコードバージョン1.6以降ではサポートされません。 visitorAPI.js v 1.6（またはそれ以降）にアップグレードする場合は、Hコードを使用し続けることはできません。

**猶予期間とは何ですか。猶予期間の設定方法を教えてください。**

See [The Identity Service Grace Period](../reference/analytics-reference/grace-period.md) and contact [Customer Care](https://helpx.adobe.com/jp/marketing-cloud/contact-support.html).

**Identity Service を使用するためにリアルタイムデータ収集（RDC）に移行しなければならない理由を教えてください。**

RDCは、全体的なパフォーマンスのメリットをもたらし、アドビのエッジノートのグローバルネットワークを利用する将来の新機能に備えるために必要です。 See [Analytics Requirements: Regional Data Collection (RDC)](../reference/requirements.md#section-7d04bb013bc84a25bae3b148bc0ca25f).

## レポート {#section-123cd55a32e54a45a23beb140becfa8f}

**Analytics を Identity Service と組み合わせて使用する場合に生じる可能性がある不整合について教えてください。**

Identity Service の使用時に不整合が生じる一般的な原因を以下に示します。

* 従来のs_vi cookieを引き続き使用。 これは、データ収集の不一致に寄与します。
* 重複が調査からポップアップに移動したときに訪問者をカウントする。

## Cookie {#section-b7d5384fbedd47b09e1030211c39a3d1}

**Identity Service が AMCV Cookie を設定できない場合、Analytics ではどのようなことが起こりますか。**

これが新しい訪問者のAnalyticsデータに影響する可能性がある場合は、次の3つのシナリオが考えられます。

1. AMCV cookieが正常に設定される前に（30秒のタイムアウト時間内に）、エンドユーザーがページを離れる。

   訪問者が読み込みが完了する前にページを離れた場合、Analyticsヒットは送信されません。 Analyticsはこのシナリオからデータを受け取らず、データが失われ、ページが早く閉じられたものと見なします。 外部の地域を含むアドビのテストに基づき、このシナリオは平均でトラフィックの1%未満を占めていることがわかりました。 このシナリオは Identity Service が存在しない場合でも発生することに注意してください。これはページ下部に Analytics データ収集コードが含まれていることの結果です。

1. 接続が遅すぎるか、ブラウザーの読み込みが遅すぎるために、30 秒のタイムアウト期間内にエンドユーザーに Identity Service または Analytics の ID が割り当てられない。

   この場合は、Identity Service も Analytics ID も設定されず、訪問者にはクライアント側の ID が割り当てられます。これによりAnalyticsデータを取り込むことができますが、Analytics IDが設定された後続のページでは、訪問者のプロファイルは中断されます。 また、クライアント側IDは、オーディエンスマネージャーまたはAnalyticsに保存されている既存の訪問者プロファイルとは一致しません。 また、2つの異なる訪問者が同じレポートスイートに送信される場合、このクライアント側IDは、Analyticsでも2つの異なるドメインとして表示されます。

1. 30 秒のタイムアウト期間内に Identity Service の ID がエンドユーザーに割り当てられていないが、標準の Analytics トラッキング ID は割り当てられ、猶予期間は無効になっている。

   シナリオ 3 はシナリオ 2 と同じ結果になり、クライアント側 ID が使用されます。

>[!TIP]
>
>上記 3 つのシナリオが発生する可能性はきわめて低いですが、VisitorAPI.js および AppMeasurement.js の最新アップデートをデフォルト設定で使用すると、これらのシナリオによる重大な影響や目立つ影響を避けることができます。

>[!MORELIKETHIS]
>
>* [カスタマーケア](https://helpx.adobe.com/jp/marketing-cloud/contact-support.html)

