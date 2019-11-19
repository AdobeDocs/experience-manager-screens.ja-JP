---
title: コンポーネントの作成
seo-title: コンポーネントの作成
description: AEM コンポーネントを使用して、Web ページ上で使用できるコンテンツを保持、書式設定およびレンダリングします。チャネルのオーサリングとコンポーネントのレンダリングについて学習するには、このページの説明に従います。
seo-description: AEM コンポーネントを使用して、Web ページ上で使用できるコンテンツを保持、書式設定およびレンダリングします。チャネルのオーサリングとコンポーネントのレンダリングについて学習するには、このページの説明に従います。
uuid: 66c76dd5-495a-4dcb-ad18-7f8a92669752
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: cdc530d8-ef0e-4b61-b1f0-5f4d831f1392
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# コンポーネントの作成 {#creating-components}

AEM コンポーネントを使用して、Web ページ上で使用できるコンテンツを保持、書式設定およびレンダリングします。

>[!NOTE]
>
>AEMコンポーネントの作成の詳細については、「AEMコンポーネントの開発」を参照してください。

## チャネルのオーサリング {#authoring-channels}

チャネルは、一連のディスプレイに配信されるコンテンツの中心となるオブジェクトです。このため、コンテンツ作成者は通常、エディターでチャネルを開いてコンテンツを追加または変更します。Since the Channel is a ***cq:Page*** it will follow the same traditional UX pattern to add and change components on the channel.

ただし、チャネル内のコンポーネントは通常フルスクリーンでレンダリングされるので、単一コンポーネントの編集や新しい順序の編成をおこなう際にオーサリングエクスペリエンスに影響を及ぼします。そのため、チャネルはコンポーネントの様々なビューをレンダリングするためにセレクターを使用します。オーサリング環境では、編集セレクターを使用して、カスタムチャネルレンダリングをアクティブにします。

For example, `http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html`

ユーザーは、編集時に URL にセレクターを追加する必要はありません。A client side logic is listening to the layer switch event and adds the selector if a the channel has the dedicated resource type *screens/core/components/channel.*

## コンポーネントのレンダリング {#rendering-components}

適切なオーサリングを有効にするために、コンポーネントでは次の 2 つのレンダリングを提供する必要があります。

| **コンポーネント** | **レンディション** |
|---|---|
| *my-component/my-component.html* | 生産レンダリング |
| *my-component/edit.html* | 編集，レンダリングを小さいビューで |

組み込みのコンポーネントでは、次のクライアントライブラリカテゴリが使用されます。

| **コンポーネント** | **クライアントライブラリ** |
|---|---|
| *cq.screens.components.edit* | オーサリング時に読み込む必要があるCSSとJS |
| *cq.screens.components.production* | チャネルの実行時に読み込む必要があるCSSとJS |
| *cq.screens.components* | 共有CSSとJS |

>[!NOTE]
>
>To develop custom components, use the *** [AEM Screens sample component template](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)***.

