---
title: Google Chrome SameSite のラベル付けの変更
description: Adobe ECID（ID サービス）ライブラリのドキュメントです。
exl-id: f20b25a4-c9bc-41b9-8e49-79b8424e62a0
TQID: https://experienceleague.adobe.com/VlmpxMM0Jm4ExEL1WdjeA3h9brGBslGoJCqgQ-xFaRs
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 1125
ht-degree: 99%

---

# Google Chrome SameSite のラベル付けの変更 {#google-chrome-samesite-labelling-changes}

SameSite 属性は、ファーストパーティシナリオとサードパーティシナリオで cookie を起動するタイミングと方法をブラウザーに通知します。 SameSite 属性には、`strict`、`lax` または `none` の3つの値のいずれかを指定できます。 Chrome、Firefox、Edge、Safari、Opera は 2017 年 11 月 以降 `strict` および `lax` でサポートされ、`none` は 2018 年に導入されました。 ただし、古いブラウザーではこの設定がサポートされない場合があります。

2020 年 2 月、Google は Chrome 80 をリリースし、cookie で SameSite 属性値が指定されていない場合のデフォルト設定を `none` から `lax` に変更しました。 この設定は、「クロスサイト」とも呼ばれるサードパーティコンテキストで cookie が使用されるのを防ぎます。 その後のサードパーティ cookie は、`SameSite=none` に設定し、セキュアとしてラベル付けする必要があります。

SameSite 属性値が指定されていない cookie は、デフォルトで `lax` に設定され ます。

SameSite 属性の詳細については、[Cookie 標準ドキュメント](https://tools.ietf.org/html/draft-ietf-httpbis-rfc6265bis-03#section-4.1)を参照してください。

## SameSite 属性値

| SameSite 属性値 | 説明 |
| ------ | ------------ |
| `strict` | この設定を持つ Cookie は、参照元ページとランディングページの両方が Cookie と同じドメインに属している場合にのみ送信されます。 |
| `lax` | この設定を持つ Cookie は、ブラウザーの URL に表示されるドメインが Cookie のドメインと一致する場合にのみ送信されます。 これは、Chrome の Cookie の新しいデフォルトです。 |
| `none` | この設定の Cookie は、「クロスサイト」などの外部アクセスまたはサードパーティアクセスに使用できます。 この変更がおこなわれるより前、`none` は cookie に対するデフォルトの SameSite 設定でした。そのため、この設定を使用すると、cookie の動作が従来の動作と最も似た動作になります。 ただし、Google では現在、この設定を持つ cookie に secure フラグを指定する必要があります。つまり、cookie は常に HTTPS 経由リクエストで作成および送信されます。 secure フラグの付いていないクロスサイト cookie はすべて Google によって拒否されます。 |

## Adobe Experience Cloud の顧客が知っておくべき情報

**JavaScript の更新は不要**

アドビ製品は、サードパーティ cookie に適切な属性を設定するため、サーバーサイドのアップデートをリリースしました。 顧客側で JavaScript ライブラリを更新する必要ありません。

**サードパーティのエンドポイントで HTTPS が使用されていることを確認する**

すべての顧客は、JavaScript 設定でアドビのサービスへの呼び出しに HTTPS が使用されていることを確認する必要があります。 Target、Audience Manager および Experience Cloud ID サービス（ECID）は、サードパーティの HTTP 呼び出しをそれぞれの HTTPS エンドポイントにリダイレクトしているので、待機時間が長くなる可能性があります。 つまり、設定を変更する必要はありません。 Analytics の顧客は、HTTPS のみを使用するように実装を更新する必要があります。これは、Analytics に固有のリダイレクトによってデータが失われる可能性があるためです。

**正しくラベル付けされた cookie は、意図したとおりにデータを収集する**

Cookie に正しいラベルが付けられている限り、ブラウザーは cookie をブロックするアクションを実行しません。 コンシューマーには特定の種類の cookie をブロックするオプションがありますが、現在のところ、これはオプトイン設定のみのようです。

**ラベルが更新されていない既存のサードパーティ cookie は無視されます**

Chrome 80 で SameSite=`none` と secure フラグ設定の適用が開始される前に作成されたサードパーティ cookie は、これらのフラグが存在しない場合、Chrome 80 では無視されます。

既存の Adobe サードパーティ cookie には、これらのフラグがないものが多く、ユーザーが Chrome 80 にアップグレードする前に Edge サーバーで更新する必要があります。そうしないと、それらの cookie は失われます。 Cookie を使用している Web サイトにユーザーがアクセスすると、Edge サーバーは自動的に更新されます。

ほとんどのアドビ製品では、適切なフラグが cookie に割り当てられています。 ただし、サードパーティのデータ収集を使用し、ECID を使用しない Analytics 実装は例外です。 本来は再訪問者とするべき訪問者が新規訪問者としてカウントされ、新規訪問者数が一時的に増加する場合があります。

**宛先と Marketplace のパートナーに対して、cookie の一致が減少する可能性がある（Audience Manager のみ）**

アドビは Cookie の更新を制御できますが、パートナーに必要な変更を強制することはできません。 宛先パートナーや Marketplace パートナーを使用している Audience Manager の顧客が、まだこれらの更新を行っていない場合、cookie の一致が減少する可能性があります。

**Analytics 対応のサードパーティ cookie（Analytics `s_vi` cookies のみ）**

一部の Analytics 実装では、Analytics CNAME エイリアスを使用して、その CNAME のドメインで `s_vi` cookie を作成できるようにします。 CNAME が Web サイトと同じドメインにある場合、これはファーストパーティ cookie として指定されます。 ただし、複数のドメインを所有し、すべてのドメインで同じ CNAME をデータ収集に使用する場合、他のドメインではサードパーティ cookie として指定されます。

`lax` が Chrome の新しいデフォルトの SameSite 設定になると、CNAME は他のドメインでは表示されなくなります。

この変更に対応するため、Analytics では明示的に、`s_vi` cookie の SameSite 値を `lax` に設定するようになりました。 この cookie をわかりやすいサードパーティのコンテキストで使用するには、SameSite 値を `none` に設定します。つまり、常に HTTPS を使用する必要があります。 セキュアな CNAME に対して SameSite の値を変更する場合は、カスタマーケアにお問い合わせくだください。

>[!IMPORTANT]
>
>ECID を使用する Analytics のお客様、ドメインごとに個別の CNAME を使用するお客様、またはサードパーティの Analytics データ収集のみを使用するお客様は、このアクションを実行する必要はありません。

## アドビ標準訪問者 Cookie

次の表には、一般的な標準訪問者 cookie のみを示します。 Cookie のその他の設定については、製品固有のドキュメントを参照するか、アドビ担当者にお問い合わせください。

### ECID

| Cookie | タイプ | SameSite 属性 | セキュア属性 |
| ------ | ---- | ------------------ | ---------------- |
| AMCV_###@AdobeOrg | クライアントサイドのファーストパーティ | 値は追加されません。*Chrome のデフォルトは `lax` 設定になります。 | 設定可能 |
| AMCVS_###@AdobeOrg | クライアントサイドのファーストパーティ | 値は追加されません。*Chrome のデフォルトは `lax` 設定になります。 | 設定可能 |
| s_ecid | サーバーサイドのファーストパーティ | SameSite==`lax` | 設定なし |

### Audience Manager

| Cookie | タイプ | SameSite 属性 | セキュア属性 |
| ------ | ---- | ------------------ | ---------------- |
| Demdex | サードパーティ | `none` | セキュアに設定 |
| Dextp | サードパーティ | `none` | セキュアに設定 |

### Analytics

| Cookie | タイプ | SameSite 属性 | セキュア属性 |
| ------ | ---- | ------------------ | ---------------- |
| s_vi | <ul><li> `CNAME` を使用している場合はサーバーサイドのファーストパーティ </li> <li>2o7.net または omtrdc.net を使用している場合はサードパーティ</li></ul> | <ul><li>`lax`（ファーストパーティの場合）</li> <li>`none`（サードパーティの場合）</li></ul> *顧客は、カスタマーケアチケットを介して、ファーストパーティドメインの設定を編集できます* | 設定（`none` および HTTPS リクエストを使用する場合） |
| s_fid | クライアントサイドのファーストパーティ | 値は追加されません。*Chrome のデフォルトは `lax` 設定になります。 | 設定なし |

### ターゲット

| Cookie | タイプ | SameSite 属性 | セキュア属性 |
| ------ | ---- | ------------------ | ---------------- |
| mbox | ファーストパーティ | 値は追加されません。*Chrome のデフォルトは `lax` 設定になります。 | 設定なし |

### Ad Cloud

| Cookie | タイプ | SameSite 属性 | セキュア属性 |
| ------ | ---- | ------------------ | ---------------- |
| everest_g_v2 | サードパーティ | `none` *Google Chrome および Chromium ベースのブラウザーのみ* | 設定（`none` および HTTPS リクエストを使用する場合） |
| data_adcloud | ファーストパーティ | 値は追加されません。*Chrome のデフォルトは `lax` 設定になります。 | 設定なし |
| ev_tm | サードパーティ | `none` *Google Chrome および Chromium ベースのブラウザーのみ* | 設定（`none` および HTTPS リクエストを使用する場合） |

### Bizible

| Cookie | タイプ | SameSite 属性 | セキュア属性 |
| ------ | ---- | ------------------ | ---------------- |
| _buid | サードパーティ | `none` | 安全 |

### Marketo Munchkin

| Cookie | タイプ | SameSite 属性 | セキュア属性 |
| ------ | ---- | ------------------ | ---------------- |
| _mkto_trk | クライアントサイドのファーストパーティ | 値は追加されません。*Chrome のデフォルトは `lax` 設定になります。 | 外部ページ用に設定可能 |

>[!IMPORTANT]
>
>Adobeのサードパーティ Cookieは、サーバーサイドで設定されます。

詳しくは、[Target の Google Chrome SameSite ポリシー](https://experienceleague.adobe.com/docs/target-dev/developer/implementation/privacy/google-chrome-samesite-cookie-policies.html?lang=ja)のドキュメントを参照してください。

