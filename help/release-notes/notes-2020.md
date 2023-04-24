---
description: Experience Cloud Identity Service の機能リリース、更新、変更点です。
keywords: ID サービス
title: 2020 年リリースノート
exl-id: c9d7876e-debc-4c8e-8ebc-91646610c876
source-git-commit: dce2c0036f697507381d0763c2f6a9538155681c
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 66%

---

# Experience Cloud リリースノート - 2020 {#release-notes}

Experience Cloud ID サービスの機能リリース、更新、変更点です。

## バージョン 5.1.1

* AMCV Cookie を次の値で設定するためのパッチ修正 `SameSite=None` VisitorJS が iFrame に読み込まれる際に使用します。

## バージョン 5.1.0

* 追加中 `sameSiteCookie` config を使用して `SameSite` 属性を設定します。 この設定では、 `SameSite` 属性：
   * `Strict`
   * `Lax`
   * `None`

これらの属性値の詳細については、 [web.dev](https://web.dev/samesite-cookies-explained/) および [Chromium プロジェクトによる SameSite の更新](https://www.chromium.org/updates/same-site/).

## バージョン 5.0.1

* を含めるためのパッチ修正 `d_cf` フラグは、新しい IAB コンセントストリングがAdobeデータ収集エッジに送信されたときに発生します。

## バージョン 5.0.0

* 訪問者 5.0.0 リリース（をサポート） `IAB 2.0`.

## バージョン 4.6

* デフォルトで `loadSSL` フラグをオンにしました。ID サービスへのすべての呼び出しは、デフォルトにより、`https` でオンになります。`non-ssl` ページから http で ID サービスを呼び出す場合は、false に設定できます。
* `ESLint` によって報告される問題を修正するため、`Internet-Explorer (IE)` のバージョン検出に使用する関数を更新しました。ECID に optIn `pre-approval` が提供され、後で承認された場合、`Internet-Explorer (IE) 11` でパフォーマンスの問題が発生するバグを修正しました。

## バージョン 4.5

* バージョン 4.5 以降では、ECID は `setCustomerIDs` メソッドに送信された空の ID を拒否します。
* オプトインが誤って `doesOptInApply=false` および `isIabContext=true` として設定されている際の問題を修正しました。

すべての製品の月別リリースノートについては、[Experience Cloud リリースノート](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=ja)を参照してください。
