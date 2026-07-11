---
description: 訪問者ID サービスは、IMS組織ID、CX エンタープライズ AMCV Cookie、およびdemdex Cookieを使用して、サイト訪問者の一意の永続的なIDを作成および保存します。 こうしたCookieにより、Visitor ID Serviceは様々なドメインをまたいで訪問者を追跡し、様々なCX Enterprise ソリューション間でのデータ共有を可能にします。
keywords: playstation；訪問者ID サービス
title: CookieとAdobe Visitor ID サービス
exl-id: 727c6381-56b9-44b8-8e59-355d072769be
TQID: https://experienceleague.adobe.com/iLOFGQ9t-DqYfqOZs3K5yZI7903dMPEjANaJ7lH8K0o
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 990
ht-degree: 42%

---

# CookieとAdobe Visitor ID サービス{#cookies-and-the-experience-cloud-id-service}

訪問者ID サービスは、IMS組織ID、CX エンタープライズ AMCV Cookie、およびdemdex Cookieを使用して、サイト訪問者の一意の永続的なIDを作成および保存します。 こうしたCookieにより、Visitor ID Serviceは様々なドメインをまたいで訪問者を追跡し、様々なCX Enterprise ソリューション間でのデータ共有を可能にします。

## 訪問者ID サービス Cookieについて {#section-f438168beaec409ab8b2cc58bd021e26}

訪問者ID サービスは、適切に機能するためにAMCV、AMCVS、およびdemdex Cookieに依存しています。 これらのCookieは、訪問者ID サービスで使用されるデータを保存するファイルです。 これらの訪問者ID サービス Cookieは、他のファーストパーティ Cookieとサードパーティ Cookieを管理する同じルールに従って、Web サイトまたはサービスがブラウザーに保存する他のファーストパーティ Cookieやサードパーティ Cookieとは危険でも悪意もなく、異なるものでもありません。 訪問者ID サービスで使用されるCookieについて詳しくは、以下の節を参照してください。

### 訪問者ID サービス Cookieの機能

* サイト訪問者に一意の ID（MID）を設定して保存する。
* 訪問者ID サービスが他のCX Enterprise ソリューションとデータを収集および共有できるように、この一意のIDを保持します。
* 複数のドメインをまたいでユーザーを追跡する。 ただし、そのためには、他のドメインを所有し、訪問者ID サービスコードがデプロイされている必要があります。

### 訪問者ID サービス Cookieで実行できないこと

* コンピューターウィルスを格納して転送し、実行する。
* 電子メールアドレスなどの個人を特定できる情報（PII）にアクセスしたり、そのような情報を保存したりする。
* コンピューターのハードウェアまたはソフトウェアを制御する。
* コンピューターを不安定にしたりパフォーマンスの問題を引き起こしたりする。
* 訪問者ID サービスを使用しないサイトのユーザーを追跡します。

## AMCV Cookie {#section-c55af54828dc4cce89f6118655d694c8}

訪問者ID サービスによって設定されたCookieの次の属性。

**名前**

AMCV Cookie 名は、`AMCV_<variable name>@AdobeOrg` という構文に従います。 名前では、`<variable name>`要素はIMS組織IDの一部のプレースホルダーです。 このIDは、訪問者ID サービスコードの`Visitor.getInstance`関数によってDCSに渡されます。

完全形式の Cookie 名は以下のようになります。

```
AMCV_1FD6776A524453CC0A490D44%40AdobeOrg
```

**内容**

AMCV Cookieには、ECIDまたはMIDが含まれています。 MID は、`MCMID|<ECID>` という構文に従うキーと値のペアとして保存されます。

完全形式のキーと値のペアは以下のようになります。

```
MCMID|20265673158980419722735089753036633573
```

この永続的な識別子によって、クロスソリューションのデータ共有が可能になります。

**ドメイン**

AMCV Cookie は、ブラウザーのファーストパーティドメインに設定されます。 つまり、ユーザーが現在訪問しているサイトのドメインに設定されます。 そのため、訪問者ID サービスコードおよびその他のCX エンタープライズコードライブラリは、AMCV Cookieに保存されているMIDを読み取ることができます。

ただし、AMCV Cookie はファーストパーティドメインに設定されているので、異なるドメインでユーザーを追跡して識別するために使用することはできません。 代わりに、訪問者ID サービスは、IMS組織IDとdemdex IDに依存して、サイト訪問者が別のドメインに移動したときに正しいMIDを返します。

## AMCVS Cookie {#section-92a9454f1ac645948f9059b9fad928bf}

**名前**

AMCVS Cookie 名は、`AMCVS_####@AdobeOrg` 構文に従います。 名前では、####要素は、IMS組織IDの一部のプレースホルダーです。 このIDは、訪問者ID サービスコードの`theVisitor.getInstance`関数によってDCSに渡されます。

完全形式の Cookie 名は以下のようになります。

```
AMCVS_1FD6776A524453CC0A490D44%40AdobeOrg
```

**内容**

AMCVS Cookie は、セッションが初期化されたことを示すフラグの役割を果たします。 その値は常に「`1`」となり、セッションが終了したときに中断されます。

**ドメイン**

AMCVS Cookie は、ブラウザーのファーストパーティドメインに設定されます。 つまり、ユーザーが現在訪問しているサイトのドメインに設定されます。

![](assets/AMCVS-cookie.png)

## Demdex Cookie {#section-7ff7d96d6e4141b08a84a75a63d7814c}

以下の表に、demdex Cookie の重要な属性の一覧とその定義を示します。

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
   <td colname="col2"> <p>Cookie 名は「demdex」です。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>内容</b> </p> </td> 
   <td colname="col2"> <p>demdex Cookie には DCS によって生成される demdex ID が含まれています。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>ドメイン</b> </p> </td> 
   <td colname="col2"> <p>demdex Cookie は、ブラウザーの demdex.net というサードパーティドメインに設定されます。 サードパーティドメインは、ユーザーが現在訪問しているサイトとは異なります。 </p> <p>ファーストパーティの AMCV Cookie とは異なり、demdex Cookie および demdex ID は異なるドメインをまたいで維持されます。 Demdex IDとIMS組織IDは、訪問者ID サービスが適切な訪問者IDを持つサイト訪問者を返して識別できるようにする一般的な値です。 </p> </td> 
  </tr> 
 </tbody> 
</table>

Demdex に関する開示について詳しくは、[Audience Manager デバイスのストレージの開示](https://aam-iab-tcf-vendor.s3.amazonaws.com/aam_device_storage_disclosures.json)にアクセスしてください。

関連情報については、[Demdex ドメインの呼び出しについて](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=ja)に関するドキュメントを参照してください。

## ECIDの生成 {#section-15f69c0bac394b4b9966a23fbc586d17}

ECIDは、IMS組織IDとdemdex IDから数学的に導き出されます。 これらの ID が変わらない限り、特定のユーザーに関する正しい MID を生成できるかどうかは、単純に計算上の問題になります。 同じIMS組織IDとdemdex IDを使用すると、毎回同じMID値を取得できます。 これにより、訪問者ID サービスは、ユーザーが制御し、訪問者ID サービスコードで設定したドメイン間で訪問者を追跡できます。

訪問者ID サービスは、ページの読み込み時にMIDの作成を開始します。 このプロセス中に、`VisitorAPI.js` コードライブラリによって提供されたコードは、イベント呼び出しでIMS組織IDを訪問者ID サービスに送信します。 訪問者ID サービスは、それぞれAMCVおよびdemdex CookieでMIDおよびdemdex IDを作成して返します。

## Cookie フラグ

次の表に、CX Enterprise Cookieのフラグを示します。

| cookie（設定元） | httpOnly | 安全 | SameSite |
|--- |--- |--- |--- |
| demdex（http 応答） | × | ○ | &quot;None&quot; |
| AMCV（JavaScript） | × | 設定可能 | Unset（既定は Lax） |
| AMCVS（JavaScript） | × | 設定可能 | Unset（既定は Lax） |

*注意：セキュア属性を使用した AMCV および AMCVS の Ccokie の設定について詳しくは、[secureCookie](../library/function-vars/securecookie.md) のトピックを参照してください。*

## 次の手順 {#section-8db1727a63bc4ff68b495f270315d453}

[訪問者ID サービスがIDを要求および設定する方法を参照してください…](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a)。

