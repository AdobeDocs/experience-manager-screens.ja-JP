---
title: アダプティブレンディションのアーキテクチャの概要と設定
description: このページでは、AEM ScreensのアダプティブレンディションのCRXDE Liteにおけるアーキテクチャの概要と設定について説明します。
source-git-commit: d30426f871d319bcfacb7a832479b87400e18fc2
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 3%

---


# アダプティブレンディション：アーキテクチャの概要と設定 {#adaptive-renditions}

## はじめに {#introduction}

アダプティブレンディションを使用すると、デバイスは、顧客定義のルールに基づいて、デバイスに最適なレンディションを自動的に選択できます。 これらのルールに基づいて、デバイスはアセットの最も適切なレンディションを自動的にダウンロードして再生し、お客様は&#x200B;*メイン*&#x200B;エクスペリエンスのデザインに専念できます。

## 目的 {#objective}

AEM Screens開発者は、すべてのコンテンツバリエーションを手動で作成することなく、デバイス固有のアセットレンディションをダウンロードして自動的に再生するように設定できるようになりました。 コンテンツ作成者がこの機能をAEM Screensチャネルで使用するには、アダプティブレンディションを設定する必要があります。

## アーキテクチャの概要 {#architectural-overview}

アダプティブレンディションは、特定の命名規則に従って複数のアセットレンディションの名前を付けるという考えに基づいています。 特定のレンディションを再生するかどうかは、期待される機能を持つデバイス上でのみ解決できるメディアクエリ式を評価することで決定されます。

関連するレンディション命名パターンを持つ機能は、縦や横などのレンディションマッピングルールを定義します（下図を参照）。 使用可能なすべての式を計算した後、Screensプレーヤーは、一致するルールに対応する命名パターンを収集します。 パターンは、シーケンスの再生中にレンディション名のパターンを探すことで、正しいレンディションを見つけるために使用されます。

![画像](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## Screensプロジェクトへのレンディションマッピングプロパティの追加 {#rendition-mapping-new}

アダプティブレンディション機能を有効にするには、次のマッピングルールが存在し、チャネルとディスプレイに対してコンテキスト対応(CA)設定を解決できる必要があります。

>[!NOTE]
>コンテンツ対応設定の詳細については、[こちら](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html)を参照してください。

次の手順に従って、設定を指定します。

1. **CRXDE Lite**&#x200B;に移動します。 次の図に示すように、 **rendition-mapping**&#x200B;設定が`/conf/screens/sling:configs/rendition-mapping`に存在するかどうかを確認します。

   >![画像](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

   >[!IMPORTANT]
   >最新の機能パック202109をインストールした場合は、CRXDE Liteの`/conf/screens/sling:configs/rendition-mapping`に&#x200B;**rendition-mapping**&#x200B;ノード構造が事前に設定されています。 最新の機能パックの詳細については、[機能パック202109](/help/user-guide/release-notes-fp-202109.md)のリリースノートを参照してください。
   >既存のプロジェクトの場合、Screensプロジェクトに&#x200B;**rendition-mapping**&#x200B;設定が関連付けられていることを確認します。 詳しくは、 [既存のプロジェクトへのレンディションマッピングの追加](#rendition-mapping-existing)の節を参照してください。

### 既存のプロジェクトへのレンディションマッピングプロパティの追加 {#rendition-mapping-existing}

1. **CRXDE Lite**&#x200B;に移動します。

1. 次の図に示すように、`/conf/screens`を指す`sling:configRef`プロパティをプロジェクトコンテンツノードに追加して、レンディションマッピングの関連付けを明示的に定義します。

   ![画像](/help/user-guide/assets/adaptive-renditions/renditon-mapping2.png)


## レンディションマッピングルールの追加 {#add-rendition-mapping-rules}

以下の手順に従って、「レンディションマッピング」の下にノードを追加します。

1. **CRXDE Lite**&#x200B;からこのパス`/conf/screens/sling:configs/rendition-mapping`に移動します。

1. **rendition-mapping**&#x200B;の下にノードを作成します。 **rendition-mapping**&#x200B;を右クリックし、**Create** —> **Create Node**&#x200B;をクリックします（下図を参照）。

   ![画像](/help/user-guide/assets/adaptive-renditions/add-node1.png)

1. **rule1**&#x200B;や、**Create Node**&#x200B;ダイアログボックスで、**Name**&#x200B;を&#x200B;**Type**&#x200B;を&#x200B;**nt:unstructured**&#x200B;として入力します。 「**OK**」をクリックします。

   ![画像](/help/user-guide/assets/adaptive-renditions/add-node2.png)


1. クエリ式を含む値を持つ式プロパティを追加する必要があります。

   >[!NOTE]
   >詳しくは、[メディアクエリ構文](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries)の使用を参照してください。

   作成した&#x200B;**ルール1**&#x200B;をクリックし、次に示すように、**名前**&#x200B;に&#x200B;**式**&#x200B;を入力し、**値**&#x200B;に&#x200B;**(orientation:landscape)**&#x200B;を入力します。 「**追加**」をクリックします。

   ![画像](/help/user-guide/assets/adaptive-renditions/add-node3.png)

1. レンディションの命名パターンを含む値を使用して、パターンプロパティを追加します。

   >[!NOTE]
   >式がtrueと評価される場合、パターンプロパティで定義された値が新しいアセットレンディションと照合され、値が選択されます。

   パターンプロパティを追加するには、作成した&#x200B;**rule1**&#x200B;をクリックし、次に示すように、**名前**&#x200B;に&#x200B;**パターン**&#x200B;を、**値**&#x200B;に&#x200B;**横**&#x200B;を入力します。 「**追加**」をクリックします。

   ![画像](/help/user-guide/assets/adaptive-renditions/add-node4.png)

1. 「**すべて保存**」をクリックすると、**rendition-mapping**&#x200B;で作成したノードの下にプロパティが表示されます。

   ![画像](/help/user-guide/assets/adaptive-renditions/add-node5.png)


## 次の手順 {#next-steps}

レンディションマッピングのプロパティとルールをコンテンツ作成者として追加したら、アセットでアダプティブレンディションを使用するように設定し、大規模なネットワーク用のデバイスを移行して、AEM Screensチャネルでこの機能を利用できます。
