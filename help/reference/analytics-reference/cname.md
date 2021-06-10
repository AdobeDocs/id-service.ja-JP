---
description: メインのエントリサイトがあり、顧客が他のドメインを訪問する前にメインのエントリサイトで顧客の識別ができる場合には、CNAME を使用することで、サードパーティ Cookie を受け入れないブラウザー（Safari など）でもクロスドメイントラッキングをおこなうことができます。
keywords: 操作の順序;ID サービス
title: CNAME 実装の概要
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 100%

---


# CNAME 実装の概要 {#cname-implementation-overview}

CNAME 実装を使用すると、アドビで使用される収集ドメインをカスタマイズして、独自のドメインと一致させることができます。 これにより、アドビは JavaScript を使用して、クライアントサイドではなくサーバーサイドでファーストパーティ Cookie を設定できます。 これまでは、これらのサーバーサイドのファーストパーティ Cookie は、Apple の Intelligent Tracking Prevention（ITP）ポリシーに基づいて課せられる制限の対象ではありませんでした。 しかし、2020 年 11 月、[!DNL Apple] はポリシーを更新し、CNAME を使用して設定された Cookie にもこれらの制限が適用されるようにしました。 現在、CNAME を使用してサーバーサイドで設定された Cookie と、JavaScript を使用してクライアントサイドで設定された Cookie はどちらも、ITP の下で 7 日間または 24 時間の有効期限に制限されています。 ITP ポリシーの詳細については、[トラッキング防止](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp)に関する [!DNL Apple] ドキュメントを参照してください。

CNAME の実装には、Cookie の有効期限に関しては何のメリットもありませんが、場合によっては、広告ブロッカーや一般的でないブラウザーで、トラッカーとして分類したドメインへのデータの送信を防止できるといったメリットがあります。 このような場合、CNAME を使用すると、これらのツールを使用しているユーザーのデータ収集が中断されるのを防ぐことができます。