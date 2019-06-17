---
description: 2015 年版のリリースノートと更新情報です。
keywords: ID サービス
seo-description: 2015 年版のリリースノートと更新情報です。
seo-title: 2015 年リリースノート
title: 2015 年リリースノート
uuid: 49423699-1e0f-49e4-9135-2ae84b4f92df
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# 2015 年リリースノート {#release-notes}

2015 年版のリリースノートと更新情報です。

## バージョン1.5.3 {#section-7c09ba2832bd4644a1ccc3aa83abe66a}

2015 年 11 月

児童オンラインプライバシー保護法（COPPA）では、証明可能な親の同意なく13歳未満の子供からの個人情報をオンラインで収集できません。COPPA を遵守するために、オプションの変数を [!DNL Experience Cloud] ID サービスコードに追加して、ブラウザーのサードパーティドメインに cookie を設定できなくすることができます。[Experience Cloud ID サービスでの COPPA のサポート](../mcvid-reference/mcvid-coppa.md#concept-d7ddf81bebd74f129661fcec1ca19413)を参照してください。バージョン 1.5.3 以降でサポートされています。

## バージョン 1.5.2 {#section-e3c73e47539942a89b02d33061128148}

2015 年 9 月

* Safari ブラウザーでサードパーティの Cookie をブロックしている場合、同期サービスが機能しなかったバグを修正しました。（AAM-20764）
* IDサービスの呼び出しに `d_visid_ver=` 、パラメーターにバージョンIDが含まれるようになりました。返される ID は、内部チームが問題をトラブルシューティングしたりサポートするのに役立ちます。（AAM-20824）

## バージョン 1.5.1 {#section-f4309d7917964a748fee4bdb45bffa44}

2015 年 8 月

* 同期または送信するデータがない場合に、ID サービスをリクエストできないバグを修正しました。（AAM-20164）
* ID サービスで、マルチパートのトップレベルドメイン Cookie を適切に設定できないバグを修正しました。例えば、`my_company.co.uk` のようなドメインの場合、状況によっては、ID サービスは、`co.uk` にのみ Cookie を設定していました。（AN-104683）

   これは、次の基準のすべて**に当てはまる少数のクライアントのみに影響していました。

   * ID サービスを使用している。
   * [猶予期限](../mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md)を有効にしているか、**猶予期限がファーストパーティ cookie を使用していて、ユーザーが cookie をブロックしている。

   * マルチパートのトップレベルドメインのページがある。

このリリースのドキュメントで見直された内容は以下のとおりです。

* [APIメソッドとコードライブラリ](../mcvid-library/mcvid-library.md#concept-ff27497375644a898d47984aefb21c97):コンテンツとテキストを再構成しました。ほとんどの場合、メソッドごとにページを設けました。
* [Experience Cloud ID サービスの要件](../mcvid-reference/mcvid-requirements.md)：内容を改訂し、テキストを再構成しました。

## バージョン1.5 {#section-db5edfa11ae143ada07a96e0ab06dc57}

2015 年 7 月

[!DNL Experience Cloud] ID サービスは複数の ID と認証状態をサポートします。この変更により、[!DNL Audience Manager] 関数で使用されているユーザー ID への `setCustomerIDs` DPID マッピングのサポートが完全に廃止されました。[顧客IDと認証状態を参照してください](../mcvid-reference/mcvid-authenticated-state.md)

## バージョン 1.4 {#section-f5c596f355b14da28f45c798df513572}

2015 年 5 月

バージョン 1.4 以降では、設定オブジェクトを `Visitor.getInstance` 関数の第 2 パラメーターとして渡す設定方法が推奨されます。

```js
var visitor = Visitor.getInstance("016D5C175213CCA80A490D05@AdobeOrg",{ 
    "loadTimeout":1000, 
    "trackingServer":"myco.sc.omtrdc.net", 
    "idSyncContainerID":80 
});
```

[Experience Cloud](../mcvid-implementation-guides/mcvid-setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd) に関する説明を参照してください。

## バージョン 1.3.5 {#section-eed4567f058f446d9a819e4682621aed}

2015 年 2 月

AAM Blob およびロケーションヒントの要求で、タイムアウトの処理を修正しました。現在は、タイムアウトでは、現在のページのこれらのフィールドを正しく空のままにしておき、すべてのコールバックを呼び出します。タイムアウトは、エラー条件として扱われ、次のページで再試行されます。（AN-94473、AN-94474）

## バージョン 1.3.4 {#section-bca4a3e7c05546b7af1c9ec47fdb3331}

2015 年 1 月

JSONP `<head>/<body>` リクエスト `<script>` タグコンテナ用のタグ検索を修正しました。また、大文字と小文字の区別の設定が異なる様々なDOM実装（HTMLとXHTML）に対応する `<script>` ためのタグを作成しました。（AN-9355）
