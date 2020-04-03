---
title: テキストオーバーレイのカスタムブランドとスタイルの適用
seo-title: テキストオーバーレイのカスタムブランドとスタイルの適用
description: このページでは、テキストオーバーレイのカスタムブランドとスタイル設定を適用する方法について説明します。
seo-description: このページでは、テキストオーバーレイのカスタムブランドとスタイル設定を適用する方法について説明します。
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: f91faa23c7c5c4f0f705c77251554b64efaf2611

---


# テキストオーバーレイのカスタムブランドとスタイル設定 {#creating-custom-branding-styling}

このページでは、テキストオーバーレイのカスタムブランドとスタイル設定を適用する方法について説明します。

## テキストオーバーレイのカスタムブランドとスタイルの作成 {#steps-custom-branding}

次の手順に従って、テキストオーバーレイのカスタムブランドとスタイルを作成します。

1. 次の図に示すように、「 **customstyle** 」というAEM Screensプロジェクトと「 **DemoBrand**」というチャネルを作成します。

   ![画像](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. エディターから画像をドラッグ&amp;ドロップし、テキストオーバーレイをアセットに追加します。

   ![画像](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >テキストオーバーレイをチャネルエディタでアセットに追加する方法については、「テキストオーバーレイ」を参照 [してください](/help/user-guide/text-overlay.md)。

1. AEM インスタンスの **CRXDE lite**／ツール／CRXDE Lite に移動します。

1. 例えば、この場合は、でカスタムデザ `/apps/settings/wcm/designs/<your-project>/`インを作成する必要があります。

   ![画像](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. static.cssファイルに移動し、次のCSSルールを設定します。 次の図にも示します。

   ```shell
    //global styles
    .cq-Screens-textOverlay
    { … }
    //authoring overrides
    .aem-AuthorLayer-Edit .cq-Screens-textOverlay { … }
    // light text variant
    .cq-Screens-textOverlay-color--light
    { … }
     // dark text variant
    .cq-Screens-textOverlay-color--dark { … }
   ```
   ![画像](/help/user-guide/assets/custom-brand/custom-brand4.png)

1. パスをプロジェクトにコピーします。この場合、パスはとなります `/apps/settings/wcm/designs/customstyle`。

1. 「 **DemoBrand** （手順1で作成）」というタイトルのチャネルに移動し、チャネルを選択した後、アクションバーの「 **Properties** 」をクリックします。

1. 「詳細」タブに移 **動し** 、「デザイン」フィールドを **確認します** 。
   ![画像](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >デフォルトでは、「 **Design** 」フィールドには、libsフォルダー内のデザインを指すパスが表示されます。

1. プロジェクト **フォルダへのパスで** 、[デザイン]フィールドを更新します。 この場合は、次のようになります `/apps/settings/wcm/designs/customstyle`。

   ![画像](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. 「保存し **て閉じる** 」をクリックして、デザインパスを更新します。


## 結果の表示 {#viewing-the-result}

上記の手順を完了したら、 *CRXDE Liteから* statis.css **** ファイルを更新し、その結果、アセットに追加されたテキストレイアウトに更新を表示できます。

次の手順に従って、更新されたデザインを表示し、テキストレイアウトにします。

1. 「 **customstyle** 」というAEM Screensプロジェクト、「 **DemoBrand** 」というチャネルに移動し、アクションバーの「 **Edit** 」をクリックしてエディターを開きます。

1. これでデザインが「 **Designs** 」フィールドに追加されたので、前述のように「 **プレビュー** 」をクリックし、画像上の現在のスタイルをテキストオーバーレイで表示します。

   ![画像](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. CRXDE Liteでstatic.cssファイルに移動し、例えばフォントを追加します。
   ![画像](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. 変更を保存し、プレビューを再度読み込むと、次の図に示すように、テキストオーバーレイのフォントが更新されます。

   ![画像](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. また、static.cssファイルから最後の2つのコードブロックを削除して、テキストオーバーレイの周囲のボックス化されたスタイルを削除できます。
   ![画像](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. 次に示すように、表示内での更新後の変更をプレビューに反映し、テキストオーバーレイを画像に追加します。

   ![画像](/help/user-guide/assets/custom-brand/custom-brand11.png)

このため、前の節の手順に従って、アセットに追加したテキストオーバーレイのブランドとカスタムのスタイルを更新できます。









