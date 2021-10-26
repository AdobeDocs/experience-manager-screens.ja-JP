---
title: AEM Screens でのアダプティブレンディションの使用
description: このページでは、AEM Screens でアダプティブレンディションを使用する方法について説明します。
exl-id: e7f68ed4-73c3-492a-b33a-dd915ef1f8be
source-git-commit: cd26f77b9b41a5854aaa1f936abed3b410533684
workflow-type: ht
source-wordcount: '561'
ht-degree: 100%

---

# AEM Screens でのアダプティブレンディションの使用 {#adaptive-renditions}

## はじめに {#introduction}

アダプティブレンディションを使用すると、顧客定義のルールに基づいて、デバイスに最適なレンディションをデバイスで自動的に選択できます。これらのルールに基づいて、アセットの最も適切なレンディションをデバイスが自動的にダウンロードして再生するので、ユーザーは&#x200B;*メイン*&#x200B;のエクスペリエンスの設計に専念できます。

## 目的 {#objective}

AEM Screens コンテンツ作成者は、すべてのコンテンツバリエーションを手動で作成しなくても、デバイス固有のアセットレンディションが自動的にダウンロードされて再生されるように設定できるようになりました。開発者がレンディションマッピングのプロパティとルールを追加したら、レンディションマッピングをアセットに適用したあと、アセットを AEM Screens チャネルに含めることができます。

>[!IMPORTANT]
>AEM Screens チャネルでのアダプティブレンディションの使用を開始する前に、この機能のアーキテクチャ概要と設定について理解しておくことをお勧めします。詳しくは、[アダプティブレンディション：アーキテクチャ概要と設定](/help/user-guide/adaptive-renditions.md)を参照してください。

## チャネルでのアダプティブレンディションの使用 {#using-adaptive-renditions}

>[!NOTE]
>[レンディションマッピングプロパティを Screens プロジェクトに追加](/help/user-guide/adaptive-renditions.md#rendition-mapping-new)し[レンディションマッピングルールを追加](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules)したら、コンテンツ作成者としてアセットにレンディションを適用することができます。

### アセットへのレンディションの適用 {#apply-renditions-assets}

次の手順に従って、Screens チャネルで使用するレンディションをアセットに適用するには、次の手順に従います。

1. AEM インスタンスの&#x200B;**アセット**&#x200B;フォルダーに移動します。

1. サイネージディスプレイに適したバージョンのアセット（例：`seahorse.jpg`）を作成します。

1. レンディション命名パターン（例：`landscape`）を選択します。これは、**CRXDE Lite** で **pattern** プロパティに定義したものと同様です。詳しくは、[レンディションマッピングルールの追加](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules)を参照してください。

1. 「**レンディションを追加**」をクリックして、レンディションをアップロードします（下図を参照）。

   ![画像](/help/user-guide/assets/adaptive-renditions/manage-pub-asset2.png)

1. 名前を変更したアセットファイルを選択します。追加するレンディションには、（手順 3 で定義した）パターン（例：`seahorse-landscape.png`）が含まれている必要があります。

1. アセットを追加したら、そのアセットを選択し、アクションバーの「**公開を管理**」をクリックして、アセットを公開します。

   ![画像](/help/user-guide/assets/adaptive-renditions/manage-pub-asset1.png)

   >[!NOTE]
   >公開の管理と、オーサーからパブリッシュ経由でデバイスにコンテンツの更新を配信する方法について詳しくは、[オンデマンドのコンテンツ更新](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/authoring/content-updates/on-demand-content.html?lang=ja)を参照してください。


## 移行戦略 {#migration-strategy}

>[!IMPORTANT]
>この機能によってマニフェストとファイルストレージ形式に変更が加えられるので、大規模なネットワークの場合は、リスクを軽減するために、徐々に移行を行うことをお勧めします。プロジェクト全体に `sling:configRef` を追加するには、すべてのプレーヤーを機能パック 6.5.9 に更新する必要があります。一部のプレーヤーを更新した場合は、すべてのプレーヤーが機能パック 6.5.9 に更新されているディスプレイ、ロケーション、チャネルフォルダーにのみ `sling:configRef` を追加します。

次の図は、大規模なネットワークの場合の移行戦略を示しています。

![画像](/help/user-guide/assets/adaptive-renditions/migration-strategy1.png)

この機能を有効にするには、少なくとも 1 つのマッピングルールを追加し、ディスプレイとチャネルのコンテキストでレンディションマッピング設定が解決可能であることを確認します。移行するには、次の手順に従います。

1. [レンディションマッピングルール](/help/user-guide/adaptive-renditions.md)を追加します。
1. 新しいチャネルのフォルダーを作成し、レンディションマッピング設定を指す参照を追加します。
1. 古いチャネルに取って代わる新しいチャネルを作成し、レンディションをアップロードします。
1. 新しいチャネルにディスプレイを再割り当てします。
1. レンディションマッピング設定を指す参照を、移行済みのディスプレイまたはロケーションに追加します。
1. 残りのすべてのチャネルとディスプレイについて、手順 3、4、5 を繰り返します。

   >[!NOTE]
   >移行が完了したら、必ずチャネル、ディスプレイ、ロケーションからすべての設定参照を削除し、設定参照を 1 つだけプロジェクトのコンテンツノードに追加します。
