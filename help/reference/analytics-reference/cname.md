---
description: メインのエントリサイトがあり、顧客が他のドメインを訪問する前にメインのエントリサイトで顧客の識別ができる場合には、CNAME を使用することで、サードパーティ Cookie を受け入れないブラウザー（Safari など）でもクロスドメイントラッキングをおこなうことができます。
keywords: 操作の順序;ID サービス
title: CNAME 実装の概要
exl-id: f95dda3c-7bb2-4c7d-a25a-a4d20b58fe27
source-git-commit: 61f9f1888430ff0fdbb90a8cf6561bf23d204a45
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 45%

---

# CNAME 実装の概要{#cname-implementation-overview}

CNAME 実装を使用すると、アドビで使用される収集ドメインをカスタマイズして、独自のドメインと一致させることができます。 これらのドメインは、ファーストパーティの収集ドメインとも呼ばれます。 これらの実装により、Adobeは、JavaScript を使用して、クライアント側ではなく、サーバー側でファーストパーティ cookie を設定できます。 これまでは、これらのサーバーサイドのファーストパーティ Cookie は、Apple の Intelligent Tracking Prevention（ITP）ポリシーに基づいて課せられる制限の対象ではありませんでした。 しかし、2020 年 11 月、[!DNL Apple] はポリシーを更新し、CNAME を使用して設定された Cookie にもこれらの制限が適用されるようにしました。 現在、CNAME を使用してサーバー側で設定された Cookie と JavaScript を使用してクライアント側で設定された Cookie の両方が、ITP の下で 7 日間または 24 時間の有効期限に制限されています。 ITP ポリシーの詳細については、[トラッキング防止](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp)に関する [!DNL Apple] ドキュメントを参照してください。

CNAME 実装には cookie の有効期間に関するメリットはありませんが、他にもメリットがある場合があります。 これらのメリットには、広告ブロッカーや、データがトラッカーとして分類するドメインに送信されるのを防ぐ一般的でないブラウザーなどが含まれます。 このような場合、CNAME を使用すると、これらのツールを使用するユーザーのデータ収集が中断されるのを防ぐことができます。

また、CNAME 実装では、次の項目も指定できます。 **[!UICONTROL カスタム RDC タイプを選択]** ：ユーザーのヒットが最初にルーティングされる場所を制御します。 ほとんどのお客様は、カスタムの RDC タイプを使用しません。
