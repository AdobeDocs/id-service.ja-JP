---
description: AMCV Cookie には、サイト訪問者の Experience Cloud ID（MID）および地域 ID が含まれます。これらの ID は、キーと値のペアとして格納されます。mid user ID は、訪問者の Experience Cloud ID を保持します。aamlh region ID は、サイト訪問者の地域 ID を保持します。AMCV Cookie を解析することで、この情報を復元できます。
keywords: ID サービス
title: AMCV Cookie または ID サービスからの地域およびユーザー ID の取得
exl-id: 986e761e-4bc7-4511-86b7-7d13a7761a2b
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 100%

---

# AMCV Cookie または ID サービスからの地域およびユーザー ID の取得 {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

AMCV Cookie には、サイト訪問者の Experience Cloud ID（MID）および地域 ID が含まれます。これらの ID は、キーと値のペアとして格納されます。mid:user ID は、訪問者の Experience Cloud ID を保持します。aamlh:region ID は、サイト訪問者の地域 ID を保持します。AMCV Cookie を解析することで、この情報を復元できます。

詳しくは、[Experience Cloud ID サービスを使用したユーザー ID と地域の取得](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-mcid-ids.html?lang=ja)を参照してください。

[!DNL Audience Manager] のお客様の場合、データ収集サーバー（DCS）によって送信された応答から、地域 ID を取得できます。[DCS 応答からのユーザー ID と地域の取得](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-aam-ids.html?lang=ja)を参照してください。

また、ID サービスによって提供される `GET` メソッドを使用して、地域 ID を取得できます。[地域 ID（ロケーションヒント）の取得](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c)を参照してください。
