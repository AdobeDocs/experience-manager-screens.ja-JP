---
title: アダプティブレンディションのアーキテクチャ概要と設定
description: AEM ScreensのアダプティブレンディションCRXDE Liteにおけるアーキテクチャ概要と設定について説明します。
exl-id: 0419b9c6-3c27-4a61-84ff-a6fe697e773f
source-git-commit: 97084aee861e152abcc5f117a2a4759dced038cc
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 43%

---

# アダプティブレンディション：アーキテクチャ概要と設定 {#adaptive-renditions}

## はじめに {#introduction}

アダプティブレンディションを使用すると、顧客定義のルールに基づいて、デバイスに最適なレンディションをデバイスで自動的に選択できます。これらのルールに基づいて、アセットの最も適切なレンディションをデバイスが自動的にダウンロードして再生するので、ユーザーはアセットの設計に専念できます。 *メイン* 経験。

## 目的 {#objective}

AEM Screens 開発者は、すべてのコンテンツバリエーションを手動で作成しなくても、デバイス固有のアセットレンディションが自動的にダウンロードされて再生されるように設定できるようになりました。コンテンツ作成者がこの機能をAEM Screens チャネルで使用するには、アダプティブレンディションを設定しておく必要があります。

## アーキテクチャの概要 {#architectural-overview}

アダプティブレンディションは、特定の命名規則に従ってアセットに複数のレンディションに名前を付けるという考えに基づいています。 特定のレンディションを再生するかどうかは、想定される機能を持つデバイスでのみ解決できるメディアクエリ式を評価することで決定されます。

関連するレンディションの命名パターンを用意できるので、縦長や横長などのレンディションマッピングルールを定義できます（下図を参照）。 使用可能なすべての式を計算すると、Screens プレーヤーは、一致するルールに対応する命名パターンを収集します。 これらのパターンは、レンディション名のパターンを探すことでシーケンスの再生時に正しいレンディションを見つけるために使用されます。

![画像](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## Screens プロジェクトへのレンディションマッピングプロパティの追加 {#rendition-mapping-new}

アダプティブレンディション機能を有効にするには、次のマッピングルールが存在し、チャネルとディスプレイのコンテキスト対応（CA）設定が解決可能である必要があります。

>[!NOTE]
>コンテキスト対応設定について詳しくは、[こちら](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html)を参照してください。

セットアップを設定するには、次の手順に従います。

1. **CRXDE Lite** に移動します。**rendition-mapping** 設定が `/conf/screens/sling:configs/rendition-mapping` に存在するかどうかを確認します（下図を参照）。

   >![画像](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

   >[!IMPORTANT]
   >最新の機能パック 202109 をインストールした場合は、 **rendition-mapping** で事前入力されたノード構造 `/conf/screens/sling:configs/rendition-mapping` CRXDE Liteで。 最新の機能パックについて詳しくは、[機能パック 202109 のリリースノート](/help/user-guide/release-notes-fp-202109.md)を参照してください。
   >既存プロジェクトの場合は、Screens プロジェクトに **rendition-mapping** 設定が関連付けられていることを確認します。参照： [既存プロジェクトへのレンディションマッピングの追加](#rendition-mapping-existing) を参照してください。

### 既存プロジェクトへのレンディションマッピングプロパティの追加 {#rendition-mapping-existing}

1. **CRXDE Lite** に移動します。

1. を追加して、rendition-mapping 関連付けを明示的に定義します。 `sling:configRef` を指すプロパティ `/conf/screens` プロジェクトのコンテンツノードに移動します（下図を参照）。

   ![画像](/help/user-guide/assets/adaptive-renditions/renditon-mapping2.png)


## レンディションマッピングルールの追加 {#add-rendition-mapping-rules}

レンディションマッピングの配下にノードを追加するには、次の手順に従います。

1. **CRXDE Lite** から `/conf/screens/sling:configs/rendition-mapping` のパスに移動します。
1. **rendition-mapping** の配下にノードを作成します。右クリック **rendition-mapping** をクリックして、 **作成** > **ノードを作成**&#x200B;を参照してください（下図を参照）。

   ![画像](/help/user-guide/assets/adaptive-renditions/add-node1.png)

1. を入力 **名前** などのマッピングルールの場合 **rule1** およびノード **タイプ** as **`nt:unstructured`** 。対象： **ノードを作成** ダイアログが表示されます。 「**OK**」をクリックします。

   ![画像](/help/user-guide/assets/adaptive-renditions/add-node2.png)


1. クエリ式を値とする expression プロパティを追加します。

   >[!NOTE]
   >参照： [メディアクエリの構文の使用](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_media_queries/Using_media_queries) を参照してください。

   クリック **rule1** を作成し、を入力します **式** 。対象： **名前** および **（方向：横）** 。対象： **値**&#x200B;を参照してください。 「**追加**」をクリックします。

   ![画像](/help/user-guide/assets/adaptive-renditions/add-node3.png)

1. レンディション命名パターンを値とする pattern プロパティを追加します。

   >[!NOTE]
   >pattern プロパティで定義された値は新しいアセットレンディションと照合され、式が true と評価された場合は選択されます。

   pattern プロパティを追加するには、以下をクリックします。 **rule1** を作成し、を入力します **pattern** 。対象： **名前** および **横** 。対象： **値**&#x200B;を参照してください。 「**追加**」をクリックします。

   ![画像](/help/user-guide/assets/adaptive-renditions/add-node4.png)

1. クリック **すべて保存** 次に、作成したノードの下のプロパティに注目してください **rendition-mapping**.

   ![画像](/help/user-guide/assets/adaptive-renditions/add-node5.png)

## 次の手順 {#next-steps}

rendition-mapping プロパティおよびルールを追加したら、コンテンツ作成者はアセットを設定できます。 これを行うには、アダプティブレンディションを使用し、また、この機能をAEM Screens チャネルで使用するために、デバイスを大規模なネットワーク用に移行します。 参照： [AEM Screensでのアダプティブレンディションの使用](/help/user-guide/using-adaptive-renditions.md) を参照してください。
