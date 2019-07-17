---
description: 2016年のExperience Cloud IDサービスの機能リリース、更新、変更点です。
keywords: ID サービス
seo-description: 2016年のExperience Cloud IDサービスの機能リリース、更新、変更点です。
seo-title: 2016 年リリースノート
title: 2016 年リリースノート
uuid: 7a5a314a-3ff8-4561-9c64-6c10d2223887
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# 2016 年リリースノート {#release-notes}

2016年のExperience Cloud IDサービスの機能リリース、更新、変更点です。

これらの変更点は、[Experience Cloud リリースノート](https://marketing.adobe.com/resources/help/en_US/whatsnew/)にも記載されています。過去の発表内容については、[以前のリリースノート](https://marketing.adobe.com/resources/help/en_US/whatsnew/?f=c_legacy_releases.html)を参照してください。[!DNL Experience Cloud]

## バージョン 1.10 {#section-7d719b3213344a46858835042e0214ed}

2016 年 11 月

>[!IMPORTANT]
>
>* バージョン 1.10 には [!DNL AppMeasurement] 1.8.0 が必要です。
>* Experience Cloud IDサービスライブラリ2.0.0以上を使用すると、Adobe Media ManagerのID同期がデフォルトで開始されます。[ID 同期と一致率について](/help/introduction/match-rates.md)を参照してください。


**修正点および改善点**

* サーバー側環境での ID サービスの実装方法に関する説明を追加しました。
* クロスドメイン遷移時に Experience Cloud と Analytics の ID を上書きできるブール関数である `Visitor.overwriteCrossDomainMCIDAndAID` が追加されました。[訪問者 ID の上書き](../library/function-vars/overwrite-visitor-id.md#reference-9db13d637ce44fb6a8d519de5743ccde)を参照してください。

* `TS = UTC` timestamp が `visitor.appendVisitorIDsTo` 関数のプロパティとして追加されました。ID サービスではタイムスタンプを使用して、5 分間隔でリダイレクト URL に ID を使用するかどうかを決定します。詳しくは、[訪問者 ID 追加関数](../library/get-set/appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce)を参照してください。

* 地域 ID を返す新しい関数である `Visitor.getLocationHint,` が追加されました。[地域 ID（ロケーションヒント）の取得](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c)を参照してください。

* ターゲットパブリッシング iFrame で ID 同期を手動で実装するための 2 つの関数として、`idSyncByURL` と `idSyncByDataSource` が追加されました。[URL またはデータソースによる ID 同期](../library/get-set/idsync.md#reference-b01b88c083434cf8abbeabd3c6956c48)を参照してください。

* `disableThirdPartyCalls:true` の場合に AppMeasurement のトラッキングコールがブロックされる問題を修正しました。
* 異なるドメイン間で Experience Cloud ID（MID）が渡されなかった、ID サービスの問題を修正しました。

## バージョン 1.9.0 {#section-04e1b4d4b10d40468f2116b8119998e7}

2016 年 10 月

**修正点および改善点**

* Audience Manager の一意のユーザー ID（AAMUUID）を Experience Cloud ID として ID サービスに渡していた問題を修正しました。
* AMCV Cookie の有効期間（TTL：time-to-live）が切れた場合でも、Experience Cloud ID が Cookie に含まれている限り ID サービスはその情報をサーバーに戻します。この呼び出しの後、ID サービスは非同期で呼び出しをおこない、Cookie を更新します。ID サービスはサーバーからの応答を待つ必要がないので、パフォーマンスの改善に役立ちます。既存の AMCV cookie の値を使用して、更新をリクエストできます。
* ID サービスは直接ページ上で自動的に Experience Cloud ID（MID）を Adobe Media Manager と他の内部アドビドメインに同期します。自動同期は、すべての既存アカウントおよび新規アカウントで有効です。これは、Media Manager の一致率の改善に役立ちます。VisitorAPI.js バージョン 1.8 またはそれ以降で適用されます。[ID 同期と一致率について](../introduction/match-rates.md#concept-e55cf228b90c457fbee8c3cb06b195ab)も参照してください。

**新規および改訂されたドキュメント**

**新規：** [AMCV Cookie から地域とユーザー ID を取得する](../reference/regions.md#concept-15b2c8c894b846a48f1f61a353cfdf4e)

## バージョン 1.8.0 {#section-69f2eb5b246b4c7aafe116b7a2a5448a}

2016 年 9 月

**修正点および改善点**

関数 `disableThirdPartyCalls` で設定できるオプションのブール値のフラグとして、`Visitor.getInstance` が追加されました。`disableThirdPartyCalls= true` の場合、この ID サービスは他のドメインの呼び出しをおこないません。デフォルト値は `disableThirdPartyCalls= false` です。[disableThirdPartyCalls](../library/function-vars/disablethirdpartycalls.md#reference-fba90b095e9746daad46e3abb790d18b) を参照してください。

## バージョン 1.7.0 {#section-f7d59104de6644fca3691480383d4644}

2016 年 8 月

**修正点および改善点**

* 関数 `idSyncAttachIframeOnWindowLoad` で設定できるオプションのブール値のフラグとして、`Visitor.getInstance` が追加されました。`idSyncAttachIframeOnWindowLoad= true` の場合、ID サービスは、ウィンドウの読み込み時に ID 同期 iFrame を読み込みます。デフォルトでは、ID サービスは、可能な限り迅速に iFrame を読み込みます。このフラグは、廃止される *に代わるものです。*`idSyncAttachIframeASAP`[Visitor.getInstance 関数の変数](../library/function-vars/function-vars.md)を参照してください。

* ドメイン、ネイティブアプリおよびハイブリッドアプリから Web 移行への [!DNL Experience Cloud] ID のトラッキングをサポートする機能が追加されました。[訪問者 ID 追加ヘルパー関数](../library/get-set/appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce)を参照してください。

* ID サービスが訪問者 [!DNL Experience Cloud] ID をクライアント側またはサーバー側に生成したかどうか、または ID 呼び出しがタイムアウトしたかどうかを判断する関数が visitorAPI.js コードに追加されました。[タイムアウトトラッキング関数](../library/get-set/timeout-functions.md#reference-912bae0f116540df8c5dc1c008656c23)および[クライアント側訪問者 ID 生成のトラッキング](../library/get-set/client-side-id.md#reference-8244dc6d832c4bbaaa97528096bcc2a6)を参照してください。

**新規および改訂されたドキュメント**

Revised: [Requirements for the Experience Cloud Identity Service](../reference/requirements.md)

**既知の問題**

[!DNL Audience Manager] DIL コードと visitorAPI.js コードを同じページに使用しているお客様は、DIL 変数 `secureDataCollection= false` を設定する必要があります。[secureDataCollection](https://marketing.adobe.com/resources/help/en_US/aam/?f=dil-secure-data-collection.html) を参照してください。

## バージョン 1.6.0 {#section-3faaa14bf3934c6a99b8f79ee06fc0d2}

2016 年 7 月

>[!IMPORTANT]
>
>[!DNL Experience Cloud] ID サービスの バージョン 1.6.0 には、JavaScript 版 AppMeasurement バージョン 1.6.2 が&#x200B;*必要*&#x200B;です。ID サービスバージョン 1.6.0 にアップグレードする場合は、適切な AppMeasurement コードバージョンを使用していることを確認してください。

<table id="table_5472AAFA0DD2495DB8D92DEBE44A07A9"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 機能 </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>クロスオリジンリソース共有（CORS） </p> </td> 
   <td colname="col2"> <p>CORS を利用すると、ブラウザーから、現在のドメイン以外のドメインのリソースをリクエストできます。Experience Cloud IDサービスは、クライアント側のクロスオリジンリソースリクエストを有効にするCORS標準規格をサポートしています。CORS をサポートしていないブラウザー上では、JSONP リクエストに切り替わります。 </p> <p>以下を参照してください。 </p> 
    <ul id="ul_15386385108F4E07824041DD6F2DC11E"> 
     <li id="li_DB8D5AA4A7004DE4AE9CBC31A389F5BD"> <a href="../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758" format="dita" scope="local"> Experience Cloud IDサービスでのCORSのサポート </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**修正点および改善点**

* `dpm.demdex.net` への ID 同期呼び出しに `d_fieldgroup` パラメーターが追加されました。この新しいパラメーターは、内部のトラブルシューティングおよびデバッグの目的で使用されます。

* ID サービスが生成する iFrame にタイトル属性が追加されました。iFrame のタイトルを指定すると、目の不自由な利用者向けにスクリーンリーダーで読み上げ可能なページ情報を提供できます。iFrame のタイトル属性は `Adobe ID Syncing iFrame` に設定されます。
* 関数 `Visitor.getInstance` で設定できるオプションのフラグとして、`idSyncAttachIframeASAP: true` が追加されました。`true` の場合、ID サービスは ID 同期 iFrame をできるだけ早く読み込みます。これにより、ID 同期の一致率が向上します。デフォルトでは、ID サービスはウィンドウの読み込み時に iFrame を読み込みます。[Visitor.getInstance 関数の変数](../library/function-vars/function-vars.md)を参照してください。

* AppMeasurement で無限ループが発生するコールバック関数の問題を修正しました。
* `loadTimeout` 間隔のデフォルトが 500 ミリ秒から 30,000 ミリ秒に変更されました。[Visitor.getInstance 関数の変数](../library/function-vars/function-vars.md)を参照してください。

**新規および改訂されたドキュメント**

**新規**

* [Experience Cloud IDサービスのAnalyticsへの実装](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd)
* [Experience Cloud IDサービスのAnalytics、Audience ManagerおよびTargetへの実装](../implementation-guides/setup-aam-analytics-target.md#concept-e7e2dc0d0bbe481db93328b5604b4673)

**改訂済み**

* [Experience Cloud IDサービスの要件](../reference/requirements.md)
* [Experience Cloud IDサービスのテストと検証](../implementation-guides/test-verify.md)

## バージョン 1.5.7 {#section-735b4989a5744a42aeb2d97602dbda62}

2016 年 6 月

<table id="table_5D604D0820C84EC996ACB99126C8A3DF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 機能 </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p><span class="codeph">iframe.sandbox</span> 属性の変更 </p> </td> 
   <td colname="col2"> <p>iFrame で、<span class="codeph">iframe.sandbox='allow-scripts allow-same-origin';</span> が設定できるようになりました。 </p> <p>これらの 2 トークンのみを許可することは、セキュリティを強化し、ID サービスに ID 同期で必要となる基本機能を提供するのに役立ちます。 </p> <p>sandbox 属性は、Internet Explorer のバージョン 9 以前ではサポートされていません。詳細については、この <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe" format="https" scope="external">iFrame ドキュメント</a>の属性の節を参照してください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Experience Cloud ID（MID）のエンコード </p> </td> 
   <td colname="col2"> <p>ID サービスは、サーバーから返される、または <span class="codeph">visitor.setMarketingCloudVisitorID()</span> 関数で設定された、MID 値をエンコードするようになります。MID について詳しくは、<a href="../introduction/cookies.md" format="dita" scope="local">Cookie と Experience Cloud ID</a> を参照してください。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**修正点**

訪問者 API は、従来の Analytics 訪問者 ID がない場合の、Audience Manager を使用した余分な再同期の呼び出しを強制しなくなりました。

## バージョン 1.5.x {#section-a62ae48275324058b57edf66ee5a579f}

2016 年 5 月

**ドキュメントの更新**

* [Android および iOS 向け SDK 要件](../reference/requirements.md#section-73b2446fba8e463888642c7d7dfd94f1)
* [Data WorkbenchとExperience Cloud IDサービス](../reference/dwb.md#task-72df50a051944a47b01b0c0bc3d1e1d8)
* [Experience Cloud IDサービスのテストと検証](../implementation-guides/test-verify.md)

## バージョン 1.5.x {#section-0cfeef085cff4cbc8dff6cbc6fc32920}

2016 年 4 月

**ドキュメントの更新**

[Target向けExperience Cloud IDサービスの実装](../implementation-guides/setup-target.md#concept-9b5a802132574e1181927ddd00e5c5af)

## バージョン 1.5.4 {#section-1a44ba147fb3440ea7dec551faee3528}

2016 年 3 月

<table id="table_F4ED1F88709E4D3BA69C747879A4E18F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 機能 </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>オプトアウトのサポート </p> </td> 
   <td colname="col2"> <p><span class="keyword">Experience Cloud</span> ID サービスは、訪問者によるオプトアウトに対応しました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> ID の同期間隔の変更 </p> </td> 
   <td colname="col2"> <p><span class="keyword">Experience Cloud ID</span> サービスでは、データ収集サーバーが呼び出されるたびに ID の同期が呼び出されるようになりました。これまでは、<span class="keyword">Experience Cloud</span> ID 取得の最初の呼び出し時に 1 回のみリクエストされていました。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**ドキュメントの更新**

* [Experience Cloud IDサービスのAnalyticsへの実装](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd) :IDサービスの設定方法を説明する新しい手順 [!DNL Analytics]です。

* [Experience Cloud IDサービス移行の判断ポイント](../reference/analytics-reference/migration-decisions.md#concept-ba44803eea3c4cc185232a510cec0257) :テキストを明確にしました。単一のドメインを使用する場合は、データ収集 CNAME の管理を終了したい場合に、その使用を停止できます。ただし、CNAME が機能している場合には、変更する必要はありません。

## バージョン 1.5.3 {#section-7c09ba2832bd4644a1ccc3aa83abe66a}

2016 年 1 月

**ドキュメントの更新**

<table id="table_C1A5DBED6B104C0FBA54EC663D3B0E86"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> トピック </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../reference/authenticated-state.md" format="dita" scope="local"> 顧客 ID と認証状態 </a> </p> </td> 
   <td colname="col2"> <p>テキストを修正しました。顧客 ID はエンコードされていない値でのみ渡す必要があります。ID のエンコードによって、識別子が二重にエンコードされます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

