---
description: オプトインサービスを管理するための使用例と解決策のサンプルです。
seo-description: オプトインサービスを管理するための使用例と解決策のサンプルです。
seo-title: オプトインの使用例
title: オプトインの使用例
uuid: d75a44d5-b713-43d1-b5b6-95d1d0d213a7
translation-type: tm+mt
source-git-commit: 0c300aa92991c0dec2ccdeeb34f9d886dcac7671
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 16%

---


# オプトインの使用例 {#opt-in-use-cases}

オプトインサービスを管理するための使用例と解決策のサンプルです。

## ヒントとトラブルシューティング {#section-5c566366410f4a8f89eca0d3f556d99f}

* 訪問者JSの初期化は同期的で、ページの読み込み中に実行されます。 待ち時間の長いCMPや権限の持続性を扱う場合は、 [オプトイン設定で説明されている非同期関数を使用することをお勧めします](../../implementation-guides/opt-in-service/getting-started.md#section-cf9ab638780141c9b62dc57cf00b7047)。
* オプトインは、ドメインごとの実装です。 クロスドメイン実装は処理されません。
* 特定のライブラリに対するサードパーティ呼び出しを無効にするには、各ライブラリでその環境設定を個別に設定する必要があります。

## オプトインシナリオ {#section-1178053c065c430bba26f82ef383a71c}

以下の使用例は、オプトインサービスを使用するためのアイデアの例です。

<table id="table_83C85343611344D8A8315157C1B4240F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 要件 </th> 
   <th colname="col2" class="entry"> ソリューション </th> 
   <th colname="col3" class="entry"> 影響 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Analyticsは事前同意状態で収集しても構いませんが、同意が得られるまで、他のすべてのライブラリを読み込むことはできません </p> </td> 
   <td colname="col2"> <p>オプトインを使用して、Analyticsカテゴリを事前同意状態で有効にする </p> </td> 
   <td colname="col3"> <p>Analyticsは、事前同意の収集でECIDではなくAnalyticsの識別子を使用します。 ECIDが承認されると、新しい識別子が使用され、訪問者は、アクティベーションおよび統合に使用できるECIDを受け取ります。 </p> <p>同意前/同意後の状態での訪問者フラグメント化が必要です。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>ファーストパーティの測定は、事前同意の状態で収集しても問題ありません。 その他のタイプのデータの使用は、同意を受け取るまで妨げられています。 </p> </td> 
   <td colname="col2"> <p>オプトインを使用して、Analytics + ECIDライブラリを事前同意の状態で有効にします。 </p> <p>サ追加ードパーティcookieをブロックするためのECIDライブラリに対する「disablethirdpartycookies」設定と、事前同意状態のID同期 </p> </td> 
   <td colname="col3"> <p>AdobeDemdex呼び出しはECID取得のためにトリガーされますが、Demdex cookie、他のサードパーティcookieまたはID同期は存在しません。 </p> <p>Analyticsの同意前/後の状態で、一貫した訪問者を維持します。 事前同意状態の収集は、事後同意データ収集に結び付けられます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>ファーストパーティの測定とターゲティングは、事前同意の状態で受け入れられます。 その他のタイプのデータの使用は、同意を受け取るまで妨げられています。 </p> </td> 
   <td colname="col2"> <p>オプトインを使用して、Analytics + ECID +ターゲットライブラリを事前同意の状態で有効にします。 </p> <p>ECID ライブラリに <span class="codeph">isablethirdpartycookies</span> 設定を追加し、同意前の状態のサードパーティ Cookie と ID 同期をブロックします。同意後の状態のフラグを削除します。 </p> </td> 
   <td colname="col3"> <p>AdobeDemdex呼び出しはECID取得のためにトリガーされますが、Demdex cookie、他のサードパーティcookieまたはID同期は存在しません。 </p> <p>ファーストパーティのソリューションの同意前/後の状態で一貫した訪問者を維持します。 事前同意状態の収集は、事後同意データ収集に結び付けられます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>事前同意状態でのCookieの設定は許可されません </p> </td> 
   <td colname="col2"> <p>オプトインを使用して、同意が得られるまですべてのライブラリの読み込みをブロックする </p> </td> 
   <td colname="col3"> <p>実装は期待どおりで、ECIDを含むすべてのライブラリが、同意後の状態で正しい順序で読み込まれます。 </p> <p>追跡を許可しない顧客のデータ損失。 </p> </td> 
  </tr> 
 </tbody> 
</table>

