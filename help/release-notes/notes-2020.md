---
description: Experience Cloud ID サービスの機能リリース、更新、変更点です。
keywords: ID サービス
title: 2020 年リリースノート
exl-id: c9d7876e-debc-4c8e-8ebc-91646610c876
TQID: https://experienceleague.adobe.com/hqAMIyXTeLBPU-4B6AVRXhcWux3bkyViMCrbjoGiRwk
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 229
ht-degree: 97%

---

# Experience Cloud リリースノート - 2020 {#release-notes}

Experience Cloud ID サービスの機能リリース、更新、変更点です。

## バージョン 5.1.1

* VisitorJS が iFrame に読み込まれる際に `SameSite=None` を使用して AMCV cookie を設定するためのパッチ修正。

## バージョン 5.1.0

* AMCV cookie の `SameSite` 属性を指定するために `sameSiteCookie` 設定を追加します。 この設定では、`SameSite` 属性の次の値がサポートされます。
   * `Strict`
   * `Lax`
   * `None`

これらの属性値について詳しくは、[web.dev](https://web.dev/samesite-cookies-explained/) および [Chromium プロジェクトによる SameSite の更新](https://www.chromium.org/updates/same-site/)を参照してください。

## バージョン 5.0.1

* 新しい IAB 同意文字列が Adobe データ収集エッジに送信される際に `d_cf` フラグを含めるためのパッチ修正。

## バージョン 5.0.0

* `IAB 2.0` をサポートする Visitor 5.0.0 リリース。

## バージョン 4.6

* デフォルトで `loadSSL` フラグをオンにしました。 ID サービスへのすべての呼び出しは、デフォルトにより、`https` でオンになります。  `non-ssl` ページから http で ID サービスを呼び出す場合は、false に設定できます。
* `ESLint` によって報告される問題を修正するため、`Internet-Explorer (IE)` のバージョン検出に使用する関数を更新しました。
ECID に optIn `pre-approval` が提供され、後で更新された場合、`Internet-Explorer (IE) 11` でパフォーマンスの問題が発生するバグを修正しました。

## バージョン 4.5

* バージョン 4.5 以降では、ECID は `setCustomerIDs` メソッドに送信された空の ID を拒否します。
* オプトインが誤って `doesOptInApply=false` および `isIabContext=true` として設定されている際の問題を修正しました。

すべての製品の月別リリースノートについては、[Experience Cloud リリースノート](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=ja)を参照してください。

