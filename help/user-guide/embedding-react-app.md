---
title: AEM SPA エディターを使用した React アプリケーションの埋め込みと AEM Screens Analytics との統合
description: AEM SPA エディターで REACT（または Angular）を使用してインタラクティブ単一ページアプリケーションを埋め込む方法を説明します。
content-type: reference
topic-tags: developing
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: e4ecc179-e421-4687-854c-14d31bed031d
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 7dc7d07e-cd94-4ce1-a106-98669be62046
source-git-commit: a89aec16bb36ecbde8e417069e9ed852363acd82
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 100%

---

# AEM SPA エディターを使用した React アプリケーションの埋め込みと AEM Screens Analytics との統合 {#embedding-a-react-application-using-the-aem-spa-editor-and-integrating-with-aem-screens-analytics}

React（または Angular）を使用して、インタラクティブ単一ページアプリケーションを埋め込むことができます。これを行うには、AEM でビジネスプロフェッショナルが設定した AEM SPA エディターを使用します。また、インタラクティブアプリケーションをオフライン Adobe Analytics と統合する方法についても説明します。

## AEM SPA Editor の使用 {#using-the-aem-spa-editor}

AEM SPA Editor を使用するには、以下の手順に従います。

1. AEM SPA Editor リポジトリー（[https://github.com/adobe/aem-spa-project-archetype](https://github.com/adobe/aem-spa-project-archetype)）のクローンを作成します。

   >[!NOTE]
   >
   >このアーキタイプでは、独自の SPA プロジェクトの出発点として、最小限の Adobe Experience Manager プロジェクトが作成されます。このアーキタイプの使用時に指定する必要があるプロパティを通じて、このプロジェクトのあらゆる部分に必要に応じて名前を付けることができます。

1. AEM SPA エディターアーキタイププロジェクトを作成するには、README の手順に従います。

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
   >このドキュメントは、**GroupId** として ***com.adobe.aem.screens*** を、**ArtifactId** として ***My Sample SPA***（これがデフォルト）を使用します。必要に応じて独自に選択できます。

1. プロジェクトを作成したら、任意の IDE またはエディターを使用し、生成された Maven プロジェクトを読み込みます。
1. ***mvn clean install -PautoInstallPackage*** コマンドを使用して、ローカルの AEM インスタンスにデプロイします。

### React アプリのコンテンツの編集 {#editing-content-in-the-react-app}

React アプリのコンテンツを編集するには、以下の手順に従います。

1. `https://localhost:4502/editor.html/content/mysamplespa/en/home.html` に移動します（ホスト名、ポート、プロジェクト名を実際のものに置き換えます）。
1. Hello World アプリケーションに表示されるテキストを編集できます。

### AEM Screens へのインタラクティブ React アプリの追加 {#adding-the-interactive-react-app-to-aem-screens}

AEM Screens にインタラクティブ React アプリを追加するには、以下の手順に従います。

1. AEM Screens プロジェクトを作成します。詳しくは、[プロジェクトの作成と管理](creating-a-screens-project.md)を参照してください。
1. AEM Screens プロジェクトの **Channels** フォルダーで、（できれば）**アプリケーションチャネル**（または 1x1 テンプレートまたはマルチゾーンチャネル）を作成します。

   >[!NOTE]
   >**シーケンスチャネル**には、エクスペリエンスのインタラクティブな性質と競合するスライドショーロジックがもともと備わっているため、この使用例では推奨されません。
   >詳しくは、[チャネルの作成と管理](managing-channels.md)を参照してください。

1. シーケンスチャネルを編集し、埋め込みページコンポーネントをドラッグ＆ドロップします。

   詳しくは、[チャネルへのコンポーネントの追加](adding-components-to-a-channel.md)を参照してください。

   >[!NOTE]
   >
   >チャネルをディスプレイに割り当てる際には、必ずユーザーインタラクションイベントを追加してください。

1. アクションバーの「**編集**」をクリックして、チャネルのプロパティを編集します。

   ![screen_shot_2019-02-15at100555am](assets/screen_shot_2019-02-15at100555am.png)

1. **埋め込みページ**&#x200B;コンポーネントをドラッグ＆ドロップするか、アプリケーションチャネルで既存のコンポーネントを再利用し、mysamplespa アプリケーションの下のホームページ（例：***/content/mysamplespa/en/home***）をクリックします。

   ![screen_shot_2019-02-15at101104am](assets/screen_shot_2019-02-15at101104am.png)

1. チャネルをディスプレイに割り当てます。

   >[!NOTE]
   >チャネルをディスプレイに割り当てる際には、必ずユーザーインタラクションイベントを追加してください。

1. このプロジェクトに対してプレーヤーを登録し、ディスプレイに割り当てます。これで、AEM Screens 上で実行中のインタラクティブアプリケーションが表示されるようになりました。

   デバイスの登録に関する詳細情報については、[デバイスの登録](device-registration.md)を参照してください。

## AEM Screens を使用した SPA とオフライン機能付き Adobe Analytics の統合 {#integrating-the-spa-with-adobe-analytics-with-offline-capability-through-aem-screens}

AEM Screens を通じて SPA をオフライン機能付きの Adobe Analytics と統合するには、以下の手順に従います。

1. AEM Screens で Adobe Analytics を設定します。

   AEM Screens と連携する Adobe Analytics でのシーケンス化の実行方法と、オフライン Adobe Analytics を使用したカスタムイベントの送信方法については、[AEM Screens と連携する Adobe Analytics の設定](configuring-adobe-analytics-aem-screens.md)を参照してください。

1. 選択した IDE またはエディターを使用して、React アプリ（特に、イベントの発行を開始するテキストコンポーネントなどのコンポーネント）を編集します。
1. コンポーネントに対するクリックイベントなどのイベントをキャプチャする際に、標準データモデルを使用して分析情報を追加します。

   詳しくは、[AEM Screens と連携する Adobe Analytics の設定](configuring-adobe-analytics-aem-screens.md)を参照してください。

1. AEM Screens Analytics API を呼び出して、イベントをオフラインで保存し Adobe Analytics にバースト送信します。

   次に例を示します。

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
   >プレーヤーのファームウェアによって、送信するカスタム分析データにプレーヤーとそのランタイム環境に関する詳細が自動的に追加されます。したがって、必要でない限り、低レベルの OS ／デバイスの詳細を取得する必要がある場合があります。ビジネス分析データに焦点を当てます。
