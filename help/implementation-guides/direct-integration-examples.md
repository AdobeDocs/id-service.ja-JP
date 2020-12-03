---
description: 次の例は、直接統合とExperience CloudID(MID)に関連する2つの一般的な使用例を示しています。 MIDは、サイト訪問者の一意の永続的なIDです。
keywords: ID Service
seo-description: 次の例は、直接統合とExperience CloudID(MID)に関連する2つの一般的な使用例を示しています。 MIDは、サイト訪問者の一意の永続的なIDです。
seo-title: 直接統合の使用例
title: 直接統合の使用例
uuid: 6de1eb8b-4783-4545-8a64-ab6b9ef93432
translation-type: tm+mt
source-git-commit: ec67177fc6491e4c8cea835d198574c9fdb4b01f
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 40%

---


# 直接統合の使用例 {#direct-integration-use-cases}

直接統合と Experience Cloud ID（ECID または MID）に関連する 2 つの一般的な使用例を示します。この ID は、サイト訪問者に割り当てられる一意の永続的 ID です。

>[!TIP]
>
>* 使用例を参照する前に、[コード構文と変数](../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9)をよくお読みください。
>* MID について詳しくは、[Cookie と Experience Cloud Identity Service](../introduction/cookies.md) を参照してください。

>



## 使用例 1：Experience Cloud ID（MID）はあるが、自分の訪問者 ID を渡して認証状態を設定したい {#section-a67d89a343754d1286d03cf08d34b806}

<table id="table_DA8840FCB51541109FE6DF20430E8924"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 使用例の要素 </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>条件</b> </p> </td> 
   <td colname="col2"> <p>この使用例では、次のことを前提としています。 </p> 
    <ul id="ul_F20231F83EE84889B78971A64E758757"> 
     <li id="li_20F3E96493724CD2BAF4B20AEE5CBF23">サイト訪問者のMIDを持つ。 このIDを1234と呼びましょう。 </li> 
     <li id="li_A358C58CC58C4FCBB7250F5ED108AA71">この訪問者は、独自の一意のIDで確認できます。 このIDを9876と呼びましょう。 </li> 
     <li id="li_D93CE7182EBE4927A5C7A0BF414C03BC">MID(1234)を独自の一意のID(9876)にリンクする。 </li> 
     <li id="li_4611146E56624C2AB647733487A3F046"> <i>（オプション）</i> この訪問者で認証状態を設定します。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>アクション</b> </p> </td> 
   <td colname="col2"> <p>これらの条件の場合、次を含むIDサービスを呼び出します。 </p> 
    <ul id="ul_9ECB1A65266644E89E949C57D202D5A4"> 
     <li id="li_10A6F5A9C54D44A08F4F2E405E6019E2">MID(1234)。 </li> 
     <li id="li_4869572B40E54C54B88A2474DAC475A8">データプロバイダーID。 これは、会社に割り当てられる一意のIDです。 このIDを4444と呼びましょう。 </li> 
     <li id="li_05C8ED47488C4E289D84093127EC7B19">訪問者のID (9876)。 </li> 
     <li id="li_3D1556AD18C843828A362CC604A9F76B"> <i>（オプション）</i> 、この訪問者の認証状態を定義するステータスID。 </li> 
    </ul> <p>また、 <a href="../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9" format="dita" scope="local"> 直接統合ガイドに記載されているその他のパラメーター(例：</a> d_blob<span class="codeph"> 、</span> dcs_region <span class="codeph"></span>など)がある場合は、 それらも受け取ってもいい。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>ソリューションとコードのサンプル</b> </p> </td> 
   <td colname="col2"> <p>IDサービスへの呼び出しを次のようにフォーマットします。 </p> <p> <span class="codeph">https://dpm.demdex.net/id?d_mid=1234&amp;d_cid=4444%019876%011&amp;d_ver=2</span> </p> <p>この呼び出しの例には以下が含まれていることに注意してください。 </p> 
    <ul id="ul_0667FBFD8D3C46BDBD027F484691EC97"> 
     <li id="li_FAB1FAE703DB48D1A32EE72684028964">MID：<span class="codeph">d_mid=1234</span> </li> 
     <li id="li_C97B74FF444F4BB4B4A5CB1CBBE52249">訪問者の独自の ID に結合された MID：<span class="codeph">d_mid=1234&amp;d_cid=4444%019876%011</span> </li> 
     <li id="li_D428DBF765234DD78DDF152C5EE8AB69">認証状態 ID：<span class="codeph">...d_cid=4444%019876%011</span>（ヒント：最後の 1 桁）。 </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## 使用例 2：MID がないので生成する必要がある {#section-8e81291f8b684de8b88fae4002ae0029}

<table id="table_666A92693F8A413096DF6A64770C1141"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 使用例の要素 </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>条件</b> </p> </td> 
   <td colname="col2"> <p>この使用例では、次のことを前提としています。 </p> 
    <ul id="ul_BF3BD821907B46A4B2EFA63146D35722"> 
     <li id="li_E658AE0671D14558B65FDD8992F25996">サイト訪問者のMIDがない。 </li> 
     <li id="li_28A48BB3F71C4E4297F95A2D3E10AD7B">IDサービスからMIDを要求する必要があります。 </li> 
     <li id="li_E2C306B9308D41E5BFE2F23EF48F5A41">自社の<a href="../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26" format="dita" scope="local">組織 ID</a> がわかっている。5555と呼ぼう。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>アクション</b> </p> </td> 
   <td colname="col2"> <p>これらの条件の場合、組織IDを含むIDサービスを呼び出します。 </p> <p>また、 <a href="../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9" format="dita" scope="local"> 直接統合ガイドに記載されているその他のパラメーター(例：</a> d_blob<span class="codeph"> 、</span> dcs_region <span class="codeph"></span>など)がある場合は、 それらも受け取ってもいい。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>ソリューションとコードのサンプル</b> </p> </td> 
   <td colname="col2"> <p>IDサービスへの呼び出しを次のようにフォーマットします。 </p> <p> <span class="codeph">https://dpm.demdex.net/id?d_orgid=5555&amp;d_ver=2</span> </p> <p>この呼び出しの例には組織 ID <span class="codeph">d_orgid=5555</span> が含まれていることに注意してください。この訪問者の <span class="keyword">Experience Cloud</span> ID が返されます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

