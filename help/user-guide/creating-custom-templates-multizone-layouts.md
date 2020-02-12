---
title: マルチゾーンレイアウトのカスタムテンプレートの作成
seo-title: マルチゾーンレイアウトのカスタムテンプレートの作成
description: ここでは、マルチゾーンレイアウトのカスタムテンプレートの作成について説明します。
seo-description: ここでは、マルチゾーンレイアウトのカスタムテンプレートの作成について説明します。
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 87a86d60de9ea09dae93d08a1e0b42271c39249f

---


# マルチゾーンレイアウトのカスタムテンプレートの作成 {#creating-custom-templates-multizone}

このページでは、マルチゾーンレイアウトでのカスタムテンプレートの作成方法を紹介します。

## 命名規則 {#name-terms}

AEM Screensプロジェクトで使用するカスタムマルチゾーンテンプレートの作成方法を理解する前に、作成するテンプレートのバージョンを理解しておく必要があります。

| **レイアウト名** | **説明** |
|---|---|
| Left20-LandscapeHD3Zone | 3ゾーンの横置きレイアウトを参照し、ゾーン1が左から20 %、ゾーン2が水平スクリーンの80 %、垂直スクリーンの20 %を均等配置し、ゾーン3が水平に100 %、垂直スクリーンの80 %の縦横比が16:9の3ゾーンを作成できます |
| Upper20-PortraitHD2Zone | 画面の上端から20%の領域を占め、縦横比が16:9の2ゾーンの縦長テンプレートを指します。 |
| Right20-LandscapeSD3Zone | 画面の右から20 %を占め、縦横比が4:3の3ゾーンのテンプレートを指します。 |

## 使用例 {#example-use-cases}

## Left20-LandscapeHD3Zoneレイアウトの作成 {#landscape-layout-one}

次の節に、次の設定を使用してカスタムテンプレートを作成する方法を示します。

* **「Left20** 」は、画面の横置きサイズと縦置きサイズの20%を占める左側のトップゾーンを示します。
* **横置き** ：画面の向きを示します。
* **HDは** 、縦横比を16:9と表します。
* **3Zoneは** 、ディスプレイの3つのゾーンを指します

## マルチゾーンレイアウトの視覚的表現 {#multi-layout-visual-one}

Left20-LandscapeHD3Zoneレイアウトを使用すると、プロジェクトに次のマルチゾーンレイアウトを作成できます。

![画像](/help/user-guide/assets/custom-multizone/custom-multizone1.png)






## Upper20-PortraitHD2Zoneレイアウトの作成 {#landscape-layout-two}

次の節に、次の設定を使用してカスタムテンプレートを作成する方法を示します。






![画像](assets/custom-template1.png)


## 特定の設定を使用したカスタムテンプレートの作成 {#basic-flow-setting}

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



