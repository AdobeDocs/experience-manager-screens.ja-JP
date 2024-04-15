---
title: キックスタートガイド
description: デモ用AEM Screens プロジェクトを作成する方法について説明します。 これは、インストールから新しいプロジェクトの設定、AEM Screens Player でのコンテンツの表示に至るまで、デジタルサイネージエクスペリエンスを作成するのに役立ちます。
feature: Overview, Digital Signage
role: User
level: Beginner
exl-id: 9b7c7f50-2846-4727-a0ec-0220b4cd52c4
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '1276'
ht-degree: 63%

---

# キックスタートガイド {#kickstart-guide}

AEM Screens のキックスタートで、AEM Screens プロジェクトの設定および実行方法について説明します。基本的なデジタルサイネージエクスペリエンスの設定、各チャネルへのアセットやビデオなどのコンテンツの追加、さらにそのコンテンツの AEM Screens Player への公開に関する手順を説明します。

>[!NOTE]
>プロジェクトの詳細に取り組む前に、AEM Screensの最新の機能パックがインストールされていることを確認してください。 Adobe ID を使用して、リリースの最新の機能パックを[ソフトウェア配布ポータル](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)からダウンロードできます。

## 前提条件 {#prerequisites}

次の手順に従って、AEM Screens のサンプルプロジェクトを作成し、コンテンツを Screens Player に公開します。

>[!NOTE]
>次のチュートリアルは、Chrome OS プレーヤーでチャネルのコンテンツを再生する場合を示します。

>[!IMPORTANT]
>**OSGi 設定**
>デバイスからサーバーへのデータの投稿を許可するには、空のリファラーを有効にする必要があります。例えば、空のリファラーのプロパティが無効になっていると、デバイスからスクリーンショットを投稿できません。現在、これらの機能の一部は、OSGi 設定で Apache Sling Referrer Filter の Allow Empty 設定が有効になっている場合にのみ使用できます。ダッシュボードには、セキュリティ設定がこれらの機能の一部の動作を妨げる可能性があることを示す警告が表示される場合があります。
>***Apache Sling Referrer Filter の「Allow Empty」設定***&#x200B;を有効にするには、次の手順に従います。


## 空のリファラー要求の許可 {#allow-empty-referrer-requests}

1. に移動します。 **Adobe Experience Manager Web コンソールの設定** AEM インスタンス/ハンマーアイコン/を選択 **運用** > **Web コンソール**.

   ![画像](assets/config/empty-ref1.png)

1. **Adobe Experience Manager Web コンソール設定**&#x200B;が開きます。「sling referrer」を検索します。

   「sling referrer」プロパティを検索するには、**Command + F** キー（**Mac**）または **Ctrl + F** キー（**Windows**）を押します。

1. 「**Allow Empty**」オプションをオンにします（下図を参照）。

   ![画像](assets/config/empty-ref2.png)

1. 「**保存**」をクリックして、Apache Sling Referrer Filter の「Allow Empty」を有効にします。

## デジタルサイネージエクスペリエンスを 5 分で作成する {#creating-a-digital-signage-experience-in-minutes}

### AEM Screens プロジェクトの作成 {#creating-project}

最初の手順は AEM Screens プロジェクトを作ることです。

1. Adobe Experience Manager（AEM）インスタンスに移動し、「**Screens**」をクリックします。または、`https://localhost:4502/screens.html/content/screens](https://localhost:4502/screens.html/content/screens` から直接アクセスすることもできます。

1. クリック **Screens プロジェクトの作成** そのため、Screens プロジェクトを作成できます。
1. タイトルに「」と入力 **DemoScreen**&#x200B;を選択し、 **保存**.

   ![画像](assets/kickstart/demo-1.png)

   >[!NOTE]
   >プロジェクトを作成すると、AEM Screens プロジェクトのホームページに戻ります。 これでプロジェクトを選択できます。プロジェクトには、**アプリケーション**、**チャネル**、**デバイス**、**ロケーション**&#x200B;および&#x200B;**スケジュール**&#x200B;という 5 つの異なるフォルダーがあります。

### チャネルの作成 {#creating-channel}

AEM Screens プロジェクトを作成したら、コンテンツを管理するチャネルを作成します。

プロジェクトのチャネルを作成するには、次の手順に従います。

1. プロジェクトを作成したら、 **DemoScreen** をプロジェクトおよび選択 **チャネル** フォルダー（下図を参照）。 アクションバーの「**+ 作成**」をクリックします。

   ![画像](assets/kickstart/demo-2.png)

1. ウィザードで「**シーケンスチャネル**」を選択し、「**次へ**」をクリックします。
   ![画像](assets/kickstart/demo-3.png)

1. 「**タイトル**」に「**TestChannel**」と入力し、「**作成**」をクリックします。

   ![画像](assets/kickstart/demo-4.png)

   **TestChannel** がチャネルフォルダーに追加されます（下図を参照）。

   ![画像](assets/kickstart/demo-5.png)

### チャネルへのコンテンツの追加 {#adding-content}

チャンネルを用意したら、AEM Screens Player で表示できるコンテンツをチャンネルに追加します。

以下の手順に従って、プロジェクトのチャネル（**TestChannel**）にコンテンツを追加します。

1. 作成した **DemoProject** プロジェクトに移動し、**チャネル**&#x200B;フォルダーから&#x200B;**TestChannel**&#x200B;を選択します。

1. アクションバーの「**編集**」をクリックします（下図を参照）。**TestChannel** のエディターが開きます。

   ![画像](assets/kickstart/demo-6.png)

1. アクションバーの左側のサイドパネルを切り替えるアイコンをクリックして、アセットとコンポーネントを開きます。

1. チャネルに追加するコンポーネントをドラッグ&amp;ドロップします。

   ![画像](assets/kickstart/demo-7.png)

### ロケーションの作成 {#creating-location}

チャネルを用意したら、場所を作成します。

>[!NOTE]
>***場所*** 様々なデジタルサイネージエクスペリエンスを区分化し、様々な画面の場所に応じたディスプレイの設定を含めます。

プロジェクトの場所を作成するには、次の手順に従います。

1. 作成した **DemoProject** プロジェクトに移動し、**ロケーション**&#x200B;フォルダーを選択します。
1. アクションバーの「**+ 作成**」をクリックします。
1. ウィザードから「**ロケーション**」を選択し、「**次へ**」をクリックします。
1. ロケーションの「**名前**」を入力し（タイトルには「**TestLocation**」と入力します）、「**作成**」をクリックします。

**TestLocation** が作成され、**ロケーション**&#x200B;フォルダーに追加されます。


### ロケーション用ディスプレイの作成 {#creating-display}

ロケーションを作成したら、ロケーション用のディスプレイを作成します。

>[!NOTE]
>***表示*** 1 つまたは複数の画面で実行されるデジタルエクスペリエンスを表します。

1. **TestLocation** に移動して選択します。
1. アクションバーの「**作成**」をクリックします。

   ![画像](assets/kickstart/demo-disp1.png)

1. **作成**&#x200B;ウィザードから「**ディスプレイ**」を選択し、「**次へ**」をクリックします。

   ![画像](assets/kickstart/demo-disp2.png)

1. 「**タイトル**」に「**LobbyDisplay**」と入力し、「**作成**」をクリックします。

   ![画像](assets/kickstart/demo-disp3.png)

   以下の図に示すように、「**TestDisplay**」というタイトルの新しいディスプレイがロケーション「**TestLocation**」に追加されます。

   ![画像](assets/kickstart/demo-disp4.png)

### チャネルの割り当て {#assigning-channel}

プロジェクトの設定が完了したら、チャネルをディスプレイに割り当てて、コンテンツを表示します。

1. から必要なディスプレイに移動します。 **DemoScreen** > **場所** > **TestLocation** > **LobbyDisplay**.

1. アクションバーで「**チャネルの割り当て**」をタップまたはクリックします。

   ![画像](assets/kickstart/demo-assign1.png)

   または、

   アクションバーの「**ダッシュボード**」をタップまたはクリックし、「**割り当てられたチャネルとスケジュール**」パネルで「**チャネルの割り当て**」をクリックします。

   ![画像](assets/kickstart/demo-assign2.png)

1. 「**チャネル割り当て**」ダイアログボックスが開きます。

1. 「**設定**」オプションから、チャネルを&#x200B;**パスで**&#x200B;選択し、「**サポートされているイベント**」として「**初期ロード**」と「**待機中画面**」を選択します。

   >[!NOTE]
   >
   >「**チャネルロール**」、「**優先度**」、「**中断メソッド**」は、すべてデフォルトで設定されます。参照： [チャネルプロパティ](/help/user-guide/channel-assignment-latest-fp.md#channel-properties) チャネル割り当てプロパティの詳細については、を参照してください。

   ![画像](assets/kickstart/demo-assign3.png)

   また、 **アクティベーションウィンドウ** および **繰り返しスケジュール**.

   >[!NOTE]
   >この *繰り返しスケジュール* チャネルに繰り返しスケジュールを設定できます。 1 つのチャネルに対して、複数の繰り返しスケジュールを設定します。
   >詳しくは、「[繰り返しスケジュール](/help/user-guide/channel-assignment-latest-fp.md#recurrence-schedule)」を参照してください。

1. 環境を設定したら、「**保存**」をクリックします。

### デバイスの登録とディスプレイへのデバイスの割り当て {#registering-device}

AEM ダッシュボードを使用してデバイスを登録します。

>[!IMPORTANT]
>Chrome OS プレーヤーは、実際の Chrome プレーヤーデバイスがなくても、開発者モードで Chrome ブラウザープラグインとしてインストールできます。インストールについては、次の手順に従います。
>
>1. [ここ](https://download.macromedia.com/screens/)をクリックして、最新の Chrome プレーヤーをダウンロードします。
>1. 解凍してディスクに保存します。
>1. Chrome ブラウザーを開き、メニューから「**拡張機能**」を選択するか、***chrome://extensions*** に直接移動します。
>1. をオンにする **開発者モード** 右上隅から
>1. クリック **展開されたロード** 左上隅から解凍した Chrome プレーヤーを読み込みます。
>1. チェック **AEM Screens Chrome Player** プラグイン（拡張機能のリストで使用可能な場合）。
>1. 新しいタブを開き、 **アプリ** アイコンを左上隅から選択するか、直接移動します ***chrome://apps***.
>1. クリック **AEM Screens** Chrome プレーヤーを起動するためのプラグイン。 デフォルトでは、プレーヤーはフルスクリーンモードで起動します。押す **Esc** をクリックしてフルスクリーンモードを終了します。

Chrome OS プレーヤーがオンになったら、次の手順に従って Chrome デバイスを登録します。

1. AEM インスタンスから、プロジェクトの&#x200B;**デバイス**&#x200B;フォルダーに移動します。

1. アクションバーの「**デバイスマネージャー**」をタップまたはクリックします。

   ![画像](assets/kickstart/demo-register1.png)

1. 右上にある「**デバイスの登録**」をタップまたはクリックします。

1. 目的のデバイスを選択し、「**デバイスを登録**」をタップまたはクリックします。

   ![画像](assets/kickstart/demo-register2.png)

1. デバイスが登録コードを送信するのを待機し、同時に、Chrome デバイスで&#x200B;**登録コード**を確認します。
   ![画像](assets/kickstart/demo-register3.png)

1. 両方のコンピューターの&#x200B;**登録コード**&#x200B;が同じである場合は、AEM の「**検証**」をタップおよびクリックします。

1. デバイスの名前を「**ChromeDeviceforDemo**」に設定し、「**登録**」をクリックします。

   ![画像](assets/kickstart/demo-register4.png)

1. **デバイス登録成功**&#x200B;ダイアログボックスで、「**ディスプレイを割り当て**」をクリックします。

   ![画像](assets/kickstart/demo-register5.png)

1. ディスプレイへのパスをとして選択します **DemoScreen** > **場所** > **TestLocation** > **LobbyDisplay** をクリックして、 **割り当て**.

   ![画像](assets/kickstart/demo-device6.png)

1. デバイスが正常に割り当てられると、次の確認が表示されます。

   ![画像](assets/kickstart/demo-register8.png)

1. を選択 **終了** をクリックして登録プロセスを完了します。 これで、ディスプレイ ダッシュボードから登録済みデバイスを表示できます。

   ![画像](assets/kickstart/demo-register9.png)

### Chrome Player でのコンテンツの表示 {#viewing-content-output}

チャネル内のすべてのアセットが Chrome OS プレーヤーで再生されるようになりました。

下図では、AEM Screens チャネルのコンテンツを再生しています。

![画像](assets/kickstart/demo-video-screens.gif)
