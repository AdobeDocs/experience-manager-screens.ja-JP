---
title: マルチゾーンレイアウトのカスタムテンプレートの作成
seo-title: マルチゾーンレイアウトのカスタムテンプレートの作成
description: ここでは、マルチゾーンレイアウトのカスタムテンプレートの作成について説明します。
seo-description: ここでは、マルチゾーンレイアウトのカスタムテンプレートの作成について説明します。
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: a4d48ba04bb8ab863f4f07b932892676b70e1e23

---


# マルチゾーンレイアウトのカスタムテンプレートの作成 {#creating-custom-templates-multizone}

次の例は、multiZoneレイアウトでカスタムテンプレートを作成する方法を示しています。

例えば、次の節では、以下の設定でマルチゾーンレイアウトのカスタムテンプレートを作成する方法を示します。

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



