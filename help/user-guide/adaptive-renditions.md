---
title: アダプティブレンディションのアーキテクチャ概要と設定
description: AEM Screens のアダプティブレンディションのアーキテクチャ概要と CRXDE Lite での設定について説明します。
exl-id: 0419b9c6-3c27-4a61-84ff-a6fe697e773f
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 100%

---

# アダプティブレンディション：アーキテクチャ概要と設定 {#adaptive-renditions}

## はじめに {#introduction}

アダプティブレンディションを使用すると、顧客定義のルールに基づいて、デバイスに最適なレンディションをデバイスで自動的にクリックできます。これらのルールに基づいて、アセットの最も適切なレンディションをデバイスが自動的にダウンロードして再生するので、お客様は&#x200B;*メイン*&#x200B;のエクスペリエンスの設計に専念できます。

## 目的 {#objective}

AEM Screens 開発者は、すべてのコンテンツバリエーションを手動で作成しなくても、デバイス固有のアセットレンディションが自動的にダウンロードされて再生されるように設定できるようになりました。コンテンツ作成者がこの機能を AEM Screens チャネルで使用できるようにするには、アダプティブレンディションを設定します。

## アーキテクチャの概要 {#architectural-overview}

アダプティブレンディションは、特定の命名規則に従ってアセットの複数のレンディションに名前を付けるという考えに基づいています。特定のレンディションを再生するかどうかは、想定される機能を持つデバイスでのみ解決できるメディアクエリ式を評価することで決定されます。

関連するレンディションの命名パターンを持つ機能により、縦長や横長などのレンディションマッピングルールが定義されます（下図を参照）。使用可能なすべての式を計算すると、Screens プレーヤーは、一致するルールに対応する命名パターンを収集します。これらのパターンは、レンディション名のパターンを探すことでシーケンスの再生時に正しいレンディションを見つけるために使用されます。

![画像](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## Screens プロジェクトへのレンディションマッピングプロパティの追加 {#rendition-mapping-new}

アダプティブレンディション機能を有効にするには、次のマッピングルールが存在し、チャネルとディスプレイのコンテキスト対応（CA）設定が解決可能である必要があります。

>[!NOTE]
>コンテキスト対応設定について詳しくは、[こちら](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html)を参照してください。

セットアップを設定するには、次の手順に従います。

1. **CRXDE Lite** に移動します。**rendition-mapping** 設定が `/conf/screens/sling:configs/rendition-mapping` に存在するかどうかを確認します（下図を参照）。

   >![画像](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

   >[!IMPORTANT]
   >最新の機能パック 202109 をインストールした場合は、CRXDE Lite の `/conf/screens/sling:configs/rendition-mapping` に **rendition-mapping** ノード構造が事前に設定されます。最新の機能パックについて詳しくは、[機能パック 202109 のリリースノート](/help/user-guide/release-notes-fp-202109.md)を参照してください。
   >既存プロジェクトの場合は、Screens プロジェクトに **rendition-mapping** 設定が関連付けられていることを確認します。詳しくは、[既存プロジェクトへのレンディションマッピングの追加](#rendition-mapping-existing)の節を参照してください。

### 既存プロジェクトへのレンディションマッピングプロパティの追加 {#rendition-mapping-existing}

1. **CRXDE Lite** に移動します。

1. `/conf/screens` を指す `sling:configRef` プロパティをプロジェクトのコンテンツノードに追加して、レンディションマッピングの関連付けを明示的に定義します（下図を参照）。

   ![画像](/help/user-guide/assets/adaptive-renditions/renditon-mapping2.png)


## レンディションマッピングルールの追加 {#add-rendition-mapping-rules}

レンディションマッピングの配下にノードを追加するには、次の手順に従います。

1. **CRXDE Lite** から `/conf/screens/sling:configs/rendition-mapping` のパスに移動します。
1. **rendition-mapping** の配下にノードを作成します。**rendition-mapping** を右クリックし、**作成**／**ノードを作成**&#x200B;をクリックします（下図を参照）。

   ![画像](/help/user-guide/assets/adaptive-renditions/add-node1.png)

1. **ノードを作成**&#x200B;ダイアログボックスで、マッピングルールの&#x200B;**名前**&#x200B;に「**rule1**」などと入力し、ノードの&#x200B;**タイプ**&#x200B;に「**`nt:unstructured`**」と入力します。「**OK**」をクリックします。

   ![画像](/help/user-guide/assets/adaptive-renditions/add-node2.png)


1. クエリ式を値とする expression プロパティを追加します。

   >[!NOTE]
   >詳しくは、[メディアクエリ構文の使用](https://developer.mozilla.org/ja-JP/docs/Web/CSS/CSS_media_queries/Using_media_queries)を参照してください。

   作成した「**rule1**」をクリックして、**名前**&#x200B;に「**expression**」と入力し、**値**&#x200B;に「**(orientation:landscape)**」と入力します（下図を参照）。「**追加**」をクリックします。

   ![画像](/help/user-guide/assets/adaptive-renditions/add-node3.png)

1. レンディション命名パターンを値とする pattern プロパティを追加します。

   >[!NOTE]
   >pattern プロパティで定義された値が新しいアセットレンディションと照合され、expression が true と評価された場合に選択されます。

   pattern プロパティを追加するには、作成した「**rule1**」をクリックして、**名前**&#x200B;に「**pattern**」と入力し、**値**&#x200B;に「**landscape**」と入力します（下図を参照）。「**追加**」をクリックします。

   ![画像](/help/user-guide/assets/adaptive-renditions/add-node4.png)

1. 「**すべて保存**」をクリックすると、**rendition-mapping** の下に作成したノードの下にプロパティが表示されます。

   ![画像](/help/user-guide/assets/adaptive-renditions/add-node5.png)

## 次の手順 {#next-steps}

rendition-mapping プロパティおよびルールを追加したら、コンテンツ作成者はアセットを設定できます。アダプティブレンディションを使用し、デバイスを大規模ネットワークに移行して、AEM Screens チャネルでこの機能を使用することもできます。詳しくは、[AEM Screens でのアダプティブレンディションの使用](/help/user-guide/using-adaptive-renditions.md)を参照してください。
