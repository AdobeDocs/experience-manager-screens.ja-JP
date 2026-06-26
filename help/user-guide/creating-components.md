---
title: コンポーネントの作成
description: AEM コンポーネントを使用して、web ページ上で使用できるコンテンツを保持、書式設定およびレンダリングする方法について説明します。
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 4d673039-4963-458a-89e9-023a993dd354
TQID: https://experienceleague.adobe.com/0FSVmHOxse3eUn8eKvolCKk7-Wk9SGzA10iIcykLUs0
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 340
ht-degree: 80%

---

# コンポーネントの作成 {#creating-components}

>[!IMPORTANT]
>このコンテンツは、AEM オンプレミス/AMS （AEM 6.5LTSおよびAEM 6.5）に対して有効です。 AEM as a Cloud Service Screensの内容については、[AEM as a Cloud Service ガイド ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)を参照してください。

AEM コンポーネントを使用して、web ページ上で使用できるコンテンツを保持、書式設定およびレンダリングします。

>[!NOTE]
>
>AEM コンポーネントの作成について詳しくは、AEM コンポーネントの開発を参照してください。

## チャネルの作成 {#authoring-channels}

チャネルは、一連のディスプレイに配信されるコンテンツの中心的なオブジェクトです。 したがって、コンテンツ作成者は、通常、エディターでチャネルを開いてコンテンツを追加または変更します。 チャネルは ***`cq:Page`*** なので、同じ従来の UX パターンに従って、チャネル上のコンポーネントを追加および変更します。

ただし、チャネル内のコンポーネントは通常フルスクリーンでレンダリングされるので、単一コンポーネントの編集や新しい順序の編成を行う際にオーサリングエクスペリエンスに影響を及ぼします。 そのため、チャネルはコンポーネントの様々なビューをレンダリングするためにセレクターを使用します。 オーサリング環境では、`edit` セレクターを使用して、カスタムチャネルレンダリングをアクティブ化します。

例：`http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html`

ユーザーは、編集時に URL にセレクターを追加する必要はありません。 クライアントサイドのロジックがレイヤースイッチイベントをリッスンしており、チャネルに専用のリソースタイプ *screens/core/components/channel* がある場合にセレクターを追加します。

## コンポーネントのレンダリング {#rendering-components}

適切なオーサリングを有効にするために、コンポーネントでは次の 2 つのレンダリングを提供する必要があります。

| **コンポーネント** | **レンディション** |
|---|---|
| *my-component/my-component.html* | 実稼動レンダリング |
| *my-component/edit.html* | 小さいビューでのレンダリングの編集 |

ビルトインのコンポーネントでは、次のクライアントライブラリのカテゴリが使用されます。

| **コンポーネント** | **クライアントライブラリ** |
|---|---|
| *cq.screens.components.edit* | オーサリング時に読み込む必要がある CSS および JS |
| *cq.screens.components.production* | チャネルの実行時に読み込む必要がある CSS および JS |
| *cq.screens.components* | 共有 CSS および JS |

>[!NOTE]
>
>カスタムコンポーネントを開発する場合は、[AEM Screens のサンプルコンポーネントテンプレート](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)を使用してください。

