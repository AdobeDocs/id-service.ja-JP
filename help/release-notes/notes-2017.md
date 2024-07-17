---
description: 2017 年の Experience Cloud ID サービスの機能リリース、更新、変更点です。
keywords: ID サービス
title: 2017 年リリースノート
exl-id: 0b51d3b1-e405-4473-9e1a-f89a55250e5e
source-git-commit: 384b292413bbc7e43ade97e442ab7195f3b26c7a
workflow-type: tm+mt
source-wordcount: '714'
ht-degree: 99%

---

# 2017 年リリースノート {#release-notes}

2017 年の Experience Cloud ID サービスの機能リリース、更新、変更点です。

これらの変更点は、[Experience Cloud リリースノート](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=ja)にも記載されています。

>[!NOTE]
>
>2017 年 3 月、4 月、5 月、10 月については、お客様に関わるリリースノートおよびコード変更はありません。これらの月の ID サービスコードは v2.1 から変更されていません。

## バージョン 2.5 {#section-27b441509124493f80984ed09bd9e88b}

2017 年 9 月

<!--
<p>
<note type="important">
ID service support for Internet Explorer 6, 7, and 8 is deprecated and will be discontinued in a future release.
</note> </p>
-->

<table id="table_FD24C06C7B3547C3A7673C46B1852A35"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 機能 </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> getVisitorValues</span> </p> </td> 
   <td colname="col2"> <p>これは、デフォルトで Analytics の識別子、ID サービス、データ収集オプトアウト、地域およびメタデータ「blob」コンテンツを返す非同期 API です。オプションの <span class="codeph">visitor.FIELDS</span> 列挙を使用して、返される ID を制御することもできます。<a href="../library/get-set/getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues</a> を参照してください。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**問題の修正とその他の変更**

* Chrome でブラウザーの戻るボタンをクリックしたときに ID サービスがエラー状態になる問題を修正しました。
* ID サービスで、イベント呼び出し応答の地域 ID が変更されたときに ID 同期が再実行されるようになりました。
* ID サービスで使用されるアドビドメインへの呼び出しをホワイトリストに登録する方法について、[コンテンツのセキュリティポリシーと Experience Cloud ID Service](/help/reference/csp.md#concept-968c423a7392479db0a0d821ae9783e3) のドキュメントを新たに追加しました。

<!-- ## Version 2.4 {#section-f4d1608dd8894f558a92b82e83321200}

August, 2017

<table id="table_D9623D34F4444B038F7835750932C8AA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Feature </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe</span> </p> </td> 
   <td colname="col2"> <p>An optional, Boolean configuration that determines if the ID service sends (or does not send) data to the Adobe Experience Cloud Device Co-op. See <a href="../library/function-vars/coopsafe.md#reference-7fbed36f38a048d1a5883c53d430ddf4" format="dita" scope="local"> isCoopSafe</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Revised Documentation**

Updated and revised the [FAQs](/help/faq-intro/faq-intro.md) to include separate FAQs for different [!DNL Experience Cloud] solutions. -->

## バージョン 2.3 {#section-ae7b1cb1e52e4ca5a46b453a3ba1f571}

2017 年 7 月

<table id="table_1448040D09B94A74883A694FCF91EB33"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 機能 </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> sdidParamExpiry</span> </p> </td> 
   <td colname="col2"> <p>この設定を <span class="codeph">Visitor.getInstance</span> 関数に追加すると、追加データ ID（SDID）をあるページから別のページに渡す際に、デフォルトの ID の有効期限を上書きできます。<span class="codeph">sdidParamExpiry</span> は <span class="codeph">appendSupplimentalDataTo</span> ヘルパー関数と共に使用します。<a href="../library/function-vars/sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458" format="dita" scope="local">sdidParamExpiry</a> を参照してください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> resetState</span> </p> </td> 
   <td colname="col2"> <p>この機能は、単一ページのサイト／画面またはアプリでの ID の使用に関連する問題を解決するために、主に A4T のお客様向けに設計されています。<a href="../library/get-set/resetstate.md#reference-47fc00ae139042d795d78244d9970139" format="dita" scope="local">resetState</a> を参照してください。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**問題の修正とその他の変更**

* VisitorAPI.js バージョン 2.2 で、Internet Explorer において ID サービスと Target が連携しなかった問題を修正しました。
* ID サービスが Destination Publishing iFrame にデータを送信する方法を改善するために、コードを改訂しました。これにより、CPU 負荷を低減できます。

## バージョン 2.2 {#section-b7dee2495c29470e9b3a3132ec1fd951}

リリース日：2017 年 6 月

<table id="table_7E412383E89D46759B00FE7328C9946F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 機能 </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../library/function-vars/whitelistdomain.md#reference-999899ff7b5b429a8824c9db7a379808" format="dita" scope="local"> whitelistParentDomain および whitelistIframeDomains </a> </p> </td> 
   <td colname="col2"> <p>これらの設定を使用すると、iFrame と親ページに実装されている ID サービスコードのインスタンスが互いに通信できるようになります。これらの設定は、自社が管理しているドメインの iFrame に ID サービスコードを読み込む場合の 2 つの具体的な使用例（親ページまたはドメインを制御できる場合とできない場合）に関わる問題の解決に役立つように設計されています。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 5 月のドキュメント更新 {#section-1d36b91bb7a140ce8a145251ffac9f2f}

<table id="table_CD031A716A694E8FA89695C9B614BC91"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> トピック </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../faq-intro/faq.md" format="dita" scope="local"> FAQ </a> </p> </td> 
   <td colname="col2"> <p>トラッキングサーバーの情報を見つける方法について、<span class="keyword">Analytics</span> に関する節を更新しました。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 4 月のドキュメント更新 {#section-df3e5a85448c4001a6791517520ae06e}

<table id="table_ADC2636240654C69B8B6A45849024540"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> トピック </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../library/function-vars/subdomain-config.md#reference-8ad017b3e5d24d34b3da25e8f8a56196" format="dita" scope="local"> audienceManagerServer および audienceManagerServerSecure </a> </p> </td> 
   <td colname="col2"> <p><span class="codeph">demdex.net</span> ドメインへの呼び出しについて説明する <span class="keyword">Audience Manager</span> ドキュメントへのリンクを追加しました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <a href="../library/function-vars/subdomain-config.md" format="dita" scope="local"> ID 同期と一致率について </a> </p> </td> 
   <td colname="col2"> <p><span class="keyword">Media Manager</span> に関する節を改訂し、<span class="codeph">cm.eversttech.net</span> への呼び出しについての説明を追加しました。これは、ID サービスと <span class="keyword">Media Manager</span> の間でおこなわれる自動 ID 同期です。この機能は 2017 年 1 月にリリースされました。後述の<a href="../release-notes/notes-2017.md#section-0ceac6007c1241b58ad607e2b76b2b7e" format="dita" scope="local">バージョン 2.0</a> を参照してください。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## バージョン 2.1 {#section-5e666dc47c2f4f92999e92697d75799e}

リリース日：2017 年 2 月

**機能**

<table id="table_1F7E1CF091604D22B1D9F3F1AE4DB2D7"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 機能 </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> ID サービス API プロパティ、<span class="codeph"> idSyncContainerID</span></p> </td> 
   <td colname="col2"> <p>このプロパティは、ID 同期用に <span class="keyword">Audience Manager</span> で使用されるコンテナ ID を設定します。<a href="/help/library/function-vars/idsyncontainerid.md" format="https" scope="external"> idSyncContainerID</a> を参照してください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>ID サービス API メソッド、<span class="codeph">appendSupplementalDataIDTo(<span class="varname"> URL</span>、<span class="varname"> SDID</span>)</span></p> </td> 
   <td colname="col2"> <p>この公開メソッドは、<span class="wintitle">Supplemental Data ID</span>（SDID）をクエリ文字列パラメーターとしてリダイレクト URL に追加します。<a href="../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d" format="dita" scope="local">appendSupplementalDataIDTo</a> を参照してください。（MCID-285） </p> </td> 
  </tr> 
 </tbody> 
</table>

**修正点**

ID サービスが原因で、AMCV Cookie に格納された ID を使用する代わりに ID の重複したサーバーコールを送信していた問題を修正しました。（MCID-296）

**新しいドキュメント**

[様々な Experience Cloud ソリューションおよびサービスによる DNS プリフェッチの使用](https://experienceleague.adobe.com/docs/core-services/interface/more-resources/dns-prefetch.html?lang=ja)

## バージョン 2.0 {#section-0ceac6007c1241b58ad607e2b76b2b7e}

2017 年 1 月

>[!IMPORTANT]
>
>ID サービスコード v2.0 はデフォルトで ID を自動的に Adobe Media Manager と同期します。つまり、ページから `cm.eversttech.net` への呼び出しが発生します。これは、[!DNL Adobe] が管理する従来の [!DNL Media Optimizer] ドメインです。[ID 同期と一致率について](../introduction/match-rates.md#concept-e55cf228b90c457fbee8c3cb06b195ab)も参照してください。

**修正点および改善点**

* AppMeasurement から Analytics に対してトラッキングコールを実行できない問題を修正しました。（MCID-254、MCID-256、MCID-286）
* 訪問者が demdex.net ドメインを除外するように設定された広告ブロッカーを利用している場合に ID サービスがトラッキングを停止するまでに時間がかかる問題を修正しました。demdex.net ドメインをブロックしない広告ブロックツールがほとんどなので、これはまれな問題です。（MCID-233）
* お客様の Web サイトでの ID サービスコードとカスタムスクリプトがコンフリクトすることがある問題を修正しました。この問題が原因で、Internet Explorer 9 で Web ページを読み込めませんでした。（MCID-206）

## 以前の年度 {#section-aaabe2b7b0f04641b24acffc11cd7d2e}

過去の ID サービスリリースノートです。
