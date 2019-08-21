---
description: オプトインサービスを管理するための使用例と解決策のサンプルです。
seo-description: オプトインサービスを管理するための使用例と解決策のサンプルです。
seo-title: オプトインの使用例
title: オプトインの使用例
uuid: d75a44d5-b713-43d1-b5b6-95d1d0d213a7
translation-type: ht
source-git-commit: 0c300aa92991c0dec2ccdeeb34f9d886dcac7671

---


# オプトインの使用例 {#opt-in-use-cases}

オプトインサービスを管理するための使用例と解決策のサンプルです。

## ヒントとトラブルシューティング {#section-5c566366410f4a8f89eca0d3f556d99f}

* Visitor JS の初期化は、ページの読み込み中に同期的に実行されます。待ち時間の長い CMP または権限の保持を調整している場合は、[オプトインの設定](../../implementation-guides/opt-in-service/getting-started.md#section-cf9ab638780141c9b62dc57cf00b7047)で説明した非同期関数を使用することをお勧めします。
* オプトインは、ドメインごとに実装します。ドメインをまたがった実装は処理されません。
* 特定のライブラリに対するサードパーティの呼び出しを無効にするには、各ライブラリで個別にその設定をおこなう必要があります。

## オプトインのシナリオ {#section-1178053c065c430bba26f82ef383a71c}

以下の使用例は、オプトインサービスを使用するためのアイデアの例です。

<table id="table_83C85343611344D8A8315157C1B4240F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 要件 </th> 
   <th colname="col2" class="entry"> 解決策 </th> 
   <th colname="col3" class="entry"> 影響 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Analytics は、同意前の状態での収集が可能ですが、その他すべてのライブラリは、同意が得られるまで読み込むことができません。 </p> </td> 
   <td colname="col2"> <p>オプトインを使用して、同意前の状態の Analytics カテゴリを有効にします。 </p> </td> 
   <td colname="col3"> <p>Analytics は、同意前の収集では ECID ではなく Analytics 識別子を使用します。ECID が承認されると、新しい識別子が使用され、訪問者は、アクティブ化や統合に使用できる ECID を受け取ります。 </p> <p>同意前／後の状態での訪問者のフラグメント化は期待されたとおりです。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>ファーストパーティによる測定は、同意前の状態で収集するのに適しています。その他すべての種類のデータは、同意が得られるまで使用できません。 </p> </td> 
   <td colname="col2"> <p>オプトインを使用して、同意前の状態の Analytics ライブラリおよび ECID ライブラリを有効にします。 </p> <p>ECID ライブラリに「disablethirdpartycookies」設定を追加し、同意前の状態のサードパーティ Cookie と ID 同期をブロックします。 </p> </td> 
   <td colname="col3"> <p>Adobe demdex の呼び出しは、ECID の取得に対してトリガーされますが、demdex Cookie、サードパーティ Cookie または ID 同期は存在しません。 </p> <p>訪問者を Analytics への同意前／同意後の状態で一貫して保持します。同意前の状態での収集は、同意後のデータ収集と関連付けられます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>ファーストパーティによる測定とターゲット設定は、同意前の状態で許容されます。その他すべての種類のデータは、同意が得られるまで使用できません。 </p> </td> 
   <td colname="col2"> <p>オプトインを使用して、同意前の状態の Analytics ライブラリ、ECID ライブラリおよび Target ライブラリを有効にします。 </p> <p>ECID ライブラリに <span class="codeph">isablethirdpartycookies</span> 設定を追加し、同意前の状態のサードパーティ Cookie と ID 同期をブロックします。同意前の状態のフラグを削除します。 </p> </td> 
   <td colname="col3"> <p>Adobe demdex の呼び出しは、ECID の取得に対してトリガーされますが、demdex Cookie、サードパーティ Cookie または ID 同期は存在しません。 </p> <p>訪問者をファーストパーティソリューションへの同意前／同意後の状態で一貫して保持します。同意前の状態での収集は、同意後のデータ収集と関連付けられます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Cookie は、同意前の状態で設定することが許可されていません。 </p> </td> 
   <td colname="col2"> <p>オプトインを使用して、同意が得られるまですべてのライブラリが読み込まれないようにします。 </p> </td> 
   <td colname="col3"> <p>実装は期待どおりにおこなわれ、すべてのライブラリ（ECID を含む）は、同意後の状態で正しい順序で読み込まれます。 </p> <p>同意していない顧客のデータ損失が追跡対象になります。 </p> </td> 
  </tr> 
 </tbody> 
</table>

