---
description: 訪問者ID サービス（ECID）は、顧客IDまたはメールアドレスを渡したり、ハッシュ化されたIDを渡したりできるSHA-256 ハッシュアルゴリズムをサポートしています。 これは、ハッシュ化された識別子をCX Enterpriseに送信するためのオプションのJavascript メソッドです。 顧客 ID の送信前にハッシュする独自の方法を引き続き使用できます。
keywords: 訪問者 ID サービス
title: setCustomerIDs の SHA256 ハッシュサポート
exl-id: fd30634e-6435-4d14-8804-649c1ad3aaaa
TQID: https://experienceleague.adobe.com/-JBVon-Qf2jtfd5f4UdWcHVyO7c887p1w-k3GnntUCA
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 603
ht-degree: 55%

---

# `setCustomerIDs` の SHA256 ハッシュサポート {#hashing-support}

訪問者ID サービス（ECID）は、顧客IDまたはメールアドレスを渡したり、ハッシュ化されたIDを渡したりできるSHA-256 ハッシュアルゴリズムをサポートしています。 これは、ハッシュ化された識別子をCX Enterpriseに送信するためのオプションのJavascript メソッドです。 顧客 ID の送信前にハッシュする独自の方法を引き続き使用できます。setCustomerIDs を使用してハッシュサポートを実装するには、以下の節で説明するように、2 つの方法があります。

* [ECID での setCustomerIDs メソッドの使用](/help/reference/hashing-support.md#use-setcustomerids-method)
* [タグでのアクションの追加](/help/reference/hashing-support.md#add-action-launch)

## ECID での `setCustomerIDs` メソッドの使用 {#use-setcustomerids-method}

最初の方法では、[`setCustomerIDs`](/help/library/get-set/setcustomerids.md)（`customerIDs<object>`、`hashType<string>`）のメソッドを利用します。

ハッシュ化する前に、ECID ライブラリは、customerIDs のデータの正規化を実行します。 このプロセスでは、customerIDs の両端の空白をトリミングし、すべての文字を小文字に変換します。 例えば、電子メールアドレスの場合、「 ecid@adobe.com 」は「ecid@adobe.com」になります。

以下のコード例に、SHA-256 ハッシュで単一の顧客 ID（前述の電子メールアドレス）を設定する方法を示します。

```
// Set single customerID with SHA-256 hashing
visitor.setCustomerIDs({email: {id: "ecid@adobe.com", authState: 1}}, "SHA-256");
```

ECIDと共に、追加の顧客ID、認証ステータス、ハッシュタイプ（SHA-256）を各訪問者に関連付けることができます。 ハッシュタイプを指定していない場合、ハッシュ化しないと見なされます。

`setCustomerIDs` メソッドは、同じ訪問者に対する複数の顧客 ID を受け入れます。 そのため、異なるデバイス間で個々のユーザーを識別したりターゲットにしたりすることができます。 例えば、これらのIDを[顧客属性](https://experienceleague.adobe.com/docs/core-services/interface/customer-attributes/attributes.html?lang=ja)としてCX Enterpriseにアップロードし、様々なソリューションからこのデータにアクセスできます。

顧客 ID、認証状態およびハッシュタイプは、後で使用するために Cookie に格納されることは&#x200B;*ありません*。 代わりに、顧客 ID、認証状態およびハッシュタイプは、[`getCustomerIDs`](/help/library/get-set/getcustomerids.md) を使用して取得するために、以下に示すように、インスタンス変数に格納されます。

```
> visitor.getCustomerIDs();
< {email: {…}}
    email: {id: "a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097", authState: 1, hashType: "SHA-256"}
    __proto__: Object
```

<br> 

`setCustomerIDs` メソッドを使用すると、訪問者ID サービスへの呼び出しが`dpm.demdex.net`に行われ、ハッシュ化された顧客IDを含む`d_cid_ic` クエリパラメーターが追加されます。 呼び出しの例は、以下のようになります。 わかりやすくするために改行を追加してあります。

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
| `d_cid_ic` | 統合コード、一意のユーザーID （DPUUID）、および認証済み状態IDを訪問者ID サービスに渡します。 統合コードとDPUUIDを、印刷しない制御文字<code>%01で分離します</code>: <br>例：<code>d_cid_ic=Integration_code%01DPUUID%01Authentication_state</code> <br> <b>認証状態</b> <br> これは、d_cid_ic パラメーターのオプションの ID です。 整数で表され、以下に示す認証状態によってユーザーを識別します。<br> <ul><li>0（不明または認証なし）</li><li>1（現在、このインスタンス／ページ／アプリコンテキストに対して認証済み）</li><li>2（ログアウト済み）</li></ul> <br>例：<br> <ul><li>不明：...d_cid=123%01456%01<b>0</b></li><li>認証済み：...d_cid=123%01456%01<b>1</b></li><li>ログアウト済み：...d_cid=123%01456%01<b>2</b></li></ul> |

## タグでのアクションの追加 {#add-action-launch}

Adobe Experience Platform Data Collectionのタグは、Adobeの次世代型のタグ管理機能です。 詳しくは、[&#x200B; タグのドキュメント &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=ja)を参照してください。

タグにアクションを追加するには、[&#x200B; ルールドキュメント &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/tags/ui/rules.html?lang=ja)を参照し、次のスクリーンキャプチャを参照してください。

![](/help/reference/assets/hashing-support.png)

<br> 

設定を確認すると、タグはデータを次のようにオブジェクトにラップします。

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

最初のセクションで説明した`setCustomerIDs` メソッドと同様に、この結果は訪問者ID サービスへの呼び出しとなり、`d_cid_ic` クエリパラメーターが追加されます。

