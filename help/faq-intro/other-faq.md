---
description: 他の Experience Cloud ソリューションでの ID サービス利用の特徴、機能、問題に関するよくある質問です。
keywords: ID サービス
seo-description: 他の Experience Cloud ソリューションでの ID サービス利用の特徴、機能、問題に関するよくある質問です。
seo-title: 他の Experience Cloud ソリューションに関する FAQ
title: 他の Experience Cloud ソリューションに関する FAQ
uuid: 7d848663-6cbb-4d80-ab06-7b6d2dc20e2b
exl-id: d1164951-01c9-4375-981a-f87d8a280e4b
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '211'
ht-degree: 100%

---

# 他の Experience Cloud ソリューションに関する FAQ {#faqs-for-other-experience-cloud-solutions}

他の Experience Cloud ソリューションでの ID サービス利用の特徴、機能、問題に関するよくある質問です。

## Dynamic Tag Management（DTM） {#section-7ac4b9c1f1fd45a5a03eac3fb5968af7}

**Dynamic Tag Management を使用して訪問者 ID サービスをデプロイできますか。**

はい。それが推奨されるデプロイオプションです。

[DTM を使用した標準的な実装](../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445)を参照してください。

## Analytics と Audience Manager {#section-b3dd206d497041acb04554c6fb1c912a}

**Experience Cloud Identity Service を実装すると、ユーザーの訪問履歴が [!DNL Adobe Analytics] から [!DNL Audience Manager] にエクスポートされますか。**

この場合、次の 2 つのことが考えられます。

* ID サービスの実装後にユーザーの訪問アクティビティがある場合は、[!DNL Audience Manager] へのエクスポート対象データに訪問者とその履歴が含まれます。
* ID サービスの実装後にユーザーに訪問アクティビティがない場合、訪問者とその履歴は Audience Manager へのデータエクスポートには含まれません。 新しいアクティビティが存在しないので、Analytics ID を Experience Cloud ID に関連付けることはできません。
