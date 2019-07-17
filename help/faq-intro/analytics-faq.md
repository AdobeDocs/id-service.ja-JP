---
description: Experience Cloud IDサービスとAnalyticsの使用に関連する、機能、機能、および問題に関するよくある質問です。
keywords: Experience Cloud IDサービス
seo-description: 機能、機能、およびIDサービスとAnalyticsの使用に関する問題に関するよくある質問（FAQ）です。
seo-title: AnalyticsおよびIDサービスFAQ
title: AnalyticsおよびIDサービスFAQ
uuid: 35ed79a9-eccc-4b54-8451-606f091c73b7
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Analytics and Identity Service FAQs{#analytics-and-id-service-faqs}

機能、機能、およびIDサービスとAnalyticsの使用に関する問題に関するよくある質問（FAQ）です。

## トラッキングサーバー {#section-9a2ad7842e364c869e1650480d17f8ef}

**トラッキングサーバーの情報を見つけるにはどうすればよいですか。**

適切に設定された AppMeasurement コードにはトラッキングサーバーの情報が含まれています。

しかし、お客様側で Analytics の AppMeasurement ファイルが複数のファイルに分割されている場合があります。例えば、1 つ目のファイルに設定変数を入れ、2 つ目のファイルをプラグインで使用し、3 つ目のファイルに AppMeasurement コードを入れるお客様がいます。このような方法は推奨されません。

トラッキングサーバーの情報が見つからない場合は、Analytics のインスタンスが正しく設定されない可能性があります。トラッキングサーバーの情報が見つからない場合は[カスタマーケア](https://helpx.adobe.com/marketing-cloud/contact-support.html)にお問い合わせください。

**IDサービスを使用していて、トラッキングサーバーを変更した場合はどうなりますか?**

IDサービスによって既に識別されているユーザーには、何も変更されません。IDサービスに移行しておらず、Analytics cookieで識別されていない従来の訪問者は、削除されます。影響を受けるユーザーの量は、IDサービスがアクティブになっている時間によって異なります。例えば、IDサービスが1週間アクティブになっている実装では、サイトに戻ってくるユーザーが移行されたことがあるので、IDサービスが6か月間アクティブになっている実装よりも、より従来のユーザーを持つことがあります。

## 実装と設定 {#section-6028f55d5b514ae6a631c6a79f42fb89}

**訪問者をドメイン間で追跡する場合は、CNAME を設定する必要がありますか。**

メインのエントリサイトがあり、顧客が他のドメインを訪問する前にメインのエントリサイトで顧客の識別ができる場合には、CNAME を使用することで、サードパーティ Cookie を受け入れないブラウザー（Safari など）でもクロスドメイントラッキングをおこなうことができます。

サードパーティ Cookie を受け入れるブラウザーでは、訪問者 ID の取得をリクエストしたときに、[demdex.net ドメイン](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html)に Cookie が設定されます。このcookieにより、IDサービスは同じ組織IDを使用して設定されたすべてのドメインで、同じExperience Cloud訪問者IDを返すことができます。サードパーティ Cookie を受け入れないブラウザーでは、各ドメインに対して新しい Experience Cloud 訪問者 ID が割り当てられます。

CNAME を設定しても、訪問者がメインのエントリサイトを最初に訪問しないと、サードパーティ Cookie を受け入れないブラウザーでは、セカンダリサイトとメインサイトで訪問者が別々に識別されます。

**Analytics リクエストに Experience Cloud ID（MID）パラメーターがない理由を教えてください。**

If the Identity Service is returning information correctly but you do not see the `MID` parameter, make sure that you've upgraded to a supported version of AppMeasurement.

**サイトでHコードとJavaScript版AppMeasurementをIDサービスと併用できますか。**

はい。両方のファイルが同じ VisitorAPI.js ファイルを参照していれば、H コードと JavaScript 版 AppMeasurement の両方をサイトで使用できます。

ただし、H コードは、visitorAPI.js コードバージョン 1.6 以降ではサポートされません。visitorAPI.js v 1.6（またはそれ以降）にアップグレードする場合、H コードを使用し続けることはできません。

**猶予期間とはどのようなもので、どのように設定すればよいですか。**

詳しくは、[IDサービスの猶予期間](../reference/analytics-reference/grace-period.md) と [カスタマーケア](https://helpx.adobe.com/marketing-cloud/contact-support.html)にお問い合わせください。

**IDサービスを使用するためにリアルタイムデータ収集（RDC）に移行する必要があるのはなぜですか。**

RDC は、全体的なパフォーマンスのメリットがあり、アドビのエッジノードのグローバルネットワークを利用する将来の新機能に備えるために必要です。[Analytics の要件：地域別データ収集（RDC）](../reference/requirements.md#section-7d04bb013bc84a25bae3b148bc0ca25f)を参照してください。

## レポート {#section-123cd55a32e54a45a23beb140becfa8f}

**AnalyticsをIDサービスで使用する場合、不整合の原因となる考えられる原因は何ですか?**

IDサービスを使用する場合に不整合が生じる一般的な原因は、次のとおりです。

* 従来の s_vi Cookie を継続して使用している。これはデータ収集の不整合につながります。
* 訪問者が調査からポップアップに移動したときに二重にカウントされている。

## Cookie {#section-b7d5384fbedd47b09e1030211c39a3d1}

**IDサービスがAMCV cookieを設定できない場合、Analyticsではどうなりますか。**

この問題が新規訪問者の Analytics データに影響するシナリオとしては次の 3 つが考えられます。

1. AMCV Cookie が設定される前に（30 秒のタイムアウト期間内に）エンドユーザーがページを離れた。

   読み込み完了前に訪問者がページを離れた場合、Analytics ヒットは送信されません。この場合、Analytics はデータを受信できず、ページが早期に閉じられたためにデータが失われたものとみなします。さまざまな地方を対象にアドビが実施したテストによると、このシナリオに相当するトラフィックは平均で全トラフィックの 1 ％未満であることがわかっています。このシナリオは、IDサービスが存在しなくても常に発生することが重要です。これは、ページの下部にAnalyticsデータ収集コードを含めることのアーティファクトです。

1. 低速接続またはブラウザーの「回転」が原因で、エンドユーザーに30秒のタイムアウトウィンドウ内のIDサービスまたはAnalytics IDが割り当てられていません。

   IDサービスとAnalytics IDの両方が設定されず、訪問者にはクライアント側IDが割り当てられます。この場合も Analytics データは収集できますが、次のページで Analytics ID が設定されるまで、訪問者のプロファイルは中断されます。また、クライアント側 ID は、Audience Manager または Analytics に格納されている既存の訪問者プロファイルと一致しません。2 つのドメインが同じレポートスイートに送信されている場合、クライアント側 ID は 2 人の別々の訪問者として Analytics に表示されます。

1. エンドユーザーに、30秒のタイムアウトウィンドウ内でIDサービスIDが割り当てられていないが、標準のAnalytics追跡IDが割り当てられており、猶予期間が有効になっていない。

   シナリオ 3 はシナリオ 2 と同じ結果になり、クライアント側 ID が使用されます。

>[!TIP]
>
>上記 3 つのシナリオが発生する可能性はきわめて低いですが、VisitorAPI.js および AppMeasurement.js の最新アップデートをデフォルト設定で使用すると、これらのシナリオによる重大な影響や目立つ影響を避けることができます。

>[!MORE_LIKE_THIS]
>
>* [カスタマーケア](https://helpx.adobe.com/marketing-cloud/contact-support.html)

