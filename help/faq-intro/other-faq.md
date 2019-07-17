---
description: 他の Experience Cloud ソリューションでの ID サービス利用の特徴、機能、問題に関するよくある質問です。
keywords: ID サービス
seo-description: 他の Experience Cloud ソリューションでの ID サービス利用の特徴、機能、問題に関するよくある質問です。
seo-title: 他の Experience Cloud ソリューションに関する FAQ
title: 他の Experience Cloud ソリューションに関する FAQ
uuid: 7d848663-6cbb-4d80-ab06-7b6d2dc20e2b
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# 他の Experience Cloud ソリューションに関する FAQ{#faqs-for-other-experience-cloud-solutions}

他の Experience Cloud ソリューションでの ID サービス利用の特徴、機能、問題に関するよくある質問です。

## Dynamic Tag Management（DTM）{#section-7ac4b9c1f1fd45a5a03eac3fb5968af7}

**Dynamic Tag Management を使用して訪問者 ID サービスを導入できますか。**

はい。それが推奨される導入オプションです。

詳しくは、[DTM を使用した標準的な実装](../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445)を参照してください。

## Analytics と Audience Manager {#section-b3dd206d497041acb04554c6fb1c912a}

**Experience Cloud[!DNL Adobe Analytics]IDサービスを実装した[!DNL Audience Manager]後、ユーザーの訪問履歴がエクスポートされますか。**

この場合、次の 2 つのことが考えられます。

* ID サービスの実装後にユーザーの訪問アクティビティがある場合は、[!DNL Audience Manager] へのエクスポート対象データに訪問者とその履歴が含まれます。
* ID サービスの実装後にユーザーの訪問アクティビティがない場合は、Audience Manager へのエクスポート対象データに訪問者とその履歴は含まれません。新しいアクティビティが存在しないので、Analytics ID と Experience Cloud ID を関連付けることはできません。

