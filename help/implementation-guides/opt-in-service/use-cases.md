---
description: オプトインサービスを管理するためのユースケースと解決策のサンプルです。
title: オプトインの使用例
exl-id: 4c57685f-40b7-4af4-8527-3c2795586f0f
source-git-commit: e185c7d2b7582b52adbe9b525be7868ab8bfa374
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 91%

---

# オプトインの使用例 {#opt-in-use-cases}

オプトインサービスを管理するためのユースケースと解決策のサンプルです。

## ヒントとトラブルシューティング {#section-5c566366410f4a8f89eca0d3f556d99f}

* 訪問者 JS の初期化は同期的で、ページの読み込み中に実行されます。 待ち時間の長い CMP や権限の持続性を扱う場合は、[オプトイン設定](../../implementation-guides/opt-in-service/getting-started.md#section-cf9ab638780141c9b62dc57cf00b7047)で説明されている非同期関数を使用することをお勧めします。
* オプトインはドメインごとの実装です。 クロスドメイン実装は扱いません。
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
   <td colname="col1"> <p>Analytics は、同意前の状態で収集しても問題ありませんが、同意が得られるまで、他のすべてのライブラリは読み込めません </p> </td> 
   <td colname="col2"> <p>オプトインを使用して、Analytics カテゴリを事前同意状態で有効にします。 </p> </td> 
   <td colname="col3"> <p>Analytics では、事前同意の収集では ECID ではなく Analytics の識別子を使用します。 ECID が承認されると、新しい識別子が使用され、訪問者は、アクティベーションおよび統合に使用できる ECID を受け取るようになります。 </p> <p>事前／事後同意状態での訪問者のフラグメント化が必要です。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>ファーストパーティの測定では、事前同意状態で収集しても問題ありません。 その他のタイプのデータ使用は、同意が得られるまで行えません。 </p> </td> 
   <td colname="col2"> <p>オプトインを使用して、Analytics + ECID ライブラリを事前同意状態で有効にします。 </p> <p>同意前状態でサードパーティ Cookie と ID 同期をブロックするには、ECID ライブラリに「disablethirdpartycookies」設定を追加します </p> </td> 
   <td colname="col3"> <p>ECID を取得するための Adobe Demdex 呼び出しがトリガーされますが、Demdex Cookie、他のサードパーティ Cookie、または ID 同期は存在しません。 </p> <p>Analytics の事前／事後同意状態で、一貫した訪問者を維持します。 事前同意状態での収集は、事後同意データ収集に結び付けられます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>ファーストパーティの測定とターゲティングは、事前同意状態で受け入れられます。 その他のタイプのデータ使用は、同意が得られるまで行えません。 </p> </td> 
   <td colname="col2"> <p>オプトインを使用して、事前同意状態で Analytics + ECID + Target ライブラリを有効にします。 </p> <p>ECID ライブラリに <span class="codeph">isablethirdpartycookies</span> 設定を追加し、同意前の状態のサードパーティ Cookie と ID 同期をブロックします。事後同意状態のフラグを削除します。 </p> </td> 
   <td colname="col3"> <p>ECID を取得するための Adobe Demdex 呼び出しは トリガーされますが、Demdex Cookie、他のサードパーティ Cookie または ID 同期は存在しません。 </p> <p>ファーストパーティソリューションの事前／事後同意状態で、一貫した訪問者を維持します。 事前同意状態での収集は、事後同意データ収集に結び付けられます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>事前同意状態で Cookie を設定することはできません。 </p> </td> 
   <td colname="col2"> <p>オプトインを使用して、同意が得られるまですべてのライブラリの読み込みをブロックします。 </p> </td> 
   <td colname="col3"> <p>実装は想定どおりで、ECID を含むすべてのライブラリが事後同意状態で正しい順序で読み込まれます。 </p> <p>追跡に同意しない顧客のデータ損失。 </p> </td> 
  </tr> 
 </tbody> 
</table>

