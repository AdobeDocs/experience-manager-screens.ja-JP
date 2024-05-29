---
title: デバイスの登録
description: AEM Screens プロジェクトでのデバイス登録プロセスについて説明します。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
docset: aem65
feature: Administering Screens, Device Registration
role: Admin
level: Intermediate
exl-id: b2d3a2cd-263f-4142-80da-29ce54cbf391
source-git-commit: ce8340f24d116b4268a6ed15dd4e9f626bad1ef6
workflow-type: ht
source-wordcount: '722'
ht-degree: 100%

---

# デバイスの登録 {#device-registration}

ここでは、AEM Screens プロジェクトでのデバイス登録プロセスについて説明します。

## デバイスの登録 {#registering-a-device}

デバイス登録プロセスには、次に示す 2 台のコンピューターを使用します。

* 登録する実際のデバイス（サイネージディスプレイなど）
* デバイスの登録に使用する AEM サーバー

>[!NOTE]
>
>最新の Windows プレーヤー（*.exe*）を [AEM 6.4 Screens Player のダウンロード](https://download.macromedia.com/screens/)ページからダウンロードしたら、以下の手順に従ってプレーヤーのアドホックインストールを完了します。
>
>1. 左上隅を長押しして、管理パネルを開きます。
>1. 左のアクションメニューから「**設定**」に移動し、AEM インスタンスの場所のアドレスを「**サーバー**」に入力して、「**保存**」をクリックします。
>1. 左のアクションメニューの「**登録**」リンクをクリックし、以下の手順でデバイス登録プロセスを完了します。
>

![screen_shot_2018-11-26at12118pm](assets/screen_shot_2018-11-26at12118pm.png)

1. デバイスで、AEM Screens Player を起動します。登録 UI が表示されます。

   ![screen_shot_2018-11-26at104230am](assets/screen_shot_2018-11-26at104230am.png)

1. AEM で、プロジェクトの&#x200B;**デバイス**&#x200B;フォルダーに移動します。

   >[!NOTE]
   >
   >AEM ダッシュボードで Screens のプロジェクトを作成する方法について詳しくは、[Screens プロジェクトの作成と管理](creating-a-screens-project.md)を参照してください。

1. アクションバーの「**デバイスマネージャー**」ボタンをクリックします。

   ![screen_shot_2018-11-26at104702am](assets/screen_shot_2018-11-26at104702am.png)

1. 右上にある「**デバイスの登録**」ボタンをクリックします。

   ![screen_shot_2018-11-26at104815am](assets/screen_shot_2018-11-26at104815am.png)

1. 必要なデバイス（手順 1 と同じ）をクリックし、「**デバイスを登録**」をクリックします。

   ![screen_shot_2018-11-26at105112am](assets/screen_shot_2018-11-26at105112am.png)

1. AEM で、デバイスから登録コードが送信されるのを待機します。

   ![screen_shot_2018-11-26at105150am](assets/screen_shot_2018-11-26at105150am.png)

1. デバイスで、**登録コード**&#x200B;を確認します。

   ![screen_shot_2018-11-26at105227am](assets/screen_shot_2018-11-26at105227am.png)

1. 両方のコンピューターの&#x200B;**登録コード**&#x200B;が同じ場合は、AEM の「**検証**」ボタンをクリックします（手順 6 を参照）。
1. デバイスの名前を設定し、「**登録**」をクリックします。

   ![screen_shot_2018-11-26at105357am](assets/screen_shot_2018-11-26at105357am.png)

1. 「**完了**」をクリックして、登録プロセスを完了します。

   ![screen_shot_2018-11-26at105456am](assets/screen_shot_2018-11-26at105456am.png)

   >[!NOTE]
   >
   >「**新規登録**」では、新しいデバイスを登録できます。
   >
   >「**ディスプレイを割り当て**」をタップまたはクリックすると、デバイスをディスプレイに直接追加できます。

   「**完了**」をクリックする場合は、デバイスをディスプレイに割り当てます。

   ![screen_shot_2018-11-26at105740am](assets/screen_shot_2018-11-26at105740am.png)

   >[!NOTE]
   >
   >Screens プロジェクトのディスプレイの作成と管理について詳しくは、[ディスプレイの作成と管理](managing-displays.md)を参照してください。

### ディスプレイへのデバイスの割り当て {#assigning-device-to-a-display}

デバイスをディスプレイにまだ割り当てていない場合は、以下の手順に従って、デバイスを AEM Screens プロジェクト内のディスプレイに割り当てます。

1. デバイスをクリックし、アクションバーの「**デバイスを割り当て**」をクリックします。

   ![screen_shot_2018-11-26at111026am](assets/screen_shot_2018-11-26at111026am.png)

1. 「**ディスプレイ / デバイス設定パス**」でディスプレイのパスをクリックします。

   ![screen_shot_2018-11-26at111252am](assets/screen_shot_2018-11-26at111252am.png)

1. パスをクリックしたら、「**割り当て**」をクリックします。

   ![screen_shot_2018-11-26at111722am](assets/screen_shot_2018-11-26at111722am.png)

1. デバイスが正常に割り当てられたら、「**完了**」をクリックします（下図を参照）。

   ![screen_shot_2018-11-26at112041am](assets/screen_shot_2018-11-26at112041am.png)

   また、「**完了**」を選択すると、ディスプレイダッシュボードが表示されます。

   ![screen_shot_2018-11-26at112154am](assets/screen_shot_2018-11-26at112154am.png)

## デバイスマネージャからのデバイスの検索 {#search-device}

デバイスをプレーヤーに登録すると、デバイスマネージャーの UI からすべてのデバイスを表示できます。

1. **DemoScreens**／**デバイス**&#x200B;など、AEM Screens プロジェクトからデバイスマネージャ UI に移動します。

1. **デバイス**&#x200B;フォルダーをクリックし、アクションバーの「**デバイスマネージャー**」クリックします。

   ![画像](/help/user-guide/assets/device-manager/device-manager-1.png)

1. 登録済みデバイスのリストが表示されます。

1. 長いリストの登録済みデバイスがある場合、アクションバーの検索アイコンを使用して検索できるようになりました。

   ![画像](/help/user-guide/assets/device-manager/device-manager-2.png)

   または、

   `/`（スラッシュ）をクリックして、検索機能を起動します。

   ![画像](/help/user-guide/assets/device-manager/device-manager-3.png)


### 検索機能の制限 {#limitations}

* ユーザーは、*デバイス ID*&#x200B;または&#x200B;*デバイス名*&#x200B;に存在する任意の単語を検索できます。

  >[!NOTE]
  >デバイス名は、「*`BostonStoreLobby`*」のように 1 単語ではなく、「*`Boston Store Lobby`*」のように複数の単語で作成することをお勧めします。

* *`Boston Store Lobby`* のようなデバイス名を作成した場合は、*`boston`*、*`store`*、*`lobby`* のいずれかに一致する任意の単語が検索されます。ただし、デバイス名が *`BostonStoreLobby`* の場合、*`boston`* を検索しても結果は表示されません。

* 検索ではワイルドカード（`*`）がサポートされています。「*`boston`*」で始まるすべてのデバイスを検索する場合は、「*`boston`**」を使用できます。

* デバイス名が *`BostonStoreLobby`* で、*`boston`* を検索しても結果が返されない場合は、検索条件で *`boston`** を使用すると、結果が返されます。

## デバイスの登録の制限 {#limitations-on-device-registration}

システム全体のユーザーパスワード制限により、デバイスの登録に失敗することがあります。デバイスの登録では、ランダムに生成されたパスワードを使用してデバイスユーザーを作成します。

*AuthorizableActionProvider* 設定によってパスワードが制限される場合は、デバイスユーザーの作成に失敗する可能性があります。

>[!NOTE]
>
>現在生成されるランダムパスワードは、33～122 の範囲の 36 文字の ASCII 文字で構成されます（ほぼすべての特殊文字を含む）。

```java
25.09.2016 16:54:03.140 *ERROR* [59.100.121.82 [1474844043109] POST /content/screens/svc/registration HTTP/1.1] com.adobe.cq.screens.device.registration.impl.RegistrationServlet Error during device registration
javax.jcr.nodetype.ConstraintViolationException: Password violates password constraint (^(?=.*\d).{7,9}$).
        at org.apache.jackrabbit.oak.spi.security.user.action.PasswordValidationAction.validatePassword(PasswordValidationAction.java:105)
        at org.apache.jackrabbit.oak.spi.security.user.action.PasswordValidationAction.onPasswordChange(PasswordValidationAction.java:76)
        at org.apache.jackrabbit.oak.security.user.UserManagerImpl.onPasswordChange(UserManagerImpl.java:308)
```

### その他のリソース {#additional-resources}

AEM Screens Player について詳しくは、[AEM Screens Player](working-with-screens-player.md) を参照してください。
