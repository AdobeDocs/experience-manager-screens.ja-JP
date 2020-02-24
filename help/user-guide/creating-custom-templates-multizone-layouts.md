---
title: マルチゾーンレイアウトのカスタムテンプレートの作成
seo-title: マルチゾーンレイアウトのカスタムテンプレートの作成
description: ここでは、マルチゾーンレイアウトのカスタムテンプレートの作成について説明します。
seo-description: ここでは、マルチゾーンレイアウトのカスタムテンプレートの作成について説明します。
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 6a0967580d06e749db878d74aad2ffb1fec82f43

---


# マルチゾーンレイアウトのカスタムテンプレートの作成 {#creating-custom-templates-multizone}

このページでは、マルチゾーンレイアウトでのカスタムテンプレートの作成方法を紹介します。

## 命名規則 {#name-terms}

AEM Screensプロジェクトで使用するカスタムマルチゾーンテンプレートの作成方法を理解する前に、作成するテンプレートのバージョンを理解することをお勧めします。

| **レイアウト名** | **説明** |
|---|---|
| Left20-LandscapeHD3Zone | 3ゾーンの横置きレイアウトを参照し、ゾーン1が左から20 %、ゾーン2が水平スクリーンの80 %、垂直スクリーンの20 %を均等配置し、ゾーン3が水平に100 %、垂直スクリーンの80 %の縦横比が16:9の3ゾーンを作成できます |
| Upper20-PortraitHD2Zone | 画面の上端から20%の領域を占め、縦横比が16:9の2ゾーンの縦長テンプレートを指します。 |
| Right20-LandscapeSD3Zone | 画面の右から20 %を占め、縦横比が4:3の3ゾーンのテンプレートを指します。 |

## 使用例 {#example-use-cases}

## Left20-LandscapeHD3Zoneレイアウト {#custom-template-one}

次のセクションに従って、次の設定でカスタムテ *ンプレートLeft20-LandscapeHD3Zone* を作成します。

* **「Left20** 」は、画面の横置きサイズと縦置きサイズの20%を占める左側のトップゾーンを示します。
* **横置き** ：画面の向きを示します。
* **HDは** 、縦横比を16:9と表します。
* **3Zoneは** 、ディスプレイの3つのゾーンを指します

## マルチゾーンレイアウトの視覚的表現 {#multi-layout-visual-one}

Left20-LandscapeHD3Zoneレイアウトを使用すると、プロジェクトに次のマルチゾーンレイアウトを作成できます。

![画像](/help/user-guide/assets/custom-multizone/custom-multizone1.png)

## Left20-LandscapeHD3Zoneレイアウトの作成 {#landscape-layout-one}

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

1. プロパティ `/apps/customtemplate/template/my-custom-layout` jcr:descriptionを探して、 **Left20-LandscapeHD3Template for Left20** and *jcr:title******* to Template for Left-LandscapeHD3Zoneに移動し、更新します。

1. から **offline-config** ノードに移動し `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config` 、 **jcr:titleを** Left20-LandscapeHD3Zoneに更新します **。

1. *my custom-templateの* jcr:content **プロパティに移動し、** cq:cssプロパティを `/apps/customtemplate/template/my-custom-layout/jcr:content` aem-Em-Custom-layout ******** layoutに更新します。

1. 手順(4)を参照してください。この手順では、左側のテンプレートをコピーし、の下に3つのレスポンシブグリッドを表示しま `my-custom-layout/jcr:content`す。 *cq:cssClass* プロパティに各レスポンシブCSSを追加します。例： *my-custom-custom-css—top-left*, *my-custom—top-right,* my custom-layout, ** my custom-layout)。

   >[!NOTE]
   >これらのカスタムクラスは、レスポンシブグリッドの幅/高さを設定するためにCSSで使用されます。

   >[!NOTE]
   > レスポンシブグリッドは、必要な合計グリッド数に基づいて追加または削除できます。 この例では、最初の行に2つのグリッドを、2番目の行に1つのグリッドを表示しているので、合計3つのレスポンシブグリッド(r1c1、r1c2、r2c1)があります。

1. カスタム `/libs/settings/wcm/designs/screens` テンプ `/apps/settings/wcm/designs/` レートデザインにコ **ピーし、名前を変更します。**

1. プロパティ `/apps/settings/wcm/designs/custom-template-designs` jcr:title *of custom-template-designs* に移動し、customtemplate **-design** に更新します ****。

1. コンテンツを `/apps/settings/wcm/designs/<project>-designs/static.css` 次の内容に合わせて更新する

## 特定の設定を使用したカスタムテンプレートの作成 {#basic-flow-setting}

![画像](assets/custom-template1.png)

カスタムテンプレートを作成するには、以下の手順に従います。

1. `/apps/<project>/templates/my-custom-layout` にテンプレートを作成します。

   ```shell
    <?xml version="1.0" encoding="UTF-8"?>
    <jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0" xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:nt="http://www.jcp.org/jcr/nt/1.0"
    jcr:description="My Custom 3-zones layout "
    jcr:primaryType="cq:Template"
    jcr:title="3-zones layout"
    allowedParents="[/libs/screens/core/templates/channelfolder]"
    allowedPaths="[/content/screens(/.*)?]"
    ranking="{Long}20000">
    <jcr:content
        cq:cssClass="aem-Layout aem-Layout--3x1 my-CustomLayout"
        cq:designPath="/apps/settings/wcm/designs/<project>"
        cq:deviceGroups="[mobile/groups/responsive]"
        jcr:primaryType="cq:PageContent"
        sling:resourceSuperType="screens/core/components/channel"
        sling:resourceType="screens/core/components/multiscreenchannel">
        <r1c1
            cq:cssClass="aem-LayoutCell--1-1 my-CustomLayout-top"
            jcr:primaryType="nt:unstructured"
            sling:resourceType="wcm/foundation/components/responsivegrid"/>
        <r2c1
            cq:cssClass="aem-LayoutCell--1-1 my-CustomLayout-middle"
            jcr:primaryType="nt:unstructured"
            sling:resourceType="wcm/foundation/components/responsivegrid"/>
        <r3c1
            cq:cssClass="aem-LayoutCell--1-1 my-CustomLayout-bottom"
            jcr:primaryType="nt:unstructured"
            sling:resourceType="wcm/foundation/components/responsivegrid"/>
        <cq:responsive jcr:primaryType="nt:unstructured">
            <breakpoints jcr:primaryType="nt:unstructured"/>
        </cq:responsive>
        <offline-config/>
    </jcr:content>
   </jcr:root>
   ```

1. `/apps/settings/wcm/designs/<project>` にページデザインを作成します。

   >[!NOTE]
   >
   >上記の `cq:designPath` がこのパスと一致することを確認します。

1. デザインの **offline-config** ノードも、新しいパスを指すように更新します。

1. `/apps/settings/wcm/designs/<project>` フォルダーに **static.css** ファイルを追加し、その内容を以下のように設定します。

   ```shell
   .cq-Screens-channel--multizone.my-CustomLayout {}
   .cq-Screens-channel--multizone.my-CustomLayout .my-CustomLayout-top { height: 150px; }
   .cq-Screens-channel--multizone.my-CustomLayout .my-CustomLayout-middle { height: 1470px; }
   .cq-Screens-channel--multizone.my-CustomLayout .my-CustomLayout-bottom { height: 300px; }
   ```

## 背景レイヤーとしての画像の挿入 {#inserting-image}

画像を背景レイヤーとしてレイアウトに挿入できます。

いわゆる「data-uri」を使用して画像（Base64 エンコード済み）を CSS ファイルに直接埋め込むように、CSS ルールを調整できます。

それには次のようにします。
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

または、次の手順に従うこともできます。

1. 画像を何らかの形でチャネルのオフライン設定に含めます。
1. 上記の CSS で、「data-uri」バリアントではなく、画像への直接リンクを使用します。


## 背景色の更新 {#updating-color}

背景色を変更するには、xml ファイルに次のコードを追加します。

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`



