---
description: Experience Cloud ID サービスの機能リリース、更新、変更点です。
keywords: ID Service
seo-description: Experience Cloud ID サービスの機能リリース、更新、変更点です。
seo-title: 2020 年リリースノート
title: 2020 年リリースノート
translation-type: ht
source-git-commit: c4da0f3da99a96d2be7421f49e0e88286d0505e0

---


# Experience Cloud リリースノート - 2020 {#release-notes}

Experience Cloud ID サービス（ECID）の機能リリース、更新、変更点です。

## バージョン 4.6

* デフォルトで `loadSSL` フラグをオンにしました。ID サービスへのすべての呼び出しは、デフォルトにより、`https` でオンになります。`non-ssl` ページから http で ID サービスを呼び出す場合は、false に設定できます。
* `ESLint` によって報告される問題を修正するため、`Internet-Explorer (IE)` のバージョン検出に使用する関数を更新しました。ECID に optIn `pre-approval` が提供され、後で承認された場合、`Internet-Explorer (IE) 11` でパフォーマンスの問題が発生するバグを修正しました。

## バージョン 4.5

* バージョン 4.5 以降では、ECID は `setCustomerIDs` メソッドに送信された空の ID を拒否します。
* オプトインが誤って `doesOptInApply=false` および `isIabContext=true` として設定されている際の問題を修正しました。
