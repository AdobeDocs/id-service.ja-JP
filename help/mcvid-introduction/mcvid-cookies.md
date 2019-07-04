---
description: ID サービスは組織 ID、Experience Cloud AMCV Cookie および demdex Cookie を使用して、サイト訪問者固有の永続的な識別子を作成して保存します。これらの Cookie により、ID サービスでは異なるドメインをまたいで訪問者を追跡できるようになり、異なる Experience Cloud ソリューション間でデータの共有が可能になります。
keywords: playstation;ID サービス
seo-description: ID サービスは組織 ID、Experience Cloud AMCV Cookie および demdex Cookie を使用して、サイト訪問者固有の永続的な識別子を作成して保存します。これらの Cookie により、ID サービスでは異なるドメインをまたいで訪問者を追跡できるようになり、異なる Experience Cloud ソリューション間でデータの共有が可能になります。
seo-title: Cookie と Experience Cloud ID サービス
title: Cookie と Experience Cloud ID サービス
uuid: c5cbd235-37ee-4605-8792-b1a991e190ad
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Cookie と Experience Cloud ID サービス{#cookies-and-the-experience-cloud-id-service}

ID サービスは組織 ID、Experience Cloud AMCV Cookie および demdex Cookie を使用して、サイト訪問者固有の永続的な識別子を作成して保存します。これらの Cookie により、ID サービスでは異なるドメインをまたいで訪問者を追跡できるようになり、異なる Experience Cloud ソリューション間でデータの共有が可能になります。

## ID サービス Cookie について {#section-f438168beaec409ab8b2cc58bd021e26}

ID サービスは、正常に機能するために AMCV Cookie、AMCVS Cookie および demdex Cookie を使用します。これらの Cookie は ID サービスで使用されるデータが格納されるファイルです。このような ID サービス Cookie は、他のファーストパーティ Cookie やサードパーティ Cookie を制御する場合と同様のルールに従っており、危険なものでも悪意があるものでもなく、ブラウザーの Web サイトやサービスで保存される他のファーストパーティ Cookie やサードパーティ Cookie と変わりません。ID サービスで使用される Cookie について詳しくは、次の各セクションを参照してください。

**ID サービス Cookie で実行できること**

* サイト訪問者に一意の ID（MID）を設定して保存する。
* ID サービスがデータを収集して他の Experience Cloud ソリューションと共有できるように、この一意の ID を維持する。
* 複数のドメインをまたいでユーザーを追跡する。ただし、そのためには、同じ組織が他のドメインも所有している必要があり、それらのドメインに ID サービスコードが導入されている必要があります。

** ID サービス Cookie で実行できないこと**

* コンピューターウィルスを格納して転送し、実行する。
* 電子メールアドレスなどの個人を特定できる情報（PII）にアクセスしたり、そのような情報を保存したりする。
* コンピューターのハードウェアまたはソフトウェアを制御する。
* コンピューターを不安定にしたりパフォーマンスの問題を引き起こしたりする。
* ID サービスを使用していないサイトでユーザーを追跡する。

## AMCV Cookie{#section-c55af54828dc4cce89f6118655d694c8}

ID サービスによって設定される Cookie の属性は次のとおりです。

**名前**

AMCV Cookie 名は、`AMCV_<variable name>@AdobeOrg` という構文に従います。この名前の「`<variable name>`」の部分は、Experience Cloud 組織 ID の一部を示すプレースホルダーです。ID サービスコードの `Visitor.getInstance` 関数によって、この ID が DCS に渡されます。

完全形式の Cookie 名は以下のようになります。

```
AMCV_1FD6776A524453CC0A490D44%40AdobeOrg
```

**内容**

AMCV Cookie には Experience Cloud 訪問者 ID（MID）が含まれます。MID は、`mid|<Experience Cloud ID>` という構文に従うキーと値のペアとして保存されます。

完全形式のキーと値のペアは以下のようになります。

```
mid|20265673158980419722735089753036633573
```

この永続的な識別子によって、クロスソリューションのデータ共有が可能になります。

**ドメイン**

AMCV Cookie は、ブラウザーのファーストパーティドメインに設定されます。つまり、ユーザーが現在訪問しているサイトのドメインに設定されます。その結果、ID サービスコードおよびその他の Experience Cloud コードライブラリが、AMCV Cookie に保存されている MID を読み取ることができます。

ただし、AMCV Cookie はファーストパーティドメインに設定されているので、異なるドメインでユーザーを追跡して識別するために使用することはできません。その代わりに、ID サービスは組織 ID と demdex ID を利用して、サイトの訪問者が別のドメインに移動したときに正しい MID を返します。

## AMCVS Cookie {#section-92a9454f1ac645948f9059b9fad928bf}

**名前**

AMCVS Cookie 名は、`AMCVS_####@AdobeOrg` 構文に従います。この名前の「####」の部分は、Experience Cloud 組織 ID の一部を示すプレースホルダーです。ID サービスコードの `theVisitor.getInstance` 関数によって、この ID が DCS に渡されます。

完全形式の Cookie 名は以下のようになります。

```
AMCVS_1FD6776A524453CC0A490D44%40AdobeOrg
```

**内容**

AMCVS Cookie は、セッションが初期化されたことを示すフラグの役割を果たします。その値は常に「`1`」となり、セッションが終了したときに中断されます。

**ドメイン**

AMCVS Cookie は、ブラウザーのファーストパーティドメインに設定されます。つまり、ユーザーが現在訪問しているサイトのドメインに設定されます。

![](assets/AMCVS-cookie.png)

## demdex Cookie{#section-7ff7d96d6e4141b08a84a75a63d7814c}

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
   <td colname="col2"> <p>demdex Cookie は、ブラウザーの demdex.net というサードパーティドメインに設定されます。サードパーティドメインは、ユーザーが現在訪問しているサイトとは異なります。 </p> <p>ファーストパーティの AMCV Cookie とは異なり、demdex Cookie および demdex ID は異なるドメインをまたいで維持されます。demdex ID と組織 ID は、ID サービスが正しい訪問者 ID を使用してサイト訪問者を識別し、正しい訪問者 ID を返すための共通の値です。 </p> </td> 
  </tr> 
 </tbody> 
</table>

関連情報については、[Demdex ドメインの呼び出しについて](https://marketing.adobe.com/resources/help/ja_JP/aam/demdex-calls.html)を参照してください。

## Experience Cloud ID の生成 {#section-15f69c0bac394b4b9966a23fbc586d17}

Experience Cloud ID（MID）は、組織 ID と demdex ID から計算によって生成されます。これらの ID が変わらない限り、特定のユーザーに関する正しい MID を生成できるかどうかは、単純に計算上の問題になります。同じ組織 ID と demdex ID があれば、いつでも同じ MID 値が得られます。そのため、ID サービスは、同じ組織で管理され、ID サービスコードが設定されている複数のドメインをまたいで訪問者を追跡することができます。

ページが読み込まれると、ID サービスは MID の作成を開始します。このプロセスでは、`visitorAPI.js` コードライブラリに含まれるコードによって ID サービスへのイベント呼び出しが発行され、その呼び出しを通じて組織 ID が送信されます。ID サービスは MID と demdex ID を作成して、前者を AMCV Cookie に、後者を demdex Cookie にそれぞれ返します。

## 次の手順 {#section-8db1727a63bc4ff68b495f270315d453}

[Experience Cloud ID サービスによる ID のリクエスト方法と設定方法](../mcvid-introduction/mcvid-id-request.md#concept-2caacebb1d244402816760e9b8bcef6a)を参照してください。
