---
title: アダプティブレンディションのアーキテクチャの概要と設定
description: このページでは、AEM ScreensのアダプティブレンディションのCRXDE Liteのアーキテクチャの概要と設定について説明します。
exl-id: 0419b9c6-3c27-4a61-84ff-a6fe697e773f
source-git-commit: e5da55eeb5da3d0ef9f21bd47bfec75d660a6a1e
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 10%

---

# アダプティブレンディション：アーキテクチャの概要と設定 {#adaptive-renditions}

## はじめに {#introduction}

アダプティブレンディションを使用すると、顧客定義のルールに基づいて、デバイスに最適なレンディションをデバイスで自動的に選択できます。これらのルールに基づいて、アセットの最も適切なレンディションをデバイスが自動的にダウンロードして再生するので、ユーザーは&#x200B;*メイン*&#x200B;のエクスペリエンスの設計に専念できます。

## 目的 {#objective}

AEM Screens開発者は、すべてのコンテンツバリエーションを手動で作成する必要なく、デバイス固有のアセットレンディションをダウンロードして自動的に再生するように設定できるようになりました。 コンテンツ作成者がこの機能をAEM Screensチャネルで使用するには、アダプティブレンディションを設定する必要があります。

## アーキテクチャの概要 {#architectural-overview}

アダプティブレンディションは、特定の命名規則に従って複数のアセットレンディションに名前を付けるという考えに基づいています。 特定のレンディションを再生するかどうかは、期待される機能を持つデバイスでのみ解決できるメディアクエリ式を評価することで決定されます。

関連するレンディションの命名パターンを持つ機能は、次の図に示すように、レンディションマッピングルール（縦長や横長など）を定義します。 使用可能なすべての式を計算すると、Screens プレーヤーは一致するルールに対応する命名パターンを収集します。 パターンは、シーケンスの再生中に、レンディション名のパターンを探すことで正しいレンディションを見つけるために使用されます。

![画像](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## Screens プロジェクトへのレンディションマッピングプロパティの追加 {#rendition-mapping-new}

アダプティブレンディション機能を有効にするには、次のマッピングルールが存在し、チャネルとディスプレイに対してコンテキスト対応 (CA) 設定を解決できる必要があります。

>[!NOTE]
>コンテンツ対応設定の詳細については、[ こちら ](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html) を参照してください。

次の手順に従って、設定を行います。

1. **CRXDE Lite** に移動します。 **rendition-mapping** 設定が `/conf/screens/sling:configs/rendition-mapping` に存在するかどうかを確認します（下図を参照）。

   >![画像](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

   >[!IMPORTANT]
   >最新の機能パック202109をインストールした場合は、CRXDE Liteの `/conf/screens/sling:configs/rendition-mapping` に **rendition-mapping** ノード構造が事前に設定されています。 最新の機能パックの詳細については、[ 機能パック202109](/help/user-guide/release-notes-fp-202109.md) のリリースノートを参照してください。
   >既存のプロジェクトの場合は、Screens プロジェクトに **rendition-mapping** 設定が関連付けられていることを確認します。 詳しくは、[ 既存のプロジェクトへのレンディションマッピングの追加 ](#rendition-mapping-existing) の節を参照してください。

### 既存のプロジェクトへのレンディションマッピングプロパティの追加 {#rendition-mapping-existing}

1. **CRXDE Lite** に移動します。

1. 次の図に示すように、 `/conf/screens` を指す `sling:configRef` プロパティをプロジェクトコンテンツノードに追加して、レンディションマッピングの関連付けを明示的に定義します。

   ![画像](/help/user-guide/assets/adaptive-renditions/renditon-mapping2.png)


## レンディションマッピングルールの追加 {#add-rendition-mapping-rules}

以下の手順に従って、「レンディションマッピング」の下にノードを追加します。

1. **CRXDE Lite** からこのパス `/conf/screens/sling:configs/rendition-mapping` に移動します。

1. **rendition-mapping** の下にノードを作成します。 **rendition-mapping** を右クリックし、**Create** —> **Create Node** をクリックします（下の図を参照）。

   ![画像](/help/user-guide/assets/adaptive-renditions/add-node1.png)

1. **rule1** や **Type** は **nt:unstructured** のようなマッピング規則の **Name** を **Create Node** ダイアログボックスに入力します。 「**OK**」をクリックします。

   ![画像](/help/user-guide/assets/adaptive-renditions/add-node2.png)


1. クエリ式を含む値を持つ式プロパティを追加する必要があります。

   >[!NOTE]
   >詳しくは、[ メディアクエリ構文 ](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries) の使用を参照してください。

   作成した **rule1** をクリックし、次に示すように、**名前** に **式** を入力し、**値** に **(orientation:landscape)** を入力します。 「**追加**」をクリックします。

   ![画像](/help/user-guide/assets/adaptive-renditions/add-node3.png)

1. レンディションの命名パターンを含む値を使用して、 pattern プロパティを追加します。

   >[!NOTE]
   >パターンプロパティで定義された値が新しいアセットレンディションと照合され、式が true と評価された場合に選択されます。

   パターンプロパティを追加するには、作成した **rule1** をクリックし、次に示すように、**名前** に **pattern** を、**値** に **landscape** を入力します。 「**追加**」をクリックします。

   ![画像](/help/user-guide/assets/adaptive-renditions/add-node4.png)

1. 「**すべて保存**」をクリックすると、**rendition-mapping** の下で作成したノードの下にプロパティが表示されます。

   ![画像](/help/user-guide/assets/adaptive-renditions/add-node5.png)


## 次の手順 {#next-steps}

レンディションマッピングのプロパティとルールを追加したら、コンテンツ作成者は、アダプティブレンディションを使用するようにアセットを設定し、大規模なネットワーク用にデバイスを移行して、AEM Screensチャネルでこの機能を利用できます。 詳しくは、[AEM Screensでのアダプティブレンディションの使用 ](/help/user-guide/using-adaptive-renditions.md) を参照してください。
