---
title: AEM SPAエディターを使用したREACTアプリケーションの埋め込みとAEM Screens Analyticsとの統合
seo-title: AEM SPAエディターを使用したREACTアプリケーションの埋め込みとAEM Screens Analyticsとの統合
description: このページでは、AEMのビジネスプロフェッショナルが設定できるAEM SPAエディターを使用してREACT（またはAngular）を使用し、インタラクティブな単一ページアプリケーションをオフラインのAdobe Analyticsと統合する方法について説明します。
seo-description: このページでは、AEMのビジネスプロフェッショナルが設定できるAEM SPAエディターを使用してREACT（またはAngular）を使用し、インタラクティブな単一ページアプリケーションをオフラインのAdobe Analyticsと統合する方法について説明します。
uuid: fb56ede0-7b36-4f47-b9e5-d806c9a3c707
content-type: reference
topic-tags: developing
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: e4ecc179-e421-4687-854c-14d31bed031d
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# AEM SPAエディターを使用したREACTアプリケーションの埋め込みとAEM Screens Analyticsとの統合 {#embedding-a-react-application-using-the-aem-spa-editor-and-integrating-with-aem-screens-analytics}

ここでは、AEMのビジネスプロフェッショナルが設定できるAEM SPAエディターを使用してREACT（またはAngular）を使用し、インタラクティブな単一ページアプリを埋め込む方法と、インタラクティブなアプリをオフラインのAdobe Analyticsと統合する方法について説明します。

## AEM SPAエディターの使用 {#using-the-aem-spa-editor}

AEM SPAエディターを使用するには、次の手順に従います。

1. https://github.com/adobe/aem-spa-project-archetypeでAEM SPA Editorレポートをコピー [します。](https://github.com/adobe/aem-spa-project-archetype)

   >[!NOTE]
   >
   >このアーキタイプは、独自のSPAプロジェクトの起点として最小限のAdobe Experience Managerプロジェクトを作成します。 このアーキタイプを使用する場合に指定する必要があるプロパティは、このプロジェクトのすべての部分に必要な名前を付けることができます。

1. お読みくださいの指示に従って、AEM SPAエディターアーキタイププロジェクトを作成します。

   ```
   mvn clean install archetype:update-local-catalog
   mvn archetype:crawl
   
   mvn archetype:generate \
   -DarchetypeCatalog=internal \
   -DarchetypeGroupId=com.adobe.cq.spa.archetypes \
   -DarchetypeArtifactId=aem-spa-project-archetype \
   -DarchetypeVersion=1.0.3-SNAPSHOT \
   ```

   >[!NOTE]
   >
   >GroupIdを **com.adobe.aem.screensとして使用し** 、 ***ArtifactIdを*****Sample SPA（デフォルトはデフォルト）******** として使用します。 必要に応じて独自のオプションを選択できます。

1. プロジェクトを作成したら、IDEまたは任意のエディタを使用して、生成されたMavenプロジェクトを読み込みます。
1. mvn clean install -PautoInstallPackageコマンドを使用して、ローカルAEMイン ***スタンスにデプロイします***。

### REACTアプリでのコンテンツの編集 {#editing-content-in-the-react-app}

REACTアプリでコンテンツを編集するには：

1. に移動し `https://localhost:4502/editor.html/content/mysamplespa/en/home.html` ます（必要に応じて、ホスト名、ポート、プロジェクト名を置き換えます）。
1. Hello worldアプリケーションに表示されるテキストを編集できるはずです。

### AEM ScreensへのインタラクティブREACTアプリの追加 {#adding-the-interactive-react-app-to-aem-screens}

次の手順に従って、AEM ScreensにインタラクティブREACTアプリを追加します。

1. 新しいAEM Screensプロジェクトを作成します。 詳細は、 [「プロジェクトの作成と管理](creating-a-screens-project.md) 」を参照してください。

   >[!NOTE]
   >
   >シーケンスチ **ャネルを作成すると** 、画面プロジェクトの **Channels** フォルダーでチャネルを作成します。
   >
   >
   >詳細は、「チ [ャネルの作成と管理](managing-channels.md) 」を参照してください。

   ![screen_shot_2019-02-15at100330am](assets/screen_shot_2019-02-15at100330am.png)

1. シーケンスチャネルを編集し、埋め込みページコンポーネントをドラッグ&amp;ドロップします。

   詳細は、 [「チャネルへのコンポーネントの追加](adding-components-to-a-channel.md) 」を参照してください。

   >[!NOTE]
   >
   >チャネルを表示に割り当てる際は、必ずユーザインタラクションイベントを追加してください。

1. アクシ **ョンバーの** 「編集」をクリックして、シーケンスチャネルのプロパティを編集します。

   ![screen_shot_2019-02-15at100555am](assets/screen_shot_2019-02-15at100555am.png)

1. 「埋め込みページ」コン **ポーネントをドラッグ** &amp;ドロップし、mysamplespaアプリケーションの下のホームページを選択します(例： ***/content/mysamplespa/en/home)***。

   ![screen_shot_2019-02-15at101104am](assets/screen_shot_2019-02-15at101104am.png)

1. このプロジェクトに対してプレーヤーを登録すると、AEM Screens上で実行されているインタラクティブアプリケーションが表示されます。

   デバイスの登 [録の詳細は](device-registration.md) 、「デバイスの登録」を参照してください。

## AEM Screensを使用したSPAとAdobe Analyticsのオフライン機能の統合 {#integrating-the-spa-with-adobe-analytics-with-offline-capability-through-aem-screens}

次の手順に従って、AEM Screensを通じてSPAをAdobe Analyticsとオフライン機能と統合します。

1. AEM ScreensでAdobe Analyticsを設定します。

   AEM Screensを使用したAdobe Analyticsでのシーケンスの実行方法と、オフラインAdobe Analyticsを使用したカスタムイベントの送信方法については、[AEM Screensを使用したAdobe Analyticsの設定(configuring-adobe-analytics-aem-screens.md)を参照してください。

1. 選択したIDE/エディタ（特にイベントの発行を開始するテキストコンポーネントまたは他のコンポーネント）で、リアクションアプリを編集します。
1. コンポーネント用に取り込むクリックイベントまたは他のイベントで、標準データモデルを使用して解析情報を追加します。

   詳しくは、「AEM [画面でのAdobe Analyticsの設定」](configuring-adobe-analytics-aem-screens.md)を参照してください。

1. AEM Screens Analytics APIを呼び出して、イベントをオフラインで保存し、Adobe Analyticsにバーストで送信します。

   以下に例を挙げます。  

   ```
   handleClick() {
       if ((window.parent) && (window.parent.CQ) && (window.parent.CQ.screens) && (window.parent.CQ.screens.analytics))
       {
           var analyticsEvent = {};
           analyticsEvent['event.type'] = 'play'; // Type of event
    analyticsEvent['event.coll_dts'] = new Date().toISOString(); // Start of collecting the event
    analyticsEvent['event.dts_start'] = new Date().toISOString(); // Event start
    analyticsEvent['content.type'] = 'Washing machine'; // Mime Type or product category
    analyticsEvent['content.action'] = 'Path to the washing machine asset in AEM'; // Path in AEM to relevant asset
    analyticsEvent['trn.product'] = 'Washing machine Model number'; // Product being explored
    analyticsEvent['trn.amount'] = 1000; // Product pricing or other numeric value or weight
    analyticsEvent['event.dts_end'] = new Date().toISOString(); // Event end
    analyticsEvent['event.count'] = 100; // Numeric value that may count a number of clicks or keystrokes or wait time in seconds for example
    analyticsEvent['event.value'] = 'My favorite analytics event';
           analyticsEvent['trn.quantity'] = 10; // Quantity of product selection
    analyticsEvent['event.subtype'] = 'end'; // Event subtype if applicable
    window.parent.CQ.screens.analytics.sendTrackingEvent(analyticsEvent);
       }
   }
   ```

   >[!NOTE]
   >
   >プレイヤーのファームウェアは、送信するカスタム解析データに、プレイヤーとそのランタイム環境に関する詳細を自動的に追加します。 したがって、絶対に必要な場合を除き、低レベルのOS/デバイスの詳細を取得する必要がない場合があります。 ビジネス分析データに焦点を合わせるだけで済みます。

