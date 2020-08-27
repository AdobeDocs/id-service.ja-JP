---
description: Experience Cloud ID サービスの標準実装方法と非標準実装方法を比較してください。
keywords: ID Service
seo-description: Experience Cloud ID サービスの標準実装方法と非標準実装方法を比較してください。
seo-title: 実装方法
title: 実装方法
uuid: d41250e2-09f4-4a8b-8ade-54d43e9281c9
translation-type: tm+mt
source-git-commit: 63de22a29ebd8a504800d1045a69ea7eec05077a
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 72%

---


# 実装方法

[!DNL Experience Platform Launch] を使用した標準の [!DNL Experience Cloud ID Service] 実装方法または非標準的な方法を選択できます。

>[!IMPORTANT]
>
>これらの手順を実行する前に、[ID サービスの要件](../reference/requirements.md)をよくお読みください。

## 標準的な実装 {#section-ea1e5270f2184f85a2e85214a6ac60cb}

Adobeでは、 [[!DNLExperience Platform Launch]](https://docs.adobe.com/content/help/ja-JP/launch/using/implement/solutions/idservice-save.html) を使用してIDサービスを実装することを強くお勧めします。 この方法は、他の [!DNL Experience Cloud] ソリューションとの統合を確実におこない、実装ワークフローを効率化、適切なコードの配置とシーケンシングを自動的に保証します。

## 非標準的な実装 {#section-2c4f2db1f9704315a7cccab6d2e07113}

これらの手順およびコードサンプルは、[!DNL Experience Cloud] ID サービスを手動、または非標準的な方法で設定する際に役立ちます。これらの実装は、多くの場合、技術的に困難で複雑です。 お客様側のエンジニアリングリソースが少ない場合や、Adobeコンサルタントとの契約サポート時間を消費する場合があります。
