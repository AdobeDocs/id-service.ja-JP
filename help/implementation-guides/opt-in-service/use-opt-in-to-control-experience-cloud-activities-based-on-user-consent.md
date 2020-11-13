---
title: ユーザーの同意に基づいてExperience Cloudアクティビティを制御する場合にオプトインを使用する
description: Adobeオプトインオブジェクトは、Adobe Experience PlatformIDサービスの拡張機能です。エンドユーザーの同意に基づいて、Webページにcookieを作成したり、ビーコンを開始したりできるExperience Cloudソリューションを選択するのに役立ちます。
translation-type: tm+mt
source-git-commit: 3aba8820ef40d068c732a637be5ab67652a8d35d
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---


# ユーザーの同意に基づいてExperience Cloudアクティビティを制御する

Adobe [!UICONTROL オプトインオブジェクトは、Adobe] Experience PlatformIDサービスの拡張です 。エンドユーザーの同意に基づいて、Webページにcookieを作成したり、ビーコンを開始したりできるExperience Cloudソリューションを制御できます。

## オプトインの基本 [!UICONTROL 事項]

プライバシー規制の重要な側面は、個人データの利用方法や利用者に関するユーザーの同意の取得と伝達です。 最新バージョンの [!UICONTROL Identity Service] には、ユーザー(UI)とAdobeソリューションの間に配置され、エンドユーザーの同意があるかどうかに基づいて、Adobe Experience Cloudのソリューションタグの条件付き実行（事前承諾や事後承諾など）を提供する機能が含まれます。 これは次の画像に表示されます。

![オプトイン [!UICONTROL の仕組みの図]](assets/opt-in.png)

[!UICONTROL オプトインは基本的に] 、ゲートキーパーですか。それとも、キーマスターですか。 君が決める。

要するに次のようになる。

**IDサービスで [!UICONTROL オプトイン] （Boolean変数を使用）が有効になっている場合、ソリューションの同意が得られるまで、Experience Cloudソリューションライブラリのタグの実行またはcookieの設定が遅れます。**

[!UICONTROL また、オプトインを使用すると] 、ユーザーの同意の *前にタグが発生するかどうかを決定できます。その後* 、この同意情報（エンドユーザーの同意と共に）が保存され、後続のヒットで使用できるようになります。 同意のストレージは、 [!UICONTROL オプトイン] ・オプションで利用できます。または、CMPと統合してストアの同意を得ることもできます。

## オプトインの有効化と [!UICONTROL 設定]

[!UICONTROL また、オプトイン] (opt-in)は、Adobe Experience Platform Launchで最も簡単に設定できます。 次の短いビデオを表示して、その方法を確認してください。

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

Experience Platform Launchを使用していない場合は、 [!UICONTROL ドキュメントに示すように、グローバル訪問者オブジェクトの初期化時に]オプトイン [の設定を設定できます](https://marketing.adobe.com/resources/help/en_US/mcvid/getting-started.html)。

## ページへの [!UICONTROL オプトインの実装] （英語のみ）

このセットアップとバックエンドの設定はすべて、サイト訪問者に同意オプションを提示するためのインターフェイスを提供する準備のためのものです。 このUIは自分で作成することも、CMP (Consent Management Platform)パートナーを使用してUIを作成することもできます。

同意を収集するために [!UICONTROL オプトインを使用するUIを設定する場合は、オプトインに関連付けられるAPIを呼び出して、一部またはすべてのAdobe Experience Cloudソリューションに同意するように通知するように設定する必要があります] 。 これらのAPIに関する詳細は、 [オプトインリファレンスドキュメントを参照してください](https://marketing.adobe.com/resources/help/en_US/mcvid/api.html)。 オプトインに関する追加情報は、その他のドキュメントページにもあります。

## [!UICONTROL オプトイン] ・デモ

次のビデオでは、ページでの [!UICONTROL オプトインの操作に関する簡単なデモを参照し] 、Experience Cloudソリューションがcookieを設定できるかどうか、ビーコンを開始できるかどうかにどのような影響があるかを確認します。

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**注意：** この記事を作成する際には、すべてのExperience Cloudソリューションのライブラリに [!UICONTROL オプトインが組み込まれていないことに注意してください] 。 現在、 [!UICONTROL オプトインがサポートされているライブラリは] 、次のとおりです。

* ID サービス
* Analytics
* Audience Manager
* [!DNL Target]
