---
description: ECID内の設定。Google AMPページでAMCV cookieをサポートするために使用できます。
keywords: ID サービス
seo-description: ECID内の設定。Google AMPページでAMCV cookieをサポートするために使用できます。
seo-title: セキュア設定と同じサイト設定
title: セキュア設定と同じサイト設定
translation-type: tm+mt
source-git-commit: 702d20f3989f7749fb173496765d94c3a5af46dc
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 2%

---


# セキュア設定と同じサイト設定

この設定を使用すると、cookieの設定を変更でき、Google AMPページで[AMCV cookies](../../introduction/cookies.md)をサポートします。

Adobe訪問者IDサービスは、ECID cookieに`SameSite = Lax`というブラウザーのデフォルト設定を設定します。これは、ページがGoogle AMPページなどのiframeに読み込まれた場合にアクセスできない設定です。 ECID cookieにアクセスするには、次の設定を使用してSameSite設定を`SameSite = None`に更新します。

>[!NOTE]
>
>`SameSite = None`を適用する場合、cookieを`Secure`に設定し、データを渡せるのはHTTPS接続だけにする必要があります。

**実装**:

Adobe Experience Platform Launchを使用している場合は、Experience CloudID拡張子をバージョン5.1.0にアップグレードし、`secureCookie: true`と`sameSiteCookie: none`を設定します。

Experience Platform Launchを使用していない場合は、最新訪問者5.1.0ライブラリに更新し、次の設定に従って訪問者インスタンスを初期化します。

**コードサンプル**

```js
var visitor = Visitor.getInstance("IMSORG_ID", {

     secureCookie: true,

     sameSiteCookie: "None"

});
```
