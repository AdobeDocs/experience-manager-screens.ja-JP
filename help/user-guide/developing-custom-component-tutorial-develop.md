---
title: AEM Screens 用カスタムコンポーネントの開発
description: AEM Screensのカスタムコンポーネントを作成する方法を説明します。
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
targetaudience: target-audience new
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: d14f8c55-dc09-4ac9-8d75-bafffa82ccc0
source-git-commit: c142830a37461a36baae15f543bd43b0ae8a62a7
workflow-type: tm+mt
source-wordcount: '2135'
ht-degree: 69%

---

# AEM Screens 用カスタムコンポーネントの開発 {#developing-a-custom-component-for-aem-screens}

以下のチュートリアルでは、AEM Screens 用のカスタムコンポーネントを作成する手順について説明します。AEM Screens では、他の AEM 製品の様々な既存のデザインパターンやテクノロジーを再利用しています。このチュートリアルでは、AEM Screens 用に開発する際の相違点と特別な考慮事項について重点的に説明します。

## 概要 {#overview}

このチュートリアルは、AEM Screens を初めて使用する開発者を対象としています。このチュートリアルでは、AEM Screens のシーケンスチャネル用に、シンプルな「Hello World」コンポーネントを構築します。ダイアログボックスを使用すると、作成者は表示されるテキストを更新できます。

![overviewhellow](assets/overviewhellow.png)

## 前提条件 {#prerequisites}

このチュートリアルを完了するには、以下が必要です。

1. [AEM 6.5](https://experienceleague.adobe.com/ja/docs/experience-manager-65/content/release-notes/release-notes) さらに、最新の Screens 機能パック。

1. [AEM Screens Player](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/configuring-screens-introduction)
1. ローカル開発環境

チュートリアルの手順とスクリーンショットは、を使用して実行されます。 **CRXDE-Lite**. IDE を使用してチュートリアルを完了することもできます。AEM での開発に IDE を使用する方法について詳しくは、[こちら](https://experienceleague.adobe.com/en/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/project-setup)を参照してください。


## プロジェクトのセットアップ {#project-setup}

Screens プロジェクトのソースコードは、通常、マルチモジュールの Maven プロジェクトとして管理されます。このチュートリアルを効率よく進めるために、[AEM プロジェクトアーキタイプ 13](https://github.com/adobe/aem-project-archetype) を使用してプロジェクトを事前に生成してあります。Maven AEM プロジェクトアーキタイプを使用したプロジェクトの作成について詳しくは、[こちら](https://experienceleague.adobe.com/en/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/project-setup)を参照してください。

1. [CRX パッケージマネージャー](http://localhost:4502/crx/packmgr/index.jsp)を使用して、次のパッケージをダウンロードしてインストールします。

[ファイルを入手](assets/base-screens-weretail-runuiapps-001-snapshot.zip)

   [ファイルを入手](assets/base-screens-weretail-runuicontent-001-snapshot.zip)
   **（オプション）** Eclipse などの IDE を使用して作業する場合は、以下のソースパッケージをダウンロードします。次の Maven コマンドを使用して、プロジェクトをローカルの AEM インスタンスにデプロイします。

   **`mvn -PautoInstallPackage clean install`**

   HelloWorld SRC Screens の起動 `We.Retail` プロジェクトを実行します。

[ファイルを入手](assets/src-screens-weretail-run.zip)

1. [CRX パッケージマネージャー](http://localhost:4502/crx/packmgr/index.jsp)で、次の 2 つのパッケージがインストールされていることを確認します。

   1. **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip**
   1. **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**

   ![CRX パッケージマネージャーを使用してインストールされた Screens We.Retail Run Ui.Content および Ui.Apps パッケージ](assets/crx-packages.png)

   スクリーン `We.Retail` 実行 `Ui.Apps` および `Ui.Content` crx パッケージマネージャーを通じてインストールされるパッケージ。

1. **screens-weretail-run.ui.apps** パッケージでは、`/apps/weretail-run` の下にコードがインストールされます。

   このパッケージには、プロジェクトのカスタムコンポーネントをレンダリングするコードが含まれています。このパッケージには、コンポーネントコードのほか、必要な JavaScript または CSS が含まれています。このパッケージには、**screens-weretail-run.core-0.0.1-SNAPSHOT.jar** も埋め込まれており、この中に、プロジェクトで必要な Java™ コードが含まれています。

   >[!NOTE]
   >
   >このチュートリアルでは、Java™ コードは記述されません。より複雑なビジネスロジックが必要な場合は、コア Java バンドルを使用してバックエンド Java™ コードを作成しデプロイできます。

   ![CRXDE Lite での ui.apps コードの表現](assets/uipps-contents.png)

   CRXDE Lite での ui.apps コードの表現

   この **Hello World** コンポーネントはプレースホルダーにすぎません。 チュートリアルの過程で機能が追加されて、コンポーネントに表示されるメッセージを作成者が更新できるようになります。

1. **screens-weretail-run.ui.content** パッケージでは、以下のパスにコードがインストールされます。

   * `/conf/we-retail-run`
   * `/content/dam/we-retail-run`
   * `/content/screens/we-retail-run`

   このパッケージには、プロジェクトに必要な初期コンテンツおよび設定構造が含まれています。**`/conf/we-retail-run`** には、のすべての設定が含まれています `We.Retail` プロジェクトを実行します。 **`/content/dam/we-retail-run`** には、プロジェクトの初期デジタルアセットが含まれています。**`/content/screens/we-retail-run`** には、Screens のコンテンツ構造が含まれています。これらすべてのパスの下に含まれるコンテンツは主に AEM で更新されます。環境（ローカル、開発、ステージング、実稼動）間の一貫性を高めるために、多くの場合、ベースコンテンツ構造がソース管理下に保存されます。

1. **AEM Screensに移動します。 `We.Retail` プロジェクトを実行：**

   AEM スタートメニューから、「スクリーン」アイコンを選択します。 を確認 `We.Retail` プロジェクトの実行が表示されます。

   ![we-retaiul-run-starter](assets/we-retaiul-run-starter.png)

## Hello World コンポーネントの作成 {#hello-world-cmp}

Hello World コンポーネントは、画面に表示するメッセージをユーザーが入力できるシンプルなコンポーネントです。 このコンポーネントは、[AEM Screens コンポーネントテンプレート：https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template) をベースにしています。

AEM Screens には、従来の WCM Sites コンポーネントには必ずしも当てはまらない興味深い制約がいくつかあります。

* ほとんどの Screens コンポーネントは、ターゲットのデジタルサイネージデバイス上でフルスクリーンで動作する必要があります
* スライドショーを生成するには、ほとんどの Screens コンポーネントをシーケンスチャネルに埋め込み可能にする必要があります
* オーサリングでは、シーケンスチャネル内の個々のコンポーネントを編集できる必要があります。そのため、フルスクリーンでのレンダリングは問題になりません

1. **CRXDE Lite** `http://localhost:4502/crx/de/index.jsp`（または任意の IDE）で、`/apps/weretail-run/components/content/helloworld.` に移動します。

   `helloworld` コンポーネントに次のプロパティを追加します。

   ```
       jcr:title="Hello World"
       sling:resourceSuperType="foundation/components/parbase"
       componentGroup="We.Retail Run - Content"
   ```

   ![/apps/weretail-run/components/content/helloworld のプロパティ](assets/2018-04-28_at_4_23pm.png)

   /apps/weretail-run/components/content/helloworld のプロパティ

   この **Hello World** コンポーネントはを拡張します **foundation/components/parbase** コンポーネントを使用することにより、シーケンスチャネル内で適切に使用できるようになります。

1. `/apps/weretail-run/components/content/helloworld` の下に `helloworld.html.` という名前のファイルを作成します。

   ファイルに以下のように入力します。

   ```xml
   <!--/*
   
    /apps/weretail-run/components/content/helloworld/helloworld.html
   
   */-->
   
   <!--/* production: preview authoring mode + unspecified mode (i.e. on publish) */-->
   <sly data-sly-test.production="${wcmmode.preview || wcmmode.disabled}" data-sly-include="production.html" />
   
   <!--/* edit: any other authoring mode, i.e. edit, design, scaffolding, etc. */-->
   <sly data-sly-test="${!production}" data-sly-include="edit.html" />
   ```

   Screens コンポーネントでは、使用する[オーサリングモード](https://experienceleague.adobe.com/en/docs/experience-manager-64/authoring/authoring/author-environment-tools)に応じて、2 種類のレンダリングが必要になります。

   1. **実稼動**：プレビューまたはパブリッシュモード（wcmmode=disabled）
   1. **編集**：編集、デザイン、基礎、開発者など、他のすべてのオーサリングモードに使用されます。

   `helloworld.html` はスイッチとして機能し、アクティブなオーサリングモードを確認し、別の HTL スクリプトにリダイレクトします。編集モード用に `edit.html` スクリプトを用意し、実稼動モード用に `production.html` スクリプトを用意するというのが、Screens コンポーネントで一般に使用される規則です。

1. `/apps/weretail-run/components/content/helloworld` の下に `production.html.` という名前のファイルを作成します。

   ファイルに以下のように入力します。

   ```xml
   <!--/*
    /apps/weretail-run/components/content/helloworld/production.html
   
   */-->
   
   <div data-duration="${properties.duration}" class="cmp-hello-world">
    <h1 class="cmp-hello-world__message">${properties.message}</h1>
   </div>
   ```

   上記は、Hello World コンポーネントの実稼動用マークアップです。 このコンポーネントはシーケンスチャネルで使用されるので、`data-duration` 属性が含まれています。`data-duration` 属性は、シーケンスチャネルでシーケンス項目の表示時間を把握するために使用されます。

   このコンポーネントでは、`div` タグと `h1` タグ（テキストを含む）をレンダリングします。`${properties.message}` は、という名前の JCR プロパティのコンテンツを出力する HTL スクリプトの一部です `message`. ユーザーが値を入力できるダイアログボックスが後で作成されます。 `message` プロパティテキスト。

   また、コンポーネントでは BEM（ブロック要素修飾子）表記が使用されることにも注意してください。BEM は、再利用可能なコンポーネントを容易に作成できる CSS コーディング規則です。BEM は、[AEM のコアコンポーネント](https://github.com/adobe/aem-core-wcm-components/wiki/CSS-coding-conventions)で使用される表記です。<!-- DEAD LINK More info can be found at: [https://getbem.com/](https://getbem.com/) -->

1. `/apps/weretail-run/components/content/helloworld` の下に `edit.html.` という名前のファイルを作成します。

   ファイルに以下のように入力します。

   ```xml
   <!--/*
   
    /apps/weretail-run/components/content/helloworld/edit.html
   
   */-->
   
   <!--/* if message populated */-->
   <div
    data-sly-test.message="${properties.message}"
    class="aem-Screens-editWrapper cmp-hello-world">
    <p class="cmp-hello-world__message">${message}</p>
   </div>
   
   <!--/* empty place holder */-->
   <div data-sly-test="${!message}"
        class="aem-Screens-editWrapper cq-placeholder cmp-hello-world"
        data-emptytext="${'Hello World' @ i18n, locale=request.locale}">
   </div>
   ```

   上記は、Hello World コンポーネント用に編集されたマークアップです。 ダイアログメッセージが入力された場合、最初のブロックには、コンポーネントの編集バージョンが表示されます。

   ダイアログメッセージがまだ入力されていない場合は、2 番目のブロックがレンダリングされます。その場合、`cq-placeholder` と `data-emptytext` は、「***Hello World***」というラベルをプレースホルダーとしてレンダリングします。複数のロケールでのオーサリングをサポートするために、ラベルの文字列を i18n を使用して国際化することができます。

1. **Hello World コンポーネントに使用する Screens 画像ダイアログをコピーします。**

   既存のダイアログを出発点にして、それに変更を加えるのが最も簡単です。

   1. ダイアログのコピー元：`/libs/screens/core/components/content/image/cq:dialog`
   1. ダイアログの貼り付け先のパス：`/apps/weretail-run/components/content/helloworld`

   ![copy-image-dialog](assets/copy-image-dialog.gif)

1. **メッセージのタブが含まれるように Hello World ダイアログを更新します。**

   次の条件に合致するようにダイアログを更新します。最終的なダイアログの JCR ノード構造は、次のような XML コードになります。

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:nt="https://www.jcp.org/jcr/nt/1.0"
       jcr:primaryType="nt:unstructured"
       jcr:title="Hello World"
       sling:resourceType="cq/gui/components/authoring/dialog">
       <content
           jcr:primaryType="nt:unstructured"
           sling:resourceType="granite/ui/components/coral/foundation/tabs"
           size="L">
           <items jcr:primaryType="nt:unstructured">
               <message
                   jcr:primaryType="nt:unstructured"
                   jcr:title="Message"
                   sling:resourceType="granite/ui/components/coral/foundation/fixedcolumns">
                   <items jcr:primaryType="nt:unstructured">
                       <column
                           jcr:primaryType="nt:unstructured"
                           sling:resourceType="granite/ui/components/coral/foundation/container">
                           <items jcr:primaryType="nt:unstructured">
                               <message
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/textfield"
                                   fieldDescription="Message for component to display"
                                   fieldLabel="Message"
                                   name="./message"/>
                           </items>
                       </column>
                   </items>
               </message>
               <sequence
                   jcr:primaryType="nt:unstructured"
                   jcr:title="Sequence"
                   sling:resourceType="granite/ui/components/coral/foundation/fixedcolumns">
                   <items jcr:primaryType="nt:unstructured">
                       <column
                           jcr:primaryType="nt:unstructured"
                           sling:resourceType="granite/ui/components/coral/foundation/container">
                           <items jcr:primaryType="nt:unstructured">
                               <duration
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/numberfield"
                                   defaultValue=""
                                   fieldDescription="Amount of time the image is shown in the sequence, in milliseconds"
                                   fieldLabel="Duration (ms)"
                                   min="0"
                                   name="./duration"/>
                           </items>
                       </column>
                   </items>
               </sequence>
           </items>
       </content>
   </jcr:root>
   ```

   メッセージのテキストフィールドは、という名前のプロパティに保存されます。 `message` 期間の数値フィールドがという名前のプロパティに保存されていること `duration`. `/apps/weretail-run/components/content/helloworld/production.html` では、これら 2 つのプロパティは `${properties.message}` および `${properties.duration}` として HTL で参照されます。

   ![Hello World - 完成したダイアログ](assets/2018-04-29_at_5_21pm.png)

   Hello World - 完成したダイアログ

## クライアント側ライブラリの作成 {#clientlibs}

クライアントサイドライブラリは、AEM の実装で必要な CSS および JavaScript ファイルの編成および管理のための仕組みを提供します。

AEM Screens コンポーネントは、編集モードとプレビュー／実稼動モードではレンダリングが異なります。編集モード用とプレビュー/実稼動用の 2 つのクライアントライブラリが作成されます。

1. Hello World コンポーネントのクライアントサイドライブラリ用のフォルダーを作成します。

   `/apps/weretail-run/components/content/helloworld` の下に、`clientlibs` という名前のフォルダーを作成します。

   ![2018-04-30_at_1046am](assets/2018-04-30_at_1046am.png)

1. の下 `clientlibs` フォルダーに、という名前のノードを作成します。 `shared` タイプの `cq:ClientLibraryFolder`.

   ![2018-04-30_at_1115am](assets/2018-04-30_at_1115am.png)

1. 共有クライアントライブラリに次のプロパティを追加します。

   * `allowProxy` | Boolean | `true`

   * `categories`| String[] | `cq.screens.components`

   ![/apps/weretail-run/components/content/helloworld/clientlibs/shared のプロパティ](assets/2018-05-03_at_1026pm.png)

   /apps/weretail-run/components/content/helloworld/clientlibs/shared のプロパティ

   categories プロパティは、クライアントライブラリを識別する文字列です。cq.screens.componentscategory は、編集モードとプレビュー／実稼動モードの両方で使用されます。したがって、sharedclientlib に定義された CSS／JS は、すべてのモードに読み込まれます。

   実稼動環境では、直接 /apps にパスを公開しないことをお勧めします。allowProxy プロパティにより、クライアントライブラリの CSS と JS が /etc.clientlibs というプレフィックスを付けて参照されるようになります。

1. 共有フォルダーの下に `css.txt` という名前のファイルを作成します。

   ファイルに以下のように入力します。

   ```
   #base=css
   
   styles.less
   ```

1. `shared` フォルダーの下に `css` という名前のフォルダーを作成します。`css` フォルダーの下に、`style.less` という名前のファイルを追加します。クライアントライブラリの構造は次のようになります。

   ![2018-04-30_at_3_11pm](assets/2018-04-30_at_3_11pm.png)

   このチュートリアルでは、CSS を直接記述するのではなく、LESS を使用します。[LESS](https://lesscss.org/) は、CSS 変数、ミックスイン、関数をサポートしている一般的な CSS プリコンパイラーです。AEM のクライアントライブラリは、LESS によるコンパイルをネイティブにサポートしています。Sass などのプリコンパイラーも使用できますが、AEM の外部でコンパイルする必要があります。

1. `/apps/weretail-run/components/content/helloworld/clientlibs/shared/css/styles.less` に以下を入力します。

   ```css
   /**
       Shared Styles
      /apps/weretail-run/components/content/helloworld/clientlibs/shared/css/styles.less
   
   **/
   
   .cmp-hello-world {
       background-color: #fff;
   
    &__message {
     color: #000;
     font-family: Helvetica;
     text-align:center;
    }
   }
   ```

1. をコピー&amp;ペーストします。 `shared` という名前のクライアントライブラリを作成するクライアントライブラリフォルダー `production`.

   ![共有クライアントライブラリをコピーして実稼動用の新しいクライアントライブラリを作成する](assets/copy-clientlib.gif)

   共有クライアントライブラリをコピーして実稼動用のクライアントライブラリを作成します。

1. を更新 `categories` 次となる実稼動クライアントライブラリのプロパティ `cq.screens.components.production.`

   これにより、プレビュー／実稼動モードの場合のみ、スタイルが読み込まれるようになります。

   ![/apps/weretail-run/components/content/helloworld/clientlibs/production のプロパティ](assets/2018-04-30_at_5_04pm.png)

   プロパティ： `/apps/weretail-run/components/content/helloworld/clientlibs/production`.

1. `/apps/weretail-run/components/content/helloworld/clientlibs/production/css/styles.less` に以下を入力します。

   ```css
   /**
       Production Styles
      /apps/weretail-run/components/content/helloworld/clientlibs/production/css/styles.less
   
   **/
   .cmp-hello-world {
   
       height: 100%;
       width: 100%;
       position: fixed;
   
    &__message {
   
     position: relative;
     font-size: 5rem;
     top:25%;
    }
   }
   ```

   上記のスタイルでは、メッセージが画面の中央に表示されますが、実稼動モードでのみ表示されます。

3 つ目のクライアントライブラリカテゴリ： `cq.screens.components.edit` を使用して、コンポーネントに編集のみの特定のスタイルを追加できます。

| クライアントライブラリカテゴリ | 使用方法 |
|---|---|
| `cq.screens.components` | スタイルとスクリプトが編集モードと実稼動モードの両方で共有される |
| `cq.screens.components.edit` | スタイルとスクリプトが編集モードでのみ使用される |
| `cq.screens.components.production` | スタイルとスクリプトが実稼動モードでのみ使用される |

## デザインページの作成 {#design-page}

AEM Screens では、[静的ページテンプレート](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/developing/platform/templates/page-templates-static)と[デザイン設定](https://experienceleague.adobe.com/en/docs/experience-manager-64/authoring/siteandpage/default-components-designmode)を使用して、グローバルな変更に対応します。デザイン設定は、チャネル上で使用できる ParSys コンポーネントを設定する場合によく使用されます。これらの設定をアプリに固有の方法で保存することをお勧めします。

a の下 `We.Retail` に固有のすべての設定を格納する実行デザインページが作成されます `We.Retail` プロジェクトを実行します。

1. 対象： **CRXDE Lite** `http://localhost:4502/crx/de/index.jsp#/apps/settings/wcm/designs`に移動します。 `/apps/settings/wcm/designs`.
1. designs フォルダーの下に `cq:Page` 型の `we-retail-run` という名前のノードを作成します。
1. `we-retail-run` ページの下に、`nt:unstructured` 型の `jcr:content` という名前の別のノードを追加します。この `jcr:content` ノードに次のプロパティを追加します。

   | 名前 | タイプ | 値 |
   |---|---|---|
   | `jcr:title` | 文字列 | `We.Retail` 実行 |
   | `sling:resourceType` | 文字列 | wcm/core/components/designer |
   | `cq:doctype` | 文字列 | html_5 |

   ![/apps/settings/wcm/designs/we-retail-run のデザインページ](assets/2018-05-07_at_1219pm.png)

   ページのデザイン : `/apps/settings/wcm/designs/we-retail-run`.

## シーケンスチャネルの作成 {#create-sequence-channel}

Hello World コンポーネントは、シーケンスチャネルで使用します。 このコンポーネントをテストするために、新しいシーケンスチャネルを作成します。

1. AEMのスタートメニューで、に移動します。 **スクリーン** > **`We.Retail`実行** > を選択して、 **チャネル**.

1. 「」を選択します **作成** ボタン

   1. 「**エンティティを作成**」を選択します。

   ![2018-04-30_at_5_18pm](assets/2018-04-30_at_5_18pm.png)

1. 作成ウィザードで、以下の操作をおこないます。

1. テンプレートの手順 - 「**シーケンスチャネル**」を選択します

   1. プロパティの手順

   * 「基本」タブ／「タイトル」に「**Idle Channel**」を入力
   * 「チャネル」タブ／「**チャンネルをオンラインにする**」をオン

   ![idle-channel](assets/idle-channel.gif)

1. 待機中チャネルのページプロパティを開きます。
1. デザインフィールドをを指すように更新します `/apps/settings/wcm/designs/we-retail-run`、前の節で作成したデザインページ。

   ![デザイン設定 /apps/settings/wcm/designs/we-retail-run](assets/2018-05-07_at_1240pm.png)

   /apps/settings/wcm/designs/we-retail-run を指しているデザイン設定

1. 新しく作成したアイドルチャネルを編集して開けるようにします。

1. ページモードを&#x200B;**デザイン**&#x200B;モードに切り替えます。

   1. 「」を選択します **レンチ** Parsys にアイコンが表示されるので、許可されたコンポーネントを設定できます。

   1. 「」を選択します **スクリーン** グループと **`We.Retail`実行 – コンテンツ** グループ。

   ![2018-04-30_at_5_43pm](assets/2018-04-30_at_5_43pm.png)

1. ページモードを&#x200B;**編集**&#x200B;に切り替えます。これで、Hello World コンポーネントをページに追加し、他のシーケンスチャネルコンポーネントと組み合わせることができるようになりました。

   ![2018-04-30_at_5_53pm](assets/2018-04-30_at_5_53pm.png)

1. **CRXDE Lite** `http://localhost:4502/crx/de/index.jsp#/apps/settings/wcm/designs/we-retail-run/jcr%3Acontent/sequencechannel/par` で、`/apps/settings/wcm/designs/we-retail-run/jcr:content/sequencechannel/par` に移動します。`components` プロパティに `group:Screens`、`group:We.Retail Run - Content` が含まれていることがわかります。

   ![/apps/settings/wcm/designs/we-retail-run の下のデザイン設定](assets/2018-05-07_at_1_14pm.png)

   /apps/settings/wcm/designs/we-retail-run の下のデザイン設定

## カスタムハンドラーのテンプレート {#custom-handlers}

カスタムコンポーネントでアセット（画像、ビデオ、フォント、アイコン）、特定のアセットレンディション、クライアントサイドライブラリ（css および js）などの外部リソースを使用する場合、これらはオフライン設定に自動的には追加されません。 これは、デフォルトではHTMLマークアップのみがバンドルされているからです。

プレーヤーにダウンロードされる正確なアセットをカスタマイズし最適化できるように、Adobeでは、カスタムコンポーネントの依存関係をAEM Screensのオフラインキャッシュロジックに公開する拡張メカニズムを提供しています。

次の節では、カスタムオフラインリソースハンドラーのテンプレートと、そのプロジェクトに対する `pom.xml` の最小要件について説明します。

```java
package …;

import javax.annotation.Nonnull;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.api.resource.Resource;
import org.apache.sling.api.resource.ResourceUtil;
import org.apache.sling.api.resource.ValueMap;

import com.adobe.cq.screens.visitor.OfflineResourceHandler;

@Service(value = OfflineResourceHandler.class)
@Component(immediate = true)
public class MyCustomHandler extends AbstractResourceHandler {

 @Reference
 private …; // OSGi services injection

 /**
  * The resource types that are handled by the handler.
  * @return the handled resource types
  */
 @Nonnull
 @Override
 public String[] getSupportedResourceTypes() {
     return new String[] { … };
 }

 /**
  * Accept the provided resource, visit and traverse it as needed.
  * @param resource The resource to accept
  */
 @Override
 public void accept(@Nonnull Resource resource) {
     ValueMap properties = ResourceUtil.getValueMap(resource);
     
     /* You can directly add explicit paths for offline caching using the `visit`
        method of the visitor. */
     
     // retrieve a custom property from the component
     String myCustomRenditionUrl = properties.get("myCustomRenditionUrl", String.class);
     // adding that exact asset/rendition/path to the offline manifest
     this.visitor.visit(myCustomRenditionUrl);
     
     
     /* You can delegate handling for dependent resources so they are also added to
        the offline cache using the `accept` method of the visitor. */
     
     // retrieve a referenced dependent resource
     String referencedResourcePath = properties.get("myOtherResource", String.class);
     ResourceResolver resolver = resource.getResourceResolver();
     Resource referencedResource = resolver.getResource(referencedResourcePath);
     // let the handler for that resource handle it
     if (referencedResource != null) {
         this.visitor.accept(referencedResource);
     }
   }
}
```

次のコードは、そのプロジェクトに対する `pom.xml` の最小要件を示しています。

```css
   <dependencies>
        …
        <!-- Felix annotations -->
        <dependency>
            <groupId>org.apache.felix</groupId>
            <artifactId>org.apache.felix.scr.annotations</artifactId>
            <version>1.9.0</version>
            <scope>provided</scope>
        </dependency>

        <!-- Screens core bundle with OfflineResourceHandler/AbstractResourceHandler -->
        <dependency>
            <groupId>com.adobe.cq.screens</groupId>
            <artifactId>com.adobe.cq.screens</artifactId>
            <version>1.5.90</version>
            <scope>provided</scope>
        </dependency>
        …
      </dependencies>
```

## まとめ {#putting-it-all-together}

以下のビデオでは、完成したコンポーネントと、それをシーケンスチャネルに追加する方法を示しています。この後、チャネルはロケーションのディスプレイに追加され、最終的に Screens プレーヤーに割り当てられます。

>[!VIDEO](https://video.tv.adobe.com/v/22385?quaity=9)

## 他のページやフラグメントを埋め込むカスタムコンポーネントに関するその他の考慮事項 {#additional-considerations}

カスタムコンポーネントに他のページやエクスペリエンスフラグメントを組み込み、チャネルを再公開せずに、プレーヤーで自動的に選択された埋め込みコンテンツに変更を加える場合は、次の 2 つの制約を考慮します。

1. `foundation/components/parbase` を直接拡張する代わりに、`screens/core/components/content/page` または `screens/core/components/content/experiencefragment` のいずれかを拡張する必要があります
2. 埋め込みコンテンツの参照に使用するプロパティの名前は、である必要があります `pagePath`.

また、これら 2 つの Screens コアコンポーネントを使用すると、必要な依存関係（クライアント側ライブラリ、フォントなど）の一部をバンドルできるという追加の利点も得られます。 それには、コンポーネントダイアログボックスのオフライン設定オプションが使用されます。これにより、これに対して使用する必要のあるカスタムオフラインハンドラーの責任が軽減されます。 最初の場所で使用する必要性を完全に取り除くことさえできます。

## 完成したコード {#finished-code}

チュートリアルで完成したコードは以下のとおりです。**screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip** と **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip** は、コンパイル済みの AEM パッケージです。SRC-screens-wertail-run-0.0.1.zip は、Maven を使用してデプロイできる未コンパイルのソースコードです。

[ファイルを入手](assets/screens-weretail-runuiapps-001-snapshot.zip)

[ファイルを入手](assets/screens-weretail-runuicontent-001-snapshot.zip)

[ファイルを入手](assets/screens-weretail-run.zip)
