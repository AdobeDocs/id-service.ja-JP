---
description: 2018 年の Experience Cloud ID サービスの機能リリース、更新、変更点です。
keywords: ID サービス
seo-description: 2018 年の Experience Cloud ID サービスの機能リリース、更新、変更点です。
seo-title: 2018 年リリースノート
title: 2018 年リリースノート
uuid: 771b5b11-a8e3-464c-b65e-b15135584ace
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# 2018 年リリースノート {#release-notes}

2018 年の Experience Cloud ID サービスの機能リリース、更新、変更点です。

## バージョン 3.3 {#section-3202c8d5457a45a5b5f4b4c838d44de3}

<table id="table_201417BD540E4EE69911AABE9BF77509"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 項目 説明 </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>AMCV Cookie のセキュリティを強化しました </p> </td> 
   <td colname="col2"> <p>内部セキュリティスキャン中に、DTM ライブラリを使用すると、セッション管理用の Cookie で適切な属性を指定できないことが判明しました。その結果、Cookie の情報が誤って共有される可能性があります。この問題を解決するために、お客様が AMCV Cookie を安全であると設定できる設定を追加しました。<a href="https://marketing.adobe.com/resources/help/ja_JP/mcvid/mcvid-securecookie.html" format="https" scope="external">secureCookie</a> を参照してください。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## バージョン 3.2 {#section-ae2fee1c152e405faa4eb395f960e2f6}

<table id="table_6546F5C74E4742E4B5E9793BCEAB66FA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 項目 説明 </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>AMCV Cookie のセキュリティを強化しました </p> </td> 
   <td colname="col2"> <p>内部セキュリティスキャン中に、DTM ライブラリを使用すると、セッション管理用の Cookie で適切な属性を指定できないことが判明しました。その結果、Cookie の情報が誤って共有される可能性があります。この問題を解決するために、お客様が AMCV Cookie を安全であると設定できる設定を追加しました。secureCookie を参照してください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>統合コードおよび ID は数字か空でない文字列にする必要があります </p> </td> 
   <td colname="col2"> <p>統合「code」または「id」に数字でも空でもないデータが含まれている場合に発生する「setCustomerIDs」の評価の問題を修正しました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> パブリック Git リポジトリで ECID JS を公開しました </td> 
   <td colname="col2"> Experience Cloud のすべてのお客様向けに、ECID JS をパブリック Git リポジトリ（https://github.com/Adobe-Marketing-Cloud/id-service/releases）で公開しました。 </td> 
  </tr> 
 </tbody> 
</table>

## バージョン 3.1.2{#section-3cba186f74fe4f2186a9ca2e5e0a2514}

<table id="table_9FA4E20C996746A2A4219C9A0F759AD1"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 項目 説明 </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>個別訪問者数の非現実的なスパイク </p> </td> 
   <td colname="col2"> <p>Experience Cloud ID サービス 3.1.0 のリリースでは、このバージョンが実装された際に、個別訪問者数で非現実的なスパイクが作成される問題が見つかりました。この動作は、最新バージョンの ECID v3.1.0 で、ユーザーが Safari ブラウザーのプライバシー設定で「閲覧中の Web サイトのみ許可」オプションを選択していた場合にのみ、示されます。この問題はバージョン 3.1.2 で修正されました。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## バージョン 3.1.0{#section-a20c8278bf9643018965330415091e53}

>[!NOTE]
>
>できるだけ早期に、バージョン 3.1.0 から最新バージョンにアップグレードすることをお勧めします。バージョン 3.1.2 の説明を参照してください。Adobe Launch、DTM および AppMeasurement 内で最新バンドルを使用できます。

<table id="table_512039AFC4D34038B8F116B71EEEE7F6"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 項目 説明 </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Cookie が誤ったドメインに設定されている </p> </td> 
   <td colname="col2"> <p>一時的な Visitor Cookie により、設定（initConfig）で指定したドメインではなく、「デフォルト」の Cookie ドメインに Cookie が設定されるバグを修正しました。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## バージョン 3.0{#section-5fcaef66e8b343238abeb10048dc5747}

<table id="table_7E9224D6CC924A2DB5119171C9DC5443"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 項目 説明 </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>複数の ID 同期要求に対応するためのスレッドの生成 </p> </td> 
   <td colname="col2"> <p><b>Iframe</b> </p> <p>CPU による計算が継続的におこなわれるので、ID の同期を複数実行する環境では、UI がブロックされる場合があります。そこで、ID 同期要求を 100 ミリ秒ごとに分けるスレッド生成機能を導入します。 </p> <p>この変更により、Visitor 2.3.0 以降および DIL 6.10 以降を使用する場合のパフォーマンスが向上します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> サードパーティの呼び出しを無効にする機能を追加 </td> 
   <td colname="col2"> <p><b>JavaScript - 3.0.0</b> </p> <p>サードパーティの同期呼び出しを無効にできるように、以下の設定の名前を変更しました。 </p> <p>idSyncDisableSyncs を disableIdSyncs に変更 </p> <p>idSyncDisable3rdPartySyncing を disableThirdPartyCookies に変更 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Internet Explorer のサポート </p> </td> 
   <td colname="col2"> <p>ID サービスでは、Internet Explorer 6、7、8 および 9 はサポートされなくなりました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>getInstance ドキュメントの更新 </p> </td> 
   <td colname="col2"> <p>訪問者の関数に、var visitor = new Visitor でこの関数をインスタンス化しないことに関する警告を追加しました。 </p> </td> 
  </tr> 
 </tbody> 
</table>

