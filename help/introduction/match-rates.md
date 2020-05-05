---
description: Adobe Media Manager および ID サービスを含む、ID 同期プロセスと Experience Cloud Identity Service の一致率の概要です。
keywords: ID Service
seo-description: Adobe Media Manager および ID サービスを含む、ID 同期プロセスと Experience Cloud Identity Service の一致率の概要です。
seo-title: ID 同期と一致率について
title: ID 同期と一致率について
uuid: 31bd655f-2b9e-4f8d-9a1f-e81a6110eda8
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# ID 同期と一致率について{#understanding-id-synchronization-and-match-rates}

Adobe Media Manager および ID サービスを含む、ID 同期プロセスと Experience Cloud Identity Service の一致率の概要です。

## ID 同期と一致率 {#section-f652aae7234945e89d26dd833c5215fb}

ID同期は、IDサービスによって割り当てられたIDと、お客様がサイトの訪問者に割り当てたIDとを一致させます。 例えば、IDサービスが訪問者ID 1234を割り当てたとします。 別のプラットフォームでは、この訪問者をID 4321で認識しています。 IDサービスは、同期プロセス中にこれらのIDを一緒にマッピングします。 その結果、サイトの訪問者に関するお客様の知っている新しいデータポイントが追加されます。 また、IDサービスがIDを一致させることができない場合は、新しいIDが作成され、そのIDが将来の同期に使用されます。

一致率は、ID同期プロセスの有効性を測定および検証します。 高い一致率は、特定のサービスが低い一致率のサービスよりも効果的で、より大きなオンラインオーディエンスへのアクセスを提供することを示します。 一致率の比較は、様々な統合広告技術プラットフォームを評価するための定量化可能な方法です。

![](assets/idsync2.png)

**高い一致率の確保**

高い一致率を生成するには、ID サービスを適切に設定することが重要です（[標準実装ガイド](../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445)を参照）。適切な実装を行うと、有効なデータパートナーを持つIDを機能させ、同期させるために必要なcookieをIDサービスが設定できるので、高い一致率を確保するのに役立ちます。 ただし、低速なインターネット接続、モバイルデバイスやワイヤレスネットワークからのデータ収集などの要因は、IDサービスがIDを収集、同期、一致させる程度に影響する可能性があります。 これらのクライアント側変数は、ID サービスや [!DNL Adobe] では制御できません。

## ID 同期プロセスの説明 {#section-a541a85cbbc74f5682824b1a2ee2a657}

IDサービスは、IDをリアルタイムで同期します。 このプロセスは、サーバー間のデータ転送を経由するのではなく、ブラウザーで機能します。 次の表に、ID同期プロセスの手順を示します。

**手順 1：ページの読み込み**

訪問者がサイトにアクセスしてページを読み込むと、`Visitor.getInstance` 関数は ID サービスへの [CORS](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758) または JSON-P 呼び出しをおこないます。ID サービスは、訪問者の [!DNL Experience Cloud] ID（MID）を含む Cookie を使用して応答します。MID は、各サイト訪問者に割り当てられた一意の ID です。詳しくは、[Cookie と Experience Cloud Identity Service](../introduction/cookies.md) を参照してください。

**手順 2：iFrame の読み込み**

ページ本文が読み込まれる間、ID サービスは、*`Destination Publishing iFrame`* を調整する際に便利です。The [!UICONTROL Destination Publishing iFrame] loads in a domain separate from the parent page. この設計により、iFrameは次のようになるので、ページのパフォーマンスを確保し、セキュリティを強化できます。

* 親ページとは非同期で読み込みます。 This means the parent page can load independently from the [!UICONTROL Destination Publishing iFrame]. iFrameの読み込みとiFrame内からのID同期ピクセルの読み込みは、親ページやユーザーエクスペリエンスには影響しません。
* 可能な限り早く読み込みます。 これが速すぎる場合は、ウィンドウ読み込みイベント後にiFrameを読み込むことができます（非推奨）。 See [idSyncAttachIframeOnWindowLoad](../library/function-vars/idsyncattachiframeonwindowload.md#reference-b86b7112e0814a4c82c4e24c158508f4) for details.
* iFrame内のコードが親ページへのアクセス権を取得したり、親ページに影響を与えたりするのを防ぎます。

See also, [How the Experience Cloud Identity Service Requests and Sets IDs...](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a).

**手順3: Fire ID同期**

ID同期は、ターゲットパブリッシングiFrameで実行されるURLです。 この一般的な例で示すように、ID 同期 URL には、パートナーの ID 同期エンドポイントと、その ID を含む [!DNL Adobe] に戻るリダイレクト URL が含まれます。

`http://abc.com?partner_id=abc&sync_id=123&redir=http://dpm.demdex.net/ibs:dpid=<ADOBE_PARTNER_ID>&dpuuid=<PARTNER_UUID>`

[受信データ転送のための ID 同期](https://docs.adobe.com/content/help/ja-JP/audience-manager/user-guide/implementation-integration-guides/sending-audience-data/batch-data-transfer-process/id-sync-http.html)も参照してください。

**手順 4：ID の格納**

同期されたIDは、 [エッジおよびコアデータサーバーに保存され](https://docs.adobe.com/content/help/en/audience-manager/user-guide/reference/system-components/components-edge.html)ます。

## ID 同期を管理する同期サービス {#section-cd5784d7ad404a24aa28ad4816a0119a}

*`Sync Services`* という用語は、ID 同期を担当する内部 Experience Cloud [!DNL Experience Cloud]テクノロジーのことを指します。このサービスはデフォルトで有効になっています。 無効にするには、IDサービス [関数に](../library/function-vars/disableidsync.md#reference-589d6b489ac64eddb5a7ff758945e414) オプションの変数 `Visitor.getInstance` を追加します。 同期サービスは、以下のような様々な [!DNL Experience Cloud] ID を一致させます。

* サードパーティ [!DNL Experience Cloud] Cookie ID とファーストパーティ [!DNL Experience Cloud] ID。

* ファーストパーティ [!DNL Experience Cloud] Cookie ID と [!DNL Adobe Media Optimizer]（AMO）ID。

* サードパーティ [!DNL Experience Cloud] Cookie ID とサードパーティデータプロバイダーおよびターゲットプラットフォーム ID。これには、データプロバイダー、デマンドサイドプラットフォームおよびサプライサイドプラットフォーム、アドネットワーク、アドエクスチェンジなどのサービスおよびプラットフォームが含まれます。
* ファーストパーティ [!DNL Experience Cloud] Cookie ID とクロスデバイスパートナー ID。

## Adobe Advertising CloudとのID同期 {#section-642c885ea65d45ffb761f78838735016}

[!DNL Adobe Advertising Cloud] (旧称 [!DNL Adobe Media Optimizer])は、iFrameベースのID同期プロセスの例外です。 [!DNL Advertising Cloud] は信頼されているドメインなので、ID 同期は [!UICONTROL Destination Publishing iFrame] 内ではなく親ページからおこなわれます。同期中、ID サービスは `cm.eversttech.net` の [!DNL Advertising Cloud] を呼び出します。cm.eversttech.net はアドビが [!DNL Advertising Cloud]Media Manager を買収する以前に使用されていた従来のドメイン名です。[!DNL Advertising Cloud] にデータを送信すると一致率の向上に役立ちます。バージョン 2.0 以降を使用している ID サービスのお客様の場合、このデータ送信は自動的におこなわれます。「 [Advertising Cloud Cookies](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-advertising-cloud.html)」も参照してください。

>[!MORELIKETHIS]
>
>* [demdex ドメインの呼び出しについて](https://docs.adobe.com/content/help/ja-JP/audience-manager/user-guide/reference/demdex-calls.html)

