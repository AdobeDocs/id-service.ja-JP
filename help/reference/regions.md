---
description: AMCV Cookie には、サイト訪問者の Experience Cloud ID（MID）および地域 ID が含まれます。これらの ID は、キーと値のペアとして格納されます。midユーザーIDは、訪問者のExperience Cloud IDを保持します。aamlh地域IDは、サイト訪問者の地域IDを保持します。AMCV Cookie を解析することで、この情報を復元できます。
keywords: ID サービス
seo-description: AMCV Cookie には、サイト訪問者の Experience Cloud ID（MID）および地域 ID が含まれます。これらの ID は、キーと値のペアとして格納されます。midユーザーIDは、訪問者のExperience Cloud IDを保持します。aamlh地域IDは、サイト訪問者の地域IDを保持します。AMCV cookie を解析することで、この情報を復元できます。
seo-title: AMCV cookie または ID サービスからの地域およびユーザー ID の取得
title: AMCV Cookie または ID サービスからの地域およびユーザー ID の取得
uuid: bdd9d001- f29f-4ff0-800b-8182243da218
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# AMCV Cookie または ID サービスからの地域およびユーザー ID の取得 {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

AMCV Cookie には、サイト訪問者の Experience Cloud ID（MID）および地域 ID が含まれます。これらの ID は、キーと値のペアとして格納されます。mid:user ID は、訪問者の Experience Cloud ID を保持します。aamlh:region ID は、サイト訪問者の地域 ID を保持します。AMCV Cookie を解析することで、この情報を復元できます。

詳しくは、[Experience Cloud ID サービスを使用したユーザー ID と地域の取得](https://marketing.adobe.com/resources/help/en_US/aam/dcs-mcid-ids.html)を参照してください。

[!DNL Audience Manager] のお客様の場合、データ収集サーバー（DCS）によって送信された応答から、地域 ID を取得できます。[DCS 応答からのユーザー ID と地域の取得](https://marketing.adobe.com/resources/help/en_US/aam/dcs-aam-ids.html)を参照してください。

また、ID サービスによって提供される `GET` メソッドを使用して、地域 ID を取得できます。See [Get Region IDs (Location Hint)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c).
