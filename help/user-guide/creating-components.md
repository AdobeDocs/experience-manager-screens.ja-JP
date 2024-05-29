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
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 87%

---

# コンポーネントの作成 {#creating-components}

AEM コンポーネントを使用して、web ページ上で使用できるコンテンツを保持、書式設定およびレンダリングします。

>[!NOTE]
>
>AEM コンポーネントの作成について詳しくは、AEM コンポーネントの開発を参照してください。

## チャネルのオーサリング {#authoring-channels}

チャネルは、一連のディスプレイに配信されるコンテンツの中心的なオブジェクトです。したがって、コンテンツ作成者は、通常、エディターでチャネルを開いてコンテンツを追加または変更します。チャネルは ***`cq:Page`*** なので、同じ従来の UX パターンに従って、チャネル上のコンポーネントを追加および変更します。

ただし、チャネル内のコンポーネントは通常フルスクリーンでレンダリングされるので、単一コンポーネントの編集や新しい順序の編成を行う際にオーサリングエクスペリエンスに影響を及ぼします。そのため、チャネルはコンポーネントの様々なビューをレンダリングするためにセレクターを使用します。オーサリング環境では、編集セレクターを使用して、カスタムチャネルのレンダリングをアクティベートします。

例：`http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html`

ユーザーは、編集時に URL にセレクターを追加する必要はありません。クライアントサイドのロジックがレイヤースイッチイベントをリッスンしており、チャネルに専用のリソースタイプ *screens/core/components/channel* がある場合にセレクターを追加します。

## コンポーネントのレンダリング {#rendering-components}

適切なオーサリングを有効にするために、コンポーネントでは次の 2 つのレンダリングを提供する必要があります。

| **コンポーネント** | **レンディション** |
|---|---|
| *my-component/my-component.html* | 実稼動レンダリング |
| *my-component/edit.html* | 小さいビューでのレンダリングの編集 |

組み込みのコンポーネントでは、次のクライアントライブラリのカテゴリが使用されます。

| **コンポーネント** | **クライアントライブラリ** |
|---|---|
| *cq.screens.components.edit* | オーサリング中に読み込む必要がある CSS と JS |
| *cq.screens.components.production* | チャネルの実行中に読み込む必要がある CSS と JS |
| *cq.screens.components* | 共有 CSS および JS |

>[!NOTE]
>
>カスタムコンポーネントを開発する場合は、[AEM Screens のサンプルコンポーネントテンプレート](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)を使用してください。
