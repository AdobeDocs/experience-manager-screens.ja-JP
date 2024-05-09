---
title: テキストオーバーレイのカスタムブランディングとスタイルの適用
description: AEM Screens チャネルのアセットに適用されるテキストオーバーレイにカスタムブランディングとスタイルを適用する方法を説明します。
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 059e1b19-e9b5-48f0-8f2f-141f0c2f7842
source-git-commit: ce8340f24d116b4268a6ed15dd4e9f626bad1ef6
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 44%

---

# テキストオーバーレイのカスタムブランディングとスタイル設定 {#creating-custom-branding-styling}

AEM Screens チャンネルのアセットに適用されるテキストオーバーレイにカスタムブランディングとスタイルを適用する方法を説明します。

## テキストオーバーレイのカスタムブランディングとスタイル設定の作成 {#steps-custom-branding}

次の手順に従って、テキストオーバーレイのカスタムブランディングとスタイル設定を作成します。

1. AEM Screens プロジェクトを作成します。この例では、という名前のプロジェクトを作成して、機能を示します。 **`customstyle`** および「」というタイトルのチャネル **DemoBrand**&#x200B;を参照してください（下図を参照）。

   ![画像](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. エディターから画像をドラッグ&amp;ドロップし、テキストオーバーレイをアセットに追加します。

   ![画像](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >チャネルエディターでテキストオーバーレイをアセットに追加する方法について詳しくは、[テキストオーバーレイ](/help/user-guide/text-overlay.md)を参照してください。

1. AEM インスタンス／ツール／**CRXDE Lite** から CRXDE Lite に移動します。

1. でのカスタムデザインの作成 `/apps/settings/wcm/designs/<your-project>/`例えば、この場合、次に移動します。 `/apps/settings/wcm/designs/customstyle/`

   ![画像](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. を作成 *static.css* をファイルし、次の css ルールを設定します。 また、css ルールは下の図の例としても示されています。

   ```shell
    //global styles
    cq-Screens-textOverlay {
    padding: 1em;
    font-size: 3rem;
    line-height: 1em;
     }
    //authoring overrides
   .aem-AuthorLayer-Edit .cq-Screens-textOverlay {
    display: none;
    padding: 0;
    font-size: 1rem;
    }
     // light text variant
    .cq-Screens-textOverlay-color--light {
     background-color: rgba(0, 0, 0, .6);
     }
     // dark text variant
     .cq-Screens-textOverlay-color--dark {
      background-color: rgba(255, 255, 255, .6);
    }
   ```

   ![画像](/help/user-guide/assets/custom-brand/custom-brand4.png)

1. パスをプロジェクトにコピーします。この場合、パスはです。 `/apps/settings/wcm/designs/customstyle`.

1. 手順（1）で作成した **DemoBrand** というタイトルのチャネルに移動し、チャネルを選択した後、アクションバーの&#x200B;**プロパティ**&#x200B;をクリックします。

1. 「**詳細**」タブに移動し、「**デザイン**」フィールドを確認します。
   ![画像](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >デフォルトにする **デザイン** フィールドには、libs フォルダー内のデザインを指すパスが表示されます。

1. プロジェクトフォルダーのパスで、「**デザイン**」フィールドを更新します。この場合、値は `/apps/settings/wcm/designs/customstyle` です。

   ![画像](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. 「**保存して閉じる**」をクリックして、デザインパスを更新します。

   >[!IMPORTANT]
   >オプションで、既存の Screens テンプレートをオーバーレイして、デフォルトで独自のデザインを挿入したり、独自のテンプレートを完全に作成したりできます。 詳しくは、以下の手順を参照してください。

1. 既存の Screen テンプレートをオーバーレイして独自のデザインを挿入するには、次の手順に従います。

   1. `/apps/screens/core/templates/sequencechannel` の `/libs/screens/core/templates/sequencechannel` をオーバーレイします。
   1. を変更する *`cq:designPath`* のプロパティ `/apps/screens/core/templates/sequencechannel/jcr:content` そのため、新しいデザインを指しています。

1. 完全に独自のテンプレートを作成するには：
   1. `/libs/screens/core/templates/sequencechannel` を `/apps/customstyle/templates/styled-sequencechannel` にコピーします。
   1. を変更する *`cq:designPath`* のプロパティ `/apps/customstyle/templates/styled-sequencechannel/jcr:content` そのため、新しいデザインを指しています。


### ACL の更新 {#updating-acls}

プレーヤーがダウンロードできるように、これらのデザインの ACL を更新します。

1. ユーザー管理に移動し、`screens-<project>-devices group` を選択してカスタムデザインパスの読み取り権限を付与します。

1. このパスに対する `screens-<project>-administrators` グループの読み取りおよび変更の権限を指定します。

## 結果の表示 {#viewing-the-result}

上記の手順を完了したら、 *statis.css* ファイルの送信元 **CRXDE Lite** そのため、アセットに既に追加されているテキストオーバーレイへの更新を確認します。

次の手順に従って、更新したデザインをテキストオーバーレイに表示します。

1. というタイトルのAEM Screens プロジェクトに移動します。 **`customstyle`** > **チャネル** > **DemoBrand**. チャネルをクリックし、 **編集** アクションバーから。

1. デザインは「**デザイン**」フィールドに追加されたので、前述のように「**プレビュー**」をクリックすると、現在のスタイルが画像上のテキストオーバーレイで表示されます。

   ![画像](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. CRXDE Lite の *static.css* ファイルに移動し、次に示すように、このファイルにフォント（`font-family: "Lucida Console", Courier, monospace;` など）を追加します。

   ![画像](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. 変更を保存してプレビューを再読み込みすると、テキストオーバーレイフォントが更新されます（下図を参照）。

   ![画像](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. また、コードの最後の 2 つのブロックを *static.css* テキストオーバーレイの周囲のボックス化されたスタイルを削除するファイル。

![画像](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. テキストオーバーレイが画像に追加された、更新された変更をプレビューで表示します。

   ![画像](/help/user-guide/assets/custom-brand/custom-brand11.png)

   これで、アセットに追加したテキストオーバーレイのブランドとカスタムスタイル設定を更新する準備が整いました。
