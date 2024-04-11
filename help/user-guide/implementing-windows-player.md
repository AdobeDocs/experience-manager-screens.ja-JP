---
title: Windows 10 プレーヤーの実装
description: AEM Screens Windows 10 Player の設定について説明します。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
docset: aem65
feature: Administering Screens, Windows Player
role: Admin
level: Intermediate
exl-id: 50b6d9ba-e672-4f4d-a9a8-fb8387685057
source-git-commit: a8055c5f859e401f7b1da4f5d95f1268dee243ad
workflow-type: tm+mt
source-wordcount: '1114'
ht-degree: 57%

---

# Windows 10 プレーヤーの実装 {#implementing-windows-player}

ここでは、AEM Screens Windows 10 プレーヤーの設定について説明します。使用可能な設定ファイルやオプションと、開発およびテストに使用する設定のレコメンデーションについて説明します。

## Windows プレーヤーのインストール {#installing-windows-player}

AEM Screens用 Windows プレーヤーを実装するには、AEM Screens用 Windows プレーヤーをインストールします。

[**AEM 6.5 Player のダウンロード**](https://download.macromedia.com/screens/)ページにアクセスします。

>[!NOTE]
>Windows Player にはウィンドウモードはありません。常にフルスクリーンモードになります。

### AEM Screens 6.5.5 Service Pack の環境の設定 {#fp-environment-setup}

>[!NOTE]
>AEM Screens 6.5.5 Service Pack を使用している場合は、Windows プレーヤーの環境を設定します。

AEM オーサーインスタンスおよびパブリッシュインスタンスの **Adobe Experience Manager Web コンソール設定**&#x200B;で、**login-token cookies の SameSite 属性**&#x200B;を **Lax** から **None** に設定します。

次の手順に従います。

1. `http://localhost:4502/system/console/configMgr` を使用して、**Adobe Experience Manager Web コンソールの設定**&#x200B;に移動します。

1. *Adobe Granite トークン認証ハンドラー*&#x200B;を検索します。

1. **login-token cookie の SameSite 属性**&#x200B;を **Lax** から **None** に設定します。
   ![画像](/help/user-guide/assets/granite-updates.png)

1. 「**保存**」をクリックします。

### アドホック方式 {#ad-hoc-method}

アドホック方式を使用すると、最新の Windows プレーヤー（*.exe*）に設定します。 [**AEM 6.5 Player のダウンロード**](https://download.macromedia.com/screens/)ページにアクセスします。

アプリケーションをダウンロードしたら、以下の手順に従ってプレーヤーのアドホックインストールを完了します。

1. 左上隅のを長押して、管理パネルを開きます。
1. 左のアクションメニューから「**設定**」に移動し、接続する AEM インスタンスの場所（アドレス）を入力して、「**保存**」をクリックします。
1. に移動します。 **デバイス** **登録** 左側のアクションメニューからのリンクを使用して、デバイス登録プロセスのステータスを確認できます。

>[!NOTE]
>
>次の場合 **都道府県** 等しい **登録済み**、に注目してください。 **デバイス ID** フィールドに値が入力されます。
>
>「**状態**」が「**未登録**」の場合は、**トークン**&#x200B;を使用してデバイスを登録できます。

## Windows プレーヤーの命名 {#name-windows}

ユーザーにわかりやすいデバイス名を Windows プレーヤーに割り当てて、割り当てられたデバイス名をAdobe Experience Manager（AEM）に送信することができます。 この機能により、Windows プレーヤーに名前を付けるだけでなく、適切なコンテンツを簡単に割り当てることもできます。

>[!NOTE]
>プレーヤー名は、登録にのみ選択できます。プレーヤーの登録後は、プレーヤー名を変更できなくなります。

Windows プレーヤーに名前を設定するには、次の手順に従います。

1. クリック **開始** > **実行**.
1. Enter `system.cpl`.
1. 「コンピューター名」タブを使用して、コンピューターのホスト名を設定します。

## Windows インストーラーのデフォルトのオプションの変更 {#changing-default-options}

Windows インストーラーのデフォルトオプションを変更する方法と、使用可能なカスタマイズのリストについては、この節を参照してください。

## CLI（PowerShell）を使用したインストール {#install-powershell}

1. Screens プレーヤー&#x200B;**専用**に、カスタムの場所を作成します。（例：
   `C:\Users\User\screens-player`）
1. 次をインストールします：
   `aem-screens-player-electron-xxx-signed.exe /S /D=C:\Users\User\screens-player`
1. 次を開きます：
   `Start-Process C:\Users\User\screens-player\AEMScreensPlayer.exe`

**例**

```shell
C:\Users\User\Downloads> mkdir screens-player

C:\Users\User\Downloads> .\aem-screens-player-electron-xxx-signed.exe /S /D=C:\Users\User\Downloads\screens-player

C:\Users\User\Downloads> Start-Process C:\Users\User\Downloads\screens-player\AEMScreensPlayer.exe
```

## Windows プレーヤーの一括登録 {#bulk-registration}

Windows プレーヤーを実装する場合、すべてのプレーヤーを手動で設定する必要はありません。 テストが済み、デプロイの準備ができた設定 JSON ファイルを更新することで、すべてのプレーヤーを設定できます。

設定では、すべてのプレーヤーが設定ファイルで指定したサーバーと同じサーバーに ping を送信します。 各プレーヤーを手動で登録します。

Windows 10 プレーヤーを設定するには、次の手順を実行します。

1. Windows プレーヤーをインストールします。
1. 設定ファイルは ***%appdata%\com.adobe.aem.screens.player\config.json*** の下にあります。
1. 後述の情報を使用して設定 JSON を更新し、同じフォルダーをプレーヤーが存在するすべてのシステムにコピーします。

### ポリシー属性 {#policy-attributes}

次の表に、参照用のポリシー JSON の例と共にポリシー属性を示します。


| **ポリシー名** | **目的** |
|---|---|
| server | Adobe Experience Manager（AEM）サーバーの URL。 |
| registrationKey | 事前共有キーを使用したデバイスの一括登録に使用されます。 |
| resolution | デバイスの解像度。 |
| rebootSchedule | プレーヤーを再起動するスケジュール。 |
| enableAdminUI | サイト上でデバイスを設定するための Admin UI を有効にします。設定が完了して実稼働になったら、false に設定します。 |
| enableOSD | ユーザー用のチャネルスイッチャー UI を有効にし、デバイスのチャネルを切り替えます。設定が完了して実稼働になったら、false に設定することを検討します。 |
| enableActivityUI | を有効にすると、ダウンロードや同期など、アクティビティの進行状況を表示できます。 トラブルシューティング用に有効にしておき、設定が完了して実稼働になったら無効にします。 |
| cloudMode | Windows プレーヤーから Screens as a Cloud Service に接続する場合は、true に設定します。AMS またはオンプレミス AEMに接続する場合は、false に設定します。 |
| cloudToken | Screens as a Cloud Service に登録するための登録トークン。 |

#### ポリシー JSON ファイルの例 {#example-policy-json-file}

```
{
    "server": "https://localhost:4502",
    "resolution": "auto",
    "rebootSchedule": "at 4:00 am",
    "enableAdminUI": false,
    "enableOSD": false,
    "enableActivityUI": false
}
```

## キオスクモードの有効化 {#enabling-kiosk-mode}

Windows プレーヤーを展開する場合は、他のアプリケーションやタスク バーが Windows デスクトップに表示されないように、キオスク モードを有効にすることが重要です。

>[!CAUTION]
>
>Windows のキオスクモードを有効にするには、デバイス管理ソリューションを使用することをお勧めします。キオスクモードを有効にするためのデバイス管理ソリューションがない場合は、以下の手順に従います。この方法では、Windows 10 Enterprise および Windows 10 Education のシェルランチャー機能を使用します。UWP 以外のアプリでMicrosoftが推奨するその他の方法も、特に Windows の他のエディションでキオスクを有効にするために適用できます。

キオスクモードを有効にするには、以下の手順に従います。

>[!NOTE]
>
>以下の手順を実行する前に、Windows 10 Enterprise または Windows 10 Education を使用していることを確認してください。

1. シェルランチャーを有効にします。

   参照： ***シェルランチャーの設定*** 。対象： **[シェルランチャー](https://learn.microsoft.com/en-us/windows/iot/iot-enterprise/customize/shell-launcher)** Microsoftのページ®Windows サポートを参照してください。

1. キオスクモードに使用する管理者以外のユーザーを作成します（まだ存在しない場合）。ローカルユーザーでもドメインユーザーでも構いません。
1. [AEM Screens Player のダウンロード](https://download.macromedia.com/screens/)ページから、そのキオスクユーザー用の Windows プレーヤーをインストールします。
1. 参照： [シェルランチャーを使用した Windows 10 キオスクの作成](https://learn.microsoft.com/en-us/windows/configuration/assigned-access/shell-launcher/?tabs=intune) 詳細については、PowerShell スクリプトを変更してください。

   PowerShell スクリプトを変更して、ユーザー名を作成したユーザー名に置き換えられるようにします。 アプリケーションの実行可能ファイルへのパスが正しいことを確認します。 これにより、カスタム シェルがキオスク ユーザーの windows プレーヤーアプリケーションとして設定され、他のユーザーの既定が explorer.exe に設定されます。

1. PowerShell スクリプトを管理者として実行します。
1. 再起動してキオスクユーザーとしてログインすると、プレーヤーアプリケーションが起動します。

### トラブルシューティング {#troubleshooting}

Kiosk ユーザーとしてログインした後に黒い画面が表示される場合は、Windows プレーヤーの実行可能ファイルへのパスを誤って指定した可能性があります。 管理者として再度ログインし、スクリプトを検証して再実行します。

Windows プレーヤーのデフォルトのインストールパスは次のとおりです。

***C:\Users\&lt;your user=&quot;&quot;>\AppData\Local\Programs\@aem-screensscreens-player-electron\AEM Screens Player.exe***

リンク内のサンプルスクリプトにより、カスタムシェルを有効または無効にできます。 そのため、スクリプトを 2 つに分割し、次の該当する行を有効/無効にします。

>[!NOTE]
>
>一部の Windows 環境では、PowerShell スクリプトがポリシー（特に未署名のスクリプト）によって制限される場合があります。 スクリプトを実行するには、この制限を一時的に無効にしてから再度有効にして、スクリプトを実行します。 PowerShell ウィンドウを開き、次のコマンドを使用します。
>
>*`set-executionpolicy unrestricted`*  – 制限を一時的に削除します。
>
>*`set-executionpolicy restricted`* - スクリプトの実行後に制限を再度有効にします。

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```

### Screens リモート制御の使用 {#using-remote-control}

AEM Screens には、リモート制御機能が用意されています。この機能について詳しくは、[Screens リモート制御](implementing-remote-control.md)を参照してください