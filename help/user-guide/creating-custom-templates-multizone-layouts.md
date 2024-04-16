---
title: マルチゾーンレイアウトのカスタムテンプレートの作成
description: AEM Screens用 MultiZone レイアウトでカスタムテンプレートを作成する方法について説明します。
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 3f4813f8-0438-4ce0-9046-84025de0ddd1
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 28%

---

# マルチゾーンレイアウトでのカスタムテンプレートの作成 {#creating-custom-templates-multizone}

ここでは、マルチゾーンレイアウトでのカスタムテンプレートの作成方法を説明します。

## 重要な検討事項 {#considerations}

マルチゾーンレイアウトでカスタムテンプレートを作成する前に注意する必要がある重要な検討事項は 2 つあります。

1. **固定ピクセルサイズまたはパーセンテージ**：

   カスタムレイアウトで様々なゾーンに固定ピクセルサイズを使用するか、割合を使用してカスタムレイアウトを作成するかを決定します。

   >[!NOTE]
   >パーセンテージを使用してカスタムレイアウトのゾーンを設定する利点により、様々な画面サイズでテンプレートを再利用できます。

1. **命名規則**：

   AEM Screens プロジェクトで使用するカスタムのマルチゾーンテンプレートを作成する方法を理解する前に、作成するテンプレートの概要を理解する必要があります。

   | **レイアウト名** | **説明** |
   |---|---|
   | `Left20-LandscapeHD3Zone` | 3 つのゾーンを作成できる 3 ゾーンの横長レイアウト：<br>* ゾーン 1 を左から水平および垂直スクリーンの 20% として表示<br>* ゾーン 2 を水平方向の画面の 80 %、垂直方向の画面の右に揃えて表示<br>* ゾーン 3:100 % の水平および 80 % の垂直スクリーン、アスペクト比 16:9 |
   | `Upper20-PortraitHD2Zone` | 画面の 20% を上からカバーする縦横比 16:9 の 2 ゾーンの縦長テンプレート |
   | `Right20-LandscapeSD3Zone` | 画面の 20% を右からカバーする 3 ゾーンテンプレート。縦横比は 4:3 |

   >[!IMPORTANT]
   >カスタムレイアウト内で定義されたゾーンは、レイアウト全体の縦横比と一致しない場合があります。このドキュメントで従う命名規則では、カスタムレイアウト全体の縦横比を指定します。

## 使用例 `Left20-LandscapeHD3Zone` レイアウト {#custom-template-one}

以下の節に従って、カスタムテンプレートを作成します *`Left20-LandscapeHD3Zone`* に作成し、次のように設定します。

* **`Left20`**  – 左側のトップゾーンで、画面の水平方向および垂直方向のサイズの 20% をカバーしています。
* **`Landscape`**  – 画面の向き。
* **`HD`**  – 縦横比は 16:9 です。
* **`3Zone`** - ディスプレイの 3 つのゾーン。

## マルチゾーンレイアウトの視覚的表現 {#multi-layout-visual-one}

この `Left20-LandscapeHD3Zone` レイアウトを使用すると、プロジェクトに次のマルチゾーンレイアウトを作成できます。

![画像](/help/user-guide/assets/custom-multizone/landscape-3-zone-new.png)

## の作成 `Left20-LandscapeHD3Zone` レイアウト {#landscape-layout-one}

以下の手順に従って、 `Left20-LandscapeHD3Zone` AEM Screens プロジェクトのレイアウト。

1. というタイトルのAEM Screens プロジェクトの作成 **`customtemplate`**.

   ![画像](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. に移動します。 **CRXDE Lite** AEM インスタンス/ ツール /から **CRXDE Lite**.

1. の下にフォルダーを作成 **apps** タイトルは **`customtemplate`**. 同様に、という名前の別のフォルダーを作成します。 **template** 未満 **`customtemplate`**&#x200B;を参照してください（下図を参照）。

   ![画像](/help/user-guide/assets/custom-multizone/custom-template1.png)

   >[!NOTE]
   >クリック **すべて保存** コンテンツを作成、編集または任意のノードにコピーするたびに、CRXDE Liteのアクションバーから。 追加されていない場合は、更新をコミットできません。

1. lbar-left テンプレートを`/libs/screens/core/templates/splitscreenchannel/lbar-left` から `/apps/customtemplate/template` にコピーします。

1. コピーした **lbar-left**（`/apps/customtemplate/template`）の名前を **my-custom-layout** に変更します。
   ![画像](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. に移動します。 `/apps/customtemplate/template/my-custom-layout` プロパティを更新します **`jcr:description`** 対象： *のテンプレート`Left20-LandscapeHD3Zone`* および **`jcr:title`** 対象： *`Left20-LandscapeHD3Zone`*.

   ![画像](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. に移動します。 **`offline-config`** からのノード `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config` を更新します **`jcr:title`** 対象： *`Left20-LandscapeHD3Zone`*.

   ![画像](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. に移動します。 *`jcr:content`* のプロパティ **my-custom-template** から `/apps/customtemplate/template/my-custom-layout/jcr:content` を更新します **`cq:cssClass`** 使用できるプロパティ **aem-Layout my-custom-layout**.

   ![画像](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. lbar-left テンプレートをコピーした手順（4）では、の下に 3 つのレスポンシブグリッドを表示できます `my-custom-layout/jcr:content`. の各レスポンシブグリッドへのカスタム css クラスの追加 *`cq:cssClass`* プロパティ（例：） *my-custom-layout-top-left* （用） *r1c1* ノード。

   ![画像](/help/user-guide/assets/custom-multizone/custom-template7.png)

   同様に、*r1c2* ノードに対しては *my-custom-layout--top-right* を追加し、*r2c1* ノードに対しては *my-custom-layout--bottom* を追加します。

   >[!NOTE]
   >これらのカスタムクラスは、css で使用され、これらのレスポンシブグリッドの幅と高さを設定します。

   >[!NOTE]
   >レスポンシブグリッドは、必要な合計グリッド数に基づいて追加または削除できます。この例では、最初の行に 2 つのグリッド、2 番目の行に 1 つのグリッドが表示されるので、合計 3 つのレスポンシブグリッド（r1c1、r1c2、r2c1）があります。

1. `/libs/settings/wcm/designs/screens` を `/apps/settings/wcm/designs/` にコピーして、コピーしたデザインの名前を **custom-template-designs** に変更します。

1. に移動します。 `/apps/settings/wcm/designs/custom-template-designs` およびプロパティの更新 *`jcr:title`* 件中 **custom-template-designs** 対象： **customtemplate-design**.

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

1. に移動します。 `/apps/<project>/templates/my-custom-layout/jcr:content` およびプロパティの更新 *`cq:designPath`* 対象： `/apps/settings/wcm/designs/customtemplate-designs` そのため、static.css で設定したスタイルを読み込むことができます。

   >[!NOTE]
   >コピーや貼り付けではなくスタイルをすべて入力します。空白が原因で css スタイル設定の問題が発生する可能性があります。

## 結果の表示 {#viewing-result}

以下の手順に従って、AEM Screens プロジェクトでカスタマイズされた上記のテンプレートを使用します。

1. 手順（1）で作成した Screens プロジェクトに移動し、 **チャネル** フォルダー。

   ![画像](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. クリック **作成** アクションバーでテンプレートをクリックします。 **`Left20-LandscapeHD3Zone`** から **作成** ウィザード。

   ![画像](/help/user-guide/assets/custom-multizone/custom-template9.png)

1. カスタマイズしたテンプレートでチャネルを作成したら、エディターからチャネルにアセットを追加できます。 次のプレビューは、カスタムテンプレート内の画像を示しています。

   ![画像](/help/user-guide/assets/custom-multizone/custom-template10.png)

## 画像を背景レイヤーとして挿入する  {#inserting-image}

画像を背景レイヤーとしてレイアウトに挿入できます。

CSS ルールを「data-uri」を使用するように調整し、画像を直接インライン化できます（`Base64` （エンコード済み）に保存する必要があります。（手順 13） *static.css*.

それには次のようにします。
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

または、次の手順に従うこともできます。

1. 画像がチャネルのオフライン設定に何らかの形で含まれていることを確認してください。
1. 上記の CSS で、「data-uri」バリアントの代わりに画像への直接リンクを使用します。


## 背景色の更新 {#updating-color}

背景色を変更するには、CSS ファイル（手順 13 で作成した *static.css*）に次のコードを追加します。

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`
