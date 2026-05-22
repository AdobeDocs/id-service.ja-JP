---
description: AMCV Cookie には、サイト訪問者の Experience Cloud ID（MID）および地域 ID が含まれます。 これらの ID は、キーと値のペアとして格納されます。 mid user ID は、訪問者の Experience Cloud ID を保持します。 aamlh region ID は、サイト訪問者の地域 ID を保持します。 AMCV Cookie を解析することで、この情報を復元できます。
keywords: ID サービス
title: AMCV Cookie または ID サービスからの地域およびユーザー ID の取得
exl-id: 986e761e-4bc7-4511-86b7-7d13a7761a2b
TQID: https://experienceleague.adobe.com/OBzPrrLffDFgRisA27XIIl33x-4aWmj0krXF3prLPUk
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 240
ht-degree: 91%

---

# AMCV Cookie または ID サービスからの地域およびユーザー ID の取得 {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

AMCV Cookie には、サイト訪問者の Experience Cloud ID（MID）および地域 ID が含まれます。 これらの ID は、キーと値のペアとして格納されます。 mid:user IDは、訪問者のExperience Cloud IDを保持します。 aamlh:region IDは、サイト訪問者のリージョン IDを保持します。 AMCV Cookie を解析することで、この情報を復元できます。

詳しくは、[Experience Cloud ID サービスを使用したユーザー ID と地域の取得](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-mcid-ids.html?lang=ja)を参照してください。

[!DNL Audience Manager] のお客様の場合、データ収集サーバー（DCS）によって送信された応答から、地域 ID を取得できます。 [DCS 応答からのユーザー ID と地域の取得](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-aam-ids.html?lang=ja)を参照してください。

また、ID サービスによって提供される `GET` メソッドを使用して、地域 ID を取得できます。 [地域 ID（ロケーションヒント）の取得](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c)を参照してください。

