---
description: 同じレポートスイートにデータを送信する複数の JavaScript ファイルがある場合、またはサイト上で Flash ビデオによる測定などの他のテクノロジーを使用している場合は、猶予期間を設定することをお勧めします。
keywords: ID サービス
title: ID サービスの猶予期間
exl-id: 83b4898c-8358-458b-a798-1e3c9633afe9
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '417'
ht-degree: 100%

---

# ID サービスの猶予期間 {#the-id-service-grace-period}

同じレポートスイートにデータを送信する複数の JavaScript ファイルがある場合、またはサイト上で Flash ビデオによる測定などの他のテクノロジーを使用している場合は、猶予期間を設定することをお勧めします。

[!DNL Experience Cloud] ID サービスをデプロイすると、新しい訪問者はデータ収集サーバーから Analytics 訪問者 ID を受け取らなくなります。サイトの一部で [!DNL Experience Cloud] ID サービスの実装が終わっていない場合は、訪問者がこれらのセクションを訪問したときに、Experience Cloud ID が認識されず、訪問者には従来の Analytics 訪問者 ID が割り当てられてしまいます。この結果、訪問数が重複し、誤ったアトリビューションになるおそれがあります。

例えば、サイトのサポートセクションを別の CMS で管理している場合は、そのセクション用に別の Analytics JavaScript ファイルを使用していることがあります。このサポートサイトに訪問者 ID サービスをデプロイする前にメインサイトで訪問者 ID をデプロイした場合は、新しい訪問者はサポートセクションの訪問時に従来の Analytics ID を受け取り、両方のサイトセクションへの訪問がそれぞれ異なる訪問としてレポートされます。

複数の JavaScript ファイルまたは他のテクノロジー（Flash など）を使用しているサイトに [!DNL Experience Cloud] ID サービスを挿入すると、サイトのすべての部分で同時に ID サービスを有効にする必要があるので、調整の問題が発生する可能性があります。猶予期間を設定することにより、新しい訪問者は [!DNL Experience Cloud] ID サービスから引き続き Analytics 訪問者 ID を受け取るので、アップグレードされていない、まだ ID サービスを使用していないサイトのセクションでも、訪問者を一貫性のある形で識別できます。

>[!NOTE]
>
>猶予期間のサポートには、[!DNL Experience Cloud] ID サービスバージョン 1.3 以降が必要です。

## 猶予期間が必要な場合 {#section-fd34c7ff697348a39f49258b7d39eb42}

Analytics JavaScript ファイルが 1 つだけで、他の AppMeasurement ライブラリを使用していない場合は、猶予期間は必要ありません。 1 つの JavaScript ファイルを更新すると、新しい訪問者は、訪問の間、一貫して Experience Cloud ID を使用して識別されます。

*同じレポートスイート*&#x200B;にデータを送信する複数の JavaScript ファイルがある場合、またはサイト上で Flash ビデオの測定などの他のテクノロジーを使用している場合は、猶予期間を設定することをお勧めします。

## 猶予期間を有効にする方法を教えてください。 {#section-512d5cd8570e483cbdd8b04457a16ced}

[カスタマーケア](https://helpx.adobe.com/jp/marketing-cloud/contact-support.html)にお問い合わせください。
