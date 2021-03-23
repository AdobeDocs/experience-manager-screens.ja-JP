---
title: テキストオーバーレイのカスタムブランディングとスタイルの適用
seo-title: テキストオーバーレイのカスタムブランディングとスタイルの適用
description: このページでは、テキストオーバーレイのカスタムブランディングとスタイル設定を適用する方法について説明します。
seo-description: このページでは、テキストオーバーレイのカスタムブランディングとスタイル設定を適用する方法について説明します。
contentOwner: Jyotika Syal
feature: Screens の開発
role: デベロッパー
level: 中間
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 99%

---


# テキストオーバーレイのカスタムブランディングとスタイル設定 {#creating-custom-branding-styling}

このページでは、AEM Screens チャネルのアセットに適用されたテキストオーバーレイのカスタムブランディングとスタイル設定を適用する方法について説明します。

## テキストオーバーレイのカスタムブランディングとスタイル設定の作成 {#steps-custom-branding}

次の手順に従って、テキストオーバーレイのカスタムブランディングとスタイル設定を作成します。

1. AEM Screens プロジェクトを作成します。次の図のように、この例では、**customstyle** という名前のプロジェクトと、**DemoBrand** という名前のチャネルを作成して、この機能を示しています。

   ![画像](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. エディターから画像をドラッグ＆ドロップし、テキストオーバーレイをアセットに追加します。

   ![画像](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >チャネルエディターでテキストオーバーレイをアセットに追加する方法については、[テキストオーバーレイ](/help/user-guide/text-overlay.md)を参照してください。

1. AEM インスタンス／ツール／**CRXDE Lite** から CRXDE Lite に移動します。

1. カスタムデザインを `/apps/settings/wcm/designs/<your-project>/` に作成する必要があります。例えば、この場合は、`/apps/settings/wcm/designs/customstyle/` に移動します。

   ![画像](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. *static.css* ファイルを作成し、次の css ルールを設定します。また、css ルールは下の図の例としても示されています。

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

1. パスをプロジェクトにコピーします。この場合、パスは `/apps/settings/wcm/designs/customstyle` です。

1. 手順（1）で作成した **DemoBrand** というタイトルのチャネルに移動し、チャネルを選択した後、アクションバーの&#x200B;**プロパティ**&#x200B;をクリックします。

1. 「**詳細**」タブに移動し、「**デザイン**」フィールドを確認します。
   ![画像](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >デフォルトでは、「**デザイン**」フィールドには、libs フォルダー内のデザインを指すパスが表示されます。

1. プロジェクトフォルダーのパスで、「**デザイン**」フィールドを更新します。この場合は、`/apps/settings/wcm/designs/customstyle` です。

   ![画像](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. 「**保存して閉じる**」をクリックして、デザインパスを更新します。

   >[!IMPORTANT]
   >既存の Screens テンプレートをオーバーレイして、デフォルトで独自のデザインを挿入したり、完全に独自のテンプレートを作成したりできるオプションがあります。詳しくは、以下の手順を参照してください。

1. 既存の Screen テンプレートをオーバーレイして独自のデザインを挿入するには、次の手順に従います。

   1. `/apps/screens/core/templates/sequencechannel` の `/libs/screens/core/templates/sequencechannel` をオーバーレイします。
   1. 新しいデザインを指すように、`/apps/screens/core/templates/sequencechannel/jcr:content` の *cq:designPath* プロパティを変更します。

1. 完全に独自のテンプレートを作成するには：
   1. `/libs/screens/core/templates/sequencechannel` を `/apps/customstyle/templates/styled-sequencechannel` にコピーします。
   1. 新しいデザインを指すように、`/apps/customstyle/templates/styled-sequencechannel/jcr:content` の *cq:designPath* プロパティを変更します。


### ACL の更新 {#updating-acls}

これらのデザインの ACL を更新して、プレーヤーがダウンロードできるようにする必要があります。

1. ユーザー管理に移動し、`screens-<project>-devices group` を選択してカスタムデザインパスの読み取り権限を付与します。

1. このパスに対する `screens-<project>-administrators` グループの読み取りおよび変更の権限を指定します。

## 結果の表示 {#viewing-the-result}

上記の手順を完了したら、*CRXDE Lite* から **statis.css** ファイルを更新すると、既にアセットに追加されているテキストオーバーレイに更新が表示されます。

次の手順に従って、更新したデザインをテキストオーバーレイに表示します。

1. **customstyle** という AEM Screens プロジェクトから、**チャネル**／**DemoBrand** に移動します。チャネルを選択し、アクションバーの「**編集**」をクリックして、エディターを開きます。

1. デザインは「**デザイン**」フィールドに追加されたので、前述のように「**プレビュー**」をクリックすると、現在のスタイルが画像上のテキストオーバーレイで表示されます。

   ![画像](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. CRXDE Lite の *static.css* ファイルに移動し、次に示すように、このファイルにフォント（`font-family: "Lucida Console", Courier, monospace;` など）を追加します。
   ![画像](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. 変更を保存してプレビューを再読み込みすると、次の図に示すように、テキストオーバーレイのフォントが更新されます。

   ![画像](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. さらに、*static.css* ファイルからコードの最後の 2 ブロックを削除して、テキストオーバーレイの周囲のボックススタイルを削除できます。
   ![画像](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. 画像の更新後の変更が表示されるので、プレビューで画像に追加したテキストオーバーレイが確認できます。

   ![画像](/help/user-guide/assets/custom-brand/custom-brand11.png)

   これで、アセットに追加されたテキストオーバーレイのブランドやカスタムスタイルを更新する準備が整いました。









