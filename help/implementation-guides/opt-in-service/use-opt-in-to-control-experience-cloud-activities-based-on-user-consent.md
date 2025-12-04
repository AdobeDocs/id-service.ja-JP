---
title: オプトインを使用し、ユーザーの同意に基づいて Experience Cloud アクティビティを制御する
description: Adobe Opt-in Object は、Adobe Experience Platform ID サービスの拡張機能で、エンドユーザーの同意に基づいて、Experience Cloud ソリューションが web ページに cookie を作成するかどうか、またはビーコンを開始するかどうかを制御するのに役立つよう設計されています。
exl-id: ac44e628-01ca-401c-864b-30fed0450e5f
source-git-commit: e185c7d2b7582b52adbe9b525be7868ab8bfa374
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 36%

---

# ユーザーの同意に基づいて Experience Cloud アクティビティを制御する

Adobe [!UICONTROL Opt-in] Object は、Adobe [!UICONTROL Experience Platform Identity Service] の拡張機能です。この拡張機能は、エンドユーザーの同意に基づいて、Experience Cloud ソリューションが web ページに cookie を作成するかどうか、またはビーコンを開始するかどうか制御するのに役立つよう設計されています。

## [!UICONTROL Opt-In] の基本

プライバシー規制の重要な側面は、個人データの利用方法や利用者に関するユーザーの同意の取得と伝達です。[!UICONTROL Identity Service] の最新バージョンには、エンドユーザーの同意が得られているかどうかに基づいて、Experience Cloud ソリューションタグの条件付き実行（同意の前後など）を提供する機能が含まれます。 このプロセスについては、次の画像をご覧ください。

![[!UICONTROL Opt-in] の仕組みを示す図 ](assets/opt-in.png)

[!UICONTROL Opt-in] は次のように動作します。

**ID サービスで [!UICONTROL Opt-in] が有効になっている場合（Boolean 変数を使用）、そのソリューションに対する同意が得られるまで、Experience Cloud ソリューションライブラリのタグを実行したり Cookie を設定するのが遅れます。**

[!UICONTROL Opt-in] た、ユーザーの同意前にタグを実行するかどうかを決定し、この同意情報を（エンドユーザーの同意とともに）保存して、その後のヒットで使用することもできます。 同意の保存は、[!UICONTROL Opt-in] のオプションで使用できます。または、CMP と統合して同意の選択を保存することもできます。

## [!UICONTROL Opt-In] の有効化と設定

[!UICONTROL Opt-in] は、Adobe Experience Platform タグ（以前の Launch）で最も簡単に設定できます。 方法については、次の短いビデオをご覧ください。

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

Experience Platform タグを使用していない場合は、[!UICONTROL Opt-in] ドキュメント [ に記載されているように、グローバル訪問者オブジェクトの初期化で ](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/getting-started.html?lang=ja) の設定を行うことができます。

## ページでの [!UICONTROL Opt-In] の実装

このセットアップとバックエンドの設定はすべて、サイト訪問者に同意オプションを提示するためのインターフェイスを提供するための準備です。この UI は自分で作成することも、CMP（Consent Management Platform）パートナーを使用して作成することもできます。

[!UICONTROL Opt-in] を使用して同意を収集するように UI を設定する場合は、[!UICONTROL Opt-in] にフックされる API を呼び出し、一部またはすべてのAdobe Experience Cloud ソリューションに同意を与えるように通知するように設定する必要があります。 これらの API に関する詳細は、[オプトインリファレンスドキュメント](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/api.html?lang=ja)を参照してください。オプトインに関する追加情報は、その前後のドキュメントページにも含まれています。

## [!UICONTROL Opt-In] デモ

次のビデオでは、ページ上で [!UICONTROL Opt-in] を操作する方法の簡単なデモと、Experience Cloud ソリューションによる cookie の設定、ビーコンの開始などにどのような影響が出るかを説明します。

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**注意：** この記事の作成時点では、一部のExperience Cloud アプリケーションのライブラリには [!UICONTROL Opt-in] が組み込まれていません。 現在 [!UICONTROL Opt-in] でサポートされているライブラリは次のとおりです。

* ID サービス
* Analytics
* Audience Manager
* [!DNL Target]

