---
title: オプトインを使用し、ユーザーの同意に基づいて Experience Cloud アクティビティを制御する
description: Adobe Opt-In Object は、Adobe Experience Platform ID サービスの拡張機能です。エンドユーザーの同意に基づいて、Experience Cloud ソリューション Web ページ上に cookie を作成したり、ビーコンを開始したりできるようにするか、およびどのソリューションを使用するかを制御できます。
translation-type: ht
source-git-commit: 3aba8820ef40d068c732a637be5ab67652a8d35d
workflow-type: ht
source-wordcount: '554'
ht-degree: 100%

---


# ユーザーの同意に基づいて Experience Cloud アクティビティを制御する

Adobe [!UICONTROL Opt-In] Object は、Adobe [!UICONTROL Experience Platform ID サービス]の拡張機能です。エンドユーザーの同意に基づいて、Experience Cloud ソリューション Web ページ上に cookie を作成したり、ビーコンを開始したりできるようにするか、およびどのソリューションを使用するかを制御できます。

## [!UICONTROL オプトイン]の基本

プライバシー規制の重要な側面は、個人データの利用方法や利用者に関するユーザーの同意の取得と伝達です。最新バージョンの [!UICONTROL ID サービス]には、ユーザー（UI）と Adobe ソリューションの間に配置され、エンドユーザーの同意があるかどうかに基づいて、Adobe Experience Cloud のソリューションタグの条件付き実行（事前承諾や事後承諾など）を提供する機能が含まれます。これについては、次の画像で示します。

![[!UICONTROL オプトイン]の仕組みを示す図](assets/opt-in.png)

[!UICONTROL オプトイン]が基本的にゲートキーパーとなるか、キーマスターとなるかは、あなた次第です。

つまり、

**ID サービスで[!UICONTROL オプトイン]が有効になっている場合（Boolean　変数により）、そのソリューションに対する同意が得られるまで、Experience Cloud ソリューションライブラリのタグの実行または cookie の設定は遅れます。**

また、[!UICONTROL オプトイン]を使用すると、ユーザーの同意を得る&#x200B;*前に*&#x200B;タグを実行するかどうかを決定できます。その後、この同意情報は（エンドユーザーによって提供された同意と共に）保存され、後続のヒットで使用できるようになります。同意のストレージは、[!UICONTROL オプトイン]オプションで利用できます。または、CMP と統合して同意の選択を保存することもできます。

## [!UICONTROL オプトイン]の有効化と設定

[!UICONTROL また、オプトイン]は、Adobe Experience Platform Launch で最も簡単に設定できます。次の短いビデオを閲覧して、方法をご確認ください。

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12&captions=jpn)

Experience Platform Launch を使用していない場合は、[ドキュメント](https://marketing.adobe.com/resources/help/ja_JP/mcvid/getting-started.html)に示すように、グローバル訪問者オブジェクトの初期化時に[!UICONTROL オプトイン]を設定できます。

## ページへの[!UICONTROL オプトインの実装]

このセットアップとバックエンドの設定はすべて、サイト訪問者に同意オプションを提示するためのインターフェイスを提供するための準備です。この UI は自分で作成することも、CMP（Consent Management Platform）パートナーを使用して作成することもできます。

同意を収集するために[!UICONTROL オプトイン]を使用する UI を設定する場合は、[!UICONTROL オプトイン]に関連付けられる API を呼び出して、一部またはすべての Adobe Experience Cloud ソリューションに同意するよう通知を設定する必要があります。これらの API に関する詳細は、[オプトインリファレンスドキュメント](https://marketing.adobe.com/resources/help/ja_JP/mcvid/api.html)を参照してください。オプトインに関する追加情報は、その前後のドキュメントページにも含まれています。

## [!UICONTROL オプトイン]のデモ

次のビデオでは、ページでの[!UICONTROL オプトイン]の仕組みに関する簡単なデモを参照し、Experience Cloud ソリューションで cookie を設定できるかどうか、ビーコンを開始できるかどうかなどにどのような影響があるかを確認します。

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12&captions=jpn)

**注意：**&#x200B;この記事の作成時点では、[!UICONTROL オプトイン]が組み込まれていない Experience Cloud ソリューションのライブラリもあったことに注意してください。現在、[!UICONTROL オプトイン]がサポートされているライブラリは、次のとおりです。

* ID サービス
* Analytics
* Audience Manager
* [!DNL Target]
