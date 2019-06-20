---
description: これらの説明、ツール、手順は、ID サービスが適切に動作しているかどうかを判定するのに役立ちます。これらのテストは、一般に、ID サービスに適用され、様々な ID サービスと Experience Cloud ソリューションの組み合わせに適用されます。
keywords: ID サービス
seo-description: これらの説明、ツール、手順は、ID サービスが適切に動作しているかどうかを判定するのに役立ちます。これらのテストは、一般に、ID サービスに適用され、様々な ID サービスと Experience Cloud ソリューションの組み合わせに適用されます。
seo-title: エクスペリエンスプラットフォームIDサービスのテストと検証
title: エクスペリエンスプラットフォームIDサービスのテストと検証
uuid: 442de9c3- c265-4412-89bd- aeaa286ddad6
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# エクスペリエンスプラットフォームIDサービスのテストと検証{#test-and-verify-the-experience-cloud-id-service}

これらの説明、ツール、手順は、ID サービスが適切に動作しているかどうかを判定するのに役立ちます。これらのテストは、一般に、ID サービスに適用され、様々な ID サービスと Experience Cloud ソリューションの組み合わせに適用されます。

## 始める前に {#section-b1e76ad552ed4eb793b6e521a55127d4}

IDサービスのテストと検証を始める前に知っておくべき重要な情報です。

**ブラウザー環境**

通常のブラウザーセッションでテストする場合、各テストの前にブラウザーキャッシュをクリアします。

または、匿名ブラウザーセッションで ID サービスをテストできます。匿名セッションでは、各テストの前に、ブラウザーの Cookie またはキャッシュをクリアする必要はありません。

**ツール**

[Adobe Debugger](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html) および [Charles HTTP プロキシ](https://www.charlesproxy.com/)を使用すると、Analytics を使用して ID サービスが適切に動作するように設定されていることを判定できます。この節の情報は、Adobe Debugger および Charles が返す結果に基づいています。ただし、お客様に最適なツールやデバッガーを自由に使用することができます。

## Adobe Debugger を使用したテスト {#section-861365abc24b498e925b3837ea81d469}

デバッガーの応答に（ [!DNL Experience Cloud ID] MID）が表示されると、サービス統合が適切に [!DNL Adobe] 設定されます。MIDについて詳しくは [、cookieおよびエクスペリエンスプラットフォームIDサービス](../introduction/cookies.md) を参照してください。

[!DNL Adobe][デバッガを使用してIDサービスのステータスを検証するに](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html)は:

1. ブラウザーの Cookie をクリアするか、匿名ブラウジングセッションを開きます。
1. ID サービスコードを含むテストページを読み込みます。
1. デバッガーを [!DNL Adobe] 開きます。
1. MID の結果をチェックします。

## Adobe Debuggerの結果について {#section-bd2caa6643d54d41a476d747b41e7e25}

MIDは、この構文を使用するキーと値のペアに格納されます。 `MID= *`Experience Cloud ID`*`。デバッガーは、この情報を以下に示すように表示します。

**成功**

以下に示すような応答が表示される場合、ID サービスは適切に実装されています。

```
mid=20265673158980419722735089753036633573
```

[!DNL Analytics] のお客様の場合、MID に加えて [!DNL Analytics] ID（AID）が表示されることがあります。これは、以下の場合に発生します。

* 初期のサイト訪問者または長期滞在しているサイト訪問者がいる場合。
* 猶予期間を有効にしている場合。

**失敗**

デバッガーが以下の動作をする場合は、[カスタマーケア](https://helpx.adobe.com/marketing-cloud/contact-support.html)にお問い合わせください。

* MID を返さない。
* パートナー ID がプロビジョニングされていないことを示すエラーメッセージを返す。

## Charles HTTPプロキシを使用したテスト {#section-d9e91f24984146b2b527fe059d7c9355}

Charles を使用した ID サービスのステータスを検証するには：

1. ブラウザーの Cookie をクリアするか、匿名ブラウジングセッションを開きます。
1. Charles を開始します。
1. ID サービスコードを含むテストページを読み込みます。
1. 以下に説明するリクエストと応答の呼び出しとデータをチェックします。

## Charlesの結果について {#section-c10c3dc0bb9945cbaffcf6fec7082fab}

Charles を使用して HTTP 呼び出しを監視する場合、どこを見て何を探すかに関する情報については、この節を参照してください。

**Charlesでの成功したIDサービスリクエスト**

`Visitor.getInstance` 関数が `dpm.demdex.net` に対する JavaScript 呼び出しをおこなう場合、ID サービスコードは適切に動作しています。成功したリクエストには、[組織 ID](../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26) が含まれます。組織IDは、この構文を使用するキーと値のペアとして渡されます。 `d_orgid= *`組織ID`*`。タブの下の、および `dpm.demdex.net` JavaScript呼び出しを探し [!DNL Structure] ます。タブの [!DNL Request] 下の組織IDを探します。

![](assets/charles_request.png)

**Charlesでの成功したIDサービス応答**

[データ収集サーバー](https://marketing.adobe.com/resources/help/en_US/aam/c_compcollect.html)（DCS）からの応答が MID を返す場合、アカウントは ID サービスに関して適切にプロビジョニングされています。MIDは、この構文を使用するキーと値のペアとして返されます。 `d_mid: *`visitor Experience Cloud ID`*`を参照してください。以下に示すように、タブの [!DNL Response] MIDを探します。

![](assets/charles_response_success.png)

**Charlesでの失敗したIDサービス応答**

DCS 応答に MID がない場合、アカウントは適切にプロビジョニングされています。失敗した応答は、以下に示すように [!DNL Response] 、タブにエラーコードとメッセージを返します。DCS 応答にこのメッセージが表示された場合は、カスタマーケアにお問い合わせください。

![](assets/charles_response_unsuccessful.png)

エラーコードについて詳しくは、[DCS エラーコード、メッセージおよび例](https://marketing.adobe.com/resources/help/en_US/aam/dcs_error_codes.html)を参照してください。