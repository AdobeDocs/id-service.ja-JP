---
description: サーバーのサンプル設定および必要な移行手順について説明しています。
keywords: ID サービス
seo-description: サーバーのサンプル設定および必要な移行手順について説明しています。
seo-title: Experience Cloud Identity Service の移行シナリオ
title: Experience Cloud Identity Service の移行シナリオ
uuid: 9e229045-6508-48c4-ae39-9537b4941853
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 47%

---


# Experience Cloud Identity Service の移行シナリオ {#experience-cloud-id-service-migration-scenarios}

サーバーのサンプル設定および必要な移行手順について説明しています。

## 単一の Web プロパティ {#section-6ccfea84628d46c99507cb124e7f5445}

* **お客様**：Example Company Inc.
* **Experience Cloud有効**:いいえ
* **Webプロパティ**:example.com
* **データ収集サーバー**:metrics.example.com、smetrics.example.com
* **Analytics JavaScriptファイル**:すべてのサイトページに対して単一のファイル

まず、このお客様はExperience Cloudを有効にする必要があります（[要件](../../reference/requirements.md)を参照）。 また、JavaScriptファイルは1つだけなので、猶予期間は必要ありません。 また、訪問者移行の設定を行い、データ収集CNAMEを使用しなくても済みます。

## 複数の JavaScript ファイル、ハードコーディングされた画像タグ {#section-a665f6ee202940449198e4e7a5dcac54}

* **お客様**：Another Example Company Inc.
* **Experience Cloud有効**:はい
* **Webプロパティ**:anotherexample.com
* **データ収集サーバー**:anotherexampleco.112.2o7.net
* **Analytics JavaScriptファイル**:複数のJavaScriptファイル。1つはメインサイト用のファイルで、もう1つは別のCMSで管理されるサポートセクション用のファイルです。
* **その他のデータ収集方法**:1つのサイトセクションにハードコードされた画像タグ

まず、このお客様はAdobe Experience Cloud組織IDを見つける必要があります（[要件](../../reference/requirements.md)を参照）。 次に、複数の JavaScript ファイルを使用しているので、移行の猶予期間を設定する必要があります。また、訪問者移行の設定をおこない、`*.2o7.net` から `*.sc.omtrdc.net` に移行します。

[!DNL Experience Cloud] ID サービスの展開に備えるために最新の Analytics JavaScript コードに更新する場合は、すべてのハードコーディングされた画像タグを、JavaScript を使用するように更新します。

## 複数の Web プロパティ、複数の JavaScript ファイルおよび Flash ベースのビデオプレーヤー {#section-34647995ff3740b999fdee22d885e515}

* **お客様**：A Good Customer LLC
* **Experience Cloud有効**:はい
* **Webプロパティ**:mymainsite.com、myothersiteA.com、myothersiteB.com
* **データ収集サーバー**:metrics.mymainsite.com、smetrics.mymainsite.com
* **Analytics JavaScriptファイル**:複数のJavaScriptファイル。各Webプロパティに対して1つのファイル
* **その他のデータ収集方法**:Flashベースのビデオプレーヤー

まず、このお客様はAdobe Experience Cloud組織IDを見つける必要があります（[要件](../../reference/requirements.md)を参照）。 次に、複数の JavaScript ファイルを使用しているので、移行の猶予期間を設定する必要があります。このお客様は、プライマリドメインとサブドメインの訪問者を追跡するので、引き続きデータ収集CNAMEを訪問者IDサービスと共に使用します。

[!DNL Experience Cloud] ID サービスの展開に備えるために最新の Analytics JavaScript コードに更新する場合には、Flash ベースのビデオプレーヤーも最新バージョンの Flash 版 AppMeasurement に更新します。
