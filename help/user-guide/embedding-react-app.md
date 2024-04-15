---
title: AEM SPA Editor を使用した React アプリケーションの埋め込みと AEM Screens Analytics との統合
description: AEM SPAエディターで REACT （またはAngular）を使用してインタラクティブなシングルページアプリケーションを埋め込む方法を説明します。
content-type: reference
topic-tags: developing
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: e4ecc179-e421-4687-854c-14d31bed031d
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 7dc7d07e-cd94-4ce1-a106-98669be62046
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '681'
ht-degree: 45%

---

# AEM SPA Editor を使用した React アプリケーションの埋め込みと AEM Screens Analytics との統合 {#embedding-a-react-application-using-the-aem-spa-editor-and-integrating-with-aem-screens-analytics}

React （またはAngular）を使用して、インタラクティブな単一ページアプリケーションを埋め込むことができます。 これを行うには、AEMでビジネスプロフェッショナルが設定したAEM SPAエディターを使用します。 また、インタラクティブアプリケーションをオフライン Adobe Analyticsと統合する方法についても説明します。

## AEM SPA Editor の使用 {#using-the-aem-spa-editor}

AEM SPA Editor を使用するには、以下の手順に従います。

1. AEM SPA Editor リポジトリー（[https://github.com/adobe/aem-spa-project-archetype](https://github.com/adobe/aem-spa-project-archetype)）のクローンを作成します。

   >[!NOTE]
   >
   >このアーキタイプでは、独自の SPA プロジェクトの出発点として、最小限の Adobe Experience Manager プロジェクトが作成されます。このアーキタイプを使用する際に指定する必要があるプロパティを使用すると、このプロジェクトのすべての部分に必要に応じて名前を付けることができます。

1. AEM SPAエディターアーキタイププロジェクトを作成するには、の README の手順に従います。

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
   >このドキュメントでは、を使用します **GroupId** as ***com.adobe.aem.screens*** および **ArtifactId** as ***My サンプル SPA*** （デフォルト）。 必要に応じて独自に選択できます。

1. プロジェクトが作成されたら、任意の IDE またはエディターを使用し、生成された Maven プロジェクトを読み込みます。
1. ***mvn clean install -PautoInstallPackage*** コマンドを使用して、ローカルの AEM インスタンスにデプロイします。

### React アプリのコンテンツの編集 {#editing-content-in-the-react-app}

React アプリのコンテンツを編集するには、以下の手順に従います。

1. に移動します。 `https://localhost:4502/editor.html/content/mysamplespa/en/home.html` （必要に応じて、ホスト名、ポート、プロジェクト名を置き換えます）。
1. Hello world アプリケーションに表示されるテキストを編集できます。

### AEM Screens へのインタラクティブ React アプリの追加 {#adding-the-interactive-react-app-to-aem-screens}

AEM Screens にインタラクティブ React アプリを追加するには、以下の手順に従います。

1. AEM Screens プロジェクトを作成します。参照： [プロジェクトの作成と管理](creating-a-screens-project.md) を参照してください。
1. を作成 **アプリケーションチャネル** （できれば）（または 1x1 テンプレートまたはマルチゾーンチャネル）を **チャネル** AEM Screens プロジェクトのフォルダー。

   >[!NOTE]
   >**シーケンスチャネル** は、エクスペリエンスのインタラクティブな性質と競合するスライドショーロジックがもともと備わっているため、このユースケースでは推奨されません。
   >参照： [チャネルの作成と管理](managing-channels.md) を参照してください。

1. シーケンスチャネルを編集し、埋め込みページコンポーネントをドラッグ＆ドロップします。

   参照： [チャネルへのコンポーネントの追加](adding-components-to-a-channel.md) を参照してください。

   >[!NOTE]
   >
   >チャネルをディスプレイに割り当てる際には、必ずユーザーインタラクションイベントを追加してください。

1. を選択 **編集** アクションバーのを使用して、チャネルのプロパティを編集できます。

   ![screen_shot_2019-02-15at100555am](assets/screen_shot_2019-02-15at100555am.png)

1. をドラッグ&amp;ドロップ **埋め込みページ** コンポーネントを選択するか、アプリケーションチャネルで既存のコンポーネントを再利用し、mysamplespa アプリケーションの下のホームページ（例：） ***/content/mysamplespa/en/home***.

   ![screen_shot_2019-02-15at101104am](assets/screen_shot_2019-02-15at101104am.png)

1. チャネルをディスプレイに割り当てます。

   >[!NOTE]
   >チャネルをディスプレイに割り当てる際には、必ずユーザーインタラクションイベントを追加してください。

1. このプロジェクトに対してプレーヤーを登録し、ディスプレイに割り当てます。これで、AEM Screens 上で実行中のインタラクティブアプリケーションが表示されるようになりました。

   参照： [デバイスの登録](device-registration.md) デバイスの登録に関する詳細情報。

## AEM Screens を使用した SPA とオフライン機能付き Adobe Analytics の統合 {#integrating-the-spa-with-adobe-analytics-with-offline-capability-through-aem-screens}

AEM Screens を通じて SPA をオフライン機能付きの Adobe Analytics と統合するには、以下の手順に従います。

1. AEM Screens で Adobe Analytics を設定します。

   参照： [Adobe AnalyticsとAEM Screensの設定](configuring-adobe-analytics-aem-screens.md) AEM Screensを使用してAdobe Analyticsでシーケンスを実行する方法や、オフライン Adobe Analyticsを使用してカスタムイベントを送信する方法について詳しくは、こちらを参照してください。

1. 任意の IDE またはエディターを使用して、React アプリ（特に、イベントの発行を開始するテキストコンポーネントなどのコンポーネント）を編集します。
1. コンポーネントに対して取得する選択イベントまたはその他のイベントで、標準データモデルを使用して分析情報を追加します。

   参照： [Adobe AnalyticsとAEM Screensの設定](configuring-adobe-analytics-aem-screens.md) を参照してください。

1. AEM Screens Analytics API を呼び出して、イベントをオフラインで保存し、バーストでAdobe Analyticsに送信できるようにします。

   例：

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
   >プレーヤーのファームウェアによって、送信するカスタム分析データにプレーヤーとそのランタイム環境に関する詳細が自動的に追加されます。したがって、必要でない限り、低レベルの OS/デバイスの詳細を取得する必要がある場合があります。 ビジネス分析データに焦点を当てます。
