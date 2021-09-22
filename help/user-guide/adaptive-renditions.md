---
title: AEM Screensのアダプティブレンディション
description: このページでは、AEM Screensのアダプティブレンディションのアーキテクチャの概要と設定について説明します。
index: false
source-git-commit: 951fd38d5f69cdab1bf9b23f07b4e92075e87baf
workflow-type: tm+mt
source-wordcount: '552'
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


## オーサーとパブリッシュのセットアップ {#setup-author-publish}

アダプティブレンディションを使用する前に、オーサーとパブリッシュで次の推奨事項を考慮してください。

* レンディションマッピングは手動でレプリケートする必要があります。

* アセットレンディションは、デフォルトではレプリケートされません。 関連するすべてのアセットを手動でレプリケートする必要があります。

## レンディションマッピングルールの追加 {#add-rendition-mapping-rules}

1. マッピングルールを追加するには、**rendition-mapping**&#x200B;ノードの下にタイプ`nt:unstructured`のノードを作成する必要があります。

1. クエリ式を含む値を持つ式プロパティを追加します。

   >[!NOTE]
   >詳しくは、[メディアクエリ構文](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries)の使用を参照してください。

1. 式がtrueに評価される場合、選択するレンディション命名パターンを含む値を持つパターンプロパティを追加します。

   ![画像](/help/user-guide/assets/adaptive-renditions/mapping-rules4.png)


## 次の手順 {#next-steps}

レンディションを設定してアップロードすると、コンテンツ作成者としてアダプティブレンディションを使用し、大規模なネットワーク用のデバイスを移行して、AEM Screensチャネルでこの機能を利用できるようになります。 詳しくは、[アダプティブレンディションの使用](/help/user-guide/using-adaptive-renditions.md)を参照してください。
