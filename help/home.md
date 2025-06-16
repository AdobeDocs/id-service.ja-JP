---
description: Experience Cloud ID サービスは、Experience Cloud アプリケーションおよびサービスの共通の ID フレームワークを可能にします。このサービスは、Experience Cloud ID（ECID）と呼ばれる一意の永続的 ID をサイト訪問者に割り当てることで機能します。
keywords: ID サービス; ID サービス; Experience Cloud ID サービス
title: Experience Cloud ID サービス
exl-id: fe1368db-06ca-4c79-b655-b7064e316d74
source-git-commit: 507b5c9fed0d6d16828522c0fd9c7db4fdeefe3d
workflow-type: ht
source-wordcount: '355'
ht-degree: 100%

---

# Adobe Experience Cloud ID サービス {#experience-cloud-id-service}

Experience Cloud ID サービスは、Experience Cloud アプリケーションおよびサービスの共通の ID フレームワークを可能にします。このサービスは、Experience Cloud ID（ECID）と呼ばれる一意の永続的 ID をサイト訪問者に割り当てることで機能します。

## ID のメインエンティティについて

アドビがどのように訪問者を一意に識別し、ID 情報を解決しているかを深く理解するには、以下の分類を参照してください。

* **Experience Cloud ID サービス**：Experience Cloud ID サービス&#x200B;**は、Experience Cloud ID（ECID）を設定する役割を果たします**。詳しくは、[Experience Cloud ID サービスの概要](./introduction/overview.md)を参照してください。
* **Experience Cloud ID（ECID）**：ECID は、Adobe Experience Platform および Adobe Experience Cloud アプリケーションで人物やデバイスの識別に使用される共有の ID 名前空間です。ECID について詳しくは、[ECID の概要](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html?lang=ja)を参照してください。
* **Experience Platform ID サービス**：Experience Platform ID サービスは、デバイスやシステム間で ID を橋渡しすることで、顧客とその行動を包括的に把握できるようにします。詳しくは、[Experience Platform ID サービスの概要](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=ja)を参照してください。

<!-- The Adobe Experience Cloud Identity Service provides a universal, persistent ID that identifies your visitors across all the solutions in the Experience Cloud. It can replace ID generation code for Experience Cloud solutions and services. -->

<table id="table_5E612F746A704FE095B809A013EE977F" class="simpletable"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>導入</b> </p> <p> 
     <ul id="ul_D5EC6A54A03F4AB595B588116A7C1296"> 
      <li id="li_845F6DE25A1241439BCDCBC00459D7EB"> <a href="introduction/overview.md" format="dita" scope="local"> 概要 </a> </li> 
      <li id="li_47F399E1D4AF4F08BD647DF01A423BA7"> <a href="reference/requirements.md" format="dita" scope="local">Experience Cloud ID サービスの要件</a> </li> 
      <li id="li_CBEEE79B45644F28A52B58DDF23DAD4F"> <a href="https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=ja" format="html" scope="external">Platform タグを使用した標準実装 </a> </li> 
     </ul> </p> <p><b>Experience Cloud ID Javascript ライブラリ</b> </p> <p>Experience Cloud ID サービス向けの JavaScript は、<a href="https://github.com/Adobe-Marketing-Cloud/id-service/releases" format="https" scope="external">https://github.com/Adobe-Marketing-Cloud/id-service/releases</a> にあります。 </p> <p> <b>新しいトピックまたは注目すべきトピック</b> </p> <p> 
     <ul id="ul_B0A25B6827734D55BB1E20D12334AC21"> 
      <li id="li_A66924F4948F4A5ABA545A89A28A6F6A"><a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local">オプトインサービス</a> </li> 
      <li id="li_92D49CB788AD478EA74BCF5328CB9A14"> <a href="library/get-set/getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues </a> </li> 
      <li id="li_9E512C6DD15C46C3ABD06ACD60D97E4A"> <a href="faq-intro/faq-intro.md" format="dita" scope="local"> よくある質問（FAQ） </a> </li> 
      <li id="li_7744A4898EA542B9BF009D2066810050"> <a href="library/function-vars/idsyncontainerid.md#reference-5cfbed2240fa4def90f535f017a36015" format="dita" scope="local"> idSyncContainerID </a> </li> 
     </ul> </p> 
     <!-- 
     <p> <b>Announcements:</b> </p> 
     <p> <p>Important:  ID service support for Internet Explorer 6, 7, and 8 is deprecated and will be discontinued in a future release. </p> </p> 
     --> </td> 
   <td colname="col2"> <p> <b>リリースノート</b> </p> <p><b>バージョン 4.4</b> 2019年7月17日リリースには、顧客 ID または電子メールアドレスを渡し、ハッシュされた ID を受け取ることが可能な、<a href="reference/hashing-support.md" format="dita" scope="local">SHA-256 ハッシュアルゴリズム</a>のサポートが含まれます。</p><p><b>バージョン 4.0</b> 2019年2月12日リリースには、ユーザーがサイトにアクセスする際に、ユーザーのデバイスまたはブラウザーに cookie を配置できるかどうかを識別する<a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local">オプトインサービス</a>が含まれています。 </p> <p> 
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
