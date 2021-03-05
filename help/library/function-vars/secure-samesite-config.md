---
description: Google AMP ページで AMCV Cookie をサポートするために使用できる、ECID 内の設定。
keywords: ID サービス
seo-description: Google AMP ページで AMCV Cookie をサポートするために使用できる、ECID 内の設定。
seo-title: セキュア設定と SameSite 設定
title: セキュア設定と SameSite 設定
translation-type: ht
source-git-commit: 702d20f3989f7749fb173496765d94c3a5af46dc
workflow-type: ht
source-wordcount: '174'
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
