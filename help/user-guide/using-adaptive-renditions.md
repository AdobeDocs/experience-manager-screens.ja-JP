---
title: AEM Screens でのアダプティブレンディションの使用
description: AEM Screensでアダプティブレンディションを使用する方法を説明します。
exl-id: e7f68ed4-73c3-492a-b33a-dd915ef1f8be
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 36%

---

# AEM Screens でのアダプティブレンディションの使用 {#adaptive-renditions}

## はじめに {#introduction}

アダプティブレンディションを使用すると、顧客定義のルールに基づいて、デバイスに最適なレンディションをデバイスで自動的に選択できます。これらのルールに基づいて、アセットの最も適切なレンディションをデバイスが自動的にダウンロードして再生するので、ユーザーはアセットの設計に専念できます。 *メイン* 経験。

## 目的 {#objective}

AEM Screens コンテンツ作成者は、すべてのコンテンツバリエーションを手動で作成しなくても、デバイス固有のアセットレンディションが自動的にダウンロードされて再生されるように設定できるようになりました。デベロッパーが rendition-mapping のプロパティとルールを追加したら、レンディションマッピングをアセットに適用し、AEM Screens チャネルに含める準備が整います。

>[!IMPORTANT]
>AEM Screens チャネルでアダプティブレンディションの使用を開始する前に、Adobeでは、この機能のアーキテクチャ概要と設定について学習することをお勧めします。 参照： [アダプティブレンディション：アーキテクチャ概要と設定](/help/user-guide/adaptive-renditions.md).

## チャネルでのアダプティブレンディションの使用 {#using-adaptive-renditions}

>[!NOTE]
>追加後 [rendition-mapping プロパティから Screens プロジェクトへ](/help/user-guide/adaptive-renditions.md#rendition-mapping-new) および [rendition-mapping ルール](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules)これで、コンテンツ作成者として、アセットにレンディションを適用する準備が整いました。

### アセットへのレンディションの適用 {#apply-renditions-assets}

Screens チャネルで使用するアセットにレンディションを適用するには、次の手順を実行します。

1. AEM インスタンスの&#x200B;**アセット**&#x200B;フォルダーに移動します。
1. サイネージディスプレイに適したバージョンのアセット（例：`seahorse.jpg`）を作成します。
1. レンディション命名パターン（例：`landscape`）を選択します。これは、**CRXDE Lite** で **pattern** プロパティに定義したものと同様です。参照： [レンディションマッピングルールの追加](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules) を参照してください。
1. クリック **レンディションを追加** にレンディションをアップロードします（下図を参照）。

   ![画像](/help/user-guide/assets/adaptive-renditions/manage-pub-asset2.png)

1. 名前を変更したアセットファイルを選択します。追加するレンディションには、（手順 3 で定義した）パターン（例：`seahorse-landscape.png`）が含まれている必要があります。
1. アセットを追加したら、アセットを選択し、 **公開を管理** アクションバーのを使用して、アセットを公開します。

   ![画像](/help/user-guide/assets/adaptive-renditions/manage-pub-asset1.png)

   >[!NOTE]
   >参照： [オンデマンドのコンテンツ更新](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/content-updates/on-demand-content) 公開の管理と、オーサーからパブリッシュ経由でデバイスにコンテンツの更新を配信する方法の詳細を説明します。

## 移行戦略 {#migration-strategy}

>[!IMPORTANT]
>Adobe大規模なネットワークの場合は、リスクを軽減するために移行を徐々に行うことをお勧めします。 この機能によってマニフェストとファイル保存形式に変更が加えられる可能性があるからです。 の追加 `sling:configRef` プロジェクト全体には、すべてのプレーヤーを機能パック 6.5.9 に更新する必要があります。一部のプレーヤーを更新した場合は、次を追加します `sling:configRef` すべてのプレーヤーが機能パック 6.5.9 に更新されているディスプレイ、ロケーション、チャネルフォルダーにのみ適用されます。

次の図は、大規模なネットワークの場合の移行戦略を示しています。

![画像](/help/user-guide/assets/adaptive-renditions/migration-strategy1.png)

この機能を有効にするには、少なくとも 1 つのマッピングルールを追加し、ディスプレイとチャネルのコンテキストで rendition-mapping 設定が解決可能であることを確認します。 移行するには、次の手順に従います。

1. [レンディションマッピングルール](/help/user-guide/adaptive-renditions.md)を追加します。
1. 新しいチャネルのフォルダーを作成し、rendition-mapping 設定を指す参照を追加します。
1. 古いチャネルに置き換わるチャネルを作成し、レンディションをアップロードします。
1. 新しいチャネルにディスプレイを再割り当てします。
1. rendition-mapping 設定を指す参照を、移行済みのディスプレイまたはロケーションに追加します。
1. 残りのすべてのチャネルとディスプレイについて、手順 3、4、5 を繰り返します。

   >[!NOTE]
   >移行が完了したら、必ずチャネル、ディスプレイ、ロケーションからすべての設定参照を削除し、設定参照を 1 つだけプロジェクトのコンテンツノードに追加します。
