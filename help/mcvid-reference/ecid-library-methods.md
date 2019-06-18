---
title: Safari ITP世界のECIDライブラリメソッド
seo-title: Safari ITP世界のECIDライブラリメソッド
description: Adobe ECID（IDサービス）ライブラリのドキュメント。
seo-description: Adobe ECID（IDサービス）ライブラリのドキュメント。
translation-type: tm+mt
source-git-commit: 1dd8b109f7e9567b5f72747ecc653d35d0942413

---


# Safari ITP世界のECIDライブラリメソッド

SafariがITP経由でクロスドメイントラッキングを緊密にすることにより、顧客は、顧客のプライバシーと選択肢をサポートするライブラリのベストプラクティスを維持する必要があります。

2019年2月21日に、Appleは最新のITP（インテリジェントトラッキング防止）の最新のアップデートを発表しました。サードパーティcookieに重点を置いている以前のバージョンとは異なり、このバージョンではファーストパーティcookieの新しいトラッキング防止対策について説明しています。document. cookie APIを介して設定されたファーストパーティの永続的cookieはすべて、「クライアントサイド」 cookieと呼ばれ、7日間の上限を持ちます。サードパーティcookieは、以前のバージョンのITPで説明されているように、引き続きブロックされます。TP2.1とアドビソリューションの影響について詳しくは、 [Safari ITP2.1への影響（Adobe Experience CloudおよびExperience Platformユーザーへの影響）を参照](https://medium.com/adobetech/safari-itp-2-1-impact-on-adobe-experience-cloud-customers-9439cecb55ac)してください。

## Safari Ip FAQのAdobe ECID

**AMCV cookieが、顧客のファーストパーティドメインのExperience Cloud IDライブラリ（ECID）によって設定されているのは、ITP2.1の影響を受けるのはなぜですか。**

AMCV cookieは現在、document. cookie APIに依存しており、「クライアント側」を介して設定されています。Safariは、顧客のサーバーから設定されたcookieを優先します。

**CNAMEトラッキングサーバーによって設定されたcookieがSafariの追跡に適しているのはなぜですか。**

ITPのルールは開発者に制御を制御することに重点を置いています。CNAME証明書による実装は、JavaScriptのみを使用して行うことはできません。アドビのCNAME認定プログラム（サーバー側のトラッキング）はITPと共に行に配置されており、何年にもわたってアドビの戦略の一部となっています。ECIDライブラリは、ECIDライブラリ機能をCNAME実装に移動することに重点を置いたリリースメソッドです。

**他のAnalytics訪問者トラッキング方法がCNAMEで使用されている場合、EIDライブラリにアドビがフォーカスしているのはなぜですか。**

EIDライブラリ、AMCV cookie、およびECID（MID）は、すべてのアドビソリューションを1つのIDで統合する方法として開始されます。このIDは、Adobe製品マップの優先順位のcookieレベルのIDで、Adobe Experience Platformのデフォルトのcookie IDとなります。

**CNAMEは、顧客が複数ドメインのトラッキングを有効にするのに役立ちますか。**

CNAMEが以前に存在していたのと同じルールおよび注意点が存在します。場合によっては、CNAMEが複数ドメインのシナリオで役立ちます。他のドメインを訪問する前にユーザーが識別できるメインエントリサイトがある場合、CNAMEはサードパーティcookieを受け入れないブラウザーで複数ドメイントラッキングを有効にできます。ただし、CNAMEは複数ドメインの場合に役立ちますが、CIDのシフトの理由は、複数ドメインの追跡ではなく永続的な訪問者の識別に対するものです。CNAMEおよびマルチドメインについて詳しくは [、データ収集CNAMEおよびクロスドメイントラッキング](/help/mcvid-reference/mcvid-analytics-reference/mcvid-cname.md)を参照してください。

追加のTP変更がリリースされると、その他のFAQが追加されます。詳しくは、Adobe Experience Leagueを参照 [](https://experienceleague.adobe.com/#recommended/solutions/analytics)してください。

## ITP関連の変更、メソッドおよび設定

Safari内での追跡用に追加のメソッドが作成されると、このページへの参照として追加されます。

>[!NOTE]*以下のすべてのドキュメントのECID* = *MID* = *MCID* 。

ITPおよびECIDライブラリの使用に関する取り組みについては、以下を参照してください。

## 訪問者IDの有効期限を延長するには、ECIDライブラリおよびCNAMEトラッキングを使用します

TP2.1hammerは、クライアントサイドのcookieを記述する機能を提供します。これにより、正確な訪問者追跡情報を顧客に提供する能力が損なわれます。そのため、アドビのCNAMEトラッキングサーバーで、訪問者のExperience Cloud ID（ECID）をファーストパーティcookieに保存する変更が導入されています。

この変更は、ファーストパーティコンテキストでAnalytics CNAMEを使用している場合にのみ有効です。現在CNAMEを使用していないAnalyticsユーザー、またはAnalytics以外のユーザーである場合は、CNAMEレコードの資格が依然として付与されます。[CNAMEへの登録プロセスを開始するには、カスタマーケアまたはアカウント担当者にお問い合わせ](https://marketing.adobe.com/resources/help/en_US/whitepapers/first_party_cookies/adobe_managed_cert_pgm.html)ください。

この変更を利用するには、ECIDライブラリv.4.3.0以降にアップグレードしてください。

**デザイン**

demdex. netに対してIDリクエストがおこなわれ、ECIDが取得されると、その顧客のドメインに対してトラッキングサーバーが設定されている場合、IDリクエストが顧客のドメインに対して行われます。このエンドポイントは、クエリ文字列からecidパラメーターを読み取り、ECIDと有効期限の2年後に構成される新しい [cookie](/help/mcvid-introduction/mcvid-cookies.md) を設定します。このようなエンドポイントがこの方法で呼び出されるたびに、そのcookieは `s_ecid` その呼び出しから2年の間有効期限が切れます。このcookieの値を取得できるように、ECIDライブラリをv4.3.0に更新する必要があります。

この新しい `s_ecid` cookieは、AMCV cookieと同じオプトアウトステータスに従います。recidが `s_ecid` cookieから読み取られると、demdexは常に即座に呼び出され、そのIDの最新のオプトアウトステータスを取得し、AMCV cookieに保存されます。

さらに、消費者がこの [方法](https://marketing.adobe.com/resources/help/en_US/sc/implement/opt_out_link.html)を使用してAnalyticsトラッキングをオプトアウトしている場合、この `s_ecid` cookieは削除されます。

trackingServerまたはtrackingServerSecureを使用してライブラリを初期化するときに、トラッキングサーバー名をvisitorJSライブラリに提供する必要があります。これは、Analytics設定のtrackingServer configと一致する必要があります。

この方法を利用しない場合は、以下の設定をEIDライブラリ実装に追加します。discardTrackingServerId。このconfigがtrueに設定されている場合、訪問者ライブラリはファーストパーティトラッキングサーバーによって設定されたMIDを読み取りません。

![](assets/itp-proposal-v1.png)

## AppendVisitorIDsToメソッドを、クロスドメイントラッキング（独自の会社の複数ドメイン内）に使用します。

この関数を使用すると、ブラウザーがサードパーティcookieをブロックしているときに、ドメイン間で訪問者のECIDを共有できます。この関数を使用するには、ID サービスを実装し、ソースドメインおよび宛先ドメインを所有している必要があります。VisitorAPI. jsバージョン1.7.0以降（バージョン1.10.0ではありません）で使用できます。

**デザイン**

* 訪問者が他のドメインを閲覧するとき、Visitor. appendVisitorIDsTo（url）は、クエリパラメーターとして追加されたEIDを持つURLを返します。

   このURLを使用して元のドメインから宛先ドメインにリダイレクトします。

* 宛先ドメインのIDサービスコードは、その訪問者のIDに対してアドビにリクエストを送信する代わりに、URLからECIDを抽出します。

   このリクエストにはサードパーティ Cookie が含まれますが、このケースではサードパーティ Cookie を利用できません。

* 宛先ページのIDサービスコードは、渡されたEIDを使用して訪問者を追跡します。

   >[!NOTE]
   >宛先ページに既に以前の訪問からのECIDがある場合、既存のcookieを上書きする決定は、このconfig overwriteCrossDomainMCIDAndAIDによって制御されます。このconfigについて詳しくは [、overwriteCrossDomainMCIDAndAID](/help/mcvid-library/mcvid-function-vars/mcvid-overwrite-visitor-id.md)を参照してください。
   >
   >このメソッドについて詳しくは [、appendVisitorIDsTo（クロスドメイントラッキング）](/help/mcvid-library/mcvid-get-set/mcvid-appendvisitorid.md) リファレンスページを参照してください。
