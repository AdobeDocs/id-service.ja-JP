---
description: 訪問者ID サービスで他のCX Enterprise ソリューションを使用する際に関連する機能、問題に関するよくある質問です。
keywords: 訪問者 ID サービス
title: 他のCX エンタープライズソリューションに関するFAQ
exl-id: d1164951-01c9-4375-981a-f87d8a280e4b
TQID: https://experienceleague.adobe.com/fn7ZHenELGcFGr3PI8cQRr0xk4xEIEqB180kDWTe4KM
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 164
ht-degree: 7%

---

# 他のCX エンタープライズソリューションに関するFAQ{#faqs-for-other-experience-cloud-solutions}

訪問者ID サービスで他のCX Enterprise ソリューションを使用する際に関連する機能、問題に関するよくある質問です。

## Analytics と Audience Manager {#section-b3dd206d497041acb04554c6fb1c912a}

**ユーザーの訪問履歴は、Visitor ID サービスを実装した後、Adobe AnalyticsからAudience Managerに書き出されますか？**

この場合、次の 2 つのことが考えられます。

* 訪問者ID サービスの実装後に訪問者アクティビティが発生した場合、訪問者とその履歴はAudience Managerへのデータ書き出しに含まれます。
* 訪問者ID サービスの実装後に訪問者アクティビティがない場合、訪問者とその履歴はAudience Managerへのデータ書き出しに含まれません。 新しいアクティビティは存在しないので、Analytics IDをECIDに関連付ける方法はありません。

