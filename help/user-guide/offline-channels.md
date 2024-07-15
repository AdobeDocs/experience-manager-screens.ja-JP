---
title: オフラインチャネル
description: AEM Screens Player が ContentSync テクノロジーを使用してチャネルのオフラインサポートをどのように提供するかを説明します。
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 5ad1046f-8b64-490b-9966-ce9008180d54
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 100%

---

# オフラインチャネル {#offline-channels}

Screens Player では、***ContentSync*** テクノロジーを使用してチャネルのオフラインサポートを提供しています。

プレーヤーは、解凍したコンテンツを提供するためにローカルの HTTP サーバーを使用します。

*オンライン*&#x200B;で動作するようにチャネルが設定されている場合、プレーヤーは AEM サーバーにアクセスしてチャネルリソースを提供します。ただし、*オフライン*&#x200B;で動作するようにチャネルが設定されている場合、プレーヤーは、ローカル http サーバーからチャネルリソースを提供します。

このプロセスのワークフローは次のとおりです。

1. 目的のページを解析します。
1. すべての関連アセットを収集します。
1. すべての要素を zip ファイルにパッケージ化します。
1. その zip ファイルをダウンロードし、ローカルで抽出します。
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
1. リスト内の設定をクリックします。
1. 「**キャッシュをクリア**」をクリックします。
1. 「**キャッシュを更新**」をクリックします。
1. 「**すべてダウンロード**」をクリックします。
1. zip ファイルを解凍します。
1. 解凍したフォルダーでローカルサーバーを起動します。
1. 開始ページを開き、アプリのステータスを確認します。

## チャネルのオフライン設定の有効化 {#enabling-offline-config-for-a-channel}

チャネルのオフライン設定を有効にするには、次の手順に従います。

1. チャネルコンテンツを調べて、それが AEM インスタンスから要求されているかどうかを確認します（オンライン）。

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. チャネルダッシュボードに移動します。
1. **チャネル情報**&#x200B;パネルの「**...**」をクリックします。

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. チャネルプロパティに移動します。
1. 「((Channel))」タブで、チェックボックスが無効になっていることを確認してから、「**保存して閉じる**」をクリックします。

   ![screen_shot_2017-12-19at122422pm](assets/screen_shot_2017-12-19at122422pm.png)

   コンテンツを適切にデバイスに実装する前に、「**オフラインコンテンツを更新**」をクリックします。

   ![screen_shot_2017-12-19at122637pm](assets/screen_shot_2017-12-19at122637pm.png)

   これに合わせて「**プロパティ**」の「**オフライン**」ステータスも更新されます。

   ![screen_shot_2017-12-19at124735pm](assets/screen_shot_2017-12-19at124735pm.png)

1. チャネルコンテンツを調べて、それがローカルの Player-Cache から要求されているかどうかを確認します。

   ![chlimage_1-26](assets/chlimage_1-26.png)

>[!NOTE]
>
>カスタムオフラインリソースハンドラーのテンプレートについて確認してください。また、プロジェクトの `pom.xml` の最小要件についても詳細を確認してください。**AEM Screens 用カスタムコンポーネントの開発**&#x200B;の[カスタムハンドラーのテンプレート](/help/user-guide/developing-custom-component-tutorial-develop.md#custom-handlers)を参照してください。
