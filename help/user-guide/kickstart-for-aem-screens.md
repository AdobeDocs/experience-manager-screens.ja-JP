---
title: キックスタートガイド
seo-title: キックスタートガイド
description: このページの説明に従って、AEM Screens のデモプロジェクトを作成します。インストールして新しいプロジェクトをセットアップしてから、AEM Screens Player でコンテンツを表示するまでの、デジタルサイネージエクスペリエンスを作成できます。
translation-type: tm+mt
source-git-commit: 988872003c1d01c90ccdb38fa77c99019b9a6966
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 64%

---


# キックスタートガイド {#kickstart-guide}

このセクションは、AEM Screensでのキックスタートで、AEM Screensプロジェクトの設定および実行方法を示します。 基本的なデジタル署名エクスペリエンスの設定、各チャネルへのアセットやビデオなどのコンテンツの追加、さらにそのコンテンツのAEM Screensプレーヤーへの公開に関する手順を説明します。

>[!NOTE]
>プロジェクトの詳細を操作する際に開始が発生する前に、最新の機能パックがインストールされていることを確認してください。 Adobe ID を使用して、AEM Screens 6.5.5 リリースの最新の機能パックを[ソフトウェア配布ポータル](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)からダウンロードできます。

## 前提条件 {#prerequisites}

次の手順に従って、AEM Screens向けのサンプルプロジェクトを作成し、コンテンツを画面プレイヤーにさらに公開します。

>[!NOTE]
>次のチュートリアルは、Chrome OS Playerでチャネルーのコンテンツを再生する場合を示します。

>[!IMPORTANT]
>**OSGi 設定**
>デバイスからサーバーへのデータの投稿を許可するには、空のリファラーを有効にする必要があります。例えば、空のリファラーのプロパティが無効になっていると、デバイスからスクリーンショットを投稿できません。現在、これらの機能の一部は、OSGi設定で「Apache Sling転送者フィルター」「空白を許可」が有効になっている場合にのみ使用できます。 ダッシュボードには、セキュリティ設定がこれらの機能の一部の動作を妨げる可能性があることを示す警告が表示される場合があります。
>***Apache Sling Referrer Filter の「Allow Empty」設定***&#x200B;を有効にするには、次の手順に従います。


## 空のリファラー要求の許可 {#allow-empty-referrer-requests}

1. AEM インスタンスでハンマーアイコン／**操作**／**Web コンソール**&#x200B;をクリックして、「**Adobe Experience Manager Web コンソール設定**」に移動します。

   ![画像](assets/config/empty-ref1.png)

1. **Adobe Experience Manager Web コンソール設定**&#x200B;が開きます。「sling referrer」を検索します。

   「sling referrer」プロパティを検索するには、**Command + F** キー（**Mac**）または **Ctrl + F** キー（**Windows**）を押します。

1. 「**Allow Empty**」オプションをオンにします（下図を参照）。

   ![画像](assets/config/empty-ref2.png)

1. 「**保存**」をクリックして、Apache Sling Referrer Filter の「Allow Empty」を有効にします。


## デジタルサイネージエクスペリエンスを 5 分で作成する {#creating-a-digital-signage-experience-in-minutes}

### AEM Screens プロジェクトの作成 {#creating-project}

最初のステップは、新しいAEM Screensプロジェクトを作ることです。

1. Adobe Experience Manager(AEM)インスタンスに移動し、「 **画面**」をクリックします。 Alternatively, you can navigate directly from `https://localhost:4502/screens.html/content/screens](https://localhost:4502/screens.html/content/screens`.

1. Click **Create Screens Project** to create a new Screens project. Enter the title as **DemoScreens** and click **Save**.

   ![画像](assets/kickstart/demo-1.png)

   >[!NOTE]
   >プロジェクトを作成すると、画面のプロジェクトホームページに戻ります。 これでプロジェクトを選択できます。プロジェクトには、 **Applications**、 **チャネル**、 **Devices**、Devices **、Locations、Locations、Schedulesという5つの異なるフォルダがあ******&#x200B;ります。


### チャネルの作成 {#creating-channel}

プロジェクトを作成したら、コンテンツを管理するための新しいチャネルを作成する必要があります。

以下の手順に従って、プロジェクトの新しいチャネルを作成します。

1. プロジェクトを作成したら、 **DemoScreens** プロジェクトを選択し、 **チャネルフォルダ**（下の図を参照）を選択します。 Click **+ Create** from the action bar.

   ![画像](assets/kickstart/demo-2.png)

1. Choose the **Sequence Channel** from the wizard and click **Next**.
   ![画像](assets/kickstart/demo-3.png)

1. 「**タイトル**」に「*TestChannel*」と入力し、「**作成**」をクリックします。

   ![画像](assets/kickstart/demo-4.png)

*TestChannel*&#x200B;が作成され、チャネルフォルダーに追加されます（下図を参照）。

![画像](assets/kickstart/demo-5.png)

### チャネルへのコンテンツの追加 {#adding-content}

チャネルを作成したら、Screens Player に表示するコンテンツをチャネルに追加する必要があります。

以下の手順に従って、プロジェクトのチャネル（*TestChannel*）にコンテンツを追加します。

1. 作成した **DemoProject** プロジェクトに移動し、**チャネル**&#x200B;フォルダーを選択します。

1. アクションバーの「**編集**」をクリックします（下図を参照）。TestChannel **** のエディターが開きます。

   ![画像](assets/kickstart/demo-6.png)

1. アクションバーの左側にあるサイドパネルを切り替えるアイコンをクリックし、アセットとコンポーネントを開きます。

1. チャネルに追加するコンポーネントをドラッグ＆ドロップします。

   ![画像](assets/kickstart/demo-7.png)

### ロケーションの作成 {#creating-location}

チャネルを設定したら、場所を作成する必要があります。

>[!NOTE]
>***Locations*** compartmentalize your various digital signage experiences and contains the configurations of the displays according to where the various screens are.

以下の手順に従って、プロジェクトの新しいロケーションを作成します。

1. Navigate to the **DemoProject** you created and select the **Locations** folder.

1. Click **+ Create** from the action bar.

1. ウィザードから「**ロケーション**」を選択し、「**次へ**」をクリックします。

1. Enter the **Name** for your location (enter the title as *TestLocation*) and click **Create**.

**TestLocation** が作成され、**ロケーション**&#x200B;フォルダーに追加されます。


### 場所の表示の作成 {#creating-display}

ロケーションを作成したら、ロケーションのための新しいディスプレイを作成する必要があります。

>[!NOTE]
>***ディスプレイ***&#x200B;は、1 つまたは複数のスクリーンで実行されるデジタルエクスペリエンスを表します。

1. Navigate to the **TestLocation** and select it.

1. アクションバーの「**作成**」をクリックします。

   ![画像](assets/kickstart/demo-disp1.png)

1. **作成**&#x200B;ウィザードから「**ディスプレイ**」を選択し、「**次へ**」をクリックします。

   ![画像](assets/kickstart/demo-disp2.png)

1. Enter the **Title** as **LobbyDisplay** and click **Create**.

   ![画像](assets/kickstart/demo-disp3.png)

A new display titled as **TestDisplay** is now added to your location **TestLocation**, as shown in the figure below.

![画像](assets/kickstart/demo-disp4.png)

### チャネルの割り当て {#assigning-channel}

プロジェクトの設定が完了したら、チャネルをディスプレイに割り当てて、コンテンツを表示する必要があります。

1. Navigate to the required display, for example, **DemoScreens** --> **Locations** --> **TestLocation** --> **LobbyDisplay**.

1. アクションバーで「**チャネルの割り当て**」をタップまたはクリックします。

   または、

   アクションバーの「**ダッシュボード**」をタップまたはクリックし、「**割り当てられたチャネルとスケジュール**」パネルで「**チャネルの割り当て**」をクリックします。

1. 「**チャネル割り当て**」ダイアログボックスが開きます。

1. 「**設定**」オプションから、**パス**&#x200B;または&#x200B;**名前**&#x200B;でチャネルを選択し、**チャネルロール**、**優先度**、**サポートされているイベント**、**中断方法**&#x200B;を入力できます。また、このダイアログボックスでアトラクションツールチップを有効にすることもできます。


   >[!NOTE]
   >チャネルの割り当てプロパティの詳細については、[チャネルプロパティ](/help/user-guide/channel-assignment-latest-fp.md#channel-properties)の節を参照してください。

1. 「**スケジュール**」オプションから、「**アクティベーションウィンドウ**」、「**繰り返しスケジュール**」の順に選択します。

1. 環境を設定したら、「**保存**」をクリックします。

### デバイスの登録 {#registering-device}

AEM ダッシュボードを使用して、デバイスを登録する必要があります。

### Chrome Player でのコンテンツの表示 {#viewing-content-output}

この例は、Chrome Player の出力を示します。ディスプレイにチャネルを割り当てたら、そのデバイスをプレーヤーに登録する必要があります。



