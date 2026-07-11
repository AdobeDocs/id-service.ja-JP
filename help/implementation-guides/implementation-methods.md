---
description: Visitor ID サービスの標準と非標準の実装方法。
keywords: 訪問者 ID サービス
title: 実装方法
exl-id: 0fe40a3c-bdcd-4290-bcd7-25344ff108d6
TQID: https://experienceleague.adobe.com/VcMKVPqOHJHqwX4CTYHeeQnqrEzwLLJ9xn2-e1vDr-k
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 151
ht-degree: 33%

---

# 実装方法

タグまたは非標準メソッドを使用して、標準の訪問者ID サービス実装方法を選択できます。

>[!IMPORTANT]
>
>これらの手順を開始する前に、必ず[訪問者ID サービス要件](../reference/requirements.md)を読んで理解してください。

## 標準的な実装 {#section-ea1e5270f2184f85a2e85214a6ac60cb}

Adobeでは、[tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=ja)を使用して訪問者ID サービスを実装することを強くお勧めします。 この方式により、他のCX エンタープライズソリューションとの統合が保証され、実装ワークフローが合理化され、正しいコードの配置と順序付けが自動的に行われます。

## 非標準実装 {#section-2c4f2db1f9704315a7cccab6d2e07113}

このガイドの手順とコードサンプルは、Visitor ID サービスを手動または非標準の方法で設定するのに役立ちます。 これらの実装は、多くの場合、技術的に困難で複雑です。 お客様側のエンジニアリングリソースが足りない場合や、Adobe コンサルタントとの契約サポート時間を消費する場合があります。

