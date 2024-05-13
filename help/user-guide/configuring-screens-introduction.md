---
title: AEM Screens の設定とデプロイ
description: AEM Screens Player は、Android&trade;、Chrome OS、iOSおよび Windows で使用できます。 AEM Screens の設定とデプロイメントについて説明します。
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
docset: aem65
role: Admin
level: Intermediate
exl-id: 8cf4240c-1d6c-441d-b8a0-f01516455543
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 77%

---

# AEM Screens の設定とデプロイ {#configuring-and-deploying-aem-screens}

このページでは、デバイスに Screens Player をインストールして設定する方法について説明します。

## サーバーの設定 {#server-configuration}

>[!IMPORTANT]
>
>AEM Screens Player は、クロスサイトリクエストフォージェリー（CSRF）トークンを使用しません。 そのため、AEM サーバーを AEM Screens で使用できるように設定する場合は、空のリファラーを許可してリファラーフィルターをスキップします。

## ヘルスチェックフレームワーク {#health-check-framework}

ヘルスチェックフレームワークを使用すると、AEM Screens プロジェクトを実行する前に、2 つの必要な設定が設定されているかどうかを確認できます。

次の 2 つの設定を確認して、AEM Screens プロジェクトを実行できます。つまり、次の 2 つのフィルターの状態を確認できます。

1. **空のリファラーの許可**
2. **https**

次の手順に従って、AEM Screens でこれら 2 つの重要な設定が有効になっているかどうかを確認します。

1. [Adobe Experience Manager Web コンソール Sling Health Check ](http://localhost:4502/system/console/healthcheck?tags=screensconfigs&amp;overrideGlobalTimeout=)に移動します。

   ![アセット](assets/health-check1.png)


2. クリック **選択したヘルスチェックを実行します** したがって、上記の 2 つのプロパティに対して検証を実行できます。

   両方のフィルターが有効な場合、**Screens Configuration Health Service** では&#x200B;**結果**&#x200B;が&#x200B;**OK**&#x200B;と表示され、両方の設定が有効となっています。

   ![アセット](assets/health-check2.png)

   一方または両方のフィルターが無効になっている場合は、下の図に示すように、ユーザーに対してアラートが表示されます。

   両方のフィルターが無効な場合、次のアラートが表示されます。
   ![アセット](assets/health-check3.png)

>[!NOTE]
>
>* **Apache Sling リファラーフィルター**&#x200B;を有効にするには、[空のリファラーリクエストの許可](/help/user-guide/configuring-screens-introduction.md#allow-empty-referrer-requests)を参照してください。
>* **HTTP** サービスを有効にするには、[Apache Felix Jetty ベースの HTTP サービス](/help/user-guide/configuring-screens-introduction.md#allow-apache-felix-service)を参照してください。

### 前提条件 {#prerequisites}

AEM Screens で使用できるように AEM サーバーを設定する際に役立つ重要なポイントを次に示します。

#### 空のリファラー要求の許可 {#allow-empty-referrer-requests}

1. に移動します。 **Adobe Experience Manager Web コンソールの設定** AEM インスタンス/ハンマーアイコン/から選択 **運用** > **Web コンソール**.

   ![画像](assets/config/empty-ref1.png)

1. **Adobe Experience Manager Web コンソール設定**&#x200B;が開きます。「sling referrer」を検索します。

   「sling referrer」プロパティを検索するには、**Command + F** キー（**Mac**）または **Ctrl + F** キー（**Windows**）を押します。

1. 「**Allow Empty**」オプションをオンにします（下図を参照）。

   ![画像](assets/config/empty-ref2.png)

1. 「**保存**」をクリックして、Apache Sling Referrer Filter の「Allow Empty」を有効にします。


#### Apache Felix Jetty Based HTTP Service {#allow-apache-felix-service}

1. に移動します。 **Adobe Experience Manager Web コンソールの設定** AEM インスタンス/ハンマーアイコン/から選択 **運用** > **Web コンソール**.

   ![画像](assets/config/empty-ref1.png)

1. **Adobe Experience Manager Web コンソール設定**&#x200B;が開きます。「Apache Felix Jetty Based HTTP Service」を検索します。

   このプロパティを検索するには、**Command+F** キー（**Mac**）または **Ctrl+F** キー（**Windows**）を押します。

1. 「**ENABLE HTTP**」オプションをオンにします（下図を参照）。

   ![画像](assets/config/config-1.png)

1. クリック **保存** を有効にします *Http* サービス。

#### AEM Screens のタッチ操作対応 UI の有効化 {#enable-touch-ui-for-aem-screens}

AEM Screensにはタッチ UI が必要で、Adobe Experience Manager（AEM）のクラシック UI では動作しません。

1. `*<yourAuthorInstance>/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*` に移動します。
1. 「**Default authoring UI mode**」が「**TOUCH**」に設定されていることを確認します（下図を参照）。

また、yourAuthorInstance *／*&#x200B;ツール（ハンマーアイコン）／**操作**／**Web コンソール**&#x200B;を使用し、**WCM オーサリング UI モードサービス**&#x200B;を検索して、同じ設定を実行することもできます。

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>ユーザーの環境設定を使用して、特定のユーザーに対して常にクラシック UI を有効にすることができます。

#### NOSAMPLECONTENT 実行モードの AEM {#aem-in-nosamplecontent-runmode}

本番環境での AEM の実行には、**NOSAMPLECONTENT** 実行モードを使用します。次の場所に移動して、（追加の応答ヘッダーセクションにある）*X-Frame-Options=SAMEORIGIN* ヘッダーを削除します。

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`。

この削除は、AEM Screens Player でオンラインチャネルを再生するために必要です。

#### パスワード制限 {#password-restrictions}

最新の変更で ***DeviceServiceImpl***&#x200B;パスワード制限を削除する必要はありません。

次のリンクから ***DeviceServiceImpl*** を設定して、Screens デバイスユーザーのパスワードを作成する際のパスワード制限を有効にすることができます。

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

以下の手順に従って ***DeviceServiceImpl*** を設定します。

1. AEM インスタンス／ハンマーアイコン／**操作**／**web コンソール**&#x200B;を使用して、**Adobe Experience Manager web コンソール設定**&#x200B;に移動します。

1. **Adobe Experience Manager web コンソール設定**&#x200B;が開きます。`*deviceservice*` を検索します。このプロパティを検索するには、**Command + F** キー（macOS）または **Ctrl + F** キー（Microsoft® Windows）を押します。

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### Dispatcher 設定 {#dispatcher-configuration}

AEM Screens プロジェクトの Dispatcher を設定する方法については、[AEM Screens プロジェクトの Dispatcher の設定](dispatcher-configurations-aem-screens.md)を参照してください。

#### Java™ エンコーディング {#java-encoding}

***Java™ エンコーディング***&#x200B;を Unicode に設定します。例：`*Dfile.encoding=Cp1252*` は機能しません。

>[!NOTE]
>
>本番環境では AEM Screens サーバーに HTTPS を使用してください。
