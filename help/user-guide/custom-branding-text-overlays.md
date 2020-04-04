---
title: テキストオーバーレイのカスタムブランドとスタイルの適用
seo-title: テキストオーバーレイのカスタムブランドとスタイルの適用
description: このページでは、テキストオーバーレイのカスタムブランドとスタイル設定を適用する方法について説明します。
seo-description: このページでは、テキストオーバーレイのカスタムブランドとスタイル設定を適用する方法について説明します。
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: fdbe57b2cd927c112e9faa4888e3565626712c7a

---


# テキストオーバーレイのカスタムブランドとスタイル設定 {#creating-custom-branding-styling}

このページでは、画面オーバーレイでアセットに適用するテキストオーバーレイのカスタムブランドとスタイルを適用する方法について説明します。チャネル

## テキストオーバーレイのカスタムブランドとスタイルの作成 {#steps-custom-branding}

次の手順に従って、テキストオーバーレイのカスタムブランドとスタイルを作成します。

1. AEM Screensプロジェクトを作成します。 次の例は、次の図に示すように、 **customstyle** ( **customstyle** )という名前のプロジェクトとDemoBrand(DemoBrand)という名前のチャネルを作成して、この機能を示しています。

   ![画像](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. エディターから画像をドラッグ&amp;ドロップし、テキストオーバーレイをアセットに追加します。

   ![画像](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >テキストオーバーレイをチャネルエディタでアセットに追加する方法については、「テキストオーバーレイ」を参照 [してくださ](/help/user-guide/text-overlay.md)い。

1. AEM インスタンスの **CRXDE lite**／ツール／CRXDE Lite に移動します。

1. 例えば、この場合は、 `/apps/settings/wcm/designs/<your-project>/``/apps/settings/wcm/designs/customstyle/`

   ![画像](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. static.cssファ *イルに移動し* 、次のCSSルールを設定します。 また、CSSルールの下の図の例としても示されています。

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

1. パスをプロジェクトにコピーします。この場合、パスはとなります `/apps/settings/wcm/designs/customstyle`。

1. 手順(1)で作成した **DemoBrand** ( **DemoBrand** )というタイトルのチャネルに移動し、チャネルを選択した後、アクションバーの「Properties」をクリックします。

1. 「詳細」タブに移 **動し** 、「デザイン」フィールドを **確認します** 。
   ![画像](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >デフォルトでは、「 **Design** 」フィールドには、libsフォルダー内のデザインを指すパスが表示されます。

1. プロジェクト **フォルダへのパスで** 、[デザイン]フィールドを更新します。 この場合は、次のようになります `/apps/settings/wcm/designs/customstyle`。

   ![画像](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. 「保存し **て閉じる** 」をクリックして、デザインパスを更新します。

### ACLの更新 {#updating-acls}

これらのデザインのACLを更新して、プレイヤーがダウンロードできるようにする必要があります。

1. useradminに移動し、を選択し、カス `screens-<project>-devices group` タムデザインパスの読み取り権限を付与します。

1. このパス `screens-<project>-administrators` に対するグループの読み取りおよび変更の権限を指定します。

## 結果の表示 {#viewing-the-result}

上記の手順を完了したら、 *CRXDE Lite* (CRXDE Lite)から **** statis.cssファイルを更新し、その結果、既にアセットに追加されているテキストオーバーレイに更新を表示できます。

次の手順に従って、更新されたデザインを表示し、テキストオーバーレイを作成します。

1. AEM Screensプロジェクト(「customstyle **」>「** チャネル **」** —>「 **DemoBrand**」)に移動します。  チャネルを選択し、アクションバーの「**編集**」をクリックして、エディターを開きます。

1. これでデザインが「 **Designs** 」フィールドに追加されたので、前述のように「 **プレビュー** 」をクリックし、画像上の現在のスタイルをテキストオーバーレイで表示します。

   ![画像](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. CRXDE Liteで *static.css* ファイルに移動し、次に示すように、このファイルにフ `font-family: "Lucida Console", Courier, monospace;` ォント（など）を追加します。
   ![画像](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. 変更を保存してプレビューを再読み込みすると、次の図に示すように、テキストオーバーレイのフォントが更新されます。

   ![画像](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. さらに、 *static.cssファイルからコードの最後の2つのブロックを削除して* 、テキストオーバーレイの周囲のボックス化されたスタイルを削除できます。
   ![画像](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. 画像内の更新後の変更を表示します。ここで、プレビュー内のテキストオーバーレイが画像に追加されます。

   ![画像](/help/user-guide/assets/custom-brand/custom-brand11.png)

このチュートリアルを参照して、アセットに追加されたテキストオーバーレイのブランドとカスタムのスタイル設定を更新できるようになりました。









