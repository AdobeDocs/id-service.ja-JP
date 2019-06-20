---
description: Adobe Media ManagerやIDサービスなど、ID同期プロセスとExperience Cloud IDサービスの一致率の概要を示します。
keywords: ID サービス
seo-description: Adobe Media ManagerやIDサービスなど、ID同期プロセスとExperience Cloud IDサービスの一致率の概要を示します。
seo-title: ID同期と一致率について
title: ID同期と一致率について
uuid: 31bd655f-2b9e-4f8d-9a1f- e81a6110ea8
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Understanding ID synchronization and match rates{#understanding-id-synchronization-and-match-rates}

Adobe Media ManagerやIDサービスなど、ID同期プロセスとExperience Cloud IDサービスの一致率の概要を示します。

## ID synchronization and match rates {#section-f652aae7234945e89d26dd833c5215fb}

ID 同期は、ID サービスによって割り当てられた ID を顧客によってサイト訪問者に割り当てられた ID に一致させます。例えば、ID サービスが訪問者 ID 1234 を割り当てたとします。別のプラットフォームでは、この訪問者を ID 4321 として把握しています。ID サービスは、同期プロセスの間、これらの ID を一緒にマッピングします。その結果、サイト訪問者について顧客が把握する新しいデータポイントが追加されます。そして、ID サービスが ID を一致させることができない場合、新しい ID が作成され、その ID が将来の同期に使用されます。

一致率は、ID 同期プロセスの有効性を測定および検証します。高い一致率は、特定のサービスが、低い一致率のサービスに比べて、より効率的であり、より多くのオンラインオーディエンスへのアクセスを提供することを示します。一致率の比較は、様々な統合広告技術プラットフォームを評価するための定量化可能な方法です。

![](assets/idsync2.png)

**高い一致率の確保**

To generate high match rates, it is important to set up the ID service properly (see the [standard implementation guide](../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445)). 適切な実装により、使用可能なデータパラメーターを持つ ID を機能させ、同期させるために必要な Cookie を ID サービスが設定できるので、高い一致率を確保できます。ただし、低速なインターネット接続、モバイルデバイスやワイヤレスネットワークからのデータ接続などの要因が、ID サービスによる ID の収集、同期および一致の程度に影響する可能性があります。これらのクライアント側変数は、ID サービスや [!DNL Adobe] では制御できません。

## ID synchronization process described {#section-a541a85cbbc74f5682824b1a2ee2a657}

ID サービスは、リアルタイムに ID を同期します。このプロセスは、サーバーからサーバーへのデータ転送を使用する代わりに、ブラウザーで動作します。以下の表で、ID 同期プロセスの手順を説明します。

**手順1:ロードページ**

When a visitor comes to your site and loads a page, the `Visitor.getInstance` function makes a [CORS](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758) or JSON-P call to the ID service. ID サービスは、訪問者の [!DNL Experience Cloud] ID（MID）を含む Cookie を使用して応答します。MID は、各サイト訪問者に割り当てられた一意の ID です。また、 [Cookie と Experience Cloud ID サービス](../introduction/cookies.md).

**手順 2：iFrame の読み込み**

ページ本文が読み込まれる間、ID サービスは、 *`Destination Publishing iFrame`*. The [!DNL Destination Publishing iFrame] loads in a domain separate from the parent page. この設計によって iFrame は以下の動作をするので、ページパフォーマンスを確保し、セキュリティを強化できます。

* 親ページとは非同期で読み込みます。This means the parent page can load independently from the [!DNL Destination Publishing iFrame]. iFrame の読み込みと iFrame 内からの ID 同期ピクセルの読み込みは、親ページやユーザーエクスペリエンスには影響しません。
* 可能な限り高速に読み込みます。これが速すぎる場合、ウィンドウ読み込みイベントの後で iFrame を読み込むことができます（非推奨）。詳しくは、[idSyncAttachIframeOnWindowLoad](../library/function-vars/idsyncattachiframeonwindowload.md#reference-b86b7112e0814a4c82c4e24c158508f4) を参照してください。
* iFrame のコードが親ページのアクセス権を取得したり、親ページに影響を与えたりすることを防ぎます。

また、 [Experience Cloud ID サービスによる ID のリクエスト方法と設定方法...](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a).

**手順3：ID 同期の実行**

ID 同期は、ターゲットパブリッシング iFrame で実行される URL です。この一般的な例で示すように、ID 同期 URL には、パートナーの ID 同期エンドポイントと、その ID を含む [!DNL Adobe] に戻るリダイレクト URL が含まれます。

```
http://abc.com?partner_id=abc&sync_id=123&redir=http://dpm.demdex.net/ibs:dpid=<
<varname>
  ADOBE_PARTNER_ID
</varname>>&dpuuid=<
<varname>
  PARTNER_UUID
</varname>>
```

[受信データ転送のための ID 同期](https://marketing.adobe.com/resources/help/en_US/aam/c_id_sync_in.html)も参照してください。

**手順 4：ID の格納**

同期した ID は、[エッジおよびコアデータサーバー](https://marketing.adobe.com/resources/help/en_US/aam/c_compedge.html)に格納されます。

## Sync services manages ID synchronization {#section-cd5784d7ad404a24aa28ad4816a0119a}

The term *`Sync Services`* refers to internal [!DNL Experience Cloud] technologies responsible for ID synchronization. このサービスは、デフォルトで有効になっています。無効にするには、[オプションの変数](../library/function-vars/disableidsync.md#reference-589d6b489ac64eddb5a7ff758945e414)を ID サービスの `Visitor.getInstance` 関数に追加します。Sync Services matches different [!DNL Experience Cloud] IDs such as:

* Third-party [!DNL Experience Cloud] cookie IDs to first-party [!DNL Experience Cloud] IDs.

* First-party [!DNL Experience Cloud] cookie IDs to [!DNL Adobe Media Optimizer] (AMO) IDs.

* サードパーティ [!DNL Experience Cloud] Cookie ID とサードパーティデータプロバイダーおよびターゲットプラットフォーム ID。これには、データプロバイダー、デマンドサイドプラットフォームおよびサプライサイドプラットフォーム、アドネットワーク、アドエクスチェンジなどのサービスおよびプラットフォームが含まれます。
* First-party [!DNL Experience Cloud] cookie IDs to cross-device partner IDs.

## ID synchronization with Adobe Media Optimizer {#section-642c885ea65d45ffb761f78838735016}

[!DNL Adobe Media Optimizer] は、iFrameベースのID同期プロセスの例外です。Because [!DNL Media Optimizer] is a trusted domain, ID syncs take place from the parent page rather than in the [!DNL Destination Publishing iFrame]. During synchronization, the ID service calls [!DNL Media Optimizer] at `cm.eversttech.net`, which is a legacy domain name used by [!DNL Media Optimizer] prior to its acquisition by Adobe. Sending data to [!DNL Media Optimizer] helps improve match rates and is automatic for ID service customers using version 2.0 (or higher). [Media Manager の cookie](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/cookies_media_optimizer.html) も参照してください。

>[!MORE_ LIKE_ THIS]
>
>* [demdex ドメインの呼び出しについて](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html)

