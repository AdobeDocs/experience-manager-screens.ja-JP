---
title: マルチゾーンレイアウトのカスタムテンプレートの作成
description: AEM Screens 用マルチゾーンレイアウトでカスタムテンプレートを作成する方法について説明します。
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 3f4813f8-0438-4ce0-9046-84025de0ddd1
source-git-commit: df41a8794683e241b6f12b58d39c01e069187435
workflow-type: ht
source-wordcount: '862'
ht-degree: 100%

---

# マルチゾーンレイアウトでのカスタムテンプレートの作成 {#creating-custom-templates-multizone}

ここでは、マルチゾーンレイアウトでのカスタムテンプレートの作成方法を説明します。

## 重要な検討事項 {#considerations}

マルチゾーンレイアウトでカスタムテンプレートを作成する前に、注意する必要がある重要な検討事項が 2 つあります。

1. **固定ピクセルサイズまたはパーセンテージ**：

   カスタムレイアウトで異なるゾーンに対して固定ピクセルサイズを使用するか、パーセンテージを使用したカスタムレイアウトを作成するかを決定します。

   >[!NOTE]
   >カスタムレイアウトのゾーンの設定にパーセンテージを設定すると、様々な画面サイズでテンプレートを再利用できるという利点があります。

1. **命名規則**：

   命名規則は、AEM Screens プロジェクトで使用するカスタムマルチゾーンテンプレートの作成方法を理解するのに役立ちます。ただし、まずは、作成するテンプレートの用語を理解する必要があります。

   | **レイアウト名** | **説明** |
   |---|---|
   | `Left20-LandscapeHD3Zone` | 次の 3 つのゾーンを作成できる 3 ゾーンの横長レイアウト：<br>* ゾーン 1、画面の左から縦横 20％<br>* ゾーン 2、右揃えで縦 20％、横 80％<br>* ゾーン 3、縦 80％、横 100％。縦横比は 16:9 |
   | `Upper20-PortraitHD2Zone` | 画面の上から 20％を占める、縦横比 16:9、2 ゾーンの縦長テンプレート |
   | `Right20-LandscapeSD3Zone` | 画面の右から 20％を占める、縦横比 4:3、3 ゾーンのテンプレート |

   >[!IMPORTANT]
   >カスタムレイアウト内で定義されたゾーンは、レイアウト全体の縦横比と一致しない場合があります。このドキュメントで従う命名規則では、カスタムレイアウト全体の縦横比を指定します。

## `Left20-LandscapeHD3Zone` レイアウトの使用例 {#custom-template-one}

以下の節に従って、次の設定でカスタムテンプレート *`Left20-LandscapeHD3Zone`* を作成します。

* **`Left20`** – 画面サイズの縦横 20％を占める左上部のゾーン。
* **`Landscape`** – 画面の向き。
* **`HD`** – 16:9 の縦横比。
* **`3Zone`** – ディスプレイの 3 つのゾーン。

## マルチゾーンレイアウトの視覚表現 {#multi-layout-visual-one}

`Left20-LandscapeHD3Zone` レイアウトを使用すると、プロジェクトに次のマルチゾーンレイアウトを作成できます。

![画像](/help/user-guide/assets/custom-multizone/landscape-3-zone-new.png)

## `Left20-LandscapeHD3Zone` レイアウトの作成 {#landscape-layout-one}

次の手順に従って、AEM Screens プロジェクト用の `Left20-LandscapeHD3Zone` レイアウトを作成します。

1. **`customtemplate`** というタイトルの AEM Screens プロジェクトを作成します。

   ![画像](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. AEM インスタンス／ツール／**CRXDE Lite** から **CRXDE Lite** に移動します。

1. **apps** の下に、**`customtemplate`** という名前のフォルダーを作成します。同様に、次の図に示すように、**`customtemplate`** の下に、**template** という名前の別のフォルダーを作成します。

   ![画像](/help/user-guide/assets/custom-multizone/custom-template1.png)

   >[!NOTE]
   >コンテンツを作成、編集するたび、またはいずれかのノードにコンテンツをコピーするたびに、CRXDE Lite のアクションバーから「**すべて保存**」をクリックします。そうしないと、更新をコミットできません。

1. lbar-left テンプレートを`/libs/screens/core/templates/splitscreenchannel/lbar-left` から `/apps/customtemplate/template` にコピーします。

1. コピーした **lbar-left**（`/apps/customtemplate/template`）の名前を **my-custom-layout** に変更します。
   ![画像](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. `/apps/customtemplate/template/my-custom-layout` に移動して、プロパティ **`jcr:description`** を `Left20-LandscapeHD3Zone`*の*&#x200B;テンプレートに、**`jcr:title`** を *`Left20-LandscapeHD3Zone`* に更新します。

   ![画像](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config` から **`offline-config`** ノードに移動して、**`jcr:title`** を *`Left20-LandscapeHD3Zone`* に更新します。

   ![画像](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. `/apps/customtemplate/template/my-custom-layout/jcr:content` から **my-custom-template** の *`jcr:content`* プロパティに移動して、**`cq:cssClass`** プロパティを更新し、**aem-Layout my-custom-layout** を使用できるようにします。

   ![画像](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. lbar-left テンプレートをコピーした手順（4）を参照すると、`my-custom-layout/jcr:content` の下に 3 つのレスポンシブグリッドを表示できます。*`cq:cssClass`* プロパティの各レスポンシブグリッドにカスタム css クラスを追加します。例えば、*r1c1* ノードの場合は *my-custom-layout-top-left* です。

   ![画像](/help/user-guide/assets/custom-multizone/custom-template7.png)

   同様に、*r1c2* ノードに対しては *my-custom-layout-top-right* を追加し、*r2c1* ノードに対しては *my-custom-layout-bottom* を追加します。

   >[!NOTE]
   >これらのカスタムクラスは、レスポンシブグリッドの幅と高さを設定するために CSS で使用されます。

   >[!NOTE]
   >レスポンシブグリッドは、必要な合計グリッド数に基づいて追加または削除できます。この例では、最初の行に 2 つのグリッドを、2 番目の行に 1 つのグリッドを表示しているので、合計 3 つのレスポンシブグリッド（r1c1、r1c2、r2c1）があります。

1. `/libs/settings/wcm/designs/screens` を `/apps/settings/wcm/designs/` にコピーして、コピーしたデザインの名前を **custom-template-designs** に変更します。

1. `/apps/settings/wcm/designs/custom-template-designs` に移動して、**custom-template-designs** の *`jcr:title`* プロパティを **customtemplate-design** に更新します。

1. `/apps/settings/wcm/designs/custom-template-designs` に移動して、static.css ファイルを作成します。

1. コンテンツを `static.css` ファイルにコピーします。

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
   >パーセンテージは、カスタムテンプレートの要件に合わせて更新できます。

1. `/apps/<project>/templates/my-custom-layout/jcr:content` に移動し、*`cq:designPath`* プロパティを `/apps/settings/wcm/designs/customtemplate-designs` に更新して、static.css で設定されたスタイルを読み込みます。

   >[!NOTE]
   >コピーして貼り付けると、空白が発生して CSS のスタイル設定に問題が生じる可能性があるので、すべてのスタイルを手動で入力します。

## 結果の表示 {#viewing-result}

以下の手順に従って、AEM Screens プロジェクトで上記のカスタマイズされたテンプレートを使用します。

1. 手順 1 で作成した Screens プロジェクトに移動し、**チャネル**&#x200B;フォルダーを選択します。

   ![画像](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. アクションバーで「**作成**」をクリックし、**作成**&#x200B;ウィザードで **`Left20-LandscapeHD3Zone`** テンプレートをクリックします。

   ![画像](/help/user-guide/assets/custom-multizone/custom-template9.png)

1. カスタマイズしたテンプレートを使用してチャネルを作成したら、エディターからチャネルにアセットを追加できます。次のプレビューは、カスタムテンプレート内の画像を示しています。

   ![画像](/help/user-guide/assets/custom-multizone/custom-template10.png)

## 背景レイヤーとしての画像の挿入  {#inserting-image}

画像を背景レイヤーとしてレイアウトに挿入できます。

「data-uri」を使用して画像（`Base64` エンコード済み）を CSS ファイル（手順 13 で作成した *static.css*）に直接埋め込むように、CSS ルールを調整できます。

この配置は次のようにします。
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

または、次の手順に従うこともできます。

1. 画像を何らかの形でチャネルのオフライン設定に含めます。
1. 上記の CSS で、「data-uri」バリアントではなく、画像への直接リンクを使用します。


## 背景色の更新 {#updating-color}

背景色を変更するには、xml ファイル（手順 13 で作成した *static.css*）に次のコードを追加します。

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`
