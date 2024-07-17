---
title: オプトインを使用し、ユーザーの同意に基づいて Experience Cloud アクティビティを制御する
description: Adobe Opt-in Object は、Adobe Experience Platform ID サービスの拡張機能で、エンドユーザーの同意に基づいて、Experience Cloud ソリューションが web ページに cookie を作成するかどうか、またはビーコンを開始するかどうかを制御するのに役立つよう設計されています。
exl-id: ac44e628-01ca-401c-864b-30fed0450e5f
source-git-commit: 0dca594c090095a01dfa2d02a98dfeba7ca02dca
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 100%

---

# ユーザーの同意に基づいて Experience Cloud アクティビティを制御する

Adobe [!UICONTROL Opt-In] Object は、Adobe [!UICONTROL Experience Platform ID サービス]の拡張機能です。この拡張機能は、エンドユーザーの同意に基づいて、Experience Cloud ソリューションが web ページに cookie を作成するかどうか、またはビーコンを開始するかどうか制御するのに役立つよう設計されています。

## [!UICONTROL オプトイン]の基本

プライバシー規制の重要な側面は、個人データの利用方法や利用者に関するユーザーの同意の取得と伝達です。[!UICONTROL ID サービス]の最新バージョン には、エンドユーザーの同意が得られているかどうかに基づいて、Experience Cloud ソリューションタグの条件付き実行（同意の前後など）を提供する機能が含まれます。 このプロセスについては、次の画像をご覧ください。

![ [!UICONTROL オプトイン]の仕組みを示す図 ](assets/opt-in.png)

[!UICONTROL オプトイン] は次のように動作します。

**ID サービスで[!UICONTROL オプトイン]が有効になっている場合（Boolean 変数を使用）、そのソリューションに対する同意が得られるまで、Experience Cloud ソリューションライブラリのタグを実行したり cookie を設定するのが遅れます。**

また、[!UICONTROL オプトイン] では、ユーザーの同意前にタグを実行するかどうかを決定し、この同意情報を（エンドユーザーの同意とともに）保存して、その後のヒットで使用することもできます。同意のストレージは、[!UICONTROL オプトイン]オプションで利用できます。または、CMP と統合して同意の選択を保存することもできます。

## [!UICONTROL オプトイン]の有効化と設定

[!UICONTROL オプトイン]は、Adobe Experience Platform タグ（以前の Launch）で最も簡単に設定できます。方法については、次の短いビデオをご覧ください。

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

Experience Platform タグを使用していない場合は、[ドキュメント](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/getting-started.html?lang=ja)に記載されているように、グローバル訪問者オブジェクトの初期化で[!UICONTROL オプトイン]を設定できます。

## ページへの[!UICONTROL オプトインの実装]

このセットアップとバックエンドの設定はすべて、サイト訪問者に同意オプションを提示するためのインターフェイスを提供するための準備です。この UI は自分で作成することも、CMP（Consent Management Platform）パートナーを使用して作成することもできます。

同意を収集するために[!UICONTROL オプトイン]を使用する UI を設定する場合は、[!UICONTROL オプトイン]に関連付けられる API を呼び出して、一部またはすべての Adobe Experience Cloud ソリューションに同意するよう通知を設定する必要があります。これらの API に関する詳細は、[オプトインリファレンスドキュメント](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/api.html?lang=ja)を参照してください。オプトインに関する追加情報は、その前後のドキュメントページにも含まれています。

## [!UICONTROL オプトイン]のデモ

次のビデオでは、ページ上で[!UICONTROL オプトイン]の仕組みを示す簡単なデモと、Experience Cloud ソリューションによる cookie の設定、ビーコンの開始などにどのような影響が出るかを説明します。

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**注：**&#x200B;この記事の作成時点では、一部の Experience Cloud アプリケーションのライブラリには[!UICONTROL オプトイン]が組み込まれていません。現在、[!UICONTROL オプトイン]がサポートされているライブラリは、次のとおりです。

* ID サービス
* Analytics
* Audience Manager
* [!DNL Target]
