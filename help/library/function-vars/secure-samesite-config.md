---
description: Google AMP ページで AMCV Cookie をサポートするために使用できる、ECID 内の設定。
keywords: ID サービス
title: セキュア設定と SameSite 設定
exl-id: c3bc44fc-5adc-4eae-8169-9d731d148458
TQID: https://experienceleague.adobe.com/qT9et54-InwTH7usPnjGN8mdBeMMrqK-qjxGOwqsXBA
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 156
ht-degree: 100%

---

# セキュア設定と SameSite 設定

この設定を使用すると、Cookie の設定変更と Google AMP ページでの [AMCV Cookie](../../introduction/cookies.md) のサポートが可能になります。

アドビ訪問者 ID サービスでは、ブラウザーのデフォルト設定 `SameSite = Lax` を使用して ECID Cookie を設定します。このデフォルト設定は、Google AMP ページなどの iframe にページが読み込まれる場合はアクセスできません。 ECID Cookie にアクセスするには、次の設定を使用して SameSite 設定を `SameSite = None` に更新します。

>[!NOTE]
>
>`SameSite = None` を適用する場合は、データが HTTPS 接続でのみ渡されるように、Cookie を `Secure` に設定する必要があります。

**実装**:

Adobe Experience Platform Launch を使用する場合は、Experience Cloud ID 拡張機能をバージョン 5.1.0 にアップグレードし、`secureCookie: true` と `sameSiteCookie: none` を設定します。

Experience Platform Launch を使用しない場合は、訪問者インスタンスを初期化する一方、最新の訪問者ライブラリ 5.1.0 に更新し、次の設定に従います。

**コードサンプル**

```js
var visitor = Visitor.getInstance("IMSORG_ID", {

     secureCookie: true,

     sameSiteCookie: "None"

});
```

