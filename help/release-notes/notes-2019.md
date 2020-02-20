---
description: Experience Cloud Identity Service の機能リリース、更新、変更点です。
keywords: ID Service
seo-description: Experience Cloud Identity Service の機能リリース、更新、変更点です。
seo-title: 2019 年リリースノート
title: 2019 年リリースノート
uuid: a5a59410-7f85-48f9-a30a-fef1c2e2b558
translation-type: tm+mt
source-git-commit: 25a9af7a28462bc0bd26cf4a5a58203e76a83366

---


# Experience Cloud release notes - 2019 {#release-notes}

Experience Cloud Identity Service の機能リリース、更新、変更点です。

## バージョン 4.4.1

ECID起動拡張でのメディア解析用の事前オプトイン承認チェックボックスの追加(CORE-33185)

**修正点**

* ECID起動拡張preOptInApprovals入力文字列解析に関する問題(CORE-34041)
* trackingServerが使用されている場合のパフォーマンス低下(CORE-32387)

## バージョン 4.4 {#version-4point4}

**新機能**

[setCustomerIDs の SHA256 ハッシュサポート](/help/reference/hashing-support.md)Experience Cloud ID Service（ECID）は、顧客 ID または電子メールアドレスを渡し、ハッシュされた ID を受け取ることが可能な、SHA-256 ハッシュアルゴリズムをサポートします。

**修正点、機能強化、改善点**

* `cookieDomain` の設定を更新しました。ECID ライブラリは、`initConfig` の空の文字列 `cookieDomain` を除外して、トップレベル cookie ドメインを使用できるようになりました（getDomain メソッドで返されます）。（CORE-29223）
* `getVisitorValues` の `localVisitor` に関連するバグを修正しました。（CORE-31287）
* `getVisitorValue` メソッドで返される Safari ブラウザーの MCOPTOUT 値に不整合があるバグを修正しました。（CORE-29719）
* オプトインライブラリを更新し、イベントから登録解除するための `optIn.off` を追加しました。
* `setTimeout` が一部のお客様サイトでコンテンツセキュリティポリシー（CSP）に違反する、setTimeout 関数に関するバグを修正しました。（CORE-30623）

## バージョン 4.3 {#version-4point3}

**ITP 2.1 をサポート**&#x200B;します。ファーストパーティ CNAME でトラッキングサーバーが設定されている場合、新しい cookie（s_ecid）が ECID 値と共に配置されます。ECID ライブラリは、この値を参照して、7 日以上 ID を保持します。[Safari ITP での ECID ライブラリの手法](/help/reference/ecid-library-methods.md)を参照してください。

**secureCookie 設定のバグを修正しました。**

## バージョン 4.1

新しいAPI `publishDestinations` の変更に応じて更新します。 この更新により、必要に応じて、ID — 同期中にページのリファラー情報を表示できます。（CORE-23693）

## バージョン 4.2

IAB TCF用Audience Managerプラグインがサポートされ、ECIDオプトインオブジェクトを介して利用できます。

**修正点**

* IAB + optInが顧客の再訪問のためにMIDを取得できない(CORE-26022)
* DTMのオプトインdoesOptInApply設定に関するバグを修正しました。(DTM-12958)
* ECIDオプトアウトはID同期を無効にします(CORE-23814)。

## バージョン 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**オプトインサービス**。オプトインは、Experience Cloud ID（ECID）の拡張であり、使用すると、Experience Cloud ライブラリで Web ページに訪問者に対する Cookie を作成可能にするかどうか（およびどのライブラリで作成可能にするか）を指定できます。Using [Experience Platform Launch](https://docs.adobelaunch.com/), you can simplify gathering visitor opt-in consents for Experience Cloud solution by enabling Analytics, Target, Audience Manager, and other or all select Experience Cloud solutions to opt-in to your consent management system.

## バージョン 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| 項目 | 説明 |
|---|---|
| `disableIdSyncs` フラグに文字列を渡すと動作しない | 修正しました。`getInstance` 関数の `disableidSyncs` パラメーターに設定された値は現在、有効になっています。 |
| サードパーティ iFrame が ECID を取得しない | Safari モバイル上の ECID および機能していない各種 iFrame の ECID を修正しました。 |
