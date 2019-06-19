---
description: 同じレポートスイートにデータを送信する複数の JavaScript ファイルがある場合、またはサイト上で Flash ビデオによる測定などの他のテクノロジーを使用している場合は、猶予期間を設定することをお勧めします。
keywords: ID サービス
seo-description: 同じレポートスイートにデータを送信する複数の JavaScript ファイルがある場合、またはサイト上で Flash ビデオによる測定などの他のテクノロジーを使用している場合は、猶予期間を設定することをお勧めします。
seo-title: ID サービスの猶予期間
title: ID サービスの猶予期間
uuid: 10a7db7d- de32-4379-914f- edaf929efa32
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# ID サービスの猶予期間{#the-id-service-grace-period}   

同じレポートスイートにデータを送信する複数の JavaScript ファイルがある場合、またはサイト上で Flash ビデオによる測定などの他のテクノロジーを使用している場合は、猶予期間を設定することをお勧めします。

[!DNL Experience Cloud] ID サービスを導入すると、新しい訪問者はデータ収集サーバーから Analytics 訪問者 ID を受け取らなくなります。サイトの一部で [!DNL Experience Cloud] ID サービスの実装が終わっていない場合は、訪問者がこれらのセクションを訪問したときに、Experience Cloud ID が認識されず、訪問者には従来の Analytics 訪問者 ID が割り当てられてしまいます。そうなると、訪問数が重複してカウントされ、属性が正しく認識されません。

例えば、サイトのサポートセクションを別の CMS で管理している場合は、そのセクション用に別の Analytics JavaScript ファイルを使用していることがあります。このサポートサイトに訪問者 ID サービスを導入する前にメインサイトで訪問者 ID を導入した場合は、新しい訪問者はサポートセクションの訪問時に従来の Analytics ID を受け取り、両方のサイトセクションへの訪問がそれぞれ異なる訪問としてレポートされます。

複数の JavaScript ファイルまたは他のテクノロジー（Flash など）を使用しているサイトに [!DNL Experience Cloud] ID サービスを挿入すると、サイトのすべての部分で同時に ID サービスを有効にする必要があるので、調整の問題が発生する可能性があります。猶予期間を設定することにより、新しい訪問者は [!DNL Experience Cloud] ID サービスから引き続き Analytics 訪問者 ID を受け取るので、アップグレードされていない、まだ ID サービスを使用していないサイトのセクションでも、訪問者を一貫性のある形で識別できます。

>[!NOTE]
>
>猶予期間のサポートには [!DNL Experience Cloud] 、IDサービスのバージョン1.3以降が必要です。

## 猶予期間が必要な場合 {#section-fd34c7ff697348a39f49258b7d39eb42}

Analytics JavaScript ファイルが 1 つのみで、他の AppMeasurement ライブラリを使用していない場合は、猶予期間は必要ありません。1 つの JavaScript ファイルを更新すると、新しい訪問者は、訪問の間、一貫して Marketing Cloud ID を使用して識別されます。

*同じレポートスイート*にデータを送信する複数の JavaScript ファイルがある場合、またはサイト上で Flash ビデオによる測定などの他のテクノロジーを使用している場合は、猶予期間を設定することをお勧めします。

## 猶予期間を有効にするには {#section-512d5cd8570e483cbdd8b04457a16ced}

カスタマーケアに [お問い合わせ](https://helpx.adobe.com/marketing-cloud/contact-support.html)ください。
