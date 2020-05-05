---
description: これらの説明、ツール、手順は、ID サービスが適切に動作しているかどうかを判定するのに役立ちます。これらのテストは、一般的に、IDサービスに適用され、様々なIDサービスとExperience Cloudソリューションの組み合わせに適用されます。
keywords: ID Service
seo-description: これらの説明、ツール、手順は、ID サービスが適切に動作しているかどうかを判定するのに役立ちます。これらのテストは、一般的に、IDサービスに適用され、様々なIDサービスとExperience Cloudソリューションの組み合わせに適用されます。
seo-title: Experience Cloud Identity Service のテストと検証
title: Experience Cloud Identity Service のテストと検証
uuid: 442de9c3-c265-4412-89bd-aeaa286ddad6
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# Experience Cloud Identity Service のテストと検証 {#test-and-verify-the-experience-cloud-id-service}

これらの説明、ツール、手順は、ID サービスが適切に動作しているかどうかを判定するのに役立ちます。これらのテストは、一般的に、IDサービスに適用され、様々なIDサービスとExperience Cloudソリューションの組み合わせに適用されます。

## 始める前に{#section-b1e76ad552ed4eb793b6e521a55127d4}

ID サービスのテストと検証を始める前に知っておくべき重要な情報です。

**ブラウザー環境**

通常のブラウザーセッションでテストを行う場合は、各テストの前にブラウザーのキャッシュをクリアします。

また、匿名のブラウザーセッションでIDサービスをテストすることもできます。 匿名セッションでは、各テストの前にブラウザーのCookieまたはキャッシュをクリアする必要はありません。

**ツール**

[Adobe Debugger](https://docs.adobe.com/content/help/en/analytics/implementation/validate/debugger.html) および [Charles HTTP プロキシ](https://www.charlesproxy.com/)を使用すると、Analytics を使用して ID サービスが適切に動作するように設定されていることを判定できます。この節の情報は、Adobe DebuggerとCharlesが返す結果に基づいています。 ただし、お客様に最適なツールやデバッガーを自由に使用することができます。

## Adobe Debuggerを使用したテスト {#section-861365abc24b498e925b3837ea81d469}

[!DNL Adobe] Debugger の応答に [!DNL Experience Cloud ID]（MID）が表示される場合、サービス統合は適切に設定されています。MID について詳しくは、[Cookie と Experience Cloud Identity Service](../introduction/cookies.md) を参照してください。

[[!DNL Adobe] Debugger](https://docs.adobe.com/content/help/en/analytics/implementation/validate/debugger.html) を使用した ID サービスのステータスを検証するには：

1. ブラウザーのCookieをクリアするか、匿名の閲覧セッションを開きます。
1. IDサービスコードを含むテストページを読み込みます。
1. [!DNL Adobe] Debugger を開きます。
1. MID の結果をチェックします。

## Adobe Debugger の結果について {#section-bd2caa6643d54d41a476d747b41e7e25}

MID は、キーと値のペアで格納されます（`MID= *`Experience Cloud ID`*` という構文が使用されます）。デバッガーは、この情報を以下に示すように表示します。

**成功**

次に示すような応答が表示される場合、IDサービスは適切に実装されています。

```
mid=20265673158980419722735089753036633573
```

[!DNL Analytics] のお客様の場合、MID に加えて [!DNL Analytics] ID（AID）が表示されることがあります。次のような状況が発生します。

* 初期のサイト訪問者や長期のサイト訪問者がいる場合。
* 猶予期間を有効にしている場合。

**失敗**

デバッガーが [お使いの場合は、カスタマーケア](https://helpx.adobe.com/jp/marketing-cloud/contact-support.html) (CC)にお問い合わせください。

* MIDを返しません。
* パートナーIDがプロビジョニングされていないことを示すエラーメッセージを返します。

## Charles HTTP プロキシを使用したテスト {#section-d9e91f24984146b2b527fe059d7c9355}

Charlesを使用したIDサービスのステータスを検証するには：

1. ブラウザーのCookieをクリアするか、匿名の閲覧セッションを開きます。
1. 開始チャールズ。
1. IDサービスコードを含むテストページを読み込みます。
1. 以下に説明するリクエストと応答の呼び出しとデータを確認します。

## Charles の結果について {#section-c10c3dc0bb9945cbaffcf6fec7082fab}

Charles を使用して HTTP 呼び出しを監視する場合、どこを見て何を探すかに関する情報については、この節を参照してください。

**Charles での成功した ID サービスリクエスト**

`Visitor.getInstance` 関数が `dpm.demdex.net` に対する JavaScript 呼び出しをおこなう場合、ID サービスコードは適切に動作しています。成功したリクエストには、[組織 ID](../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26) が含まれます。組織 ID は、キーと値のペアとして渡されます（`d_orgid= *`組織 ID`*` という構文が使用されます）。「[!UICONTROL 構造]」タブで、`dpm.demdex.net` および JavaScript 呼び出しを探します。「[!UICONTROL リクエスト]」タブで、組織 ID を探します。

![](assets/charles_request.png)

**Charles での成功した ID サービス応答**

[データ収集サーバー](https://docs.adobe.com/content/help/en/audience-manager/user-guide/reference/system-components/components-data-collection.html)（DCS）からの応答が MID を返す場合、アカウントは ID サービスに関して適切にプロビジョニングされています。MID は、キーと値のペアとして返されます（`d_mid: *`訪問者の Experience Cloud ID`*` という構文が使用されます）。以下に示すように、「[!UICONTROL 応答]」タブで、MID を探します。

![](assets/charles_response_success.png)

**Charles での失敗した ID サービス応答**

DCS 応答に MID がない場合、アカウントは適切にプロビジョニングされています。An unsuccessful response returns an error code and message in the [!UICONTROL Response] tab as shown below. DCS 応答にこのメッセージが表示された場合は、カスタマーケアにお問い合わせください。

![](assets/charles_response_unsuccessful.png)

エラーコードについて詳しくは、 [DCSエラーコード、メッセージ、例を参照してください](https://docs.adobe.com/content/help/en/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-error-codes.html)。
