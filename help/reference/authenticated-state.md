---
description: 通常の Experience Cloud 訪問者 ID に加えて、追加の顧客 ID と認証状態を各訪問者に関連付けることができます。
keywords: ID サービス
title: 顧客 ID と認証状態
exl-id: 0215225c-20f5-4e44-a368-b2df683aca9d
source-git-commit: 159b37e360b586bbada13e34793009e3067de668
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 98%

---

# 顧客 ID と認証状態 {#customer-ids-and-authentication-states}

通常の Experience Cloud 訪問者 ID に加えて、追加の顧客 ID と認証状態を各訪問者に関連付けることができます。

## 認証状態 {#section-68ad4065dfaa437d9070832d6e2bf85c}

`setCustomerIDs` メソッドは、同じ訪問者に対する複数の顧客 ID を受け入れます。そのため、異なるデバイス間で個々のユーザーを識別したりターゲットにしたりすることができます。例えば、これらの ID を[顧客属性](https://experienceleague.adobe.com/docs/core-services/interface/customer-attributes/attributes.html?lang=ja)として [!DNL Experience Cloud] にアップロードして、異なるソリューションからこのデータにアクセスすることができます。

>[!IMPORTANT]
>
>顧客属性とコアサービス機能には、`setCustomerIDs`（顧客 ID の同期）が必要です。顧客 ID の同期は、[!DNL Analytics] のオプションの識別方法です。[!DNL Target] には、顧客属性を機能させるために `Visitor.AuthState.AUTHENTICATED` が必要です。例については、[コアサービス - ソリューションを有効にする方法](https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html?lang=ja)を参照してください。

Experience Cloud Identity Service v1.5 以降の `setCustomerIDs` には、オプションの `AuthState` オブジェクトが含まれます。`AuthState` は、訪問者の認証状態（ログイン済み、ログアウト済みなど）に従って訪問者を識別します。認証状態は、表に示すステータス値を使用して設定します。認証状態は整数で返されます。

<table id="table_8547671CC97145529981FBF6C302BEC5"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 認証状態 </th> 
   <th colname="col2" class="entry"> ステータス整数 </th> 
   <th colname="col3" class="entry"> ユーザーステータス </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.UNKNOWN </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> 0 </span> </p> </td> 
   <td colname="col3"> <p>不明または認証なし。 </p> <p> 不明は、<span class="codeph">AuthState</span> が訪問者 ID と共に使用されていない場合や、各ページまたはアプリケーションコンテキストで明示的に設定されていない場合に、デフォルトで適用されます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.AUTHENTICATED </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> 1 </span> </p> </td> 
   <td colname="col3"> <p>特定のインスタンス、ページまたはアプリケーションに対して認証済み。 </p> <p> <p>注意：適切に動作させるために、<span class="keyword">Target</span> の顧客属性には、このステータスが必要です。 </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.LOGGED_OUT </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> 2 </span> </p> </td> 
   <td colname="col3"> <p>ログアウト済み。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 認証状態のユースケース {#section-fe9560cc490943b29dac2c4fb6efd72c}

ユーザーが Web プロパティで実行するアクションや認証されているかどうかに応じて、認証状態をユーザーに割り当てることができます。次の表の例を参照してください。

<table id="table_3769E79304014C4F87094B87A8ACE4E0"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 認証状態 </th> 
   <th colname="col2" class="entry"> 使用例 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.UNKNOWN </span> </p> </td> 
   <td colname="col2"> <p>この状態は、次のようなシナリオで使用できます。 </p> <p> 
     <ul id="ul_086C7446D258443DA7AF5BB96A6AAEC7"> 
      <li id="li_7845BBD62D7B4362AD3FE33DEDA8FBA1">電子メールの読み取り（このアクションは読者が意図した受信者であることを意味しますが、電子メールが転送された可能性もあります）。 </li> 
      <li id="li_FAB7ACFC69624631BD01FC0ED84B23C5">電子メールからランディングページへのクリックスルー。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.AUTHENTICATED </span> </p> </td> 
   <td colname="col2"> <p>ユーザーは現在、Web サイトまたはアプリのアクティブセッションで認証されています。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.LOGGED_OUT </span> </p> </td> 
   <td colname="col2"> <p>ユーザーは認証されましたが、アクティブにログアウトしました。ユーザーが認証済み状態から意図的に切断した。ユーザーが認証済みとして扱われなくなります。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 顧客 ID と認証状態の設定 {#section-ec4b367d16ad4ac1a1baca9b01f4ee98}

顧客 ID には、次の例に示すように ID と認証状態の組み合わせを含めることができます。

>[!IMPORTANT]
>
>* ID は大文字と小文字が区別されます。
>* エンコードされていない ID 値のみを使用してください。
>* 顧客 ID と認証状態は、訪問者 ID Cookie に保存されません。ページまたはアプリケーションコンテキストごとに設定する必要があります。
>* 顧客 ID に個人識別情報（PII）を含めないでください。PII（電子メールアドレスなど）を使用して訪問者を識別する場合は、情報をハッシュ化または暗号化して格納することをお勧めします。ECID ライブラリは、ハッシュユーザー識別子をサポートしています。[setCustomerIDs の SHA256 ハッシュサポート](/help/reference/hashing-support.md)を参照してください。


```js
// Single ID with a single authentication state 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    } 
}); 
 
/* 
Multiple IDs with only the first ID explicitly assigned an authentication state. 
The second ID is not explicitly assigned an authentication state and is implicitly 
assigned Visitor.AuthState.Unknown by default. 
*/ 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":"550e8400-e29b-41d4-a716-446655440000" 
}); 
 
// Multiple IDs with identical authentication states 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    } 
}); 
 
// Multiple IDs with different authentication states 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":Visitor.AuthState.LOGGED_OUT 
    } 
}); 
```

## 顧客 ID と認証状態の返送 {#section-71a610546188478fa9a3185a01d6e83b}

顧客 ID と関連する認証状態を返すには、`getCustomerIDs` を使用します。このメソッドは、訪問者の認証状態を整数で返します。

**構文**

`getCustomerIDs` は以下の構文のデータを返します。

```js
{ 
    [customerIDType1]:{ 
        "id":[customerID1], 
        "authState":[authState1] 
    }, 
    [customerIDType2]:{ 
        "id":[customerID2], 
        "authState":[authState2] 
    } 
    ... 
}
```

**例**

返された顧客 ID と認証状態データは、次の例のようになります。

```js
Object customerIDs = visitor.getCustomerIDs(); 
  
// No setCustomerIDs call on this instance 
{} 
  
// setCustomerIDs call on this instance with {"userid":{"id":"67312378756723456"}} 
{ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":0 
    } 
} 
  
// setCustomerIDs call on this instance with {"userid":{"id":"67312378756723456","authState":Visitor.AuthState.AUTHENTICATED}} 
{ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":1 
    } 
} 
  
// setCustomerIDs call on this instance with {"userid":{"authState":Visitor.AuthState.LOGGED_OUT}} 
{ 
    "userid":{ 
        "authState":2 
    } 
} 
  
// setCustomerIDs call on this instance with {"userid":{"authState":Visitor.AuthState.LOGGED_OUT},"dpuuid":{"id":"550e8400-e29b-41d4-a716-446655440000"}} 
{ 
    "userid":{ 
        "authState":2 
    }, 
    "dpuuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":0 
    } 
 }
```

## SDK のサポート {#section-861c6b3b1ba645dda133dccb22ec7bb0}

[!DNL Experience Cloud] ID サービスは、アドビの Android および iOS SDK コードで顧客 ID と認証状態をサポートします。次のコードライブラリを参照してください。

* [Android SDK のメソッド](https://experienceleague.adobe.com/docs/mobile-services/android/overview.html?lang=ja)
* [iOS SDK のメソッド](https://experienceleague.adobe.com/docs/mobile-services/ios/overview.html?lang=ja)

## Analytics および Audience Manager ユーザー向けの注意点 {#section-3a8e9d51e71c4c6e865184b81ed9d99b}

宣言済み ID を [!DNL Audience Manager] に渡す場合、`userid` オブジェクトが、データソースに関連付けられた統合コードと一致している必要があります。詳しくは、[マージルールコードの設定](https://experienceleague.adobe.com/docs/audience-manager/user-guide/features/profile-merge-rules/merge-rules-start.html?lang=en#configure-merge-rule-code)ドキュメントの「[!UICONTROL 訪問者 ID サービス]」の節を参照してください。
