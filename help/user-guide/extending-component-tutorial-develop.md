---
title: AEM Screensコンポーネントの拡張
seo-title: AEM Screensコンポーネントの拡張
description: 次のチュートリアルでは、AEM Screensコンポーネントを標準搭載した状態で拡張するための手順とベストプラクティスについて説明します。 画像コンポーネントが拡張され、承認可能なテキストオーバーレイが追加されます。
seo-description: 次のチュートリアルでは、AEM Screensコンポーネントを標準搭載した状態で拡張するための手順とベストプラクティスについて説明します。 画像コンポーネントが拡張され、承認可能なテキストオーバーレイが追加されます。
uuid: 38ee3a2b-a51a-4c35-b93a-89a0e5fc3837
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
discoiquuid: 46bdc191-5056-41a4-9804-8f7c4a035abf
targetaudience: target-audience new
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# AEM Screensコンポーネントの拡張 {#extending-an-aem-screens-component}

次のチュートリアルでは、AEM Screensコンポーネントを標準搭載した状態で拡張するための手順とベストプラクティスについて説明します。 画像コンポーネントが拡張され、承認可能なテキストオーバーレイが追加されます。

## 概要 {#overview}

このチュートリアルは、AEM Screensを初めて使用する開発者を対象としています。 このチュートリアルでは、画面の画像コンポーネントを拡張して、ポスターコンポーネントを作成します。 タイトル、説明、ロゴが画像の上に重ねて表示され、シーケンスチャネル内で魅力的なエクスペリエンスを作成できます。

>[!NOTE]
>
>このチュートリアルを開始する前に、次のチュートリアルを完了することをお勧めします。AEM Screensの [カスタムコンポーネントの開発](developing-custom-component-tutorial-develop.md)。

![カスタムポスターコンポーネント](assets/2018-05-07_at_4_09pm.png)

カスタムポスターコンポーネントは、画像コンポーネントを拡張することで作成されます。

## 前提条件 {#prerequisites}

## Project Setup {#project-setup}

1. CRXパッケージ管理を使用して、次のパッケージをダウンロードし **てインストールします** 。 `http://localhost:4502/crx/packmgr/index.jsp)r:`

   [ファイルの取得](assets/start-poster-screens-weretail-runuiapps-001-snapshot.zip)

   [ファイルの取得](assets/start-poster-screens-weretail-runuicontent-001-snapshot.zip)
   **Eclipseまたは他の** IDEを使用する場合は、以下のソースパッケージをダウンロードします。 Mavenコマンドを使用して、プロジェクトをローカルAEMインスタンスにデプロイします。

   **`mvn -PautoInstallPackage clean install`**

   SRC開始画面We.Retail実行プロジェクト

   [ファイルの取得](assets/start-poster-screens-weretail-run.zip)

1. CRX Package Managerに **は**`http://localhost:4502/crx/packmgr/index.jsp` 、次の2つのパッケージがインストールされます。

   1. **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip**
   1. **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**
   ![CRX Package Managerを使用してインストールされるScreens We.Retail Run Ui.AppsおよびUi.Contentパッケージ](assets/crx-packages.png)

   CRX Package Managerを使用してインストールされるScreens We.Retail Run Ui.AppsおよびUi.Contentパッケージ

## ポスターコンポーネントの作成 {#poster-cmp}

ポスターコンポーネントは、初期設定の画面の画像コンポーネントを拡張します。 Slingのメカニズムを使用し `sling:resourceSuperType`て、コピー&amp;ペーストを行うことなく、画像コンポーネントのコア機能を継承します。 Slingリクエスト処理の基本につ [いて詳しくは、こちらを参照してください。](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/the-basics.html#SlingRequestProcessing)

ポスターコンポーネントは、プレビュー/制作モードでフルスクリーンでレンダリングされます。 編集モードでは、シーケンスチャネルのオーサリングを容易にするために、コンポーネントを別々にレンダリングすることが重要です。

1. 下の **CRXDE-Lite** （またはIDE）で、名前を付けた `http://localhost:4502/crx/de/index.jsp` 新しい `/apps/weretail-run/components/content`IDEを作成し `cq:Component` ます `poster`。

   Add the following properties to the `poster` component:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Poster"
       sling:resourceSuperType="screens/core/components/content/image"
       componentGroup="We.Retail Run - Content"/>
   ```

   ![/apps/wertail-run/components/content/posterのプロパティ](assets/poster.png)

   /apps/wertail-run/components/content/posterのプロパティ

   このプロパティをポ `sling:resourceSuperType`スターコンポーネ `screens/core/components/content/image` ントと同じに設定すると、画像コンポーネントのすべての機能が効果的に継承されます。 機能を上書きし拡張するために、コンポ `screens/core/components/content/image` ーネントの下に同等のノード `poster` とファイルを追加することができます。

1. コンポーネントの下 `cq:editConfig` にノード `/libs/screens/core/components/content/image.`を貼り付 `cq:editConfig` けます(Paste the `/apps/weretail-run/components/content/poster` belower)。

   ノード上で、 `cq:editConfig/cq:dropTargets/image/parameters` プロパティが等し `sling:resourceType` い値に更新されま `weretail-run/components/content/poster`す。

   ![edit-config](assets/edit-config.png)

   cq:editConfigのXML表現は次のように表されます。

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

1. コンポーネントに `image` 使用するWCM Foundationをコピーし `poster` ます。

   最も簡単な方法は、既存のダイアログから開始して、変更を加えることです。

   1. ダイアログのコピー元： `/libs/wcm/foundation/components/image/cq:dialog`
   1. ダイアログを下に貼り付け `/apps/weretail-run/components/content/poster`
   ![/libs/wcm/foundation/components/image/cq:dialogから/apps/wetail-run/components/content/posterにダイアログをコピーしました。](assets/2018-05-03_at_4_13pm.png)

   /libs/wcm/foundation/components/image/cq:dialogから/apps/wetail-run/components/content/posterにダイアログをコピーしました。

   Screensコンポーネ `image` ントは、WCM Foundationコンポーネントにスーパータイプさ `image` れます。 したがって、コンポー `poster` ネントは両方から機能を継承します。 ポスターコンポーネントのダイアログは、画面と基本のダイアログの組み合わせで構成されます。 Sling Resource Margerの機能は **** 、スーパータイプ付きコンポーネントから継承された無関係なダイアログフィールドやタブを非表示にするために使用されます。

1. XMLで次の変更が表示されたら、下 `/apps/weretail-run/components/content/poster` のcq:dialogを更新します。

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
                                   sling:resourceType="granite/ui/components/coral/foundation/form/select"
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
                                   sling:resourceType="granite/ui/components/coral/foundation/form/select"
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

   リンクURLと `sling:hideChildren`サイズフィールドがダイアログに表示されないようにするた `"[linkURL,size]`めに、ノードでproperty `items` = ******** "が使用されます。 これらのノードをポスターダイアログから削除するだけでは不十分です。 「アクセシビリ `sling:hideResource="{Boolean}true"` ティ」タブのプロパティは、タブ全体を非表示にするために使用されます。

   2つの選択フィールドがダイアログに追加され、作成者がタイトルと説明のテキストの位置と色を制御できるようになります。

   ![ポスター — 最終的なダイアログ構造](assets/2018-05-03_at_4_49pm.png)

   ポスター — 最終的なダイアログ構造

   この時点で、We.Retail Runプロジェクトの `poster` Idle Channelページにコンポーネ **ントのインスタンスを追加できます** 。 `http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`.

   ![ポスターダイアログフィールド](assets/poster-dialog-full.png)

   ポスターダイアログフィールド

1. Create a file beneath `/apps/weretail-run/components/content/poster` named `production.html.`

   以下のようにファイルを設定します。

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

   上記は、ポスターコンポーネントの制作用のマークアップです。 HTLスクリプトは上書きされま `screens/core/components/content/image/production.html`す。 は、POJO `image.js` に似た画像オブジェクトを作成するサーバーサイドスクリプトです。 その後、Imageオブジェクトを呼び出して、をインラインスタイル `src` のbackground-imageとしてレンダリングできます。

   `The h1` とh2タグが追加され、コンポーネントのプロパティに基づいてタイトルと説明が表示されます。 `${properties.jcr:title}` と `${properties.jcr:description}`。

   タグとタグ `h1` を囲む `h2` のは、「」のバリエーションを持つ3つのCSSクラスを持つdivラッパー `cmp-poster__text`です。 とのプロパティの値は、 `textPosition` 作成者 `textColor` のダイアログの選択に基づいてレンダリングされるCSSクラスを変更するために使用されます。 次のセクションでは、クライアントライブラリのCSSが書き込まれ、これらの変更を表示できるようになります。

   コンポーネントには、ロゴもオーバーレイとして含まれます。 この例では、We.RetailロゴのパスがDAMにハードコードされています。 使用例に応じて、ロゴパスを動的に設定される値にする新しいダイアログフィールドを作成する方が効果的です。

   また、BEM（ブロック要素修飾子）表記がコンポーネントで使用されることにも注意してください。 BEMは、再利用可能なコンポーネントを容易に作成できるCSSコーディング規則です。 BEMは、 [AEMのコアコンポーネントで使用される表記です](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/wiki/CSS-coding-conventions)。 詳しくは、以下を参照してください。https://getbem.com/ [](https://getbem.com/)

1. Create a file beneath `/apps/weretail-run/components/content/poster` named `edit.html.`

   以下のようにファイルを設定します。

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

   上記はポスターコンポ **ーネント** の編集マークアップです。 HTLスクリプトは上書きされま `/libs/screens/core/components/content/image/edit.html`す。 マークアップはマークアップに似 `production.html` ており、画像の上にタイトルと説明が表示されます。

   コンポ `aem-Screens-editWrapper`ーネントがエディターでフルスクリーンをレンダリングしないように、が追加されます。 この属性 `data-emptytext` は、画像やコンテンツが入力されていない場合に、必ずプレースホルダーを表示するようにします。

## クライアント側ライブラリの作成 {#clientlibs}

クライアント側ライブラリは、AEM実装に必要なCSSファイルとJavaScriptファイルを整理および管理するメカニズムを提供します。 クライアント側ライブラリの使用の詳細については、[こちら](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/clientlibs.html)を参照してください。

AEM Screensコンポーネントは、編集モードとプレビュー/制作モードではレンダリングが異なります。 2組のクライアントライブラリが作成され、1つは編集モード用、もう1つはプレビュー/実稼働用です。

1. ポスターコンポーネント用のクライアント側ライブラリ用のフォルダーを作成します。

   Beneath `/apps/weretail-run/components/content/poster,`create a new folder named `clientlibs`.

   ![2018-05-03_at_1008pm](assets/2018-05-03_at_1008pm.png)

1. Beneath the `clientlibs` folder create a new node named `shared` of type `cq:ClientLibraryFolder.`

   ![2018-05-03_at_1011pm](assets/2018-05-03_at_1011pm.png)

1. 共有クライアントライブラリに次のプロパティを追加します。

   * `allowProxy` | Boolean | `true`
   * `categories` | String[] | `cq.screens.components`
   ![/apps/wertail-run/components/content/poster/clientlibs/sharedのプロパティ](assets/2018-05-03_at_1026pm-1.png)

   /apps/wertail-run/components/content/poster/clientlibs/sharedのプロパティ

   このプ `categories` ロパティは、クライアントライブラリを識別する文字列です。 カテゴリ `cq.screens.components` は、編集モードとプレビュー/実稼働モードの両方で使用されます。 したがって、clientlibで定義されたCSS/JSはすべての `shared` モードで読み込まれます。

   実稼働環境では、/appsに直接パスを公開しないことをお勧めします。 このプ `allowProxy` ロパティは、クライアントライブラリのCSSとJSが、のプレフィックスを介して参照されるようにしま `/etc.clientlibs`す。 More information about the [allowProxy property can be found here.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/clientlibs.html#main-pars_title_8ced)

1. 共有フォルダーの下に `css.txt` という名前のファイルを作成します。

   以下のようにファイルを設定します。

   ```
   #base=css
   
   styles.less
   ```

1. フォルダーの下に名前を付け `css` たフォルダーを作 `shared` 成します。 フォルダーの下に、という名前の `style.less` ファイルを追 `css` 加します。 クライアントライブラリの構造は次のようになります。

   ![2018-05-03_at_1057pm](assets/2018-05-03_at_1057pm.png)

   CSSを直接記述する代わりに、このチュートリアルではLESSを使用します。 [LESSは](https://lesscss.org/) 、CSS変数、ミックスイン、関数をサポートする、一般的なCSSプリコンパイラーです。 AEM のクライアントライブラリは、LESS のコンパイルをネイティブにサポートしています。Sassまたは他のプリコンパイラーを使用できますが、AEMの外部でコンパイルする必要があります。

1. 次の値 `/apps/weretail-run/components/content/poster/clientlibs/shared/css/styles.less` を入力します。

   ```css
   /*
    /apps/weretail-run/components/content/poster/clientlibs/shared/css/styles.less
    Poster Component - Shared Style
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
   >Google webフォントは、フォントファミリーに使用されます。 Webフォントはインターネット接続を必要とし、すべての画面を実装した場合に信頼性の高い接続が得られるわけではありません。 オフラインモードの計画は、画面のデプロイメントで重要な考慮事項です。

1. クライアントライブ `shared` ラリフォルダーをコピーします。 兄弟として貼り付け、に名前を変更しま `production`す。

   ![2018-05-03_at_1114pm](assets/2018-05-03_at_1114pm.png)

1. 本番用クライアント `categories` ライブラリのプロパティを `cq.screens.components.production.`

   カテゴ `cq.screens.components.production` リでは、プレビュー/実稼働モードでのみスタイルが読み込まれます。

   ![/apps/wertail-run/components/content/poster/clientlibs/productionのプロパティ](assets/2018-04-30_at_5_04pm.png)

   /apps/wertail-run/components/content/poster/clientlibs/productionのプロパティ

1. 次の値 `/apps/weretail-run/components/content/poster/clientlibs/production/css/styles.less` を入力します。

   ```css
   /*
    /apps/weretail-run/components/content/poster/clientlibs/production/css/styles.less
    Poster Component - Production Style
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

   上記のスタイルでは、タイトルと説明が画面上の絶対位置に表示されます。 タイトルは説明よりもかなり大きく表示されます。 コンポーネントのBEM表記により、cmp-posterクラス内のスタイルを慎重にスコープするのが非常に簡単です。

3番目のクライアントライブラリカテゴリ：特定のス `cq.screens.components.edit` タイルのみをコンポーネントに追加する場合に使用できます。

| Clientlibカテゴリ | 使用方法 |
|---|---|
| `cq.screens.components` | 編集モードと実稼働モードの両方で共有されるスタイルとスクリプト |
| `cq.screens.components.edit` | 編集モードでのみ使用されるスタイルとスクリプト |
| `cq.screens.components.production` | 実稼働モードでのみ使用されるスタイルとスクリプト |

## シーケンスチャネルへのポスターコンポーネントの追加 {#add-sequence-channel}

ポスターコンポーネントは、シーケンスチャネルでの使用を想定しています。 このチュートリアルのスターターパッケージには、アイドルチャネルが含まれていました。 アイドルチャネルは、 **We.Retail Run - Contentグループのコンポーネントを許可するように事前設定されています**。 ポスターコンポーネントのグループがに設定され、チ `We.Retail Run - Content` ャネルに追加できるようになります。

1. We.Retail runプロジェクトからアイドルチャネルを開きます。 **`http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`**
1. ポスターコンポーネントの新しいインスタンスを **サイドバー** からページにドラッグ&amp;ドロップします。

   ![2018-05-07_at_3_23pm](assets/2018-05-07_at_3_23pm.png)

1. ポスターコンポーネントのダイアログを編集して、画像、タイトル、説明を追加します。 「テキストの位置」と「テキストの色」を使用して、タイトル/説明を画像で読み取り可能にします。

   ![2018-05-07_at_3_25pm](assets/2018-05-07_at_3_25pm.png)

1. 上記の手順を繰り返して、ポスターコンポーネントをいくつか追加します。 コンポーネント間にトランジションを追加します。

   ![2018-05-07_at_3_28pm](assets/2018-05-07_at_3_28pm.png)

## まとめ {#putting-it-all-together}

次のビデオでは、完成したコンポーネントと、それをシーケンスチャンネルに追加する方法を示します。 その後、チャネルがロケーションディスプレイに追加され、最終的に画面プレイヤーに割り当てられます。

>[!VIDEO](https://video.tv.adobe.com/v/22414?quaity=9&captions=jpn)

## 完了したコード {#finished-code}

チュートリアルの完成したコードを以下に示します。 screens-weretail-run.ui.apps-0.0.1- **SNAPSHOT.zip****** とscreens-weretail-run.ui.content-0.0.1-SNAPSHOT.zipは、コンパイル済みのAEMパッケージです。 **SRC-screens-wertail-run-0.0.1.zip **は、Mavenを使用してデプロイできるコンパイルされていないソースコードです。

[ファイルの取得](assets/final-poster-screens-weretail-runuiapps-001-snapshot.zip)

[ファイルの取得](assets/final-poster-screens-weretail-runuicontent-001-snapshot.zip)

SRC最終画面We.小売ランプロジェクト

[ファイルの取得](assets/src-screens-weretail-run-001.zip)
