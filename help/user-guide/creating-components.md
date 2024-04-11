---
title: コンポーネントの作成
description: AEM コンポーネントを使用して、web ページ上で使用可能にしたコンテンツを保持、書式設定およびレンダリングする方法について説明します。
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 4d673039-4963-458a-89e9-023a993dd354
source-git-commit: a8055c5f859e401f7b1da4f5d95f1268dee243ad
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 59%

---

# コンポーネントの作成 {#creating-components}

AEM コンポーネントを使用して、web ページ上で使用できるコンテンツを保持、書式設定およびレンダリングします。

>[!NOTE]
>
>AEM コンポーネントの作成について詳しくは、AEM コンポーネントの開発を参照してください。

## チャネルのオーサリング {#authoring-channels}

チャネルは、一連のディスプレイに配信されるコンテンツの中心的なオブジェクトです。したがって、通常、コンテンツ作成者は、コンテンツを追加または変更するために、エディターでチャネルを開きます。チャネルが***であるため`cq:Page`***まり、チャネル上のコンポーネントを追加および変更する場合は、従来の UX パターンと同じパターンに従います。

ただし、チャネル内のコンポーネントは通常フルスクリーンでレンダリングされるので、単一のコンポーネントを編集したり、新しい注文を作成したりしようとすると、オーサリングエクスペリエンスが低下します。 したがって、チャネルはセレクターに依存して、コンポーネントの様々なビューをレンダリングします。 オーサリング環境では、編集セレクターを使用して、カスタムチャネルのレンダリングをアクティベートします。

例：`http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html`

ユーザーは、編集時に URL にセレクターを追加する必要はありません。クライアントサイドのロジックは、レイヤースイッチイベントをリッスンしており、チャネルに専用のリソースタイプがある場合はセレクターを追加します *screens/core/components/channel*.

## コンポーネントのレンダリング {#rendering-components}

適切なオーサリングを有効にするには、コンポーネントで次の 2 つのレンダリングを提供する必要があります。

| **コンポーネント** | **レンディション** |
|---|---|
| *my-component/my-component.html* | 実稼動レンダリング |
| *my-component/edit.html* | 小さいビューでのレンダリングの編集 |

組み込みのコンポーネントでは、次のクライアントライブラリのカテゴリが使用されます。

| **コンポーネント** | **クライアントライブラリ** |
|---|---|
| *cq.screens.components.edit* | オーサリング時に読み込む必要がある CSS および JS |
| *cq.screens.components.production* | チャネルの実行時に読み込む必要がある CSS および JS |
| *cq.screens.components* | 共有 CSS および JS |

>[!NOTE]
>
>カスタムコンポーネントを開発する場合は、[AEM Screens のサンプルコンポーネントテンプレート](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)を使用してください。
