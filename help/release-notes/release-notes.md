---
description: Experience Cloud ID サービスの機能リリース、更新、変更点です。
keywords: ID Service
seo-description: Experience Cloud ID サービスの機能リリース、更新、変更点です。
seo-title: 2020 年リリースノート
title: 2020 年リリースノート
translation-type: tm+mt
source-git-commit: c4da0f3da99a96d2be7421f49e0e88286d0505e0

---


# Experience Cloud リリースノート - 2020 {#release-notes}

Experience Cloud ID サービス（ECID）の機能リリース、更新、変更点です。

## バージョン 4.6

* デフォル `loadSSL` トでフラグをオンにしました。 IDサービスへのすべての呼び出しは、デフォルトでオ `https` ンになります。  ページからhttpでIDサービスを呼び出す場合は、falseに設定でき `non-ssl` ます。
* が報告する問題を修正するために、バージ `Internet-Explorer (IE)` ョンの検出に使用する関数を更新しまし `ESLint`た。
ECIDがoptInに設定され、後で更新され `Internet-Explorer (IE) 11` る場合のパフォーマンスの問 `pre-approval` 題を修正しました。

## バージョン 4.5

* バージョン 4.5 以降では、ECID は `setCustomerIDs` メソッドに送信された空の ID を拒否します。
* Fixed an issue occurring when opt-in is configured as `doesOptInApply=false` and `isIabContext=true`.
