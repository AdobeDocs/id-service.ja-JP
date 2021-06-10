---
description: Experience Cloud ID Service（ECID）は、顧客 ID または電子メールアドレスを渡し、ハッシュされた ID を受け取ることが可能な、SHA-256 ハッシュアルゴリズムをサポートします。これは、ハッシュされた識別子を Experience Cloud に送信するための、オプションの JavaScript メソッドです。顧客 ID の送信前にハッシュする独自の方法を引き続き使用できます。
keywords: ID サービス
title: setCustomerIDs の SHA256 ハッシュサポート
exl-id: fd30634e-6435-4d14-8804-649c1ad3aaaa
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '606'
ht-degree: 97%

---

# の SHA256 ハッシュサポート `setCustomerIDs` {#hashing-support}

Experience Cloud ID Service（ECID）は、顧客 ID または電子メールアドレスを渡し、ハッシュされた ID を受け取ることが可能な、SHA-256 ハッシュアルゴリズムをサポートします。これは、ハッシュされた識別子を Experience Cloud に送信するための、オプションの JavaScript メソッドです。顧客 ID の送信前にハッシュする独自の方法を引き続き使用できます。setCustomerIDs を使用してハッシュサポートを実装するには、以下の節で説明するように、2 つの方法があります。

* [ECID での setCustomerIDs メソッドの使用](/help/reference/hashing-support.md#use-setcustomerids-method)
* [Adobe Experience Platform Launch でのアクションの追加](/help/reference/hashing-support.md#add-action-launch)

## ECID での `setCustomerIDs` メソッドの使用 {#use-setcustomerids-method}

最初の方法では、[`setCustomerIDs`](/help/library/get-set/setcustomerids.md)（`customerIDs<object>`、`hashType<string>`）のメソッドを利用します。

ハッシュ化する前に、ECID ライブラリは、customerIDs のデータの正規化を実行します。このプロセスでは、customerIDs の両端の空白をトリミングし、すべての文字を小文字に変換します。例えば、電子メールアドレスの場合、「 ecid@adobe.com 」は「ecid@adobe.com」になります。

以下のコード例に、SHA-256 ハッシュで単一の顧客 ID（前述の電子メールアドレス）を設定する方法を示します。

```
// Set single customerID with SHA-256 hashing
visitor.setCustomerIDs({email: {id: "ecid@adobe.com", authState: 1}}, "SHA-256");
```

<br> 

通常の Experience Cloud 訪問者 ID に加えて、追加の顧客 ID、認証状態およびハッシュタイプ（SHA-256）を各訪問者に関連付けることができます。ハッシュタイプを指定していない場合、ハッシュ化しないと見なされます。

`setCustomerIDs` メソッドは、同じ訪問者に対する複数の顧客 ID を受け入れます。そのため、異なるデバイス間で個々のユーザーを識別したりターゲットにしたりすることができます。例えば、これらの ID を[顧客属性](https://experienceleague.adobe.com/docs/core-services/interface/customer-attributes/attributes.html?lang=ja)として Experience Cloud にアップロードして、様々なソリューションからこのデータにアクセスすることができます。

顧客 ID、認証状態およびハッシュタイプは、後で使用するために Cookie に格納されることはありません。**&#x200B;代わりに、顧客 ID、認証状態およびハッシュタイプは、[`getCustomerIDs`](/help/library/get-set/getcustomerids.md) を使用して取得するために、以下に示すように、インスタンス変数に格納されます。

```
> visitor.getCustomerIDs();
< {email: {…}}
    email: {id: "a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097", authState: 1, hashType: "SHA-256"}
    __proto__: Object
```

<br> 

`setCustomerIDs` メソッドを使用すると、Experience Cloud ID Service に対して `dpm.demdex.net` を、ハッシュされた 顧客 ID を含む `d_cid_ic` クエリパラメーターを追加して呼び出します。呼び出しの例は、以下のようになります。わかりやすくするために改行を追加してあります。

```
http://dpm.demdex.net/id?d_visid_ver=4.4.0&d_fieldgroup=AAM&d_rtbd=json&d_ver=2&
d_orgid=12A3F3F459CE0AD80A495CBE%40AdobeOrg&d_nsid=0&d_mid=12349850857640731290890207735189050123&
d_blob=6G1ynYcLPuiQxYZrsz_pkqfLG9yMXBpb2zX5dvJdYQJzPXImdj0y&
d_cid_ic=email%a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097%011&
ts=1563299964843
```

<br> 

以下の表に、`d_cid_ic` パラメーターおよび認証状態の説明を示します。

| パラメーター | 説明 |
|------------|----------|
| `d_cid_ic` | 統合コード、一意のユーザー ID（DPUUID）および認証状態 ID を ID サービスに渡します。統合コードおよび DPUUID を非表示の制御文字、%01</code> で区切ります。<br> 例：d_cid_ic=Integration_code%01DPUUID%01Authentication_state</code> <br> <b>認証状態</b> <br> これは、d_cid_ic パラメーターのオプションの ID です。整数で表され、以下に示す認証状態によってユーザーを識別します。<br> <ul><li>0（不明または認証なし）</li><li>1（現在、このインスタンス／ページ／アプリコンテキストに対して認証済み）</li><li>2（ログアウト済み）</li></ul> <br>例：<br> <ul><li>不明：...d_cid=123%01456%01<b>0</b></li><li>認証済み：...d_cid=123%01456%01<b>1</b></li><li>ログアウト済み：...d_cid=123%01456%01<b>2</b></li></ul> |

## Adobe Experience Platform Launch でのアクションの追加 {#add-action-launch}

Experience Platform Launch は、アドビが提供する次世代タグ管理機能です。platform launchについて詳しくは、[Launch製品ドキュメント](https://experienceleague.adobe.com/docs/launch/using/home.html?lang=en)を参照してください。

Launch にアクションを追加するには、Adobe Launch の[ルールドキュメント](https://docs.adobe.com/help/ja-JP/launch/using/reference/manage-resources/rules.html)を読み、以下のスクリーンキャプチャを参照してください。

![](/help/reference/assets/hashing-support.png)

<br> 

設定を確認したら、Launch は、以下のようにデータをオブジェクトにまとめます。

```
{
    integration_code: {
        id: "value",
        authState: auth_state,
        hashType: "hash_algorithm"
    }
}
```

以下にコード例を示します。

```
// Set single customer ID with hash type
setCustomerIDs(Ingeration code: {
    id: "string_value",
    authState: auth_state,
    hashType: "hash_algorithm"
});
```

最初の節で説明した `setCustomerIDs` メソッドと同様、これにより、Experience Cloud ID Service に対して`d_cid_ic` クエリパラメーターを追加して呼び出します。
