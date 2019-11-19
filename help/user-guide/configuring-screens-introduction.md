---
title: AEM Screensの設定とデプロイ
seo-title: Screens の設定とデプロイ
description: AEM Screensプレーヤーは、Android、Chrome OS、iOSおよびWindowsで使用できます。 このページでは、AEM Screensの設定とデプロイについて説明し、プレーヤーデバイスのh/w選択のガイドラインの概要も説明します。
seo-description: AEM Screensプレーヤーは、Android、Chrome OS、iOSおよびWindowsで使用できます。 このページでは、AEM Screensの設定とデプロイについて説明し、プレーヤーデバイスのh/w選択のガイドラインの概要も説明します。
uuid: bf730d0f-e590-4c0d-a554-e1ff914eb420
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 0c7d6248-8ac0-4387-8725-57ed941f28f7
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Configuring and Deploying AEM Screens {#configuring-and-deploying-aem-screens}

このページでは、デバイスに Screens Player をインストールして設定する方法について説明します。

## AEM Screens playerのインストール {#installing-aem-screens-player}

AEM Screensプレーヤーは、Android、Chrome OS、iOSおよびWindowsで使用できます。

AEM Screens Playerをダウンロ **ードするには**、 [**AEM 6.5 Playerのダウンロードページにアクセスします**](https://download.macromedia.com/screens/) 。

>[!NOTE]
>
>最新のプレーヤー(*.exe*)をダウンロードしたら、プレーヤー上の手順に従ってアドホックインストールを完了します。
>
>1. 左上隅を長押しして、管理パネルを開きます。
>1. 左側のアクシ **ョンメニューから「** Configuration **」に移動し、「** Server **」にAEMインスタンスの場所のアドレスを入力し、「** Save」をクリックします。
>1. 左側のアクションメ **ニューの** 「Registration」リンクをクリックし、以下の手順でデバイスの登録プロセスを完了します。
>



### その他のリソース {#additional-resources}

詳細については、次のトピックを参照してください。

* Android Playerをダウンロードするには、 **Google playにアクセスします**。 Android Watchdogの実装について詳しくは、Androidプレーヤーの実装を [参照してください](implementing-android-player.md)。

* Chrome OS playerを実装するには、 [Chrome Management Consoleを参照してください](implementing-chrome-os-player.md) 。

* AEM Screens Windows playerを設定するには、『Windows playerの実装』を [参照してください](implementing-windows-player.md)。

## サーバーの設定 {#server-configuration}

>[!NOTE]
>
>**重要**:
>
>AEM Screens Player は、クロスサイトリクエストフォージェリ（CSRF）トークンを利用していません。したがって、AEM Screens で使用できるように AEM サーバーを設定するには、空のリファラーを許可して、リファラーフィルターをスキップします。

### 前提条件 {#prerequisites}

AEM Screens で使用できるように AEM サーバーを設定する際に役立つ重要なポイントを次に示します。

#### 空のリファラー要求の許可 {#allow-empty-referrer-requests}

1. **Adobe Experience Manager Web Console Configuration **via AEM instance —&gt;ハンマーアイコン —&gt; **Operations** —&gt; **Web Consoleに移動します**。

   ![screen_shot_2019-07-31at91253am](assets/screen_shot_2019-07-31at91253am.png)

1. **Adobe Experience Manager Web Console Configuration** が開きます。 Slingリファラーを検索します。

   リファラープロパティを検索するには、 **Command** +F( **Mac** )を、 **Windows Ling(Windows)の** Control+F(Mac)を ****&#x200B;押します。

   ![screen_shot_2019-07-31at91728am](assets/screen_shot_2019-07-31at91728am.png)

1. 下の図に示すように、「**空白を許可する**」オプションを選択します。

   ![screen_shot_2019-07-31at91807am](assets/screen_shot_2019-07-31at91807am.png)

1. 「保存 **** 」をクリックして、「Apache Slingリファラーフィルターを空白にする」を有効にします。

#### AEM Screensのタッチ操作対応UIを有効にする {#enable-touch-ui-for-aem-screens}

AEM Screensではタッチ操作対応UIが必要で、Adobe Experience Manager(AEM)のクラシックUIでは動作しません。

1. &lt;yourAuthorInstance&gt;/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImplに移動します。 **
1. 次の図に示すよ **うに、デフォルトのオーサリングUI** モードが **TOUCH**&#x200B;に設定されていることを確認します。

また、*&lt;yourAuthorInstance&gt; *-&gt;* tools （ハンマーアイコン）* -&gt; **Operations** -&gt;* Web Console***を使用して同じ設定を実行し、 **WCM Authoring UI Mode Serviceを検索することもできます**。

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>ユーザーの環境設定を使用して、特定のユーザーに対して常にクラシックUIを有効にできます。

#### NOSAMPLECONTENT 実行モードの AEM {#aem-in-nosamplecontent-runmode}

Running AEM in production uses the **NOSAMPLECONTENT** runmode. *RemovetheX-Frame-Options=SAMEORIGIN* header （追加の応答ヘッダーセクション内）

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`.

これは、AEM Screens Player でオンラインチャネルを再生するために必要です。

#### パスワード制限 {#password-restrictions}

DeviceServiceImplに対する最新の変 ***更により***、パスワード制限を削除する必要がなくなりました。

次のリンクから ***DeviceServiceImplを設定して*** 、画面デバイスユーザーのパスワードを作成する際にパスワード制限を有効にすることができます。

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

次の手順に従ってDeviceServiceImplを設定 ***します***。

1. **Adobe Experience Manager Web Console Configuration **via AEM instance —&gt;ハンマーアイコン —&gt; **Operations** —&gt; **Web Consoleに移動します**。

1. **Adobe Experience Manager Web Console Configuration **が開きます。 deviceserviceを検索します。 プロパティを検索するには、 **Command + fキーを押して** Mac **、** Control + fキーを ********&#x200B;押します。

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### Dispatcher 設定 {#dispatcher-configuration}

AEM Screensプロジェクト用のディスパッチャーを設定する方法については、「AEM Screensプロジェクト用のディスパ [ッチャーの設定」を参照してください](dispatcher-configurations-aem-screens.md)。

#### Java エンコーディング {#java-encoding}

Set the ***Java encoding*** to Unicode. 例えば、Dfile.encoding=Cp1252 は機能しません。**

>[!NOTE]
>
>**推奨事項：**
>
>実稼動環境では AEM Screens サーバーに HTTPS を使用することをお勧めします。

