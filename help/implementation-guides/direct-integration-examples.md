---
description: これらの例は、直接統合と Experience Cloud ID（MID）に関連する 2 つの一般的なユースケースを扱っています。 MID はサイト訪問者の一意の永続的な ID です。
keywords: ID サービス
title: 直接統合の使用例
exl-id: f2a55b90-8307-4242-b20a-6a3c367a251b
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 100%

---

# 直接統合の使用例 {#direct-integration-use-cases}

直接統合と Experience Cloud ID（ECID または MID）に関連する 2 つの一般的な使用例を示します。この ID は、サイト訪問者に割り当てられる一意の永続的 ID です。

>[!TIP]
>
>* 使用例を参照する前に、[コード構文と変数](../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9)をよくお読みください。
>* MID について詳しくは、[Cookie と Experience Cloud ID サービス](../introduction/cookies.md)を参照してください。
>

## ユースケース 1：Experience Cloud ID（MID）は持っているが、自分の訪問者 ID を渡して認証状態を設定したい {#section-a67d89a343754d1286d03cf08d34b806}

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
   <td colname="col2"> <p>このユースケースでは、次のことを仮定します。 </p> 
    <ul id="ul_F20231F83EE84889B78971A64E758757"> 
     <li id="li_20F3E96493724CD2BAF4B20AEE5CBF23">サイト訪問者の MID がある。この ID を 1234 としましょう。 </li> 
     <li id="li_A358C58CC58C4FCBB7250F5ED108AA71">この訪問者を独自の一意の ID で確認できる。 この ID を 9876 としましょう。 </li> 
     <li id="li_D93CE7182EBE4927A5C7A0BF414C03BC">MID（1234）を独自の一意の ID（9876）にリンクする必要がある。 </li> 
     <li id="li_4611146E56624C2AB647733487A3F046"> <i>（オプション）</i>この訪問者に認証ステ－タスを設定する必要がある。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>アクション</b> </p> </td> 
   <td colname="col2"> <p>これらの条件を前提として、以下を含む ID サービスを呼び出します。 </p> 
    <ul id="ul_9ECB1A65266644E89E949C57D202D5A4"> 
     <li id="li_10A6F5A9C54D44A08F4F2E405E6019E2">MID（1234）。 </li> 
     <li id="li_4869572B40E54C54B88A2474DAC475A8">データプロバイダー ID。 これは、会社に割り当てられる一意の ID です。 この ID を 4444 としましょう。 </li> 
     <li id="li_05C8ED47488C4E289D84093127EC7B19">訪問者の ID（9876）。 </li> 
     <li id="li_3D1556AD18C843828A362CC604A9F76B"> <i>（オプション）</i>この訪問者の認証状態を定義するステータス ID。 </li> 
    </ul> <p>また、<a href="../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9" format="dita" scope="local">直接統合ガイド</a>に記載されている他のパラメーター（<span class="codeph">d_blob</span> や <span class="codeph">dcs_region</span> など）のいずれかがわかっている場合は、それらも渡してかまいません。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>ソリューションとコードサンプル</b> </p> </td> 
   <td colname="col2"> <p>ID サービスへの呼び出しを次のような形式に設定します。 </p> <p> <span class="codeph">https://dpm.demdex.net/id?d_mid=1234&amp;d_cid=4444%019876%011&amp;d_ver=2</span> </p> <p>この呼び出しの例には以下が含まれていることに注意してください。 </p> 
    <ul id="ul_0667FBFD8D3C46BDBD027F484691EC97"> 
     <li id="li_FAB1FAE703DB48D1A32EE72684028964">MID：<span class="codeph">d_mid=1234</span> </li> 
     <li id="li_C97B74FF444F4BB4B4A5CB1CBBE52249">訪問者の独自の ID に結合された MID：<span class="codeph">d_mid=1234&amp;d_cid=4444%019876%011</span> </li> 
     <li id="li_D428DBF765234DD78DDF152C5EE8AB69">認証状態 ID：<span class="codeph">...d_cid=4444%019876%011</span>（ヒント：最後の 1 桁）。 </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## ユースケース 2：MID を持っていないので生成する必要がある {#section-8e81291f8b684de8b88fae4002ae0029}

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
   <td colname="col2"> <p>このユースケースでは、次のことを仮定します。 </p> 
    <ul id="ul_BF3BD821907B46A4B2EFA63146D35722"> 
     <li id="li_E658AE0671D14558B65FDD8992F25996">サイト訪問者の MID がない。 </li> 
     <li id="li_28A48BB3F71C4E4297F95A2D3E10AD7B">ID サービスに MID をリクエストする必要がある。 </li> 
     <li id="li_E2C306B9308D41E5BFE2F23EF48F5A41">自社の<a href="../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26" format="dita" scope="local">組織 ID</a> がわかっている。これを 5555 としましょう。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>アクション</b> </p> </td> 
   <td colname="col2"> <p>これらの条件を前提として、組織 ID を含む ID サービスを呼び出します。 </p> <p>また、<a href="../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9" format="dita" scope="local">直接統合ガイド</a>に記載されている他のパラメーター（<span class="codeph">d_blob</span> や <span class="codeph">dcs_region</span> など）のいずれかがある場合は、それらも渡してかまいません。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>ソリューションとコードサンプル</b> </p> </td> 
   <td colname="col2"> <p>ID サービスへの呼び出しを次のような形式に設定します。 </p> <p> <span class="codeph">https://dpm.demdex.net/id?d_orgid=5555&amp;d_ver=2</span> </p> <p>この呼び出しの例には組織 ID <span class="codeph">d_orgid=5555</span> が含まれていることに注意してください。この訪問者の <span class="keyword">Experience Cloud</span> ID が返されます。 </p> </td> 
  </tr> 
 </tbody> 
</table>
