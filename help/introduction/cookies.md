---
description: IDサービスは、組織ID、Experience Cloud AMCV cookieおよびdemdex cookieを使用して、サイト訪問者の一意の永続的な識別子を作成し、保存します。 これらの Cookie により、ID サービスでは異なるドメインをまたいで訪問者を追跡できるようになり、異なる Experience Cloud ソリューション間でデータの共有が可能になります。
keywords: playstation;ID Service
seo-description: IDサービスは、組織ID、Experience Cloud AMCV cookieおよびdemdex cookieを使用して、サイト訪問者の一意の永続的な識別子を作成し、保存します。 これらの Cookie により、ID サービスでは異なるドメインをまたいで訪問者を追跡できるようになり、異なる Experience Cloud ソリューション間でデータの共有が可能になります。
seo-title: Cookie と Experience Cloud Identity Service
title: Cookie と Experience Cloud Identity Service
uuid: c5cbd235-37ee-4605-8792-b1a991e190ad
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# Cookie と Experience Cloud Identity Service {#cookies-and-the-experience-cloud-id-service}

IDサービスは、組織ID、Experience Cloud AMCV cookieおよびdemdex cookieを使用して、サイト訪問者の一意の永続的な識別子を作成し、保存します。 これらの Cookie により、ID サービスでは異なるドメインをまたいで訪問者を追跡できるようになり、異なる Experience Cloud ソリューション間でデータの共有が可能になります。

## ID サービス Cookie について {#section-f438168beaec409ab8b2cc58bd021e26}

IDサービスは、AMCV、AMCVS、demdexの各cookieを利用して正しく機能します。 これらのcookieは、IDサービスが使用するデータを保存するファイルにすぎません。 これらのIDサービスのcookieは、他のファーストパーティcookieやサードパーティcookieを制御するのと同じ規則に従って、Webサイトやブラウザー内のサービスに保存される、他のファーストパーティcookieやサードパーティcookieとは危険でも悪意のあるものでもありません。 ID サービスで使用される Cookie について詳しくは、次の各セクションを参照してください。

### ID サービス Cookie で実行できること

* サイト訪問者(MID)の一意のIDを設定し、保存します。
* この一意のIDを保持して、IDサービスが他のExperience Cloudソリューションとデータを収集および共有できるようにします。
* ドメイン間でのユーザーの追跡。 ただし、そのためには、同じ組織が他のドメインも所有している必要があり、それらのドメインに ID サービスコードがデプロイされている必要があります。

### ID サービス Cookie で実行できないこと

* コンピューターウイルスの保存、送信、または実行。
* 電子メールアドレスなど、個人の特定できる情報(PII)にアクセスしたり、保存したりします。
* コンピュータハードウェアまたはソフトウェアを制御します。
* コンピューターを不安定にするか、パフォーマンスの問題を引き起こします。
* IDサービスを使用しないサイトのユーザーを追跡します。

## AMCV Cookie {#section-c55af54828dc4cce89f6118655d694c8}

ID サービスによって設定される Cookie の属性は次のとおりです。

**名前**

AMCV Cookie 名は、`AMCV_<variable name>@AdobeOrg` という構文に従います。この名前の「`<variable name>`」の部分は、Experience Cloud 組織 ID の一部を示すプレースホルダーです。ID サービスコードの `Visitor.getInstance` 関数によって、この ID が DCS に渡されます。

完全形式の Cookie 名は以下のようになります。

```
AMCV_1FD6776A524453CC0A490D44%40AdobeOrg
```

**内容**

AMCV cookieには、Experience Cloud訪問者ID(MID)が含まれます。 MID は、`mid|<Experience Cloud ID>` という構文に従うキーと値のペアとして保存されます。

完全形式のキーと値のペアは以下のようになります。

```
mid|20265673158980419722735089753036633573
```

この永続的な識別子により、クロスソリューションのデータ共有が可能になります。

**ドメイン**

AMCV cookieは、ブラウザーのファーストパーティドメインに設定されます。 つまり、ユーザーが現在訪問しているサイトのドメインに設定されます。 したがって、IDサービスコードおよびその他のExperience Cloudコードライブラリは、AMCV cookieに保存されているMIDを読み取ることができます。

ただし、AMCV cookieはファーストパーティドメインに設定されているので、異なるドメインでユーザーを追跡および識別するために使用することはできません。 代わりに、IDサービスは組織IDとdemdex IDに依存して、サイト訪問者が別のドメインに移動したときに正しいMIDを返します。

## AMCVS Cookie {#section-92a9454f1ac645948f9059b9fad928bf}

**名前**

AMCVS Cookie 名は、`AMCVS_####@AdobeOrg` 構文に従います。この名前の「####」の部分は、Experience Cloud 組織 ID の一部を示すプレースホルダーです。ID サービスコードの `theVisitor.getInstance` 関数によって、この ID が DCS に渡されます。

完全形式の Cookie 名は以下のようになります。

```
AMCVS_1FD6776A524453CC0A490D44%40AdobeOrg
```

**内容**

AMCVS cookieは、セッションが初期化されたことを示すフラグとして機能します。 その値は常に「`1`」となり、セッションが終了したときに中断されます。

**ドメイン**

AMCVS cookieは、ブラウザーのファーストパーティドメインに設定されます。 つまり、ユーザーが現在訪問しているサイトのドメインに設定されます。

![](assets/AMCVS-cookie.png)

## demdex Cookie {#section-7ff7d96d6e4141b08a84a75a63d7814c}

次の表に、demdex cookieの重要な属性のリストと定義を示します。

<table id="table_18E3CAF3550E4BB6A199736AACE39202"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 属性 </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>名前</b> </p> </td> 
   <td colname="col2"> <p>cookie名は「demdex」です。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>内容</b> </p> </td> 
   <td colname="col2"> <p>demdex cookieにはDCSによって生成されるdemdex IDが含まれます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>ドメイン</b> </p> </td> 
   <td colname="col2"> <p>demdex cookieは、ブラウザーのdemdex.netというサードパーティドメインに設定されます。 このドメインは、ユーザーが現在訪問しているサイトとは別のドメインです。 </p> <p>ファーストパーティのAMCV cookieとは異なり、demdex cookieとdemdex IDは異なるドメインで保持されます。 demdex IDと組織IDは、IDサービスが正しい訪問者IDを持つサイト訪問者を返し、識別できる共通の値です。 </p> </td> 
  </tr> 
 </tbody> 
</table>

関連情報については「[Demdex ドメインの呼び出しについて](https://docs.adobe.com/content/help/ja-JP/audience-manager/user-guide/reference/demdex-calls.html)」を参照してください。

## Experience Cloud ID の生成 {#section-15f69c0bac394b4b9966a23fbc586d17}

Experience Cloud ID（MID）は、組織 ID と demdex ID から計算によって生成されます。これらのIDが一定である限り、特定のユーザーに対して適切なMIDを生成することは、単純に計算上の問題です。 同じ組織IDとdemdex IDを持つユーザーは、毎回同じMID値を取得します。 これにより、IDサービスは、管理対象のドメイン間で、IDサービスコードを使用して設定した訪問者を追跡できます。

ページの読み込み時にMIDを作成するIDサービス開始。 このプロセスでは、`visitorAPI.js` コードライブラリに含まれるコードによって ID サービスへのイベント呼び出しが発行され、その呼び出しを通じて組織 ID が送信されます。ID サービスは MID と demdex ID を作成して、前者を AMCV Cookie に、後者を demdex Cookie にそれぞれ返します。

## Cookie フラグ

Experience Cloud Cookie のフラグを次の表に示します。

| Cookie（設定者） | httpOnly | セキュア | SameSite |
|--- |--- |--- |--- |
| demdex（http 応答） | × | ○ | &quot;None&quot; |
| AMCV（JavaScript） | × | 設定可能 | Unset（既定は Lax） |
| AMCVS（JavaScript） | × | 設定可能 | Unset（既定は Lax） |

*注意：セキュア属性を使用した AMCV および AMCVS の　Ccokie の設定について詳しくは、[secureCookie](https://docs.adobe.com/content/help/ja-JP/id-service/using/id-service-api/configurations/securecookie.html) のトピックを参照してください。*

## 次の手順 {#section-8db1727a63bc4ff68b495f270315d453}

[Experience Cloud Identity Service による ID のリクエスト方法と設定方法](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a)を参照してください。
