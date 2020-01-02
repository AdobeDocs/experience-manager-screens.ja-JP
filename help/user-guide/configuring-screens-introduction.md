---
title: AEM Screens の設定とデプロイ
seo-title: Screens の設定とデプロイ
description: AEM Screens Player は Android、Chrome OS、iOS、Windows で使用できます。ここでは、AEM Screens の設定とデプロイメントについて説明し、プレーヤーデバイスのハードウェア選定ガイドラインの概要も説明します。
seo-description: AEM Screens Player は Android、Chrome OS、iOS、Windows で使用できます。ここでは、AEM Screens の設定とデプロイメントについて説明し、プレーヤーデバイスのハードウェア選定ガイドラインの概要も説明します。
uuid: bf730d0f-e590-4c0d-a554-e1ff914eb420
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 0c7d6248-8ac0-4387-8725-57ed941f28f7
docset: aem65
translation-type: tm+mt
source-git-commit: 9ee952340d8d966bbad6e6587686448b6413dcca

---


# AEM Screens の設定とデプロイ {#configuring-and-deploying-aem-screens}

このページでは、デバイスに Screens Player をインストールして設定する方法について説明します。

## サーバーの設定 {#server-configuration}

>[!NOTE]
>
>**重要**：
>
>AEM Screens Player は、クロスサイトリクエストフォージェリ（CSRF）トークンを利用していません。したがって、AEM Screens で使用できるように AEM サーバーを設定するには、空のリファラーを許可して、リファラーフィルターをスキップします。

### 前提条件 {#prerequisites}

AEM Screens で使用できるように AEM サーバーを設定する際に役立つ重要なポイントを次に示します。

#### 空のリファラー要求の許可 {#allow-empty-referrer-requests}

1. AEM インスタンスでハンマーアイコン／**操作**／**Web コンソール**&#x200B;をクリックして、「**Adobe Experience Manager Web コンソール設定**」に移動します。

   ![screen_shot_2019-07-31at91253am](assets/screen_shot_2019-07-31at91253am.png)

1. **Adobe Experience Manager Web コンソール設定**&#x200B;が開きます。「sling referrer」を検索します。

   「sling referrer」プロパティを検索するには、**Command + F** キー（**Mac**）または **Ctrl + F** キー（**Windows**）を押します。

   ![screen_shot_2019-07-31at91728am](assets/screen_shot_2019-07-31at91728am.png)

1. Check the **Allow Empty** option, as shown in the figure below.

   ![screen_shot_2019-07-31at91807am](assets/screen_shot_2019-07-31at91807am.png)

1. 「**保存**」をクリックして、Apache Sling Referrer Filter の「Allow Empty」を有効にします。

#### AEM Screens のタッチ操作対応 UI の有効化 {#enable-touch-ui-for-aem-screens}

AEM Screens にはタッチ操作対応 UI が必要で、Adobe Experience Manager（AEM）のクラシック UI では AEM Screens は動作しません。

1. *&lt;yourAuthorInstance>/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl* に移動します。
1. 「**Default authoring UI mode**」が「**TOUCH**」に設定されていることを確認します（下図を参照）。

Alternatively, you can also perform the same setting using *&lt;yourAuthorInstance>*->*tools (hammer icon)* -> **Operations** -> **Web Console** and search for **WCM Authoring UI Mode Service**.

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>ユーザーの環境設定を使用して、特定のユーザーに対して常にクラシック UI を有効にすることができます。

#### NOSAMPLECONTENT 実行モードの AEM {#aem-in-nosamplecontent-runmode}

実稼動環境での AEM の実行には、**NOSAMPLECONTENT** 実行モードを使用します。次の場所に移動して、（追加の応答ヘッダーセクションにある）*X-Frame-Options=SAMEORIGIN* ヘッダーを削除します。

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`.

これは、AEM Screens Player でオンラインチャネルを再生するために必要です。

#### パスワード制限 {#password-restrictions}

***DeviceServiceImpl ***の最新の変更により、パスワード制限を削除する必要がなくなりました。

次のリンクから ***DeviceServiceImpl ***を設定して、Screens デバイスユーザーのパスワードを作成する際のパスワード制限を有効にすることができます。

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

以下の手順に従って ***DeviceServiceImpl ***を設定します。

1. AEM インスタンスでハンマーアイコン／**操作**／**Web コンソール**&#x200B;をクリックして、「**Adobe Experience Manager Web コンソール設定**」に移動します。

1. 「Adobe Experience Manager Web コンソール設定」が開きます。「deviceservice」を検索します。このプロパティを検索するには、**Command + F** キー（**Mac**）または **Ctrl + F** キー（**Windows**）を押します。

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### Dispatcher 設定 {#dispatcher-configuration}

AEM Screens プロジェクトの Dispatcher を設定する方法については、[AEM Screens プロジェクトの Dispatcher の設定](dispatcher-configurations-aem-screens.md)を参照してください。

#### Java エンコーディング {#java-encoding}

***Java エンコーディング&#x200B;***を Unicode に設定します。例えば、*Dfile.encoding=Cp1252 *は機能しません。

>[!NOTE]
>
>**推奨事項：**
>
>実稼動環境では AEM Screens サーバーに HTTPS を使用することをお勧めします。

