---
title: マルチゾーンレイアウトのカスタムテンプレートの作成
seo-title: マルチゾーンレイアウトのカスタムテンプレートの作成
description: ここでは、マルチゾーンレイアウトのカスタムテンプレートの作成について説明します。
seo-description: ここでは、マルチゾーンレイアウトのカスタムテンプレートの作成について説明します。
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 9e3f26e10a5168511b2bf138f8ce36b94778b339

---


# Creating Custom Templates for MultiZone Layouts {#creating-custom-templates-multizone}

このページでは、マルチゾーンレイアウト用のカスタムテンプレートの作成方法を紹介します。

## 重要な検討事項 {#considerations}

マルチゾーンレイアウトでカスタムテンプレートを作成する前に、次の2つの点に注意する必要があります。

1. **Fixed Pixel Size or Percentage**:

   カスタムレイアウトで異なるゾーンに対して固定ピクセルサイズを使用するか、パーセント値を使用してカスタムレイアウトを作成するかは、決定する必要があります。

   > [!NOTE]
   > 割合を使用してカスタムレイアウトのゾーンを設定すると、様々な画面サイズでテンプレートを再利用できるという利点があります。

1. **命名規則**:

   AEM Screensプロジェクトで使用するカスタムマルチゾーンテンプレートの作成方法を理解する前に、作成するテンプレートのバージョンを理解することをお勧めします。

   | **レイアウト名** | **説明** |
   |---|---|
   | Left20-LandscapeHD3Zone | ゾーン 1 が左上、縦横 20％、ゾーン 2 が右上、縦 20％横 80％、ゾーン 3 が縦 80％横 100％のスクリーンサイズを占める 3 ゾーンで構成される、縦横比 16:9 の 3 ゾーン横型レイアウトが作成可能 |
   | Upper20-PortraitHD2Zone | 上部から 20％、2 ゾーンで構成される、縦横比 16:9 の縦型テンプレート |
   | Right20-LandscapeSD3Zone | 右から 20％、3 ゾーンで構成される、縦横比 4:3 のテンプレート |

   > [!IMPORTANT]
   > カスタムレイアウト内で定義されたゾーンは、レイアウト全体の全体的な縦横比と一致しない場合があります。 このドキュメントで従う命名規則では、カスタムレイアウト全体の縦横比を指定します。

## 使用例left20-LandscapeHD3Zoneレイアウト {#custom-template-one}

次のセクションに従って、次の設定でカスタムテ *ンプレートLeft20-LandscapeHD3Zone* を作成します。

* **Left20** は、縦横 20％のスクリーンサイズを占める左上部のゾーンを示します。
* **Landscape** は画面の向きを示します。
* **HD** は、縦横比 16:9 を示します。
* **3Zone** は、ディスプレイの 3 ゾーンを示します。

## マルチゾーンレイアウトの視覚表現 {#multi-layout-visual-one}

Left20-LandscapeHD3Zone レイアウトを使用すると、プロジェクトに次のマルチゾーンレイアウトを作成できます。

![画像](/help/user-guide/assets/custom-multizone/custom-multizone1.png)

## Left20-LandscapeHD3Zone レイアウトの作成 {#landscape-layout-one}

次の手順に従って、AEM Screensプロジェクト用のLeft20-LandscapeHD3Zoneレイアウトを作成します。

1. Create an AEM Screens project titled as **customtemplate**.

   ![画像](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. AEMインスタンス **—>ツール —>** CRXDE liteからCRXDE Liteに移動します ****。

1. 「 **apps** 」の下に「customtemplate」という名前のフォルダーを **作成します**。 同様に、次の図に示すように、 **customtemplateの下に****** templateという名前の別のフォルダーを作成します。

   ![画像](/help/user-guide/assets/custom-multizone/custom-template1.png)

   > [!NOTE]
   > CRXDE Liteのアクションバーで **「** Save all」をクリックし、コンテンツをノードのいずれかに作成、編集、コピーするたびに更新を保存することをお勧めします。そうしないと、更新をコミットできなくなります。

1. 左バーのテンプレートをからにコピ `/libs/screens/core/templates/splitscreenchannel/lbar-left` ーしま `/apps/customtemplate/template`す。

1. コピーした **lbar-left** (`/apps/customtemplate/template`)の名前を **my-custom-layoutに変更します**。
   ![画像](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. プロパティ `/apps/customtemplate/template/my-custom-layout` jcr:descriptionを探して、 **Left20-LandscapeHD3Template for Left20** and *jcr:title******* to Template for Left-LandscapeHD3Zoneに移動し、更新します。

   ![画像](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. から **offline-config** ノードに移動し `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config` 、 **jcr:titleを** Left20-LandscapeHD3Zoneに更新します **。

   ![画像](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. *my custom-templateの* jcr:content **プロパティに移動し、** cq:cssプロパティを `/apps/customtemplate/template/my-custom-layout/jcr:content` aem-Em-Custom-layout ******** layoutに更新します。

   ![画像](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. 手順(4)を参照してください。この手順では、左側のテンプレートをコピーし、の下に3つのレスポンシブグリッドを表示しま `my-custom-layout/jcr:content`す。 *cq:cssClass* プロパティの各レスポンシブグリッドにカスタムcssクラスを追加します。例えば、 *my-custom-layout—* top-left *for* r1c1 nodeと指定します。

   ![画像](/help/user-guide/assets/custom-multizone/custom-template7.png)

   同様に、 *my-custom-layout—top-right* for *r1c2* 、my-custom-layout bottom for *r2c1*** nodeを追加します。

   >[!NOTE]
   >これらのカスタムクラスは、レスポンシブグリッドの幅/高さを設定するためにCSSで使用されます。

   >[!NOTE]
   > レスポンシブグリッドは、必要な合計グリッド数に基づいて追加または削除できます。 この例では、最初の行に2つのグリッドを、2番目の行に1つのグリッドを表示しているので、合計3つのレスポンシブグリッド(r1c1、r1c2、r2c1)があります。

1. コピーし `/libs/settings/wcm/designs/screens` たデザ `/apps/settings/wcm/designs/` インをにコピーし、カスタムテンプ **レートデザインとして名前を変更します**。

1. プロパティ `/apps/settings/wcm/designs/custom-template-designs` jcr:title *of custom-template-designs* に移動し、customtemplate **-design** に更新します ****。

1. static.cssに移 `/apps/settings/wcm/designs/custom-template-designs` 動し、ファイルを作成します。

1. コンテンツをstatic.cssファイルにコピーします。

   ```shell
       /*my-custom-layout styles*/
      .cq-Screens-channel--multizone.my-custom-layout .my-custom-layout--top-left {
       width:20%;
       height: 36%;
      float: left !important;
      }
     .cq-Screens-channel--multizone.my-custom-layout .my-custom-layout--top-right {
      width:80%;
      height: 36%;
     float: left !important;
     }
     .cq-Screens-channel--multizone.my-custom-layout .my-custom-layout--bottom {
     width:100%;
     height: 64%;
     }
   ```

   >[!NOTE]
   > 割合は、カスタムテンプレートの要件に合わせて更新できます。

1. プロパティ `/apps/<project>/templates/my-custom-layout/jcr:content` cq:designPathに移動して更新し **`/apps/settings/wcm/designs/customtemplate-designs` 、static.cssで設定されたスタイルを読み込みます。

   >[!NOTE]
   > コピーや貼り付けではなく、すべてのスタイルを入力することをお勧めします。これにより、空白が発生し、CSSのスタイル設定に問題が生じる可能性があります。

## 結果の表示 {#viewing-result}

AEM Screensプロジェクトで上記のカスタマイズ済みテンプレートを使用するには、次の手順に従います。

1. 手順(1)で作成したScreensプロジェクトに移動し、 **Channelsフォルダーを選択し** ます。

   ![画像](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. アクシ **ョンバーで「作成** 」をクリックし、作成ウィザードで **「Left20-LandscapeHD3Zone** 」テンプレートを **** 選択します。

   ![画像](/help/user-guide/assets/custom-multizone/custom-template9.png)

1. カスタマイズしたテンプレートを使用してチャネルを作成したら、エディターからチャネルにアセットを追加できます。 次のプレビューは、カスタムテンプレート内の画像を示しています。

   ![画像](/help/user-guide/assets/custom-multizone/custom-template10.png)

## 背景レイヤーとしての画像の挿入 {#inserting-image}

画像を背景レイヤーとしてレイアウトに挿入できます。

You can adjust the CSS rule to use what is called “data-uri” and directly inline the image (Base64 encoded) in the CSS file, you created in (step 13), *static.css*.

それには次のようにします。
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

または、次の手順に従うこともできます。

1. 画像を何らかの形でチャネルのオフライン設定に含めます。
1. 上記の CSS で、「data-uri」バリアントではなく、画像への直接リンクを使用します。


## 背景色の更新 {#updating-color}

To change the background color, add the following code to the xml file (step 13), *static.css*.

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`



