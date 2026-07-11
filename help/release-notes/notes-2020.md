---
description: 訪問者ID サービスの機能リリース、更新、変更。
keywords: 訪問者 ID サービス
title: 2020 年リリースノート
exl-id: c9d7876e-debc-4c8e-8ebc-91646610c876
TQID: https://experienceleague.adobe.com/hqAMIyXTeLBPU-4B6AVRXhcWux3bkyViMCrbjoGiRwk
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 235
ht-degree: 71%

---

# 2020 年リリースノート {#release-notes}

訪問者ID サービスの機能リリース、更新、変更。

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

* デフォルトで `loadSSL` フラグをオンにしました。 訪問者ID サービスへのすべての呼び出しは、デフォルトで`https`に行われます。  お客様が`non-ssl` ページからhttpで訪問者ID サービスを呼び出す場合は、falseに設定できます。
* `ESLint` によって報告される問題を修正するため、`Internet-Explorer (IE)` のバージョン検出に使用する関数を更新しました。ECID に optIn `pre-approval` が提供され、後で更新された場合、`Internet-Explorer (IE) 11` でパフォーマンスの問題が発生するバグを修正しました。

## バージョン 4.5

* バージョン 4.5 以降では、ECID は `setCustomerIDs` メソッドに送信された空の ID を拒否します。
* オプトインが誤って `doesOptInApply=false` および `isIabContext=true` として設定されている際の問題を修正しました。

すべての製品の月次リリースノートについては、[CX エンタープライズ版リリースノート ](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=ja)を参照してください。

