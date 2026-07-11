---
description: 訪問者ID サービスの機能リリース、更新、変更。
keywords: 訪問者 ID サービス
title: 2019 年リリースノート
exl-id: 11439e27-9740-4afc-a2b8-5e35d179f34f
TQID: https://experienceleague.adobe.com/KnO04dnP6z7gKrr8vkFiiToDSBfClpiOJkGq8949ahA
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 426
ht-degree: 67%

---

# 2019 年リリースノート {#release-notes}

訪問者ID サービスの機能リリース、更新、変更。

## バージョン 4.4.1

[!UICONTROL Experience Cloud ID Service] タグ拡張機能でMedia Analyticsの事前オプトイン承認チェックボックスを追加します。

**修正点**

* [!UICONTROL Experience Cloud ID Service] タグ拡張機能のpreOptInApprovals入力文字列解析で問題が発生しました。
* trackingServer 使用時のパフォーマンスの低下の問題を修正しました。

## バージョン 4.4 {#version-4point4}

**新機能**

[setCustomerIDs の SHA256 ハッシュサポート](/help/reference/hashing-support.md) 訪問者ID サービス（ECID）は、顧客IDまたはメールアドレスを渡したり、ハッシュ化されたIDを渡したりできるSHA-256 ハッシュアルゴリズムをサポートしています。

**修正点、機能強化、改善点**

* `cookieDomain` の設定を更新しました。 ECID ライブラリは、`initConfig` の空の文字列 `cookieDomain` を除外して、トップレベル cookie ドメインを使用できるようになりました（getDomain メソッドで返されます）。
* `getVisitorValues` の `localVisitor` に関連するバグを修正しました。
* `getVisitorValue` メソッドで返される Safari ブラウザーの MCOPTOUT 値に不整合があるバグを修正しました。
* オプトインライブラリを更新し、イベントから登録解除するための `optIn.off` を追加しました。
* `setTimeout` が一部のお客様サイトでコンテンツセキュリティポリシー（CSP）に違反する、setTimeout 関数に関するバグを修正しました。

## バージョン 4.3 {#version-4point3}

**ITP 2.1 をサポートします**。 ファーストパーティ CNAME でトラッキングサーバーが設定されている場合、新しい cookie（s_ecid）が ECID 値と共に配置されます。 ECID ライブラリは、この値を参照して、7 日以上 ID を保持します。 [Safari ITP での ECID ライブラリの手法](/help/reference/ecid-library-methods.md)を参照してください。

**secureCookie 設定のバグを修正しました。**

## バージョン 4.1

新しい API の変更に伴い、`publishDestinations` を更新しました。 この更新により、必要に応じて、ID — 同期中にページのリファラー情報を表示できます。

## バージョン 4.2

ECID オプトインオブジェクトで使用できる、IAB TCF 用の Audience Manager プラグインをサポートします。

**修正点**

* IAB と OptIn で、再訪問する顧客の MID を取得できない問題を修正しました。
* オプトイン doesOptInApply設定のバグを修正しました。
* ECID オプトアウトで ID 同期が無効になる問題を修正しました。

## バージョン 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**オプトインサービス**。 オプトインは、ECIDの拡張機能で、CX エンタープライズライブラリが訪問者のweb ページにCookieを作成できるかどうかを（どのライブラリで）制御できます。 [tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=ja)を使用すると、Analytics、Target、Audience Managerなどの一部のCX Enterprise ソリューションを有効にして、CX Enterprise ソリューションに対する訪問者のオプトイン同意を簡単に収集できます。また、一部のCX Enterprise ソリューションを有効にして、同意管理システムにオプトインすることもできます。

## バージョン 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| 項目 | 説明 |
|---|---|
| `disableIdSyncs` フラグに文字列を渡すと動作しない | 修正しました。 `getInstance` 関数の `disableidSyncs` パラメーターに設定された値は現在、有効になっています。 |
| サードパーティ iFrame が ECID を取得しない問題を修正しました。 | Safari モバイル上の ECID および機能していない各種 iFrame の ECID を修正しました。 |

