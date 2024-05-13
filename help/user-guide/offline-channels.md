---
title: オフラインチャネル
description: AEM Screens Player がコンテンツ同期テクノロジーを使用してチャネルをオフラインサポートする方法について説明します。
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 5ad1046f-8b64-490b-9966-ce9008180d54
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 67%

---

# オフラインチャネル {#offline-channels}

Screens Player では、以下を使用してチャネルをオフラインサポートします。 ***ContentSync*** 技術。

プレーヤーは、解凍したコンテンツを提供するためにローカルの HTTP サーバーを使用します。

チャネルが実行されるように設定されている場合 *オンライン*&#x200B;プレーヤーは、AEM サーバーにアクセスしてチャネルリソースを提供します。 ただし、チャネルが実行されるように設定されている場合は、 *オフライン*&#x200B;プレーヤーは、ローカル http サーバーからチャネルリソースを提供します。

プロセスのワークフローは次のとおりです。

1. 目的のページを解析します。
1. 関連するすべてのアセットを収集します。
1. すべてを zip ファイルにパッケージ化します。
1. zip ファイルをダウンロードし、ローカルで抽出します。
1. コンテンツのローカルコピーを表示します。

## 更新ハンドラー {#update-handlers}

***ContentSync*** は、更新ハンドラーを使用して、特定のプロジェクトに必要なすべてのページとアセットを解析および収集します。AEM Screens では、次の更新ハンドラーが使用されます。

### 共通オプション {#common-options}

* *type*：使用する更新ハンドラーのタイプ
* *path*：リソースのパス
* *[targetRootDirectory]*：zip ファイル内のターゲットフォルダー

<table>
 <tbody>
  <tr>
   <td><strong>タイプ</strong></td> 
   <td><strong>説明</strong></td> 
   <td><strong>Options</strong></td> 
  </tr>
  <tr>
   <td><code>channels</code></td> 
   <td>チャネルを収集します</td> 
   <td>extension：収集するリソースの拡張子<br />[pathSuffix='']：チャネルパスに追加するサフィックス<br /> </td> 
  </tr>
  <tr>
   <td><code>clientlib</code></td> 
   <td>指定されたクライアントライブラリを収集します</td> 
   <td>[extension='']：css か js のどちらか（前者のみか後者のみを収集するために指定）</td> 
  </tr>
  <tr>
   <td><code>assetrenditions</code></td> 
   <td>アセットレンディションを収集します</td> 
   <td>[renditions=[]]：収集するレンディションのリスト。デフォルトで元のレンディションに設定</td> 
  </tr>
  <tr>
   <td><code>copy</code></td> 
   <td>指定された構造をパスからコピーします</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### ContentSync 設定のテスト {#testing-contentsync-configuration}

ContentSync 設定をテストするには、以下の手順に従います。

1. `https://localhost:4502/libs/cq/contentsync/content/console.html` を開きます。
1. リストで設定をクリックします
1. 「キャッシュをクリア」をクリックします。
1. 「キャッシュを更新」をクリックします。
1. 「すべてダウンロード」をクリックします。
1. zip ファイルを解凍します。
1. 解凍したフォルダーでローカルサーバーを起動します。
1. 開始ページを開き、アプリのステータスを確認します。

## チャネルのオフライン設定の有効化 {#enabling-offline-config-for-a-channel}

チャネルのオフライン設定を有効にするには、次の手順に従います。

1. チャネルコンテンツを調べて、それが AEM インスタンスから要求されているかどうかを確認します（オンライン）。

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. チャネルダッシュボードに移動します。
1. クリック **...** が含まれる **チャネル情報** パネル。

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. チャネルプロパティに移動します。
1. 「（（チャネル））」タブで、チェックボックスが無効になっていることを確認し、クリックします **保存して閉じる**.

   ![screen_shot_2017-12-19at122422pm](assets/screen_shot_2017-12-19at122422pm.png)

   コンテンツを適切にデバイスに実装する前に、「**オフラインコンテンツを更新**」をクリックします。

   ![screen_shot_2017-12-19at122637pm](assets/screen_shot_2017-12-19at122637pm.png)

   これに合わせて「**プロパティ**」の「**オフライン**」ステータスも更新されます。

   ![screen_shot_2017-12-19at124735pm](assets/screen_shot_2017-12-19at124735pm.png)

1. チャネルコンテンツを調べて、それがローカルの Player-Cache から要求されているかどうかを確認します。

   ![chlimage_1-26](assets/chlimage_1-26.png)

>[!NOTE]
>
>カスタムオフラインリソースハンドラーのテンプレートの詳細と、そのプロジェクトの `pom.xml` の最小要件については、**AEM Screens 用カスタムコンポーネントの開発**&#x200B;の[カスタムハンドラーのテンプレート](/help/user-guide/developing-custom-component-tutorial-develop.md#custom-handlers)を参照してください。
