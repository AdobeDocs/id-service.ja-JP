---
title: Safari ITP での ECID ライブラリの手法
seo-title: Safari ITP での ECID ライブラリの手法
description: Adobe ECID（ID サービス）ライブラリのドキュメントです。
seo-description: Adobe ECID（ID サービス）ライブラリのドキュメントです。
translation-type: ht
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# Safari ITP での ECID ライブラリの手法

Safari は ITP を使用したクロスドメイントラッキングと強く結びついているので、アドビでは、お客様および消費者のプライバシーおよび選択肢をサポートするライブラリのベストプラクティスを維持する必要があります。

2019 年 2 月 21 日に、Apple は ITP（Intelligent Tracking Prevention）の最新アップデートを発表しました。サードパーティ Cookie に注力していた以前のバージョンと異なり、このバージョンでは、ファーストパーティ Cookie 用の新しい Tracking Prevention 測定を説明しています。document.cookie API（多くの場合、「クライアント側」Cookie とも呼ばれる）を使用して設定されたすべてのファーストパーティ永続 Cookie は、7 日を上限として期限が切れます。サードパーティ Cookie は、ITP の以前のバージョンで記載されているように、引き続きブロックされます。ITP 2.1 およびアドビソリューションへの影響について詳しくは、[Safari ITP 2.1 が Adobe Experience Cloud および Experience Platform のお客様に与える影響](https://medium.com/adobetech/safari-itp-2-1-impact-on-adobe-experience-cloud-customers-9439cecb55ac)を参照してください。

## Safari ITP 用 Adobe ECID に関する FAQ

**お客様のファーストパーティドメインの Experience Cloud ID ライブラリ（ECID）で設定された AMCV Cookie が ITP 2.1 の影響を受けるのはなぜですか？**

AMCV Cookie は、現在、document.cookie API に依存しており、「クライアント側」で設定されます。Safari は、お客様のサーバーで設定された Cookie を優先します。

**CNAME トラッキングサーバーで設定された Cookie が Safari でのトラッキングに適したオプションなのはなぜですか？**

ITP のルールは、開発者に制御を取り戻すことに注力しています。CNAME 証明書を使用した実装は、JavaScript のみではできません。アドビの CNAME 証明書プログラム（サーバー側トラッキング）は、ITP と合致し、長年、アドビの戦略の一端をなしています。ECID ライブラリは、ECID ライブラリ機能の CNAME 実装への移行に注力したメソッドをリリースしています。

**現在、他の Analytics 訪問者トラッキングメソッドが CNAME と共に使用されているのに、アドビが ECID ライブラリに注力しているのはなぜですか？**

ECID ライブラリ、AMCV Cookie および ECID（MID とも呼ばれる）は、すべてのアドビソリューションを 1 つの ID のもとに統合するための方法として開始されました。この ID は、引き続きアドビ製品ロードマップにおいて優先度の高い Cookie レベル ID であり、Adobe Experience Platform のデフォルト Cookie ID です。

**CNAME は、顧客が複数ドメイントラッキングを有効にするのに役立ちますか？**

CNAME と共に以前から存在していたのと同じルールおよび注意事項がまだ存在します。場合によっては、CNAME が複数ドメインのシナリオで役立つことがあります。メインのエントリサイトがあり、ユーザーが他のドメインを訪問する前にメインのエントリサイトでユーザーの識別ができる場合には、CNAME を使用することで、サードパーティ Cookie を受け入れないブラウザーでも複数ドメイントラッキングをおこなうことができます。ただし、一部のシナリオで CNAME が複数ドメインに役立っている間は、ECID の CNAME 実装への移行の理由は、複数ドメイントラッキングのためではなく、永続的な訪問者 ID のためということになります。CNAME および複数ドメインについて詳しくは、[データ収集 CNAME およびクロスドメイントラッキング](/help/reference/analytics-reference/cname.md)を参照してください。

その他の FAQ は、追加の ITP 変更がリリースされたら、こちらに追加されます。その他の質問については、[Adobe Experience League](https://experienceleague.adobe.com/#recommended/solutions/analytics) を参照してください。

## ITP 関連の変更、方法および設定

Safari 内でのトラッキングのための追加の方法が作成されたら、リファレンスとしてこのページに追加されます。

>[!NOTE] 以下のすべてのドキュメントでは、*ECID*、*MID*、*MCID* は同じです。

ITP および ECID ライブラリの使用に関する取り組みについては、以下を参照してください。

## ECID ライブラリおよび CNAME トラッキングを使用した訪問者 ID の有効期限の延長

ITP 2.1 は、クライアント側 Cookie の書き込み機能を阻止し、正確な訪問者トラッキング情報をお客様に提供する機能を低下させます。そのため、訪問者の Experience Cloud ID（ECID）をファーストパーティ Cookie に格納するという変更が、アドビの CNAME トラッキングサーバーに導入されています。

この変更は、ファーストパーティのコンテキストで Analytics CNAME を使用している ECID お客様にのみ役立ちます。Analytics のお客様で現在 CNAME を使用していない場合や Analytics のお客様でない場合でも、CNAME レコードが適しています。カスタマーケアまたは担当のアカウント担当者に問い合わせて、[CNAME](https://marketing.adobe.com/resources/help/en_US/whitepapers/first_party_cookies/adobe_managed_cert_pgm.html) の登録プロセスを開始してください。

この変更を活用するには、ECID ライブラリ v. 4.3.0 以降にアップグレードしてください。

**デザイン**

demdex.net に対して ID リクエストがおこなわれ、ECID が取得されると、ECID ライブラリでトラッキングサーバーが設定されている場合、お客様のドメインに対して ID リクエストがおこなわれます。このエンドポイントは、クエリ文字列から ecid パラメーターを読み取り、ECID および今後の 2 年間の有効期限のみから成る新しい [Cookie](/help/introduction/cookies.md) を設定します。この方法でこのエンドポイントが呼び出されるたびに、`s_ecid` Cookie は、呼び出されたときから 2 年間の有効期限に書き換えられます。ECID ライブラリは、この Cookie の値が取得できるように、v 4.3.0 に更新される必要があります。

この新しい `s_ecid` Cookie は、AMCV Cookie と同じオプトアウトステータスに従います。ecid が `s_ecid` Cookie から読み取られる場合、常に demdex が即座に呼び出されて、その ID の最新のオプトアウトステータスが取得され、AMCV Cookie に格納されます。

さらに、消費者がこの[方法](https://marketing.adobe.com/resources/help/en_US/sc/implement/opt_out_link.html)を使用して Analytics トラッキングをオプトアウトした場合、この `s_ecid` Cookie は削除されます。

trackingServer または trackingServerSecure を使用してライブラリを初期化する際に、トラッキングサーバー名が Visitor JS ライブラリに提供される必要があります。これは、Analytics 設定の trackingServer 設定に一致する必要があります。

この方法を利用しないことを選択する場合、discardtrackingServerECID の設定を ECID ライブラリ 実装に追加します。この設定が true に設定されている場合、訪問者ライブラリは、ファーストパーティトラッキングサーバーによって設定された MID を読み込みません。

![](assets/itp-proposal-v1.png)

## クロスドメイントラッキング（自社内の複数のドメイン）用の appendVisitorIDsTo メソッドの使用

この関数を使用すると、ブラウザーでサードパーティ Cookie がブロックされている場合でも、複数のドメインにまたがって訪問者の ECID を共有できます。この関数を使用するには、ID サービスを実装し、ソースドメインおよび宛先ドメインを所有している必要があります。VisitorAPI.js バージョン 1.7.0 以降（ただし、バージョン 1.10.0 を除く）で利用できます。

**デザイン**

* 訪問者が自社の他のドメインを閲覧すると、Visitor.appendVisitorIDsTo(url) は、クエリパラメーターとして追加された ECID を含む URL を返します。

   この URL を使用して、元のドメインから宛先ドメインにリダイレクトします。

* アドビに訪問者の ID のリクエストを送信するのではなく、宛先ドメインの ID サービスコードによって、URL から ECID が抽出されます。

   このリクエストにはサードパーティ Cookie が含まれますが、このケースではサードパーティ Cookie を利用できません。

* 宛先ページの ID サービスコードは、ECID で渡された値を使用して訪問者を追跡します。

   >[!NOTE]
   >宛先ページが既に以前の訪問での ECID を持っている場合、既存の Cookie を上書きする決定がこの設定 overwriteCrossDomainMCIDAndAID によって制御されます。この設定について詳しくは、[overwriteCrossDomainMCIDAndAID](/help/library/function-vars/overwrite-visitor-id.md) を参照してください。
   >
   >このメソッドについて詳しくは、[appendVisitorIDsTo（クロスドメイントラッキング）](/help/library/get-set/appendvisitorid.md)リファレンスページを参照してください。
