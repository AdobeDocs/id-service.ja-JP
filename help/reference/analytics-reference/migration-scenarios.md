---
description: サーバーのサンプル設定および必要な移行手順について説明しています。
keywords: ID サービス
title: Experience Cloud Identity Service の移行シナリオ
exl-id: 419532bf-399f-4646-a95f-31c35535d6fc
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '380'
ht-degree: 100%

---

# Experience Cloud Identity Service の移行シナリオ {#experience-cloud-id-service-migration-scenarios}

サーバーのサンプル設定および必要な移行手順について説明しています。

## 単一の web プロパティ {#section-6ccfea84628d46c99507cb124e7f5445}

* **お客様**：Example Company Inc.
* **Experience Cloud が有効**：いいえ
* **Web プロパティ**：example.com
* **データ収集サーバー**：metrics.example.com、smetrics.example.com
* **Analytics JavaScript ファイル**：すべてのサイトページに対して単一のファイル

まず、この顧客は Experience Cloud を有効にする必要があります（[要件](../../reference/requirements.md)を参照）。 また、JavaScript ファイルは 1 つだけなので、この顧客には猶予期間は必要ありません。 また、この顧客は訪問者移行の設定を行い、データ収集 CNAME から移行しますが、これは必須ではありません。

## 複数の JavaScript ファイル、ハードコーディングされた画像タグ {#section-a665f6ee202940449198e4e7a5dcac54}

* **お客様**：Another Example Company Inc.
* **Experience Cloud が有効**：はい
* **Web プロパティ**：anotherexample.com
* **データ収集サーバー**：anotherexampleco.112.2o7.net
* **Analytics JavaScript ファイル**：複数の JavaScript ファイル。 1 つはメインサイト用のファイルで、もう 1 つは別個の CMS で維持管理されているサポートセクション用のファイルです。
* **その他のデータ収集方法**：1 つのサイトセクションにハードコードされた画像タグ

まず、この顧客は Adobe Experience Cloud 組織 ID を見つける必要があります（[要件](../../reference/requirements.md)を参照）。 次に、複数の JavaScript ファイルを使用しているので、移行の猶予期間を設定する必要があります。また、訪問者移行の設定をおこない、`*.2o7.net` から `*.sc.omtrdc.net` に移行します。

[!DNL Experience Cloud] ID サービスの展開に備えるために最新の Analytics JavaScript コードに更新する場合は、すべてのハードコーディングされた画像タグを、JavaScript を使用するように更新します。

## 複数の web プロパティ、複数の JavaScript ファイルおよび Flash ベースのビデオプレーヤー {#section-34647995ff3740b999fdee22d885e515}

* **お客様**：A Good Customer LLC
* **Experience Cloud が有効**：はい
* **Web プロパティ**：mymainsite.com、myothersiteA.com、myothersiteB.com
* **データ収集サーバー**：metrics.mymainsite.com、smetrics.mymainsite.com
* **Analytics JavaScript ファイル**：複数の JavaScript ファイル。 Web プロパティごとに 1 つのファイル。
* **その他のデータ収集方法**：Flash ベースのビデオプレーヤー

まず、この顧客は Adobe Experience Cloud 組織 ID を見つける必要があります（[要件](../../reference/requirements.md)を参照）。 次に、複数の JavaScript ファイルを使用しているので、移行の猶予期間を設定する必要があります。この顧客は、プライマリドメインとサブドメインの間で訪問者を追跡するので、引き続きデータ収集 CNAME を訪問者 ID サービスと共に使用します。

[!DNL Experience Cloud] ID サービスの展開に備えるために最新の Analytics JavaScript コードに更新する場合には、Flash ベースのビデオプレーヤーも最新バージョンの Flash 版 AppMeasurement に更新します。
