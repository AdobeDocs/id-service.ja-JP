---
description: 2018 年の Experience Cloud Identity Service の機能リリース、更新、変更点です。
keywords: ID サービス
seo-description: 2018 年の Experience Cloud Identity Service の機能リリース、更新、変更点です。
seo-title: 2018 年リリースノート
title: 2018 年リリースノート
uuid: 771b5b11-a8e3-464c-b65e-b15135584ace
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 36%

---


# 2018 年リリースノート {#release-notes}

2018 年の Experience Cloud Identity Service の機能リリース、更新、変更点です。

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
   <td colname="col1"> <p>AMCV cookieのセキュリティの強化 </p> </td> 
   <td colname="col2"> <p>内部セキュリティスキャン中に、DTMライブラリを使用する場合に、セッション管理に使用されるcookieで正しい属性を指定できないことが検出されました。 この場合、cookieの情報が誤って共有される可能性があります。 この問題を解決するために、お客様がAMCV cookieを安全なものとして設定できる設定を導入しました。 <a href="/help/library/function-vars/securecookie.md" format="https" scope="external">secureCookie</a> を参照してください。 </p> </td> 
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
   <td colname="col1"> <p>AMCV cookieのセキュリティの強化 </p> </td> 
   <td colname="col2"> <p>内部セキュリティスキャン中に、DTMライブラリを使用する場合に、セッション管理に使用されるcookieで正しい属性を指定できないことが検出されました。 この場合、cookieの情報が誤って共有される可能性があります。 この問題を解決するために、お客様がAMCV cookieを安全なものとして設定できる設定を導入しました。 secureCookie を参照してください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>統合コードとIDは数値または空以外の文字列にする必要があります </p> </td> 
   <td colname="col2"> <p>データに数値でも空でもない統合'code'または'id'が含まれている場合に、'setCustomerIDs'の検証で発生していた問題を修正しました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> ECID JSはパブリックGitリポジトリで使用可能 </td> 
   <td colname="col2"> ECID JSは、すべてのExperience Cloudのお客様向けに、公開Gitリポジトリ(https://github.com/Adobe-Marketing-Cloud/id-service/releases)で利用できるようになりました。 </td> 
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
   <td colname="col2"> <p>Experience Cloud Identity Service 3.1.0 のリリースでは、このバージョンが実装された際に、ユニーク訪問者数で非現実的なスパイクが作成される問題が見つかりました。この動作は、最新バージョンのECID v3.1.0でのみ表示され、Safariブラウザーのプライバシー設定で「現在のWebサイトのみを許可」オプションが選択されている場合にのみ表示されます。 バージョン3.1.2では、この問題が修正されています。 </p> </td> 
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
   <td colname="col1"> <p>Cookieが正しくないドメインに設定されている </p> </td> 
   <td colname="col2"> <p>一時訪問者ーのcookieが、configで指定されたドメイン(initConfig)で設定されるのではなく、「デフォルト」のcookieドメインでcookieを設定していたバグを修正しました。 </p> </td> 
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
   <td colname="col2"> <p><b>Iframe</b> </p> <p>複数のID同期を実行するお客様の場合、継続的なCPUの計算が行われるため、UIがブロックされることがあります。 ID同期要求を100ミリ秒ずつ分離するスレッドを導入します。 </p> <p>この変更により、訪問者2.3.0以降およびDIL6.10以降を使用しているお客様のパフォーマンスが向上します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> サードパーティの呼び出しを無効にする機能を追加 </td> 
   <td colname="col2"> <p><b>JavaScript - 3.0.0</b> </p> <p>サードパーティの同期呼び出しを無効にできるように、以下の設定の名前を変更しました。 </p> <p>idSyncDisableSyncs を disableIdSyncs に変更 </p> <p>idSyncDisable3rdPartySyncing を disableThirdPartyCookies に変更 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Internet Explorerのサポート </p> </td> 
   <td colname="col2"> <p>IDサービスは、Internet Explorer 6、7、8および9をサポートしなくなりました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>getInstance ドキュメントの更新 </p> </td> 
   <td colname="col2"> <p>訪問者の関数に、var visitor = new Visitor でこの関数をインスタンス化しないことに関する警告を追加しました。 </p> </td> 
  </tr> 
 </tbody> 
</table>

