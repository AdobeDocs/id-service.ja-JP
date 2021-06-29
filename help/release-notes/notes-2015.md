---
description: 2015 年版のリリースノートと更新情報です。
keywords: ID サービス
title: 2015 年リリースノート
exl-id: 57c45726-f856-4af5-a30a-9a1bdcaa6411
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '408'
ht-degree: 100%

---

# 2015 年リリースノート {#release-notes}

2015 年版のリリースノートと更新情報です。

## バージョン 1.5.3 {#section-7c09ba2832bd4644a1ccc3aa83abe66a}

2015 年 11 月

児童オンラインプライバシー保護法（COPPA）では、証明可能な親の同意なく 13 歳未満の子供からの個人情報をオンラインで取得することを禁止しています。COPPA を遵守するために、オプションの変数を [!DNL Experience Cloud] ID サービスコードに追加して、ブラウザーのサードパーティドメインに cookie を設定できなくすることができます。[Experience Cloud Identity Service での COPPA のサポート](../reference/coppa.md#concept-d7ddf81bebd74f129661fcec1ca19413)を参照してください。バージョン 1.5.3 以降でサポートされています。

## バージョン 1.5.2 {#section-e3c73e47539942a89b02d33061128148}

2015 年 9 月

* Safari ブラウザーでユーザーがサードパーティ Cookie をブロックしたときに同期サービスが機能しなくなるバグを修正しました。 （AAM-20764）
* ID サービスの呼び出しで、`d_visid_ver=` パラメーターにバージョン ID が含まれるようになりました。返された ID は、内部チームが問題をトラブルシューティングしたりサポートしたりするのに役立ちます。 （AAM-20824）

## バージョン 1.5.1 {#section-f4309d7917964a748fee4bdb45bffa44}

2015 年 8 月

* 同期または送信するデータがない場合に、ID サービスが iframe をリクエストできないバグを修正しました。 （AAM-20164）
* ID サービスでマルチパートのトップレベルドメイン Cookie を適切に設定できないバグを修正しました。 例えば、`my_company.co.uk` のようなドメインの場合、状況によっては、ID サービスは、`co.uk` にのみ Cookie を設定していました。（AN-104683）

   これは、次の条件の&#x200B;*すべて*&#x200B;を満たす少数のクライアントにのみ影響がありました。

   * ID サービスの使用。
   * [猶予期限&#x200B;](../reference/analytics-reference/grace-period.md)*を有効にしているか、*&#x200B;猶予期限がファーストパーティ cookie を使用していて、ユーザーが cookie をブロックしている。

   * マルチパートのトップレベルドメインのページがある。

このリリースでのドキュメントの改訂には、次のものが含まれます。

* [API メソッドとコードライブラリ](../library/library.md#concept-ff27497375644a898d47984aefb21c97)：コンテンツとテキストを再構成しました。ほとんどの場合、メソッドごとにページを設けました。
* [Experience Cloud Identity Service の要件](../reference/requirements.md)：内容を改訂し、テキストを再構成しました。

## バージョン 1.5 {#section-db5edfa11ae143ada07a96e0ab06dc57}

2015 年 7 月

[!DNL Experience Cloud] ID サービスは複数の ID と認証状態をサポートします。この変更により、[!DNL Audience Manager] 関数で使用されているユーザー ID への `setCustomerIDs` DPID マッピングのサポートが完全に廃止されました。詳しくは、[顧客 ID と認証状態](../reference/authenticated-state.md)を参照してください。

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

[Experience Cloud](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd) に関する説明を参照してください。

## バージョン 1.3.5 {#section-eed4567f058f446d9a819e4682621aed}

2015 年 2 月

AAM Blob およびロケーションヒントのリクエストに関するタイムアウトの処理を修正しました。 これで、タイムアウト時に、システムは現在のページのこれらのフィールドを正しく空欄のままにして、すべてのコールバックを実行するようになりました。タイムアウトはエラー状況として扱われるため、次のページで再試行します。 （AN-94473、AN-94474）

## バージョン 1.3.4 {#section-bca4a3e7c05546b7af1c9ec47fdb3331}

2015 年 1 月

JSONP リクエストの `<head>/<body>` タグコンテナ用に `<script>` タグの検索を見直しました。また、大文字と小文字の区別に関する設定がそれぞれ異なる多様な DOM 実装（HTML か XHTML）に対応するための `<script>` タグを作成しました。（AN-9355）
