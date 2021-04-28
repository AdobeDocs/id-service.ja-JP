---
description: この設定を使用すると、更新対象の ID サービスのバージョンに基づいて、孤立したり古くなったりした Experience Cloud ID（ECID）を消去できます。
keywords: ID サービス
seo-description: この設定を使用すると、更新対象の ID サービスのバージョンに基づいて、孤立したり古くなったりした Experience Cloud ID（ECID）を消去できます。
seo-title: resetBeforeVersion
title: resetBeforeVersion
uuid: b00d18b8-6720-42f9-9c83-bd306184cc0c
exl-id: 9fa40baa-433d-4f16-824b-521948a92a4b
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '270'
ht-degree: 100%

---

# resetBeforeVersion {#resetbeforeversion}

この設定を使用すると、更新対象の ID サービスのバージョンに基づいて、孤立したり古くなったりした Experience Cloud ID（ECID）を消去できます。

`resetBeforeVersion` 変数の値として ID サービスのバージョンを指定すると、クライアント側 ID から古い ECID が消去されます。

セッションのタイムアウトなど、条件によっては、ID サービスでサーバーサイド ID が正常に取得されずに、クライアントサイド ID が生成されることがあります。 この場合、孤立したクライアントサイド ID は ID サービスによって追跡されますが、ドメイン間で追跡したり、他のソリューションと適切に同期したりすることはできません。 この動作では、現在の AMCV Cookie のバージョンと `resetBeforeVersion` の値が比較されます。Cookie が存在しないか、Cookie のバージョンが最新リリースバージョンの `resetBeforeVersion` よりも小さい（古い）場合、AMCV Cookie は削除され、ID サービスは新しい ECID をリクエストします。

ブラウザーにサードパーティ Demedex Cookie がある訪問者の場合、ECID が、この Demedex Cookie の UUID を使用して適切に生成されたかどうかがチェックされます。そのチェックの結果が真であるとわかった場合、新しい ECID は同じになり、訪問者は新規と見なされます。 何らかの理由で、クリアされる ECID が demdex Cookie を使用して生成されなかった場合、または demdex Cookie がない場合、訪問者は新しい ECID を受け取り、新規と見なされます。

**構文：** `resetBeforeVersion = "3.3"`

**コードサンプル**

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Marketing Cloud organization ID here", { 
  
    //Same as s.trackingServer 
    trackingServer: "Insert tracking server here ", 
  
    //Same as s.trackingServerSecure 
    trackingServerSecure: "Insert secure tracking server here", 
  
    //For CNAME support only. Exclude these variables if you're not using CNAME 
    marketingCloudServer: "Insert tracking server here", 
    marketingCloudServerSecure: "Insert secure tracking server here", 
  
    //Changing the version 
    resetBeforeVersion: "3.3" 
});
```
