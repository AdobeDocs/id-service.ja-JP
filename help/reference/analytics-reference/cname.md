---
description: メインのエントリサイトがあり、顧客が他のドメインを訪問する前にメインのエントリサイトで顧客の識別ができる場合には、CNAME を使用することで、サードパーティ Cookie を受け入れないブラウザー（Safari など）でもクロスドメイントラッキングをおこなうことができます。
keywords: 操作の順序;ID サービス
title: CNAME 実装の概要
exl-id: f95dda3c-7bb2-4c7d-a25a-a4d20b58fe27
source-git-commit: d2586fc722be25df1b82caaf2cc6de6a2a6c31bf
workflow-type: ht
source-wordcount: '275'
ht-degree: 100%

---

# CNAME 実装の概要 {#cname-implementation-overview}

CNAME 実装を使用すると、アドビで使用される収集ドメインをカスタマイズして、独自のドメインと一致させることができます。 これらのドメインは、ファーストパーティコレクションドメインとも呼ばれます。これらの実装により、アドビは、JavaScript を使用して、クライアントサイドではなく、サーバーサイドでファーストパーティ Cookie を設定できます。これまでは、これらのサーバーサイドのファーストパーティ Cookie は、Apple の Intelligent Tracking Prevention（ITP）ポリシーに基づいて課せられる制限の対象ではありませんでした。 しかし、2020 年 11 月、[!DNL Apple] はポリシーを更新し、CNAME を使用して設定された Cookie にもこれらの制限が適用されるようにしました。 現在、CNAME を使用してサーバーサイドで設定された Cookie と、JavaScript を使用してクライアントサイドで設定された Cookie はどちらも、ITP の下で 7 日間または 24 時間の有効期限に制限されています。ITP ポリシーの詳細については、[トラッキング防止](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp)に関する [!DNL Apple] ドキュメントを参照してください。

CNAME 実装には Cookie の有効期間に関するメリットはありませんが、他にもメリットがある場合があります。これらのメリットには、広告ブロッカーや、データがトラッカーとして分類するドメインに送信されるのを防ぐ一般的でないブラウザーなどが含まれます。このような場合、CNAME を使用すると、これらのツールを使用しているユーザーのデータ収集が中断されるのを防ぐことができます。

さらに、CNAME 実装では、ユーザーのヒットが最初にルーティングされる場所を制御する[カスタム RDC タイプの選択](https://experienceleague.adobe.com/docs/analytics/technotes/rdc/regional-data-collection.html?lang=ja)を指定できます。ほとんどのお客様は、カスタム RDC タイプを使用しません。
