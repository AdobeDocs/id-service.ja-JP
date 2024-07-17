---
description: 2018 年の Experience Cloud ID サービスの機能リリース、更新、変更点です。
keywords: ID サービス
title: 2018 年リリースノート
exl-id: ad3cccf1-2753-4ac9-a68c-15b2d62bbc1a
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 100%

---

# 2018 年リリースノート {#release-notes}

2018 年の Experience Cloud ID サービスの機能リリース、更新、変更点です。

## バージョン 3.3 {#section-3202c8d5457a45a5b5f4b4c838d44de3}

<table id="table_201417BD540E4EE69911AABE9BF77509"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 項目の説明 </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>AMCV Cookie のセキュリティの強化 </p> </td> 
   <td colname="col2"> <p>内部セキュリティスキャンで、DTM ライブラリ使用時に、セッション管理に使用する Cookie で正しい属性を指定できないことがわかりました。 この結果、Cookie の情報が誤って共有されるおそれがあります。 この問題を解決するために、お客様が AMCV Cookie を安全なものとして指定できる設定を導入しました。 <a href="/help/library/function-vars/securecookie.md" format="https" scope="external">secureCookie</a> を参照してください。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## バージョン 3.2 {#section-ae2fee1c152e405faa4eb395f960e2f6}

<table id="table_6546F5C74E4742E4B5E9793BCEAB66FA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 項目の説明 </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>AMCV Cookie のセキュリティの強化 </p> </td> 
   <td colname="col2"> <p>内部セキュリティスキャンで、DTM ライブラリ使用時に、セッション管理に使用する Cookie で正しい属性を指定できないことがわかりました。 この結果、Cookie の情報が誤って共有されるおそれがあります。 この問題を解決するために、お客様が AMCV Cookie を安全なものとして指定できる設定を導入しました。 secureCookie を参照してください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>統合コードと ID を数値または空以外の文字列にする必要がある </p> </td> 
   <td colname="col2"> <p>数値でも空以外の文字列でもない統合「code」または「id」がデータに含まれている場合の、「setCustomerIDs」の検証に関する問題を修正しました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> ECID JS がパブリック Git リポジトリで使用可能 </td> 
   <td colname="col2"> ECID JS がパブリック Git リポジトリ（https://github.com/Adobe-Marketing-Cloud/id-service/releases）ですべての Experience Cloud ユーザーに公開されました。 </td> 
  </tr> 
 </tbody> 
</table>

## バージョン 3.1.2 {#section-3cba186f74fe4f2186a9ca2e5e0a2514}

<table id="table_9FA4E20C996746A2A4219C9A0F759AD1"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 項目の説明 </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>ユニーク訪問者数の非現実的なスパイク </p> </td> 
   <td colname="col2"> <p>Experience Cloud ID サービス3.1.0 のリリースでは、このバージョンが実装された際に、ユニーク訪問者数で非現実的なスパイクが作成される問題が見つかりました。この動作は、最新バージョンの ECID v3.1.0 で、Safari ブラウザーのプライバシー設定で「現在の Web サイトからのみ許可」オプションを選択した場合にのみ発生します。バージョン 3.1.2 では、この問題が修正されています。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## バージョン 3.1.0 {#section-a20c8278bf9643018965330415091e53}

>[!NOTE]
>
>できるだけ早期に、バージョン 3.1.0 から最新バージョンにアップグレードすることをお勧めします。バージョン 3.1.2 の説明を参照してください。Adobe Experience Platform Launch、DTM および AppMeasurement 内で最新バンドルを使用できます。

<table id="table_512039AFC4D34038B8F116B71EEEE7F6"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 項目の説明 </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>正しくないドメインに設定された Cookie </p> </td> 
   <td colname="col2"> <p>一時訪問者の Cookieが、設定（initConfig）で指定されるドメインではなく、「デフォルト」の Cookie ドメインで設定されていたバグを修正しました。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## バージョン 3.0 {#section-5fcaef66e8b343238abeb10048dc5747}

<table id="table_7E9224D6CC924A2DB5119171C9DC5443"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 項目の説明 </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>複数の ID 同期要求に対応するためのスレッドの生成 </p> </td> 
   <td colname="col2"> <p><b>Iframe</b> </p> <p>複数の ID 同期を実行する場合は、CPU での計算処理が連続して行われるので、UI がブロックされることがあります。 ID 同期リクエストを 100 ミリ秒ごとに分離するスレッドイールドを導入しています。 </p> <p>この変更により、Visitor 2.3.0 以降および DIL 6.10 以降を使用している顧客のパフォーマンスが向上します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> サードパーティの呼び出しを無効にする機能を追加 </td> 
   <td colname="col2"> <p><b>JavaScript - 3.0.0</b> </p> <p>サードパーティの同期呼び出しを無効にできるように、以下の設定の名前を変更しました。 </p> <p>idSyncDisableSyncs を disableIdSyncs に変更 </p> <p>idSyncDisable3rdPartySyncing を disableThirdPartyCookies に変更 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Internet Explorer のサポート </p> </td> 
   <td colname="col2"> <p>ID サービスでは、Internet Explorer 6、7、8 および 9 をサポートしなくなりました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>getInstance ドキュメントの更新 </p> </td> 
   <td colname="col2"> <p>訪問者の関数に、var visitor = new Visitor でこの関数をインスタンス化しないことに関する警告を追加しました。 </p> </td> 
  </tr> 
 </tbody> 
</table>
