---
title: Google Chrome SameSiteのラベル付けの変更
seo-title: Google Chrome SameSiteのラベル付けの変更
description: Adobe ECID（ID サービス）ライブラリのドキュメントです。
seo-description: Adobe ECID（ID サービス）ライブラリのドキュメントです。
translation-type: tm+mt
source-git-commit: 592ca6ca6a72e57b728e286d0b730c5bd93c0c7b
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 3%

---


# Google Chrome SameSiteのラベル付けの変更 {#google-chrome-samesite-labelling-changes}

SameSite属性は、ファーストパーティシナリオとサードパーティシナリオでcookieを起動するタイミングと方法をブラウザーに通知します。 SameSite属性には、次の3つの値のいずれかを指定できます。 `strict`、 `lax`または `none`。 Chrome、Firefox、Edge、Safari、Operaは2017年11月 `strict` 以降、2018年 `lax` で `none` 導入されています。 ただし、古いブラウザーではこの設定がサポートされない場合があります。

2020年2月、GoogleはChrome 80をリリースし、cookieに指定されたSameSite属性値がない場合のデフォルト設定 `none``lax` をからに変更しました。 この設定は、「クロスサイト」とも呼ばれるサードパーティコンテキストでcookieが使用されるのを防ぎます。 その後のサードパーティCookieは、に設定され、セキュリティで保護されているとラベル付けさ `SameSite=none` れる必要があります。

SameSite属性値が指定されていないCookieは、デフォルトでに設定され `lax`ます。

SameSite属性の詳細については、 [cookie標準ドキュメント](https://tools.ietf.org/html/draft-ietf-httpbis-rfc6265bis-03#section-4.1) （英語）を参照してください。

## SameSite属性値

| SameSite属性値 | 説明 |
| ------ | ------------ |
| `strict` | この設定を持つCookieは、参照ページとランディングページの両方がCookieと同じドメインに属している場合にのみ送信されます。 |
| `lax` | この設定を持つCookieは、ブラウザーのURLに表示されるドメインがCookieのドメインと一致する場合にのみ送信されます。 これは、ChromeのCookieの新しいデフォルトです。 |
| `none` | この設定を持つCookieは、「クロスサイト」など、外部またはサードパーティからのアクセスに使用できます。 この変更より前 `none` は、がcookieのデフォルトのSameSite設定だったので、この設定を使用すると、cookieの動作が従来の動作と最も似た動作になります。 ただし、Googleでは、この設定を持つCookieにsecureフラグを指定する必要があります。つまり、CookieはHTTPS経由のリクエストと共にのみ作成され、送信されます。 保護フラグを指定しないクロスサイトCookieはすべてGoogleによって拒否されます。 |

## Adobe Experience Cloudのお客様に必要な情報

**JavaScriptの更新は不要**

Adobe製品では、適切な属性を持つサードパーティcookieを設定するためのサーバー側の更新が既にリリースされています。 お客様はJavaScriptライブラリの更新は必要ありません。

**サードパーティのエンドポイントでHTTPSが使用されていることを確認する**

すべてのお客様は、JavaScriptの設定で、Adobeサービスの呼び出しにHTTPSが使用されていることを確認する必要があります。 ターゲット、Audience ManagerおよびExperience CloudIDサービス(ECID)は、サードパーティのHTTP呼び出しをそれぞれのHTTPSエンドポイントにリダイレクトしているので、待ち時間が長くなる可能性があります。 つまり、設定を変更する必要はありません。 Analyticsのお客様は、HTTPSのみを使用するように実装を更新する必要があります。これは、Analyticsに固有のリダイレクトによってデータが失われる可能性があるためです。

**正しくラベル付けされたcookieは、意図したとおりにデータを収集する必要があります**

cookieに正しいラベルが付いている限り、ブラウザーはcookieをブロックするためのアクションを実行しません。 ユーザーには、特定の種類のCookieをブロックするオプションがありますが、現在のところ、これはオプトイン設定のみであると見なされます。

**ラベルが更新されていない既存のサードパーティCookieは無視されます**

Chrome 80でSameSite=の適用が開始される前に作成されたサードパーティCookie`none` 、およびこれらのフラグが存在しない場合は、Chrome 80ではセキュアフラグ設定が無視されます。

既存のAdobeのサードパーティCookieには、これらのフラグがないものが多く、Chrome 80にアップグレードする前にEdgeサーバーが更新する必要があります。そうしないと、それらのCookieが失われます。 Edgeサーバーは、cookieが使用されているWebサイトにユーザーがアクセスすると自動的に更新されます。

ほとんどのAdobe製品には、cookieに適切なフラグが割り当てられています。 ただし、サードパーティのデータ収集を使用し、ECIDを使用しないAnalyticsの導入は例外です。 顧客は、新規訪問者が少し増えた場合に、それがなければ再訪問者になったと思われる新規訪問者数が一時的に増加する可能性があります。

**宛先とマーケットプレイスのパートナーに対して、cookieの一致が減少する可能性がある(Audience Managerのみ)**

AdobeはCookieの更新を制御できますが、Adobeはパートナーに必要な変更を強制できません。 対象パートナーやマーケットプレイスパートナーを使用しているAudience Managerのお客様が、まだこれらの更新を行っていない場合、cookieの一致が減少する可能性があります。

**Analytics対応のサードパーティCookie(Analytics`s_vi`cookieのみ)**

一部のAnalyticsの導入では、Analytics CNAMEエイリアスを使用して、そのCNAMEのドメインで `s_vi` cookieを作成できるようにします。 CNAMEがWebサイトと同じドメインにある場合、これはファーストパーティCookieとして指定されます。 ただし、複数のドメインを所有し、すべてのドメインで同じCNAMEをデータ収集に使用する場合は、それらの他のドメインではサードパーティCookieとして指定されます。

Chromeの新しいデフォルトのSameSite設定 `lax` になった場合、CNAMEは他のドメインでは表示されなくなります。

この変更に対応するために、Analyticsでは、 `s_vi` cookieのSameSite値をに明示的に設定するようにな `lax`りました。 このCookieをわかりやすいサードパーティのコンテキストで使用するには、SameSite値をに設定します。つまり、常にHTTPSを使用する必要があ `none`ります。 セキュアなCNAMEのSameSite値を変更する場合は、カスタマーケアにお問い合わせください。

>[!IMPORTANT]
>
>ECIDを使用するAnalyticsのお客様、ドメインごとに個別のCNAMEを使用するお客様、またはサードパーティのAnalyticsデータ収集のみを使用するお客様には、このアクションは必要ありません。

## Adobe標準訪問者Cookie

次の表に、一般的な訪問者標準cookieのみを示します。 Cookieのその他の設定については、製品固有のドキュメントを参照するか、Adobeの担当者にお問い合わせください。

### ECID

| cookie | タイプ | SameSite属性 | セキュア属性 |
| ------ | ---- | ------------------ | ---------------- |
| AMCV_###@AdobeOrg | クライアントサイドのファーストパーティ | 値が追加されない*Chromeのデフォルトは `lax` 、 | 設定可能 |
| AMCVS_###@AdobeOrg | クライアントサイドのファーストパーティ | 値が追加されない*Chromeのデフォルトは `lax` 、 | 設定可能 |
| s_ecid | サーバーサイドのファーストパーティ | SameSite==`lax` | 未設定 |

### Audience Manager

| cookie | タイプ | SameSite属性 | セキュア属性 |
| ------ | ---- | ------------------ | ---------------- |
| Demdex | サードパーティ | `none` | セキュアに設定 |
| Dextp | サードパーティ | `none` | セキュアに設定 |

### Analytics

| cookie | タイプ | SameSite属性 | セキュア属性 |
| ------ | ---- | ------------------ | ---------------- |
| s_vi | <ul><li> サーバーサイドのファーストパーティ( `CNAME` </li> <li>2o7.netまたはomtrdc.netを使用している場合はサードパーティ</li></ul> | <ul><li>`lax` ファーストパーティの場合</li> <li>`none` 第三者が</li></ul> *顧客は、カスタマーケアチケットを介して、ファーストパーティドメインの設定を編集できます。* | HTTPSリクエストを使用する場合 `none` に設定 |
| s_fid | クライアントサイドのファーストパーティ | 値が追加されません。*Chromeのデフォルトは `lax` 、 | 未設定 |

### Target

| cookie | タイプ | SameSite属性 | セキュア属性 |
| ------ | ---- | ------------------ | ---------------- |
| mbox | ファーストパーティ | 値が追加されない*Chromeのデフォルトは `lax` 、 | 未設定 |

### Ad Cloud

| cookie | タイプ | SameSite属性 | セキュア属性 |
| ------ | ---- | ------------------ | ---------------- |
| everest_g_v2 | サードパーティ | `none` *Google ChromeおよびChromiumベースのブラウザーのみ* | HTTPSリクエストを使用する場合 `none` に設定 |
| data_adcloud | ファーストパーティ | 値が追加されない*Chromeのデフォルトは `lax` 、 | 未設定 |
| ev_tm | サードパーティ | `none` *Google ChromeおよびChromiumベースのブラウザーのみ* | HTTPSリクエストを使用する場合 `none` に設定 |

### Bizible

| cookie | タイプ | SameSite属性 | セキュア属性 |
| ------ | ---- | ------------------ | ---------------- |
| _buid | サードパーティ | `none` | Secure |

### Marketo Munchkin

| cookie | タイプ | SameSite属性 | セキュア属性 |
| ------ | ---- | ------------------ | ---------------- |
| _mkto_trk | クライアントサイドのファーストパーティ | 値が追加されない*Chromeのデフォルトは `lax` 、 | 外部ページ用に設定可能 |

> !![IMPORTANT] AdobeのサードパーティCookieがサーバーサイドで設定されている

詳しくは、 [ターゲットのGoogle Chrome SameSiteポリシーのドキュメントを参照してください](https://docs.adobe.com/content/help/en/target/using/implement-target/before-implement/privacy/google-chrome-samesite-cookie-policies.html)。