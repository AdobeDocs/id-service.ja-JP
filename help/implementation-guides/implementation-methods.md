---
description: Experience Cloud ID サービスの標準実装方法と非標準実装方法を比較してください。
keywords: ID サービス
title: 実装方法
exl-id: 0fe40a3c-bdcd-4290-bcd7-25344ff108d6
source-git-commit: fa2549090e6790763a7ac6b87348789678d18ab6
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 100%

---

# 実装方法

[!DNL Experience Platform Launch] を使用した標準の [!DNL Experience Cloud ID Service] 実装方法または非標準的な方法を選択できます。

>[!IMPORTANT]
>
>これらの手順を実行する前に、[ID サービスの要件](../reference/requirements.md)をよくお読みください。

## 標準的な実装 {#section-ea1e5270f2184f85a2e85214a6ac60cb}

ID サービスの実装には、[[!DNL Experience Platform tags]](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=ja)を使用することを強くお勧めします。この方法は、他の [!DNL Experience Cloud] ソリューションとの統合を確実に行い、実装ワークフローを効率化、適切なコードの配置とシーケンスを自動的に保証します。

## 非標準実装 {#section-2c4f2db1f9704315a7cccab6d2e07113}

これらの手順およびコードサンプルは、[!DNL Experience Cloud] ID サービスを手動、または非標準的な方法で設定する際に役立ちます。これらの実装は、多くの場合、技術的に困難で複雑です。お客様側のエンジニアリングリソースが足りない場合や、Adobe コンサルタントとの契約サポート時間を消費する場合があります。
