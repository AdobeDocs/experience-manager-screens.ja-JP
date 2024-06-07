---
title: AEM Screens コンポーネントの拡張
description: このチュートリアルでは、標準搭載の AEM Screens コンポーネントを拡張する際の手順とベストプラクティスについて説明します。画像コンポーネントが拡張されて、オーサリング可能なテキストオーバーレイが追加されます。
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
targetaudience: target-audience new
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: e316614f-2d40-4b62-a1e5-f30817def742
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: ht
source-wordcount: '1700'
ht-degree: 100%

---

# AEM Screens コンポーネントの拡張

以下のチュートリアルでは、標準搭載の AEM Screens コンポーネントを拡張する際の手順とベストプラクティスについて説明します。画像コンポーネントが拡張されて、オーサリング可能なテキストオーバーレイが追加されます。

## 概要 {#overview}

このチュートリアルは、AEM Screens を初めて使用する開発者を対象としています。このチュートリアルでは、Screens 画像コンポーネントを拡張して、ポスターコンポーネントを作成します。タイトル、説明、ロゴを画像の上にオーバーレイして、シーケンスチャネル内に魅力的なエクスペリエンスを作成します。

>[!NOTE]
>
>このチュートリアルを開始する前に、[AEM Screens 用カスタムコンポーネントの開発](developing-custom-component-tutorial-develop.md)のチュートリアルを完了しておくことをお勧めします。

![カスタムポスターコンポーネント](assets/2018-05-07_at_4_09pm.png)

`Custom Poster` コンポーネントは、画像コンポーネントを拡張して作成します。

## 前提条件 {#prerequisites}

このチュートリアルを完了するには、以下が必要になります。

1. AEM 6.5 および最新の Screens 機能パック
1. [AEM Screens Player](/help/user-guide/aem-screens-introduction.md)
1. ローカル開発環境

CRXDE-Lite を使用して、チュートリアルの手順とスクリーンショットを実行します。[Eclipse](https://experienceleague.adobe.com/ja/docs/experience-manager-65/content/implementing/developing/devtools/aem-eclipse) IDE または [IntelliJ](https://experienceleague.adobe.com/ja/docs/experience-manager-65/content/implementing/developing/devtools/ht-intellij) IDE を使用しても、このチュートリアルを完了できます。AEM での開発に IDE を使用する方法について詳しくは、[こちら](https://experienceleague.adobe.com/ja/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/project-setup)を参照してください。

## プロジェクトのセットアップ {#project-setup}

Screens プロジェクトのソースコードは、通常、マルチモジュールの Maven プロジェクトとして管理されます。このチュートリアルを効率よく進めるために、[AEM プロジェクトアーキタイプ 13](https://github.com/adobe/aem-project-archetype) を使用してプロジェクトを事前に生成してあります。Maven AEM プロジェクトアーキタイプを使用したプロジェクトの作成について詳しくは、[こちら](https://experienceleague.adobe.com/ja/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/project-setup)を参照してください。

1. **CRX パッケージマネージャー**（`http://localhost:4502/crx/packmgr/index.jsp)r:`）を使用して、次のパッケージをダウンロードしてインストールします。

[ファイルの取得](assets/start-poster-screens-weretail-runuiapps-001-snapshot.zip)

   [ファイルを入手](assets/start-poster-screens-weretail-runuicontent-001-snapshot.zip)
   **（オプション）** Eclipse などの IDE を使用して作業する場合は、以下のソースパッケージをダウンロードします。次の Maven コマンドを使用して、プロジェクトをローカルの AEM インスタンスにデプロイします。

   **`mvn -PautoInstallPackage clean install`**

   SRC Start Screens `We.Retail` Run Project

[ファイルの取得](assets/start-poster-screens-weretail-run.zip)

1. **CRX パッケージマネージャー**（`http://localhost:4502/crx/packmgr/index.jsp`）で、次の 2 つのパッケージがインストールされていることを確認します。

   1. **`screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip`**
   1. **`screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip`**

   ![CRX パッケージマネージャーを使用してインストールされた Screens We.Retail Run Ui.Apps および Ui.Content パッケージ](assets/crx-packages.png)

   CRX パッケージマネージャーを使用してインストールされた AEM Screens `We.Retail Run Ui.Apps` および `Ui.Content` パッケージ

## ポスターコンポーネントの作成 {#poster-cmp}

ポスターコンポーネントは、標準の AEM Screens 画像コンポーネントを拡張します。 Sling の `sling:resourceSuperType` メカニズムを使用すると、画像コンポーネントのコア機能をコピーして貼り付けなくても継承できるようになります。Sling のリクエスト処理の基本について詳しくは、[こちら](https://experienceleague.adobe.com/ja/docs/experience-manager-65/content/implementing/developing/introduction/the-basics)を参照してください。

ポスターコンポーネントは、プレビュー／実稼動モードではフルスクリーンでレンダリングされます。編集モードでは、シーケンスチャネルのオーサリングを容易に行えるように、コンポーネントをフルスクリーン以外でレンダリングすることが重要です。

1. **CRXDE-Lite** `http://localhost:4502/crx/de/index.jsp`（または任意の IDE）で、`/apps/weretail-run/components/content` の下に `poster` という名前の `cq:Component` を作成します。

   `poster` コンポーネントに次のプロパティを追加します。

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Poster"
       sling:resourceSuperType="screens/core/components/content/image"
       componentGroup="We.Retail Run - Content"/>
   ```

   ![/apps/weretail-run/components/content/poster のプロパティ](assets/poster.png)

   /apps/weretail-run/components/content/poster のプロパティ

   `sling:resourceSuperType` プロパティを `screens/core/components/content/image` に設定すると、ポスターコンポーネントは画像コンポーネントのすべての機能を事実上継承します。機能を上書きおよび拡張するために、`screens/core/components/content/image` の下にある同等のノードおよびファイルを `poster` コンポーネントの下に追加することができます。

1. `/libs/screens/core/components/content/image` の下にある `cq:editConfig` ノードをコピーします。`/apps/weretail-run/components/content/poster` コンポーネントの下に `cq:editConfig` をペーストします。

   `cq:editConfig/cq:dropTargets/image/parameters` ノードで、`sling:resourceType` プロパティを `weretail-run/components/content/poster` と等しくなるように更新します。

   ![edit-config](assets/edit-config.png)

   `cq:editConfig` の XML 表現は次のようになります。

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:nt="https://www.jcp.org/jcr/nt/1.0"
       jcr:primaryType="cq:EditConfig">
       <cq:dropTargets jcr:primaryType="nt:unstructured">
           <image
               jcr:primaryType="cq:DropTargetConfig"
               accept="[image/.*]"
               groups="[media]"
               propertyName="./fileReference">
               <parameters
                   jcr:primaryType="nt:unstructured"
                   sling:resourceType="weretail-run/components/content/poster"
                   imageCrop=""
                   imageMap=""
                   imageRotate=""/>
           </image>
       </cq:dropTargets>
   </jcr:root>
   ```

1. WCM 基盤コンポーネントの `image` ダイアログをコピーして、`poster` コンポーネントに使用します。

   既存のダイアログを出発点にして、それに変更を加えるのが最も簡単です。

   1. ダイアログのコピー元：`/libs/wcm/foundation/components/image/cq:dialog`
   1. ダイアログの貼り付け先のパス：`/apps/weretail-run/components/content/poster`

   ![/libs/wcm/foundation/components/image/cq:dialog を /apps/weretail-run/components/content/poster にコピーした後](assets/2018-05-03_at_4_13pm.png)

   ダイアログを `/libs/wcm/foundation/components/image/cq:dialog` から `/apps/weretail-run/components/content/poster` にコピーしました

   WCM の `image` 基盤コンポーネントは、AEM Screens `image` コンポーネントのスーパータイプになります。したがって、`poster` コンポーネントは両者から機能を継承します。ポスターコンポーネントのダイアログは、Screens ダイアログと基盤ダイアログの組み合わせで構成されます。**Sling Resource Merger** の機能を使用して、スーパータイプコンポーネントから継承した無関係なダイアログフィールドやタブを非表示にします。

1. `/apps/weretail-run/components/content/poster` の下の `cq:dialog` を更新して、XML で表現された以下の変更を反映します。

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:nt="https://www.jcp.org/jcr/nt/1.0"
       jcr:primaryType="nt:unstructured"
       jcr:title="Poster"
       sling:resourceType="cq/gui/components/authoring/dialog">
       <content
           jcr:primaryType="nt:unstructured"
           sling:resourceType="granite/ui/components/foundation/container">
           <layout
               jcr:primaryType="nt:unstructured"
               sling:resourceType="granite/ui/components/foundation/layouts/tabs"
               type="nav"/>
           <items jcr:primaryType="nt:unstructured">
               <image
                   jcr:primaryType="nt:unstructured"
                   jcr:title="Elements"
                   sling:resourceType="granite/ui/components/foundation/section">
                   <layout
                       jcr:primaryType="nt:unstructured"
                       sling:resourceType="granite/ui/components/foundation/layouts/fixedcolumns"
                       margin="{Boolean}false"/>
                   <items jcr:primaryType="nt:unstructured">
                       <column
                           jcr:primaryType="nt:unstructured"
                           sling:resourceType="granite/ui/components/foundation/container">
                           <items
                               jcr:primaryType="nt:unstructured"
                               sling:hideChildren="[linkURL,size]">
                               <file
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="cq/gui/components/authoring/dialog/fileupload"
                                   autoStart="{Boolean}false"
                                   class="cq-droptarget"
                                   fieldLabel="Image asset"
                                   fileNameParameter="./fileName"
                                   fileReferenceParameter="./fileReference"
                                   mimeTypes="[image]"
                                   multiple="{Boolean}false"
                                   name="./file"
                                   title="Upload Image Asset"
                                   uploadUrl="${suffix.path}"
                                   useHTML5="{Boolean}true"/>
                               <title
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/foundation/form/textfield"
                                   fieldLabel="Title"
                                   name="./jcr:title"/>
                               <description
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/foundation/form/textarea"
                                   fieldLabel="Description"
                                   name="./jcr:description"/>
                               <position
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/click"
                                   fieldLabel="Text Position"
                                   name="./textPosition">
                                   <items jcr:primaryType="nt:unstructured">
                                       <left
                                           jcr:primaryType="nt:unstructured"
                                           text="Left"
                                           value="left"/>
                                       <center
                                           jcr:primaryType="nt:unstructured"
                                           text="Center"
                                           value="center"/>
                                       <right
                                           jcr:primaryType="nt:unstructured"
                                           text="Right"
                                           value="right"/>
                                   </items>
                               </position>
                               <color
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/click"
                                   fieldLabel="Text Color"
                                   name="./textColor">
                                   <items jcr:primaryType="nt:unstructured">
                                       <light
                                           jcr:primaryType="nt:unstructured"
                                           text="Light"
                                           value="light"/>
                                       <dark
                                           jcr:primaryType="nt:unstructured"
                                           text="Dark"
                                           value="dark"/>
                                   </items>
                               </color>
                           </items>
                       </column>
                   </items>
               </image>
               <accessibility
                   jcr:primaryType="nt:unstructured"
                   sling:hideResource="{Boolean}true"/>
           </items>
       </content>
   </jcr:root>
   ```

   `items` ノードでプロパティ `sling:hideChildren`= `"[linkURL,size]`&quot; を使用して、**linkURL** フィールドと **size** フィールドがダイアログで非表示になるようにします。これらのノードをポスターダイアログから削除するだけでは不十分です。「アクセシビリティ」タブのプロパティ `sling:hideResource="{Boolean}true"` は、タブ全体を非表示にするために使用されます。

   ダイアログボックスに、テキストの位置とテキストの色という 2 つのクリックフィールドが追加され、作成者がタイトルと説明のテキストの位置と色を制御できるようになります。

   ![ポスター - 最終的なダイアログ構造](assets/2018-05-03_at_4_49pm.png)

   ポスター - 最終的なダイアログ構造

   この段階で、`poster` コンポーネントのインスタンスを `We.Retail` 実行プロジェクトの&#x200B;**アイドルチャネルl**&#x200B;ページ（`http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`）に追加できます。

   ![ポスターダイアログのフィールド](assets/poster-dialog-full.png)

   ポスターダイアログのフィールド

1. `/apps/weretail-run/components/content/poster` の下に `production.html.` という名前のファイルを作成します。

   ファイルに以下のように入力します。

   ```xml
   <!--/*
   
       /apps/weretail-run/components/content/poster/production.html
   
   */-->
   <div data-sly-use.image="image.js"
        data-duration="${properties.duration}"
        class="cmp-poster"
        style="background-image: url(${request.contextPath @ context='uri'}${image.src @ context='uri'});">
       <div class="cmp-poster__text
                   cmp-poster__text--${properties.textPosition @ context='attribute'}
                   cmp-poster__text--${properties.textColor @ context='attribute'}">
           <h1 class="cmp-poster__title">${properties.jcr:title}</h1>
            <h2 class="cmp-poster__description">${properties.jcr:description}</h2>
       </div>
    <img class="cmp-poster__logo" src="/content/dam/we-retail-run/logos/we-retail-run_dark.png" alt="we-retail-logo" />
   </div>
   ```

   ポスターコンポーネントの実稼動マークアップは、すぐ上に表示されます。HTL スクリプトで `screens/core/components/content/image/production.html` が上書きされます。`image.js` は、POJO に似た画像オブジェクトを作成するサーバー側スクリプトです。この画像オブジェクトを呼び出して、`src` をインラインスタイルの背景画像としてレンダリングできます。

   `The h1` タグと h2 タグを追加して、コンポーネントプロパティ `${properties.jcr:title}` および `${properties.jcr:description}` に基づいて「タイトル」と「説明」を表示します。

   「`cmp-poster__text`」のバリエーションを使用する 3 つの CSS クラスを含んだ div ラッパーで、`h1` タグと `h2` タグを囲みます。`textPosition` プロパティと `textColor` プロパティの値を使用し、作成者によるダイアログ選択に基づいてレンダリングされる CSS クラスを変更します。次の節では、クライアントライブラリの CSS を記述して、これらの変更をディスプレイに反映します。

   コンポーネントには、ロゴもオーバーレイとして含まれます。この例では、` We.Retail` ロゴのパスが DAM にハードコーディングされています。ユースケースによっては、ダイアログフィールドを作成して、ロゴのパスを動的に入力される値にする方が合理的な場合があります。

   また、コンポーネントでは BEM（ブロック要素修飾子）表記が使用されることにも注意してください。BEM は、再利用可能なコンポーネントを容易に作成できる CSS コーディング規則です。BEM は、[AEM のコアコンポーネント](https://github.com/adobe/aem-core-wcm-components/wiki/CSS-coding-conventions)で使用される表記です。<!-- DEAD LINK More info can be found at: [https://getbem.com/](https://getbem.com/) -->

1. `/apps/weretail-run/components/content/poster` の下に `edit.html.` という名前のファイルを作成します。

   ファイルに以下のように入力します。

   ```xml
   <!--/*
   
       /apps/weretail-run/components/content/poster/edit.html
   
   */-->
   
   <div class="aem-Screens-editWrapper ${image.cssClass} cmp-poster" data-sly-use.image="image.js" data-emptytext="${'Poster' @ i18n, locale=request.locale}">
       <img class="cmp-poster__image" src="${request.contextPath}${image.src @ context='uri'}" width="100%" />
       <div class="cmp-poster__text
              cmp-poster__text--${properties.textPosition @ context='attribute'}
          cmp-poster__text--${properties.textColor @ context='attribute'}">
         <p class="cmp-poster__title">${properties.jcr:title}</p>
         <p class="cmp-poster__description">${properties.jcr:description}</p>
       </div>
   </div>
   ```

   ポスターコンポーネントの&#x200B;**編集**&#x200B;マークアップは、すぐ上に表示されます。HTL スクリプトで `/libs/screens/core/components/content/image/edit.html` が上書きされます。このマークアップは `production.html` のマークアップと似ており、画像の上にタイトルと説明が表示されます。

   コンポーネントがエディターでフルスクリーンでレンダリングされないように、`aem-Screens-editWrapper` を追加します。`data-emptytext` 属性を指定すると、画像やコンテンツが入力されていない場合には必ずプレースホルダーが表示されるようになります。

## クライアント側ライブラリの作成 {#clientlibs}

クライアント側ライブラリは、AEM の実装で必要な CSS および JavaScript ファイルの編成および管理のための仕組みを提供します。クライアント側ライブラリの使用の詳細については、[こちら](https://experienceleague.adobe.com/ja/docs/experience-manager-65/content/implementing/developing/introduction/clientlibs)を参照してください。

AEM Screens コンポーネントは、編集モードとプレビュー／実稼動モードではレンダリングが異なります。2 組のクライアントライブラリが作成されます。1 つは編集モード用、もう 1 つはプレビュー／実稼動用です。

1. ポスターコンポーネントのクライアント側ライブラリ用のフォルダーを作成します。

   `/apps/weretail-run/components/content/poster` の下に、`clientlibs` という名前のフォルダーを作成します。

   ![2018-05-03_at_1008pm](assets/2018-05-03_at_1008pm.png)

1. `clientlibs` フォルダーの下に、タイプ `cq:ClientLibraryFolder.` の `shared` という名前のノードを作成します。

   ![2018-05-03_at_1011pm](assets/2018-05-03_at_1011pm.png)

1. 共有クライアントライブラリに次のプロパティを追加します。

   * `allowProxy` | Boolean | `true`
   * `categories` | String[] | `cq.screens.components`

   ![/apps/weretail-run/components/content/poster/clientlibs/shared のプロパティ](assets/2018-05-03_at_1026pm-1.png)

   /apps/weretail-run/components/content/poster/clientlibs/shared のプロパティ

   `categories` プロパティは、クライアントライブラリを識別する文字列です。`cq.screens.components` カテゴリは、編集モードとプレビュー／実稼動モードの両方で使用されます。したがって、`shared` clientlib で定義された CSS／JavaScript は、すべてのモードで読み込まれます。

   ベストプラクティスとして、実稼動環境の `/apps` を直接指すパスは、公開しないでください。`allowProxy` プロパティにより、クライアントライブラリの CSS と JavaScript が `/etc.clientlibs` の接頭辞を付けて参照されるようになります。allowProxy について詳しくは、[こちら](https://experienceleague.adobe.com/ja/docs/experience-manager-65/content/implementing/developing/introduction/clientlibs)を参照してください。

1. 共有フォルダーの下に `css.txt` という名前のファイルを作成します。

   ファイルに以下のように入力します。

   ```
   #base=css
   
   styles.less
   ```

1. `shared` フォルダーの下に `css` という名前のフォルダーを作成します。`css` フォルダーの下に、`style.less` という名前のファイルを追加します。クライアントライブラリの構造は次のようになります。

   ![2018-05-03_at_1057pm](assets/2018-05-03_at_1057pm.png)

   このチュートリアルでは、CSS を直接記述するのではなく、LESS を使用します。[LESS](https://lesscss.org/) は、CSS 変数、ミックスイン、関数をサポートしている一般的な CSS プリコンパイラーです。AEM のクライアントライブラリは、LESS によるコンパイルをネイティブにサポートしています。Sass などのプリコンパイラーも使用できますが、AEM の外部でコンパイルする必要があります。

1. `/apps/weretail-run/components/content/poster/clientlibs/shared/css/styles.less` に以下を入力します。

   ```css
   /*
    /apps/weretail-run/components/content/poster/clientlibs/shared/css/styles.less
    Poster component - Shared Style
   */
   
   @import url('https://fonts.googleapis.com/css?family=Fjalla+One|Open+Sans:400i');
   
   @text-light-color: #fff;
   @text-dark-color: #000;
   @title-font-family: 'Fjalla One', sans-serif;
   @description-font-family: 'Open Sans', sans-serif;
   
   .cmp-poster {
   
         &__text {
         position: absolute;
         color: @text-light-color;
         top: 0;
         text-align:center;
         width: 100%;
   
         &--left {
          text-align: left;
                margin-left: 1em;
         }
   
         &--right {
          text-align: right;
                margin-right: 1em;
         }
   
         &--dark {
          color: @text-dark-color;
         }
       }
   
       &__title {
         font-weight: bold;
            font-family: @title-font-family;
            font-size: 1.2em;
       }
   
       &__description {
     font-style: italic;
           font-family: @description-font-family;
    }
   
   }
   ```

   >[!NOTE]
   >
   >フォントファミリーには Google web フォントが使用されます。Web フォントを使用するにはインターネット接続が必要ですが、すべての AEM Screens 実装に信頼性の高い接続があるとは限りません。オフラインモードへの対応を計画することは、AEM Screens デプロイメントの重要な考慮事項です。

1. クライアントライブラリフォルダー `shared` をコピーします。兄弟として貼り付け、名前を `production` に変更します。

   ![2018-05-03_at_1114pm](assets/2018-05-03_at_1114pm.png)

1. 本番用クライアントライブラリの `categories` プロパティを `cq.screens.components.production.` に更新します。

   `cq.screens.components.production` カテゴリにより、プレビュー／実稼動モードの場合のみ、スタイルが読み込まれるようになります。

   ![/apps/weretail-run/components/content/poster/clientlibs/production のプロパティ](assets/2018-04-30_at_5_04pm.png)

   /apps/weretail-run/components/content/poster/clientlibs/production のプロパティ

1. `/apps/weretail-run/components/content/poster/clientlibs/production/css/styles.less` に以下を入力します。

   ```css
   /*
    /apps/weretail-run/components/content/poster/clientlibs/production/css/styles.less
    Poster component - Production Style
   */
   
   .cmp-poster {
   
       background-size: cover;
    height: 100%;
    width: 100%;
    position:absolute;
   
        &__text {
   
           top: 2em;
   
           &--left {
               width: 40%;
               top: 5em;
           }
   
           &--right {
               width: 40%;
               right: 1em;
           }
       }
   
       &__title {
     font-size: 5rem;
     font-weight: 900;
     margin: 0.1rem;
    }
   
    &__description {
     font-size: 2rem;
     margin: 0.1rem;
     font-weight: 400;
   
    }
   
       &__logo {
     position: absolute;
     max-width: 200px;
     top: 1em;
     left: 0;
    }
   
   }
   ```

   上記のスタイルでは、「タイトル」と「説明」がスクリーン上の絶対位置に表示されます。タイトルは説明よりも大きく表示されます。コンポーネントの BEM 表記により、cmp-poster クラス内のスタイルを注意深くスコープ設定するのが容易になります。

3 番目のクライアントライブラリカテゴリ `cq.screens.components.edit` は、コンポーネントに編集専用のスタイルを追加する場合に使用できます。

| クライアントライブラリカテゴリ | 使用方法 |
|---|---|
| `cq.screens.components` | スタイルとスクリプトが編集モードと実稼動モードの両方で共有される |
| `cq.screens.components.edit` | スタイルとスクリプトが編集モードでのみ使用される |
| `cq.screens.components.production` | スタイルとスクリプトが実稼動モードでのみ使用される |

## シーケンスチャネルへのポスターコンポーネントの追加 {#add-sequence-channel}

ポスターコンポーネントは、シーケンスチャネルで使用されます。このチュートリアルのスターターパッケージには、アイドルチャネルが含まれています。アイドルチャネルは、**`We.Retail Run - Content`** グループのコンポーネントを許可するように事前設定されています。ポスターコンポーネントのグループは `We.Retail Run - Content` に設定されており、チャネルに追加できるようになっています。

1. `We.Retail` 実行プロジェクトのアイドルチャネル（**`http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`**）を開きます。
1. **ポスター**&#x200B;コンポーネントの新しいインスタンスをサイドバーからページにドラッグ＆ドロップします。

   ![2018-05-07_at_3_23pm](assets/2018-05-07_at_3_23pm.png)

1. ポスターコンポーネントのダイアログボックスを編集して、「画像」、「タイトル」、「説明」を追加します。「テキストの位置」と「テキストの色」の選択フィールドを使用して、「タイトル」や「説明」が画像上で読みやすくなるようにします。

   ![2018-05-07_at_3_25pm](assets/2018-05-07_at_3_25pm.png)

1. いくつかのポスターコンポーネントを追加するには、上記の手順を繰り返します。 コンポーネント間にトランジション（トランジション）を追加します。

   ![2018-05-07_at_3_28pm](assets/2018-05-07_at_3_28pm.png)

## まとめ {#putting-it-all-together}

以下のビデオでは、完成したコンポーネントと、それをシーケンスチャネルに追加する方法を示しています。この後、チャネルはロケーションのディスプレイに追加され、最終的には Screens Player に割り当てられます。

>[!VIDEO](https://video.tv.adobe.com/v/22414?quaity=9)

## 完成したコード {#finished-code}

チュートリアルで完成したコードは以下のとおりです。**screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip** と **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip** は、コンパイル済みの AEM パッケージです。**SRC-screens-weretail-run-0.0.1.zip** は、Maven を使用してデプロイできる未コンパイルのソースコードです。

[ファイルの取得](assets/final-poster-screens-weretail-runuiapps-001-snapshot.zip)

[ファイルの取得](assets/final-poster-screens-weretail-runuicontent-001-snapshot.zip)

SRC Final AEM Screens `We.Retail` Run Project

[ファイルの取得](assets/src-screens-weretail-run-001.zip)
