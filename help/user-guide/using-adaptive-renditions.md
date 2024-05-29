---
title: AEM Screens でのアダプティブレンディションの使用
description: AEM Screens でアダプティブレンディションを使用する方法について説明します。
exl-id: e7f68ed4-73c3-492a-b33a-dd915ef1f8be
source-git-commit: 2a51258ffe7b969962378dcd0558bd001b616ba1
workflow-type: ht
source-wordcount: '541'
ht-degree: 100%

---

# AEM Screens でのアダプティブレンディションの使用 {#adaptive-renditions}

## はじめに {#introduction}

アダプティブレンディションを使用すると、顧客定義のルールに基づいて、デバイスに最適なレンディションをデバイスが自動的にクリックできます。これらのルールに基づいて、アセットの最適なレンディションをデバイスが自動的にダウンロードして再生します。これにより、顧客は&#x200B;*メイン*&#x200B;エクスペリエンスの設計に専念できます。

## 目的 {#objective}

AEM Screens コンテンツ作成者は、すべてのコンテンツバリエーションを手動で作成することなく、デバイス固有のアセットレンディションの自動ダウンロードおよび再生を設定できるようになりました。
開発者がレンディションマッピングのプロパティとルールを追加したら、レンディションマッピングをアセットに適用し、アセットを AEM Screens チャネルに含めることができます。

>[!IMPORTANT]
>AEM Screens チャネルでのアダプティブレンディションの使用を開始する前に、この機能のアーキテクチャ概要と設定について理解しておくことをお勧めします。[アダプティブレンディション：アーキテクチャ概要と設定](/help/user-guide/adaptive-renditions.md)を参照してください。

## チャネルでのアダプティブレンディションの使用 {#using-adaptive-renditions}

>[!NOTE]
>[レンディションマッピングプロパティを Screens プロジェクト](/help/user-guide/adaptive-renditions.md#rendition-mapping-new)および[レンディションマッピングルール](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules)に追加したら、コンテンツ作成者としてアセットにレンディションを適用できます。

### アセットへのレンディションの適用 {#apply-renditions-assets}

Tour Screens チャネルで使用するアセットにレンディションを適用するには、次の手順を実行します。

1. AEM インスタンスの **Assets** フォルダーに移動します。
1. サイネージディスプレイに適したアセットのバージョン（例：`seahorse.jpg`）を作成します。
1. レンディション命名パターン（例：`landscape`）を選択します。これは、**CRXDE Lite** の **pattern** プロパティで定義したものと同様です。詳しくは、[レンディションマッピングルールの追加](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules)を参照してください。
1. 「**レンディションを追加**」をクリックして、下図のようにレンディションをアップロードします。

   ![画像](/help/user-guide/assets/adaptive-renditions/manage-pub-asset2.png)

1. 名前を変更したアセットファイルをクリックします。追加するレンディションには、（手順 3 で定義した）パターン（例：`seahorse-landscape.png`）が含まれている必要があります。
1. アセットを追加したら、そのアセットをクリックし、アクションバーの「**公開を管理**」をクリックしてアセットを公開します。

   ![画像](/help/user-guide/assets/adaptive-renditions/manage-pub-asset1.png)

   >[!NOTE]
   >公開の管理と、オーサーから公開経由でデバイスにコンテンツの更新を配信する方法について詳しくは、[オンデマンドのコンテンツ更新](https://experienceleague.adobe.com/ja/docs/experience-manager-screens/user-guide/authoring/content-updates/on-demand-content)を参照してください。

## 移行戦略 {#migration-strategy}

>[!IMPORTANT]
>大規模なネットワークの場合は、リスクを軽減するために移行を段階的に行うことをお勧めします。この機能によってマニフェストとファイルストレージ形式に変更が加えられる可能性があるためです。プロジェクト全体に `sling:configRef` を追加するには、すべてのプレーヤーを機能パック 6.5.9. にアップデートする必要があります。一部のプレーヤーをアップデートした場合は、すべてのプレーヤーが機能パック 6.5.9. にアップデートされているディスプレイ、ロケーション、チャネルフォルダーにのみ `sling:configRef` を追加します。

次の図は、大規模なネットワークの場合の移行戦略を示しています。

![画像](/help/user-guide/assets/adaptive-renditions/migration-strategy1.png)

この機能を有効にするには、少なくとも 1 つのマッピングルールを追加し、ディスプレイとチャネルのコンテキストでレンディションマッピング設定が解決可能であることを確認します。移行するには、次の手順に従います。

1. [レンディションマッピングルール](/help/user-guide/adaptive-renditions.md)を追加します。
1. 新しいチャネルのフォルダーを作成し、レンディションマッピング設定を指す参照を追加します。
1. 古いチャネルに取って代わる新しいチャネルを作成し、レンディションをアップロードします。
1. 新しいチャネルにディスプレイを再割り当てします。
1. レンディションマッピング設定を指す、移行済みのディスプレイまたは場所に参照を追加します。
1. 残りのすべてのチャネルとディスプレイについて、手順 3、4、5 を繰り返します。

   >[!NOTE]
   >移行が完了したら、必ずチャネル、ディスプレイ、ロケーションからすべての設定参照を削除し、設定参照を 1 つだけプロジェクトのコンテンツノードに追加します。
