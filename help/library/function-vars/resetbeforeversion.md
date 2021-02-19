---
description: この設定を使用すると、更新対象の ID サービスのバージョンに基づいて、孤立したり古くなったりした Experience Cloud ID（ECID）を消去できます。
keywords: ID サービス
seo-description: この設定を使用すると、更新対象の ID サービスのバージョンに基づいて、孤立したり古くなったりした Experience Cloud ID（ECID）を消去できます。
seo-title: resetBeforeVersion
title: resetBeforeVersion
uuid: b00d18b8-6720-42f9-9c83-bd306184cc0c
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 61%

---


# resetBeforeVersion{#resetbeforeversion}

この設定を使用すると、更新対象の ID サービスのバージョンに基づいて、孤立したり古くなったりした Experience Cloud ID（ECID）を消去できます。

`resetBeforeVersion` 変数の値として ID サービスのバージョンを指定すると、クライアント側 ID から古い ECID が消去されます。

セッションのタイムアウトなど、状況によっては、IDサービスがサーバー側IDを正常に取得しない場合に、クライアント側IDが生成されることがあります。 この場合、複数のドメイン間で追跡したり、他のソリューションと適切に同期したりする機能を持たずに、IDサービスによって単独のクライアント側IDが追跡されます。 この動作では、現在の AMCV Cookie のバージョンと `resetBeforeVersion` の値が比較されます。Cookie が存在しないか、Cookie のバージョンが最新リリースバージョンの `resetBeforeVersion` よりも小さい（古い）場合、AMCV Cookie は削除され、ID サービスは新しい ECID をリクエストします。

ブラウザーにサードパーティ Demedex Cookie がある訪問者の場合、ECID が、この Demedex Cookie の UUID を使用して適切に生成されたかどうかがチェックされます。そのチェックが真である場合、新しいECIDも同じになり、訪問者は新しいと見なされます。 何らかの理由で消去されるECIDがDemdex cookieを使用して生成されなかった場合、またはDemdex cookieがない場合、訪問者は新しいECIDを受け取り、新しいと見なされます。

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

