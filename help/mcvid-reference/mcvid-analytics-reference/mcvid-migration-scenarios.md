---
description: サーバーのサンプル設定および必要な移行手順について説明しています。
keywords: ID サービス
seo-description: サーバーのサンプル設定および必要な移行手順について説明しています。
seo-title: Experience Cloud ID サービスの移行シナリオ
title: Experience Cloud ID サービスの移行シナリオ
uuid: 9e229045-6508-48c4- ae39-9537b4941853
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Experience Cloud ID サービスの移行シナリオ {#experience-cloud-id-service-migration-scenarios}

サーバーのサンプル設定および必要な移行手順について説明しています。

## 単一の Web プロパティ {#section-6ccfea84628d46c99507cb124e7f5445}

* **お客様**：Example Company Inc.
* **Experience Cloud の有効化**：まだ
* **Web プロパティ**：example.com
* **データ収集サーバー**：metrics.example.com、smetrics.example.com
* **Analytics JavaScript ファイル**：すべてのサイトページで単一のファイル

最初に、Experience Cloud を有効にする必要があります（[要件](../../mcvid-reference/mcvid-requirements.md)を参照）。単一の JavaScript ファイルを使用するので、猶予期間を設定する必要はありません。さらに、訪問者移行の設定をおこないます。データ収集 CNAME は必要ないので、使用しない方式に移行します。

## 複数の JavaScript ファイル、ハードコーディングされた画像タグ {#section-a665f6ee202940449198e4e7a5dcac54}

* **お客様**：Another Example Company Inc.
* **Experience Cloud の有効化**：済み
* **Web プロパティ**：anotherexample.com
* **データ収集サーバー**：anotherexampleco.112.2o7.net
* **Analytics JavaScript ファイル**：複数の JavaScript ファイル。1 つはメインサイト用のファイル、もう 1 つは別の CMS で保持されているサポートセクション用のファイルです。
* **その他のデータ収集方法**：1 つのサイトセクションにハードコーディングされた画像タグ

最初に、この会社の Adobe Experience Cloud 組織 ID を見つける必要があります（[要件](../../mcvid-reference/mcvid-requirements.md)を参照）。次に、複数の JavaScript ファイルを使用しているので、移行の猶予期間を設定する必要があります。また、このお客様は、訪問者移行を設定してから、移行 `*.2o7.net``*.sc.omtrdc.net`します。

[!DNL Experience Cloud] ID サービスの展開に備えるために最新の Analytics JavaScript コードに更新する場合は、すべてのハードコーディングされた画像タグを、JavaScript を使用するように更新します。

## 複数の Web プロパティ、複数の JavaScript ファイルおよび Flash ベースのビデオプレーヤー {#section-34647995ff3740b999fdee22d885e515}

* **お客様**：A Good Customer LLC
* **Experience Cloud の有効化**：済み
* **Web プロパティ**：mymainsite.com、myothersiteA.com、myothersiteB.com
* **データ収集サーバー**：metrics.mymainsite.com、smetrics.mymainsite.com
* **Analytics JavaScript ファイル**：複数の JavaScript ファイル。各 Web プロパティにつき 1 つのファイルです。
* **その他のデータ収集方法**：Flash ベースのビデオプレーヤー

最初に、この会社の Adobe Experience Cloud 組織 ID を見つける必要があります（[要件](../../mcvid-reference/mcvid-requirements.md)を参照）。次に、複数の JavaScript ファイルを使用しているので、移行の猶予期間を設定する必要があります。このお客様は、プライマリドメインとサブドメインとの間で訪問者を追跡しているので、引き続きデータ収集 CNAME を訪問者 ID サービスと併用します。

[!DNL Experience Cloud] ID サービスの展開に備えるために最新の Analytics JavaScript コードに更新する場合には、Flash ベースのビデオプレーヤーも最新バージョンの Flash 版 AppMeasurement に更新します。
