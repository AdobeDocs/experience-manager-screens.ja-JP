---
title: キックスタートガイド
seo-title: キックスタートガイド
description: このページの説明に従って、AEM Screens のデモプロジェクトを作成します。インストールして新しいプロジェクトをセットアップしてから、AEM Screens Player でコンテンツを表示するまでの、デジタルサイネージエクスペリエンスを作成できます。
translation-type: tm+mt
source-git-commit: f2fef18cc73825b3f062a79c560097e8fd00ac9f
workflow-type: tm+mt
source-wordcount: '1080'
ht-degree: 73%

---


# キックスタートガイド {#kickstart-guide}

このセクションは、AEM Screensでのキックスタートで、AEM Screensプロジェクトの設定および実行方法を示します。 基本的なデジタル署名エクスペリエンスの設定、各チャネルへのアセットやビデオなどのコンテンツの追加、さらにそのコンテンツのAEM Screensプレーヤーへの公開に関する手順を説明します。

>[!NOTE]
>プロジェクトの詳細を操作する際に開始が発生する前に、最新の機能パックがインストールされていることを確認してください。 Adobe ID を使用して、AEM Screens 6.5.5 リリースの最新の機能パックを[ソフトウェア配布ポータル](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)からダウンロードできます。

## デジタルサイネージエクスペリエンスを 5 分で作成する {#creating-a-digital-signage-experience-in-minutes}

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


## チュートリアル {#tutorial}

### Creating a new AEM Screens Project {#creating-project}

最初のステップは、新しいAEM Screensプロジェクトを作ることです。

1. Adobe Experience Manager(AEM)インスタンスに移動し、「 **画面**」をクリックします。 Alternatively, you can navigate directly from `https://localhost:4502/screens.html/content/screens](https://localhost:4502/screens.html/content/screens`.

1. Click **Create Screens Project** to create a new Screens project. Enter the title as **DemoScreens** and click **Save**.

   ![画像](assets/kickstart/demo-1.png)

   >[!NOTE]
   >プロジェクトを作成すると、画面のプロジェクトホームページに戻ります。 これでプロジェクトを選択できます。プロジェクトには、 **Applications**、 **チャネル**、 **Devices**、Devices **、Locations、Locations、Schedulesという5つの異なるフォルダがあ******&#x200B;ります。


### 新しいチャネルの作成 {#creating-channel}

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

1. 作成した *Test_Project* に移動し、**チャネル**&#x200B;フォルダーを選択します。

1. アクションバーの「**編集**」をクリックします（下図を参照）。TestChannel ** のエディターが開きます。

1. アクションバーの左側にあるサイドパネルを切り替えるアイコンをクリックし、アセットとコンポーネントを開きます。

1. チャネルに追加するコンポーネントをドラッグ＆ドロップします。

   ![chlimage_1-8](assets/chlimage_1-8.png)

この例では、チャネルに追加された画像がエディターに表示されます。

![chlimage_1-9](assets/chlimage_1-9.png)

### 新しい場所の作成 {#creating-location}

チャネルを作成したら、ロケーションを作成する必要があります。

***場所*** ：様々なデジタル署名のエクスペリエンスを区分けし、様々な画面の位置に応じたディスプレイの設定を含みます。

以下の手順に従って、プロジェクトの新しいロケーションを作成します。

1. 作成した *Test_Project* に移動し、**ロケーション**&#x200B;フォルダーを選択します。

1. アクションバーで、プラスアイコンの隣にある「**作成**」をクリックします（下図を参照）。ウィザードが開きます。
1. ウィザードから「**ロケーション**」を選択し、「**次へ**」をクリックします。

1. ロケーションの「**名前**」と「**タイトル**」を入力し（タイトルには「*TestLocation*」と入力します）、「**作成**」をクリックします。

   ![chlimage_1-10](assets/chlimage_1-10.png)

*TestLocation* が作成され、**ロケーション**&#x200B;フォルダーに追加されます。

![chlimage_1-11](assets/chlimage_1-11.png)

### TestLocation{#creating-display} の新しいディスプレイの作成 

ロケーションを作成したら、ロケーションのための新しいディスプレイを作成する必要があります。

***ディスプレイ***&#x200B;は、1 つまたは複数のスクリーンで実行されるデジタルエクスペリエンスを表します。

1. 上記の図に示すように、ディスプレイを作成するロケーションに移動し（** Test_Project／**Locations**／*TestLocation*）、「*TestLocation*」を選択します。

1. アクションバーの「**作成**」をクリックします。
1. **作成**&#x200B;ウィザードから「**ディスプレイ**」を選択し、「**次へ**」をクリックします。

1. ディスプレイロケーションの「**名前**」および「**タイトル**」を入力します（タイトルには *TestDisplay* と入力します）。

1. 「**ディスプレイ**」タブで、レイアウトの詳細を選択します。

   1. 「**解像度**」で「**フル HD**」を選択します。

   1. 「**デバイスの数 - 水平**」で「1」を選択します。

   1. 「**デバイスの数 - 垂直**」で「1」を選択します。

   1. 「**作成**」をクリックします。

以下の図に示すように、新しいディスプレイ（*TestDisplay*）がロケーション（*TestLocation*）に追加されます。

![chlimage_1-12](assets/chlimage_1-12.png)

### チャネルの割り当て {#assigning-channel}

1. *Test_Project*／**Locations**／*TestLocation*／*TestDisplay* からディスプレイに移動します。

1. 「*TestDisplay*」を選択して、アクションバーの「チャネルを割り当て」をタップ／クリックします。*または、*

1. 「**ダッシュボード**」をクリックし、**割り当てられたチャネルとスケジュール**&#x200B;パネルの右上にある「**+ チャネルを割り当て**」を選択します（下図を参照）。**チャネル割り当て**&#x200B;ダイアログボックスが開きます。

1. 「**チャネルを参照...**」で「**パス別**」を選択します。

1. 「**チャネルロール**」に「*LiveStream*」と入力します。

1. 「**チャネル**」で、**チャネルパス**（*Test_Project*／*チャネル*／*TestChannel*）を選択します。

1. このチャネルの「**優先度**」として「*1*」を選択します。

1. 「**サポートされているイベント**」として「**最初の読み込み**」および「**待機中画面**」を選択します。

1. 「**スケジュール**」を入力し、「**次の日から有効**」および「**次の日まで有効**」で日付を選択します。

1. 「**保存**」をクリックします。

チャネルが作成されてパネルに追加されます。

![chlimage_1-15](assets/chlimage_1-15.png)

### デバイスの登録 {#registering-device}

AEM ダッシュボードを使用して、デバイスを登録する必要があります。

>[!NOTE]
>Screens Player を開くには、ダウンロードした AEM Screens アプリケーションまたは Web ブラウザーを使用します。



### Viewing the content in AEM Screens Player {#viewing-the-content-in-screens-player}

上記の設定を追加すると、プレイヤーはデバイス上のディスプレイのデフォルトチャネルを自動的に表示する必要があります。

![chlimage_1-23](assets/chlimage_1-23.png)

AEM Screens Player について詳しくは、[AEM Screens Player](working-with-screens-player.md) を参照してください。
