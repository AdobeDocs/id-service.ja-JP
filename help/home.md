---
description: 'Experience Cloud ID サービスは、Experience Cloud のすべてのソリューションにわたって訪問者を識別する、普遍的、永続的な ID を提供します。 '
keywords: ID サービス
seo-description: Adobe Experience Cloud IDサービスは、Experience Cloudのすべてのソリューションで訪問者を識別する永続的な永続的IDを提供します。このサービスを、Analytics、Audience Manager、Target などのサービスや、その他の Experience Cloud のソリューションまたは機能の ID 生成コードの代わりに使用できます。
seo-title: Experience Cloud ID サービス
title: Experience Cloud ID サービス
uuid: b68194b5- e549-4f6f- bfaf-7744926aaac
translation-type: tm+mt
source-git-commit: cce8f5559baa0598fedaccf2fece6ec90cb641b7

---


# Experience Cloud ID サービス {#experience-cloud-id-service}

Experience Cloud ID サービス（ID サービス）は、Experience Cloud のすべてのソリューションにわたって訪問者を識別する、普遍的、永続的な ID を提供します。このサービスを、Analytics、Audience Manager、Target などのサービスや、その他の Experience Cloud のソリューションまたは機能の ID 生成コードの代わりに使用できます。

<table id="table_5E612F746A704FE095B809A013EE977F" class="simpletable"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>導入</b> </p> <p> 
     <ul id="ul_D5EC6A54A03F4AB595B588116A7C1296"> 
      <li id="li_845F6DE25A1241439BCDCBC00459D7EB"> <a href="mcvid-introduction/mcvid-overview.md" format="dita" scope="local"> 概要 </a> </li> 
      <li id="li_47F399E1D4AF4F08BD647DF01A423BA7"> <a href="mcvid-reference/mcvid-requirements.md" format="dita" scope="local"> Experience Cloud ID サービスの要件 </a> </li> 
      <li id="li_CBEEE79B45644F28A52B58DDF23DAD4F"> <a href="mcvid-implementation-guides/mcvid-standard.md#concept-89cd0199a9634fc48644f2d61e3d2445" format="dita" scope="local"> DTM を使用した標準的な実装 </a> </li> 
     </ul> </p> <p><b>Experience Cloud ID Javascript ライブラリ</b> </p> <p>Experience Cloud ID サービス向けの JavaScript は、<a href="https://github.com/Adobe-Marketing-Cloud/id-service/releases" format="https" scope="external">https://github.com/Adobe-Marketing-Cloud/id-service/releases</a> にあります。 </p> <p> <b>新しいトピックまたは注目すべきトピック</b> </p> <p> 
     <ul id="ul_B0A25B6827734D55BB1E20D12334AC21"> 
      <li id="li_A66924F4948F4A5ABA545A89A28A6F6A"><a href="mcvid-implementation-guides/opt-in-service/mcvid-optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local"> オプトインサービス</a> </li> 
      <li id="li_92D49CB788AD478EA74BCF5328CB9A14"> <a href="mcvid-library/mcvid-get-set/mcvid-getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues </a> </li> 
      <li id="li_9E512C6DD15C46C3ABD06ACD60D97E4A"> <a href="mcvid-faq-intro/ecid-faq-intro.md" format="dita" scope="local"> よくある質問（FAQ） </a> </li> 
      <li id="li_B28082F3D075413D89E5AFB718657E17"> <a href="mcvid-library/mcvid-function-vars/mcvid-coopsafe.md#reference-7fbed36f38a048d1a5883c53d430ddf4" format="dita" scope="local"> isCoopSafe </a> </li> 
      <li id="li_7744A4898EA542B9BF009D2066810050"> <a href="mcvid-library/mcvid-function-vars/mcvid-idsyncontainerid.md#reference-5cfbed2240fa4def90f535f017a36015" format="dita" scope="local"> idSyncContainerID </a> </li> 
     </ul> </p> 
    <draft-comment> 
     <p> <b>お知らせ：</b> </p> 
     <p> <p>重要:Internet Explorer6、7および8のIDサービスサポートは廃止され、今後のリリースで終了する予定です。 </p> </p> 
    </draft-comment> </td> 
   <td colname="col2"> <p> <b>リリースノート</b> </p> <p><b>バージョン4.0</b> の2019年2月12日リリースには <a href="mcvid-implementation-guides/opt-in-service/mcvid-optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local"> 、サイトの訪問時にユーザーのデバイスまたはブラウザーにcookieを配置できるかどうかを識別するために</a> 使用されるオプトインサービスが含まれています。 </p> <p>2018 年 1 月 18 日のリリースには、3.0.0 JavaScript アップデートおよび API メソッドのアップデートが含まれます。詳しくは、<a href="mcvid-library/mcvid-function-vars/mcvid-disableidsync.md#reference-589d6b489ac64eddb5a7ff758945e414" format="dita" scope="local"> disableIDSynccs</a> および <a href="mcvid-library/mcvid-function-vars/mcvid-disable-cookies.md#reference-2dd2d60d12f34f0b98bbb5606b3734cc" format="dita" scope="local"> disableThirdPartyCookies</a>。 </p> 
    <draft-comment> 
     <p>2017年10月リリースには、IDサービスのコード変更や更新は含まれていません。IDサービスコードは、v2.5では変更されません。 </p> 
    </draft-comment> 
    <draft-comment> 
     <p> 2017年9月リリースでは、IDサービスコードがv2.5に増分されています。 </p> 
    </draft-comment> <p> 
     <ul id="ul_4F06F170F214492780C7D25A069F799F"> 
      <li id="li_45A7CD556FE44F4DAB035C736A058F36"> 新機能と修正点については、最新の <a href="https://marketing.adobe.com/resources/help/en_US/whatsnew/" format="https" scope="external">Experience Cloud リリースノート</a>を参照してください。 </li> 
      <li id="li_10CC4FBFEFC947CA9AD15F52D9715257">過去のリリースについては、<a href="https://marketing-stage.adobe.com/resources/help/en_US/whatsnew/c_legacy_releases.html" format="html" scope="external">以前のリリースノート</a>を参照してください。 </li> 
     </ul> </p> <p> <b>Experience Cloud リソース</b> </p> <p> 
     <ul id="ul_E30EC96BDC624B5591F0470D430B7F41"> 
      <li id="li_F3A5CCFAE0F247CEB41A03CA8E03106B"> <a href="http://www.adobe.com/privacy.html" format="http" scope="external"> アドビプライバシーセンター</a> </li> 
      <li id="li_A54C1EB170EA4B8FA6A81B90AB0C39DD"> <a href="http://www.adobe.com/marketing-cloud.html" scope="external" format="http"> Adobe Experience Cloud</a> </li> 
      <li id="li_1938F7044F544481A6CC0F45CC22B80A"> <a href="http://helpx.adobe.com/learning.html?promoid=KAUDK" scope="external" format="http"> アドビトレーニングおよびチュートリアル</a> </li> 
      <li id="li_C71459E0D1464C05B8B9387C43541F17"> <a href="https://marketing.adobe.com/resources/help/en_US/home/index.html" scope="external" format="https"> 製品ドキュメントのホーム</a> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

