---
description: この設定を使用すると、更新対象の ID サービスのバージョンに基づいて、孤立したり古くなったりした Experience Cloud ID（ECID）を消去できます。
keywords: ID サービス
seo-description: この設定を使用すると、更新対象の ID サービスのバージョンに基づいて、孤立したり古くなったりした Experience Cloud ID（ECID）を消去できます。
seo-title: resetBeforeVersion
title: resetBeforeVersion
uuid: b00d18b8-6720-42f9-9c83-bd306184cc0c
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# resetBeforeVersion{#resetbeforeversion}

この設定を使用すると、更新対象の ID サービスのバージョンに基づいて、孤立したり古くなったりした Experience Cloud ID（ECID）を消去できます。

`resetBeforeVersion` 変数の値として ID サービスのバージョンを指定すると、クライアント側 ID から古い ECID が消去されます。

セッションのタイムアウトなどの特定の状況では、ID サービスがサーバー側 ID を正常に取得しなくても、クライアント側 ID が生成されることがあります。このようになった場合、孤立しているクライアント側 ID は ID サービスで追跡されますが、ドメイン全体で追跡したり、他のソリューションと適切に同期したりすることはできません。この動作では、現在の AMCV Cookie のバージョンと `resetBeforeVersion` の値が比較されます。Cookie が存在しないか、Cookie のバージョンが最新リリースバージョンの `resetBeforeVersion` よりも小さい（古い）場合、AMCV Cookie は削除され、ID サービスは新しい ECID をリクエストします。

ブラウザーにサードパーティ Demedex Cookie がある訪問者の場合、ECID が、この Demedex Cookie の UUID を使用して適切に生成されたかどうかがチェックされます。このチェックにより適切に生成されたことが判明した場合、新しい ECID は同じになり、訪問者は新規訪問者とみなされます。何らかの理由で消去対象の ECID の生成に Demdex Cookie が使用されなかった場合または Demdex Cookie が存在しない場合は、訪問者に新しい ECID が付与され、新規訪問者とみなされます。

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

