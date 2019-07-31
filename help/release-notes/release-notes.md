---
description: Experience Cloud IDサービスの機能リリース、更新、または変更。
keywords: ID サービス
seo-description: Experience Cloud IDサービスの機能リリース、更新、または変更。
seo-title: 2019 年リリースノート
title: 2019 年リリースノート
uuid: a5a59410-7f85-48f9-a30a-fef1c2e2b558
translation-type: tm+mt
source-git-commit: 4532d09cc9b4d83fa62c13bd1adac7abdae222b1

---


# 2019 年リリースノート {#release-notes}

Experience Cloud IDサービスの機能リリース、更新、または変更。

## 2019 年リリースノート {#topic-1b9a1c3ec5044e1c987785950f697e25}

[!DNL Experience Cloud] ID サービスの機能リリース、更新、変更点です。

## バージョン 4.4 {#version-4point4}

**新機能**

[setCustomerIDsのSHA256ハッシュサポート](/help/reference/hashing-support.md)。Experience Cloud IDサービス（ECID）は、SHA-256ハッシュアルゴリズムをサポートし、顧客IDまたは電子メールアドレスを渡すことができ、ハッシュIDを渡すことができます。

**修正点、機能強化、改善点**

* We made a configuration update to `cookieDomain`. The ECID library now filters out the empty string `cookieDomain` in `initConfig` and uses the top level cookie domain, which is returned by the getDomain method. （CORE-29223）
* `getVisitorValues` に関連するバグを修正 `localVisitor`しました。（CORE-31287）
* We fixed a bug where there was an inconsistency for the MCOPTOUT value in the Safari browser, returned by the `getVisitorValue` method. （CORE-29719）
* We updated the Opt-in library by adding `optIn.off` to unsubscribe from events.
* We fixed a bug related to the setTimeout function, where `setTimeout` violated the Content Security Policy (CSP) on some customer sites. （CORE-30623）

## バージョン 4.3 {#version-4point3}

**ITP2.1のサポート**。トラッキングサーバーがファーストパーティCNAMEで設定されている場合、新しいcookie（s_ ecid）がEID値で配置されます。ECIDライブラリは、7日を超えてIDを永続化するための値を参照します。See [ECID library methods in a Safari ITP world](/help/reference/ecid-library-methods.md).

**SecureCookie設定のバグ修正。**

## バージョン 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**オプトインサービス**。オプトインは、Experience Cloud ID（ECID）の拡張機能で、Experience Cloudライブラリで訪問者のWebページにcookieを作成できるかどうかを制御できます。[Experience Platform Launch](https://docs.adobelaunch.com/)を使用すると、Analytics、Target、Audience Managerを有効にして、Experience Cloudソリューションの訪問者オプトインの承諾を単純化したり、選択したExperience Cloudソリューションを使用して同意管理システムにオプトインしたりできます。

## バージョン 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| 項目 | 説明 |
|---|---|
| `disableIdSyncs` フラグに文字列を渡すと動作しない | 修正しました。`getInstance` 関数の `disableidSyncs` パラメーターに設定された値は現在、有効になっています。 |
| サードパーティ iFrame が ECID を取得しない | Safari モバイル上の ECID および機能していない各種 iFrame の ECID を修正しました。 |

