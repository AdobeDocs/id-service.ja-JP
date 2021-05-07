---
description: メインのエントリサイトがあり、顧客が他のドメインを訪問する前にメインのエントリサイトで顧客の識別ができる場合には、CNAME を使用することで、サードパーティ Cookie を受け入れないブラウザー（Safari など）でもクロスドメイントラッキングをおこなうことができます。
keywords: 操作の順序;ID サービス
seo-description: メインのエントリサイトがあり、顧客が他のドメインを訪問する前にメインのエントリサイトで顧客の識別ができる場合には、CNAME を使用することで、サードパーティ Cookie を受け入れないブラウザー（Safari など）でもクロスドメイントラッキングをおこなうことができます。
seo-title: CNAME実装の概要
title: CNAME実装の概要
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: ebeca9e285af71872c05d58ba252ca65bde24f3d
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 28%

---


# CNAME実装の概要{#cname-implementation-overview}

CNAMEの実装を使用すると、Adobeが使用する収集ドメインをカスタマイズして、独自のドメインと一致させることができます。 これにより、Adobeは、JavaScriptを使用してクライアント側ではなく、サーバー側でファーストパーティcookieを設定できます。 以前は、これらのサーバーサイドのファーストパーティcookieには、Appleのインテリジェントトラッキング防止(ITP)ポリシーに基づいて課された制限は適用されませんでした。 しかし、2020年11月、[!DNL Apple]はポリシーを更新し、CNAMEを使用して設定されたcookieにもこれらの制限が適用されるようにしました。 現在、CNAMEを介してサーバー側に設定されたCookieと、JavaScriptを介してクライアント側に設定されたCookieの両方が、ITPの下で7日または24時間の有効期限に制限されています。 ITPポリシーの詳細については、この[!DNL Apple]ドキュメント[をトラッキング防止](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp)に対して参照してください。

CNAMEの導入ではcookieの有効期間に関して何のメリットも得られませんが、広告ブロッカーや一般的でないブラウザーなど、データがトラッカーとして分類されるドメインに送信されないというメリットがある可能性があります。 このような場合、CNAMEを使用すると、これらのツールを使用するユーザーにとってデータ収集が中断されるのを防ぐことができます。