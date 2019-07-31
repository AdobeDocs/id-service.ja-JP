---
description: Experience Cloud IDサービス（ECID）は、SHA-256ハッシュアルゴリズムをサポートし、顧客IDまたは電子メールアドレスを渡すことができ、ハッシュIDを渡すことができます。これは、ハッシュ化された識別子をExperience Cloudに送信するためのオプションのJavascriptメソッドです。顧客IDを送信する前に、独自のハッシュのメソッドを引き続き使用できます。
keywords: ID サービス
seo-description: Experience Cloud IDサービス（ECID）は、SHA-256ハッシュアルゴリズムをサポートし、顧客IDまたは電子メールアドレスを渡すことができ、ハッシュIDを渡すことができます。これは、ハッシュ化された識別子をExperience Cloudに送信するためのオプションのJavascriptメソッドです。顧客IDを送信する前に、独自のハッシュのメソッドを引き続き使用できます。
seo-title: setCustomerIDsのSHA256ハッシュサポート
title: setCustomerIDsのSHA256ハッシュサポート
translation-type: tm+mt
source-git-commit: c670939cbeaebf4530df0e7d12e992ca5f0963bd

---


# SHA256 Hashing Support for `setCustomerIDs` {#hashing-support}

Experience Cloud IDサービス（ECID）は、SHA-256ハッシュアルゴリズムをサポートし、顧客IDまたは電子メールアドレスを渡すことができ、ハッシュIDを渡すことができます。これは、ハッシュ化された識別子をExperience Cloudに送信するためのオプションのJavascriptメソッドです。顧客IDを送信する前に、独自のハッシュのメソッドを引き続き使用できます。
以下の節で説明するように、setCustomerIDsを使用してハッシュサポートを実装するには、2つの方法があります。

* EIDのsetCustomerIDsメソッドを使用する
* Adobe Experience Platform Launchでのアクションの追加

## Use the `setCustomerIDs` method in ECID {#use-setcustomerids-method}

The first method leverages using the [`setCustomerIDs`](/help/library/get-set/setcustomerids.md) (`customerIDs<object>`, `hashType<string>`) method.

ハッシュの前に、ECIDライブラリはCustomerIDsでデータの正規化を実行します。このプロセスでは、両方のCustomerIDsのホワイトスペースがトリミングされ、すべての文字が小文字に変換されます。例えば、電子メールアドレスの場合:"ecid@adobe.com"は"ecid@adobe.com"になります。

SHA-256ハッシュを使用して、単一の顧客ID（前述の電子メールアドレス）を設定する方法のコード例を参照してください。

```
// Set single customerID with SHA-256 hashing
visitor.setCustomerIDs({email: {id: "ecid@adobe.com", authState: 1}}, "SHA-256");
```

Experience Cloud訪問者IDとともに、追加の顧客ID、認証ステータスおよびハッシュタイプ（SHA-256）を各訪問者に関連付けることができます。ハッシュタイプを指定しない場合、ハッシュなしと見なされます。

`setCustomerIDs` メソッドは、同じ訪問者に対する複数の顧客 ID を受け入れます。そのため、異なるデバイス間で個々のユーザーを識別したりターゲットにしたりすることができます。例えば、これらの ID を[顧客属性](https://docs.adobe.com/content/help/en/core-services/interface/customer-attributes/attributes.html)として Experience Cloud にアップロードして、異なるソリューションからこのデータにアクセスすることができます。

Customer IDs, authenticated states and hash type *are not* stored in a cookie to be used later. Instead, Customer IDs, authenticated states and hash type should be stored in an instance variable, to be retrieved using [`getCustomerIDs](/help/library/get-set/getcustomerids.md), as shown below:

```
> visitor.getCustomerIDs();
< {email: {…}}
    email: {id: "a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097", authState: 1, hashType: "SHA-256"}
    __proto__: Object
```

`setCustomerIDs` このメソッドを使用すると、ハッシュ `dpm.demdex.net`化された顧客IDを含む `d_cid_ic` クエリパラメーターが追加され、Experience Cloud IDサービスの呼び出しが実行されます。サンプルの呼び出しは以下のようになります。明確にするために改行が追加されました。

```
http://dpm.demdex.net/id?d_visid_ver=4.4.0&d_fieldgroup=AAM&d_rtbd=json&d_ver=2&
d_orgid=12A3F3F459CE0AD80A495CBE%40AdobeOrg&d_nsid=0&d_mid=12349850857640731290890207735189050123&
d_blob=6G1ynYcLPuiQxYZrsz_pkqfLG9yMXBpb2zX5dvJdYQJzPXImdj0y&
d_cid_ic=email%a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097%011&
ts=1563299964843
```

`d_cid_ic` パラメーターと認証状態の説明については、以下の表を参照してください。

| パラメーター | 説明 |
|------------|----------|
| `d_cid_ic` | 統合コード、個別ユーザーID（DPUUID）および認証済み状態IDをIDサービスに渡します。Separate the Integration Code and DPUUID with the non-printing control character, <code>%01</code>: <br> Example: <code>d_cid_ic=Integration_code%01DPUUID%01Authentication_state</code> <br> <b>認証状態</b> <br> d_ cid_ icパラメータ内のオプションのIDです。Expressed as an integer, it identifies users according to their authentication status as shown below: <br> <ul><li>0（不明または認証なし）</li><li>1（現在、このインスタンス/ページ/アプリケーションコンテキストで認証されています）</li><li>2（ログアウト済み）</li></ul> <br>例：<br> <ul><li>不明：...d_cid=123%01456%01<b>0</b></li><li>認証済み：...d_cid=123%01456%01<b>1</b></li><li>ログアウト済み：...d_cid=123%01456%01<b>2</b></li></ul> |

## Add an Action in Adobe Experience Platform Launch {#add-action-launch}

Experience Platform Launchは、アドビのタグ管理機能の次世代です。[起動製品ドキュメントの起動について](https://docs.adobe.com/content/help/en/launch/using/overview.html)詳しくは、を参照してください。

To add an action in Launch, read the [rules documentation](https://docs.adobe.com/help/en/launch/using/reference/manage-resources/rules.html) in Adobe Launch and see the screen capture below:

![](/help/reference/assets/hashing-support.png)

設定を確認すると、起動すると、次のようにデータがオブジェクトにラップされます。

```
{
    integration_code: {
        id: "value",
        authState: auth_state,
        hashType: "hash_algorithm"
    }
}
```

以下にコードサンプルを示します。

```
// Set single customer ID with hash type
setCustomerIDs(Ingeration code: {
    id: "string_value",
    authState: auth_state,
    hashType: "hash_algorithm"
});
```

Similarly to the `setCustomerIDs` method described in the first section, this results in a call to the Experience Cloud ID Service, with the addition of the `d_cid_ic` query parameter.