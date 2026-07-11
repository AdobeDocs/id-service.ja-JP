---
description: Google AMP ページで AMCV Cookie をサポートするために使用できる、ECID 内の設定。
keywords: 訪問者 ID サービス
title: セキュア設定と SameSite 設定
exl-id: c3bc44fc-5adc-4eae-8169-9d731d148458
TQID: https://experienceleague.adobe.com/qT9et54-InwTH7usPnjGN8mdBeMMrqK-qjxGOwqsXBA
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 151
ht-degree: 54%

---

# セキュア設定と SameSite 設定

この設定を使用すると、Cookie の設定変更と Google AMP ページでの [AMCV Cookie](../../introduction/cookies.md) のサポートが可能になります。

Adobe訪問者ID サービスは、ブラウザーのデフォルト設定`SameSite = Lax`でECID Cookieを設定します。これは、ページがGoogle AMP ページのようなiframeに読み込まれた場合にアクセスできません。 ECID Cookie にアクセスするには、次の設定を使用して SameSite 設定を `SameSite = None` に更新します。

>[!NOTE]
>
>`SameSite = None` を適用する場合は、データが HTTPS 接続でのみ渡されるように、Cookie を `Secure` に設定する必要があります。

**実装**:

タグを使用している場合は、[!UICONTROL Experience Cloud ID Service] タグ拡張機能をバージョン 5.1.0にアップグレードし、`secureCookie: true`と`sameSiteCookie: none`を設定します。

タグを使用していない場合は、Visitor インスタンスを初期化しながら、最新のVisitor 5.1.0 ライブラリにアップデートし、以下の設定に従います。

**コードサンプル**

```js
var visitor = Visitor.getInstance("IMSORG_ID", {

     secureCookie: true,

     sameSiteCookie: "None"

});
```

