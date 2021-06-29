---
description: 'Experience Cloud Identity Service は、Experience Cloud のすべてのソリューションにわたって訪問者を識別する、普遍的、永続的な ID を提供します。 '
keywords: ID サービス
title: Experience Cloud Identity Service
exl-id: fe1368db-06ca-4c79-b655-b7064e316d74
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '253'
ht-degree: 100%

---

# Adobe Experience Cloud Identity Service {#experience-cloud-id-service}

Adobe Experience Cloud Identity Service（ID サービス）は、Experience Cloud のすべてのソリューションにわたって訪問者を識別する、普遍的、永続的な ID を提供します。このサービスを、Analytics、Audience Manager、Target などのサービスや、その他の Experience Cloud のソリューションまたは機能の ID 生成コードの代わりに使用できます。

<table id="table_5E612F746A704FE095B809A013EE977F" class="simpletable"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>導入</b> </p> <p> 
     <ul id="ul_D5EC6A54A03F4AB595B588116A7C1296"> 
      <li id="li_845F6DE25A1241439BCDCBC00459D7EB"> <a href="introduction/overview.md" format="dita" scope="local"> 概要 </a> </li> 
      <li id="li_47F399E1D4AF4F08BD647DF01A423BA7"> <a href="reference/requirements.md" format="dita" scope="local">Experience Cloud Identity Service の要件</a> </li> 
      <li id="li_CBEEE79B45644F28A52B58DDF23DAD4F"> <a href="implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445" format="dita" scope="local"> DTM を使用した標準的な実装 </a> </li> 
     </ul> </p> <p><b>Experience Cloud ID Javascript ライブラリ</b> </p> <p>Experience Cloud Identity Service 向けの JavaScript は、<a href="https://github.com/Adobe-Marketing-Cloud/id-service/releases" format="https" scope="external">https://github.com/Adobe-Marketing-Cloud/id-service/releases</a> にあります。 </p> <p> <b>新しいトピックまたは注目すべきトピック</b> </p> <p> 
     <ul id="ul_B0A25B6827734D55BB1E20D12334AC21"> 
      <li id="li_A66924F4948F4A5ABA545A89A28A6F6A"><a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local">オプトインサービス</a> </li> 
      <li id="li_92D49CB788AD478EA74BCF5328CB9A14"> <a href="library/get-set/getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues </a> </li> 
      <li id="li_9E512C6DD15C46C3ABD06ACD60D97E4A"> <a href="faq-intro/faq-intro.md" format="dita" scope="local"> よくある質問（FAQ） </a> </li> 
      <li id="li_B28082F3D075413D89E5AFB718657E17"> <a href="library/function-vars/coopsafe.md#reference-7fbed36f38a048d1a5883c53d430ddf4" format="dita" scope="local"> isCoopSafe </a> </li> 
      <li id="li_7744A4898EA542B9BF009D2066810050"> <a href="library/function-vars/idsyncontainerid.md#reference-5cfbed2240fa4def90f535f017a36015" format="dita" scope="local"> idSyncContainerID </a> </li> 
     </ul> </p> 
     <!-- 
     <p> <b>Announcements:</b> </p> 
     <p> <p>Important:  ID service support for Internet Explorer 6, 7, and 8 is deprecated and will be discontinued in a future release. </p> </p> 
     --> </td> 
   <td colname="col2"> <p> <b>リリースノート</b> </p> <p><b>バージョン 4.4</b> 2019 年 7 月 17 日リリースには、顧客 ID または電子メールアドレスを渡し、ハッシュされた ID を受け取ることが可能な、<a href="reference/hashing-support.md" format="dita" scope="local">SHA-256 ハッシュアルゴリズム</a>のサポートが含まれます。</p><p><b>バージョン 4.0</b> 2019 年 2 月 12 日リリースには、ユーザーがサイトにアクセスする際に、ユーザーのデバイスまたはブラウザーに cookie を配置できるかどうかを識別する<a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local">オプトインサービス</a>が含まれています。 </p> <p> 
     <ul id="ul_4F06F170F214492780C7D25A069F799F"> 
      <li id="li_45A7CD556FE44F4DAB035C736A058F36"> 新機能と修正点については、最新の <a href="https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=ja" format="https" scope="external">Experience Cloud リリースノート</a>を参照してください。 </li> 
      <li id="li_10CC4FBFEFC947CA9AD15F52D9715257">過去のリリースについては、<a href="https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=ja" format="html" scope="external">以前のリリースノート</a>を参照してください。 </li> 
     </ul> </p> <p> <b>Experience Cloud リソース</b> </p> <p> 
     <ul id="ul_E30EC96BDC624B5591F0470D430B7F41"> 
      <li id="li_F3A5CCFAE0F247CEB41A03CA8E03106B"> <a href="http://www.adobe.com/jp/privacy.html" format="http" scope="external"> アドビプライバシーセンター</a> </li> 
      <li id="li_A54C1EB170EA4B8FA6A81B90AB0C39DD"> <a href="https://experienceleague.adobe.com/docs/home.html?lang=ja" scope="external" format="http"> Adobe Experience Cloud</a> </li> 
      <li id="li_1938F7044F544481A6CC0F45CC22B80A"> <a href="http://helpx.adobe.com/jp/learning.html?promoid=KAUDK" scope="external" format="http"> アドビトレーニングおよびチュートリアル</a> </li> 
      <li id="li_C71459E0D1464C05B8B9387C43541F17"> <a href="https://helpx.adobe.com/jp/support/experience-cloud.html" scope="external" format="https"> 製品ドキュメントのホーム</a> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>
