---
description: 一部の実装では、追加の Analytics イベント（購入など）をサーバーから送信できるようにするために、訪問者 ID を JavaScript からサーバーに渡します。
keywords: ID サービス
seo-description: 一部の実装では、追加の Analytics イベント（購入など）をサーバーから送信できるようにするために、訪問者 ID を JavaScript からサーバーに渡します。
seo-title: JavaScript を利用したサーバー側実装
title: JavaScript を利用したサーバー側実装
uuid: 256ea0e7-1eb4-4c92-9a7e-f61cb1ed13c7
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# JavaScript を利用したサーバー側実装 {#server-side-implementation-mixed-with-javascript}

一部の実装では、追加の Analytics イベント（購入など）をサーバーから送信できるようにするために、訪問者 ID を JavaScript からサーバーに渡します。

ID サービス API には、サーバーに渡す ID の値を取得するメソッド [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md) および [getAnalyticsVisitorID](../../library/get-set/getanalyticsvisitorid.md) が用意されています。

Experience Cloud 訪問者 ID と Analytics 訪問者 ID の両方を確認して、（存在する場合は）両方の ID を送信し、既存の Analytics 訪問者プロファイルに関連付けられているすべてのデータが送信されるようにします。

>[!IMPORTANT]
>
>Java 版 AppMeasurement は、現在 Experience Cloud Identity Service をサポートしていません。

## Data Insertion API {#section-955ce7664a4646d38b3005cb2df40baf}

`<visitorID>` 要素に Analytics 訪問者 ID を含めます（設定されている場合）。

`<marketingCloudVisitorID>` 要素に Experience Cloud 訪問者 ID を含めます。

[サポートされる XML タグ](https://marketing.adobe.com/developer/en_US/documentation/data-insertion/r-supported-tags)を参照してください。

## Java 版 AppMeasurement {#section-d664b94934924d048300d9c2b6560085}

Java 版 AppMeasurement は、現在 Experience Cloud Identity Service をサポートしていません。
