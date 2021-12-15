---
title: オプトインを使用し、ユーザーの同意に基づいて Experience Cloud アクティビティを制御する
description: Adobeオプトインオブジェクトは、Adobe Experience Platform ID サービスの拡張機能です。エンドユーザーの同意に基づいて、Web ページで Cookie を作成したり、ビーコンを開始したりできるExperience Cloudソリューションの種類と種類を制御できます。
exl-id: ac44e628-01ca-401c-864b-30fed0450e5f
source-git-commit: 0dca594c090095a01dfa2d02a98dfeba7ca02dca
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 47%

---

# ユーザーの同意に基づいて Experience Cloud アクティビティを制御する

Adobe [!UICONTROL オプトイン] オブジェクトはAdobeの拡張です [!UICONTROL Experience PlatformID サービス]は、エンドユーザーの同意に基づいて、web ページで cookie を作成したり、ビーコンを開始したりできるExperience Cloudソリューションの種類と種類を制御するのに役立ちます。

## [!UICONTROL オプトイン]の基本

プライバシー規制の重要な側面は、個人データの利用方法や利用者に関するユーザーの同意の取得と伝達です。の最新バージョン [!UICONTROL ID サービス] には、エンドユーザーの同意が得られているかどうかに基づいて、Experience Cloudソリューションタグの条件付き実行（同意の前後など）を提供する機能が含まれます。 このプロセスを次の画像に示します。

![ [!UICONTROL オプトイン]の仕組みを示す図 ](assets/opt-in.png)

[!UICONTROL オプトイン] は次のように機能します。

**ID サービスで[!UICONTROL オプトイン]が有効になっている場合（Boolean　変数により）、そのソリューションに対する同意が得られるまで、Experience Cloud ソリューションライブラリのタグの実行または cookie の設定は遅れます。**

[!UICONTROL オプトイン] また、タグがユーザーの同意の前に実行されるかどうかを指定し、その後のヒットで使用できるように、この同意情報（エンドユーザーの同意と共に）を保存することもできます。 同意のストレージは、[!UICONTROL オプトイン]オプションで利用できます。または、CMP と統合して同意の選択を保存することもできます。

## [!UICONTROL オプトイン]の有効化と設定

[!UICONTROL オプトイン] は、Adobe Experience Platformタグ（以前の Launch）を使用して最も簡単に設定できます。 次の短いビデオを閲覧して、方法をご確認ください。

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

Experience Platformタグを使用しない場合、 [!UICONTROL オプトイン]グローバル訪問者オブジェクトの初期化時のの設定 ( [ドキュメント](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/getting-started.html?lang=en).

## ページへの[!UICONTROL オプトインの実装]

このセットアップとバックエンドの設定はすべて、サイト訪問者に同意オプションを提示するためのインターフェイスを提供するための準備です。この UI は自分で作成することも、CMP（Consent Management Platform）パートナーを使用して作成することもできます。

同意を収集するために[!UICONTROL オプトイン]を使用する UI を設定する場合は、[!UICONTROL オプトイン]に関連付けられる API を呼び出して、一部またはすべての Adobe Experience Cloud ソリューションに同意するよう通知を設定する必要があります。これらの API に関する詳細は、[オプトインリファレンスドキュメント](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/api.html?lang=en)を参照してください。オプトインに関する追加情報は、その前後のドキュメントページにも含まれています。

## [!UICONTROL オプトイン]のデモ

次のビデオでは、 [!UICONTROL オプトイン] の機能と、Experience Cloudソリューションで cookie を設定できるかどうか、ビーコンを開始できるかどうかなどにどのような影響があるかを説明します。

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**注意：** この記事を書く時点では注意が必要だ [!UICONTROL オプトイン] には、すべてのライブラリアプリケーション用のライブラリが組み込まれているわけではありません。Experience Cloud 現在、[!UICONTROL オプトイン]がサポートされているライブラリは、次のとおりです。

* ID サービス
* Analytics
* Audience Manager
* [!DNL Target]
