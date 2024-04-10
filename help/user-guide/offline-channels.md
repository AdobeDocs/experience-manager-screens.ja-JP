---
title: オフラインチャネル
seo-title: Offline Channels
description: AEM Screens Player は、ContentSync テクノロジーを活用して、チャネルをオフラインサポートします。 ここでは、更新ハンドラーと、チャネルに対してオフライン設定を有効にする方法について説明します。
seo-description: The AEM Screens player provides offline support for channels by leveraging the ContentSync technology. Follow this page to learn more about update handlers and enabling offline configuration for a channel.
uuid: 18b9d175-ff26-42db-86aa-5ea978909f71
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: bd572743-652f-4fc5-8b75-a3c4c74536f4
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 5ad1046f-8b64-490b-9966-ce9008180d54
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 56%

---

# オフラインチャネル {#offline-channels}

Screens Player では、***ContentSync*** テクノロジーを利用してチャネルのオフラインサポートを提供しています。

プレーヤーは、解凍されたコンテンツを提供するためにローカル http サーバーを使用します。

チャネルが&#x200B;*オンライン*&#x200B;で実行されるように設定されている場合、プレーヤーは AEM サーバーにアクセスしてチャネルリソースを提供します。これに対し、チャネルが&#x200B;*オフライン*&#x200B;で実行されるように設定されている場合、プレーヤーはローカルの HTTP サーバーからチャネルリソースを提供します。

プロセスのワークフローは次のとおりです。

1. 目的のページを解析します
1. 関連するすべてのアセットを収集
1. すべてを zip ファイルにパッケージ化
1. zip ファイルをダウンロードし、ローカルで抽出します。
1. コンテンツのローカルコピーを表示

## 更新ハンドラー {#update-handlers}

***ContentSync*** は、更新ハンドラーを使用して、特定のプロジェクトに必要なすべてのページとアセットを解析および収集します。AEM Screensでは、次の更新ハンドラーを使用します。

### 共通オプション {#common-options}

* *タイプ*：使用する更新ハンドラーのタイプ
* *パス*：リソースへのパス
* *[targetRootDirectory]*：zip ファイル内のターゲットフォルダー

<table>
 <tbody>
  <tr>
   <td><strong>タイプ</strong></td> 
   <td><strong>説明</strong></td> 
   <td><strong>Options</strong></td> 
  </tr>
  <tr>
   <td>channels</td> 
   <td>チャネルを収集します</td> 
   <td>extension：収集するリソースの拡張子<br />[pathSuffix='']：チャネルパスに追加するサフィックス<br /> </td> 
  </tr>
  <tr>
   <td>clientlib</td> 
   <td>指定されたクライアントライブラリを収集します</td> 
   <td>[extension='']：css か js のどちらか（前者のみか後者のみを収集するために指定）</td> 
  </tr>
  <tr>
   <td>assetrenditions：</td> 
   <td>アセットレンディションを収集します</td> 
   <td>[renditions=[]]：収集するレンディションのリスト。デフォルトで元のレンディションに設定</td> 
  </tr>
  <tr>
   <td>copy</td> 
   <td>指定された構造をパスからコピーします</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### コンテンツ同期設定のテスト {#testing-contentsync-configuration}

ContentSync 設定をテストするには、以下の手順に従います。

1. `https://localhost:4502/libs/cq/contentsync/content/console.html` を開きます。
1. リストから設定を選択します。
1. 「キャッシュをクリア」をクリックします。
1. 「キャッシュを更新」をクリックします。
1. 「すべてダウンロード」をクリックします。
1. zip ファイルを解凍します。
1. 解凍したフォルダーでローカルサーバーを起動します。
1. 開始ページを開き、アプリのステータスを確認します

## チャネルのオフライン設定の有効化 {#enabling-offline-config-for-a-channel}

チャネルのオフライン設定を有効にするには、次の手順に従います。

1. チャネルコンテンツをInspectし、チャネルコンテンツがAEM インスタンス（オンライン）からリクエストされたものかどうかを確認します。

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. チャネルのダッシュボードに移動し、**チャネル情報**&#x200B;パネルの「**...**」をクリックして、プロパティを変更します。

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. チャネルプロパティに移動し、の下にあるチェックボックスが無効になっていることを確認します **チャネル** タブ。 「**保存して閉じる**」をクリックします。

   ![screen_shot_2017-12-19at122422pm](assets/screen_shot_2017-12-19at122422pm.png)

   コンテンツを適切にデバイスに実装する前に、「**オフラインコンテンツを更新**」をクリックします。

   ![screen_shot_2017-12-19at122637pm](assets/screen_shot_2017-12-19at122637pm.png)

   これに合わせて「**プロパティ**」の「**オフライン**」ステータスも更新されます。

   ![screen_shot_2017-12-19at124735pm](assets/screen_shot_2017-12-19at124735pm.png)

1. チャネルコンテンツを調べて、それがローカルの Player-Cache から要求されているかどうかを確認します。

   ![chlimage_1-26](assets/chlimage_1-26.png)

>[!NOTE]
>
>カスタムのオフラインリソースハンドラーのテンプレートと最小要件について詳しくは、を参照してください。 `pom.xml` 具体的なプロジェクトについては、を参照してください。 [カスタムハンドラーのテンプレート](/help/user-guide/developing-custom-component-tutorial-develop.md#custom-handlers) 。対象： **AEM Screens用カスタムコンポーネントの開発**.
