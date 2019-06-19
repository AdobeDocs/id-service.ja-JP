---
description: 2017 年の Experience Cloud ID サービスの機能リリース、更新、変更点です。
keywords: ID サービス
seo-description: 2017 年の Experience Cloud ID サービスの機能リリース、更新、変更点です。
seo-title: 2017 年リリースノート
title: 2017 年リリースノート
uuid: 79452df0-49db-42b8-96fe-01aa7629fbb5
translation-type: tm+mt
source-git-commit: 4dc668afd37cd1d6f9104adb1b102f1dd4c5746e

---


# 2017 年リリースノート {#release-notes}

2017 年の Experience Cloud ID サービスの機能リリース、更新、変更点です。

これらの変更点は、[Experience Cloud リリースノート](https://marketing.adobe.com/resources/help/en_US/whatsnew/)にも記載されています。以前の ID サービスリリースノートについては、[以前のリリースノート](https://marketing.adobe.com/resources/help/en_US/whatsnew/?f=c_legacy_releases.html)またはこのページの下部にあるリンクを参照してください。

>[!NOTE]
>
>お客様向けリリースノートやコードの変更は、3月、4月、2017年5月、および10月には変更されません。これらの月の ID サービスコードは v2.1 から変更されていません。

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
   <td colname="col2"> <p>これは、デフォルトで Analytics の識別子、ID サービス、データ収集オプトアウト、地域およびメタデータ「blob」コンテンツを返す非同期 API です。オプションの <span class="codeph">visitor.FIELDS</span> 列挙を使用して、返される ID を制御することもできます。<a href="../mcvid-library/mcvid-get-set/mcvid-getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues</a>を参照してください。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**問題の修正とその他の変更**

* Chrome でブラウザーの戻るボタンをクリックしたときに ID サービスがエラー状態になる問題を修正しました。
* ID サービスで、イベント呼び出し応答の地域 ID が変更されたときに ID 同期が再実行されるようになりました。
* 新たに追加したドキュメント、[コンテンツセキュリティポリシーおよび Experience Cloud ID サービス](/help/mcvid-reference/mcvid-csp.md#concept-968c423a7392479db0a0d821ae9783e3)で、ID サービスで使用されるアドビドメインへの呼び出しをホワイトリストに登録する方法を説明しています。

## バージョン2.4 {#section-f4d1608dd8894f558a92b82e83321200}

2017 年 8 月

<table id="table_D9623D34F4444B038F7835750932C8AA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 機能 </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe</span> </p> </td> 
   <td colname="col2"> <p>ID サービスから Adobe Experience Cloud Device Co-op にデータを送信するかどうかを指定する任意のブール型設定です。<a href="../mcvid-library/mcvid-function-vars/mcvid-coopsafe.md#reference-7fbed36f38a048d1a5883c53d430ddf4" format="dita" scope="local">isCoopSafe</a> を参照してください。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**改訂されたドキュメント**

更新および [FAQs](/help/mcvid-faq-intro/mcvid-faq-intro.md) to include separate FAQs for different [!DNL Experience Cloud] solutions.

## バージョン2.3 {#section-ae7b1cb1e52e4ca5a46b453a3ba1f571}

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
   <td colname="col2"> <p>この設定を <span class="codeph">Visitor.getInstance</span> 関数に追加すると、追加データ ID（SDID）をあるページから別のページに渡す際に、デフォルトの ID の有効期限を上書きできます。<span class="codeph">sdidParamExpiry</span> は <span class="codeph">appendSupplimentalDataTo</span> ヘルパー関数と共に使用します。<a href="../mcvid-library/mcvid-function-vars/mcvid-sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458" format="dita" scope="local">sdidParamExpiry</a> を参照してください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> resetState</span> </p> </td> 
   <td colname="col2"> <p>この機能は、単一ページのサイト／画面またはアプリでの ID の使用に関連する問題を解決するために、主に A4T のお客様向けに設計されています。<a href="../mcvid-library/mcvid-get-set/mcvid-resetstate.md#reference-47fc00ae139042d795d78244d9970139" format="dita" scope="local">resetState</a> を参照してください。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**問題の修正とその他の変更**

* VisitorAPI.js バージョン 2.2 で、Internet Explorer において ID サービスと Target が連携しなかった問題を修正しました。
* ID サービスが Destination Publishing iFrame にデータを送信する方法を改善するために、コードを改訂しました。これにより、CPU 負荷を低減できます。

## バージョン 2.2 {#section-b7dee2495c29470e9b3a3132ec1fd951}

リリース日:2017年6月

<table id="table_7E412383E89D46759B00FE7328C9946F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 機能 </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../mcvid-library/mcvid-function-vars/mcvid-whitelistdomain.md#reference-999899ff7b5b429a8824c9db7a379808" format="dita" scope="local"> whitelistParentDomain および whitelistIframeDomains </a> </p> </td> 
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
   <td colname="col1"> <p> <a href="../mcvid-faq-intro/mcvid-faq.md" format="dita" scope="local"> FAQ </a> </p> </td> 
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
   <td colname="col1"> <p> <a href="../mcvid-library/mcvid-function-vars/mcvid-subdomain-config.md#reference-8ad017b3e5d24d34b3da25e8f8a56196" format="dita" scope="local"> audienceManagerServer および audienceManagerServerSecure </a> </p> </td> 
   <td colname="col2"> <p><span class="codeph">demdex.net</span> ドメインへの呼び出しについて説明する <span class="keyword">Audience Manager</span> ドキュメントへのリンクを追加しました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <a href="../mcvid-library/mcvid-function-vars/mcvid-subdomain-config.md" format="dita" scope="local"> ID 同期と一致率について </a> </p> </td> 
   <td colname="col2"> <p><span class="keyword">Media Manager</span> に関する節を改訂し、<span class="codeph">cm.eversttech.net</span> への呼び出しについての説明を追加しました。これは、ID サービスと <span class="keyword">Media Manager</span> の間でおこなわれる自動 ID 同期です。この機能は 2017 年 1 月にリリースされました。後述の<a href="../mcvid-release-notes/mcvid-notes-2017.md#section-0ceac6007c1241b58ad607e2b76b2b7e" format="dita" scope="local">バージョン 2.0</a> を参照してください。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## バージョン2.1 {#section-5e666dc47c2f4f92999e92697d75799e}

リリース日:2017年2月

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
   <td colname="col1"> <p> ID サービス API のプロパティ、<span class="codeph">idSyncContainerID</span></p> </td> 
   <td colname="col2"> <p>このプロパティは、ID 同期用に <span class="keyword">Audience Manager</span> で使用されるコンテナ ID を設定します。<a href="https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-idsyncontainerid.html" format="https" scope="external">idSyncContainerID</a> を参照してください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>ID サービス API メソッド <span class="codeph"> appendSupplementalDataIDTo( <span class="varname"> URL </span>, <span class="varname"> SDID</span>)</span></p> </td> 
   <td colname="col2"> <p>この公開メソッドは、<span class="wintitle">Supplemental Data ID</span>（SDID）をクエリ文字列パラメーターとしてリダイレクト URL に追加します。<a href="../mcvid-library/mcvid-get-set/mcvid-appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d" format="dita" scope="local"> appendSupplementalDataIDToを参照</a>してください。（MCID-285） </p> </td> 
  </tr> 
 </tbody> 
</table>

**修正点**

ID サービスが原因で、AMCV Cookie に格納された ID を使用する代わりに ID の重複したサーバーコールを送信していた問題を修正しました。（MCID-296）

**新しいドキュメント**

[様々な Experience Cloud ソリューションおよびサービスによる DNS プリフェッチの使用`Learn how to use DNS prefetch to help reduce page load times.`](https://marketing.adobe.com/resources/help/en_US/mcloud/dns-prefetch.html)

## バージョン2.0 {#section-0ceac6007c1241b58ad607e2b76b2b7e}

2017 年 1 月

>[!IMPORTANT]
>
>IDサービスコードv2.0は、デフォルトでIDを自動的にAdobe Media Managerと同期します。つまり、ページからの呼び出しが、そのページから制御されます `cm.eversttech.net`。これは、によって制御されるレガシー [!DNL Media Optimizer] ドメイン [!DNL Adobe]です。[ID 同期と一致率について](../mcvid-introduction/mcvid-match-rates.md#concept-e55cf228b90c457fbee8c3cb06b195ab)も参照してください。

**修正点および改善点**

* AppMeasurement から Analytics に対してトラッキングコールを実行できない問題を修正しました。（MCID-254、MCID-256、MCID-286）
* 訪問者が demdex.net ドメインを除外するように設定された広告ブロッカーを利用している場合に ID サービスがトラッキングを停止するまでに時間がかかる問題を修正しました。demdex.net ドメインをブロックしない広告ブロックツールがほとんどなので、これはまれな問題です。（MCID-233）
* お客様の Web サイトでの ID サービスコードとカスタムスクリプトがコンフリクトすることがある問題を修正しました。この問題が原因で、Internet Explorer 9 で Web ページを読み込めませんでした。（MCID-206）

## 以前の年度 {#section-aaabe2b7b0f04641b24acffc11cd7d2e}

過去の ID サービスリリースノートです。
