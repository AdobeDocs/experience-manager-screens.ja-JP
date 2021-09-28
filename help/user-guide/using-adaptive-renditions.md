---
title: AEM Screensでのアダプティブレンディションの使用
description: このページでは、AEM Screensでのアダプティブレンディションの使用方法について説明します。
source-git-commit: 6d9dab9fd59289aafdb688682fea47589d3ec873
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 1%

---


# AEM Screensでのアダプティブレンディションの使用 {#adaptive-renditions}

## はじめに {#introduction}

アダプティブレンディションを使用すると、デバイスは、顧客定義のルールに基づいて、デバイスに最適なレンディションを自動的に選択できます。 これらのルールに基づいて、デバイスはアセットの最も適切なレンディションを自動的にダウンロードして再生し、お客様は&#x200B;*メイン*&#x200B;エクスペリエンスのデザインに専念できます。

## 目的 {#objective}

AEM Screensコンテンツ作成者は、すべてのコンテンツバリエーションを手動で作成することなく、デバイス固有のアセットレンディションをダウンロードして自動的に再生するように設定できるようになりました。
開発者がレンディションマッピングのプロパティとルールを追加したら、レンディションマッピングをアセットに適用し、その後AEM Screensチャネルに含める準備が整います。

>[!IMPORTANT]
>アダプティブレンディションの使用を開始する前に、AEM Screensチャネルで、この機能のアーキテクチャの概要と設定について学ぶことをお勧めします。 [アダプティブレンディションを参照してください。アーキテクチャの概要と設定](/help/user-guide/adaptive-renditions.md)を参照してください。

## チャネルでのアダプティブレンディションの使用 {#using-adaptive-renditions}

>[!NOTE]
>[レンディションマッピングプロパティをScreensプロジェクト](/help/user-guide/adaptive-renditions.md#rendition-mapping-new)および[レンディションマッピングルール](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules)に追加すると、コンテンツ作成者として、アセットにレンディションを適用する準備が整います。

### アセットへのレンディションの適用 {#apply-renditions-assets}

次の手順に従って、ツアー画面チャネルで使用するアセットにレンディションを適用します。

1. AEMインスタンスの&#x200B;**Assets**&#x200B;フォルダーに移動します。

1. 例えば`seahorse.jpg`のように、サイネージの表示に適したバージョンのアセットを作成します。

1. レンディションの命名パターン（例：`landscape`）を選択します。これは、**CRXDE Lite**&#x200B;の&#x200B;**pattern**&#x200B;プロパティで定義したものと同様です。 詳しくは、[レンディションマッピングルールの追加](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules)を参照してください。

1. 「 **レンディションを追加** 」をクリックして、レンディションをアップロードします（下図を参照）。

   ![画像](/help/user-guide/assets/adaptive-renditions/manage-pub-asset2.png)

1. 名前を変更したアセットファイルを選択します。 追加するレンディションには、（手順3で定義した）パターン（例：`seahorse-landscape.png`）が含まれている必要があります。

1. アセットを追加したら、アセットを選択し、アクションバーの「**公開を管理**」をクリックして、アセットを公開します。

   ![画像](/help/user-guide/assets/adaptive-renditions/manage-pub-asset1.png)

   >[!NOTE]
   >公開の管理と、オーサーからパブリッシュ経由でデバイスにコンテンツの更新を配信する方法について詳しくは、 [オンデマンドコンテンツの更新](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/authoring/content-updates/on-demand-content.html?lang=en)を参照してください。


## 移行戦略 {#migration-strategy}

>[!IMPORTANT]
>大規模なネットワークの場合は、機能によってマニフェストおよびファイルストレージ形式に変更が加えられるので、リスクを軽減するために、移行を徐々におこなうことをお勧めします。 プロジェクト全体に`sling:configRef`を追加するには、すべてのプレーヤーを機能パック6.5.9に更新する必要があります。一部のプレーヤーを更新した場合は、`sling:configRef`を、すべてのプレーヤーを機能パック6.5.9に更新したディスプレイ、場所、チャネルフォルダーにのみ追加します。

次の図は、大規模なネットワークの移行戦略を示しています。

![画像](/help/user-guide/assets/adaptive-renditions/migration-strategy1.png)

この機能を有効にするには、少なくとも1つのマッピングルールを追加し、ディスプレイとチャネルのコンテキストでレンディションマッピング設定が解決可能であることを確認します。 移行するには、次の手順に従います。

1. [レンディションマッピングルール](/help/user-guide/adaptive-renditions.md)を追加します。
1. 新しいチャネル用のフォルダーを作成し、レンディションマッピング設定を指す参照を追加します。
1. 古いチャネルを置き換える新しいチャネルを作成し、レンディションをアップロードします。
1. ディスプレイを新しいチャネルに再割り当てします。
1. レンディションマッピング設定を指す、移行済みのディスプレイまたは場所への参照を追加します。
1. 残りのすべてのチャネルとディスプレイに対して、手順3、4、5を繰り返します。

   >[!NOTE]
   >移行が完了したら、チャネル、ディスプレイ、場所からすべての設定参照を削除し、1つの設定参照をプロジェクトコンテンツノードに追加します。

