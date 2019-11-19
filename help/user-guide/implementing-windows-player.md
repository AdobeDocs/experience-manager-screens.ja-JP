---
title: Windows 10 playerの実装
seo-title: Windows 10 playerの実装
description: このページでは、AEM Screens Windows 10 プレーヤーの設定について説明します。
seo-description: このページでは、AEM Screens Windows 10 プレーヤーの設定について説明します。
uuid: da7e88bf-c251-481e-9029-f8fc4768b309
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 4228e8a1-9749-49a6-a1bb-365492bc2a3d
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Windows 10 playerの実装 {#implementing-windows-player}

ここでは、AEM Screens Windows 10プレーヤーの設定について説明します。 開発およびテストで使用する設定に関して、使用可能および推奨される設定ファイルおよびオプションの情報を提供します。

## Windows playerのインストール {#installing-windows-player}

AEM Screens用のWindows playerを実装するには、AEM Screens用のWindows playerをインストールしてください。

「 [**AEM 6.4 Player Downloads**](https://download.macromedia.com/screens/) 」ページにアクセスします。

### アドホックメソッド {#ad-hoc-method}

アドホック方式を使用すると、最新のWindows Player (*.exe*)をインストールできます。 AEM 6.4 [**プレイヤーのダウンロードページにアクセス**](https://download.macromedia.com/screens/) 。

アプリケーションをダウンロードしたら、プレーヤーの次の手順に従ってアドホックインストールを完了します。

1. 左上隅を長押しして、管理パネルを開きます。
1. 左側のアク **ション** メニューから「Configuration」に移動し、接続するAEMインスタンスの場所（アドレス）を入力し、「 **Save」をクリックします**。
1. 左側のアクションメニ **ューから** 「Device **** Registration」リンクに移動して、デバイス登録プロセスのステータスを確認します。

>[!NOTE]
>
>「 **State** 」が「 **REGISTERED**」の場合は **、「** Device id」フィールドに値が入力されます。
>
>状態が **UNREGISTEREDの場合** 、ト **ークンを**&#x200B;使用して **** デバイスを登録できます。

### バルクサーバーの設定：1つの構成で複数のWindows 10プレーヤーを登録する {#bulk-server-configuration-registering-multiple-windows-players-with-one-configuration}

Windows playerをインストールしたら、1つの設定で複数のプレーヤーを登録できます。

>[!NOTE]
>
>**Windows playerのバルク登録**
>
>Windows プレーヤーを実装する場合、すべてのプレーヤーを個別に手動で設定する必要はありません。テスト済みで導入の準備ができた設定 JSON ファイルを更新することで、すべてのプレーヤーを設定できます。
>
>設定では、すべてのプレーヤーが設定ファイルで指定された同じサーバーに接続されていることが確認されます。プレーヤーの登録は個別に手動でおこなう必要があります。

Windows 10 プレーヤーを設定するには、次の手順を実行します。

1. Windows playerをインストールします。
1. 設定ファイルは、 ***%appdata%\com.adobe.aem.screens.player\config.jsonの下にあります***。
1. 後述の情報を使用して設定 JSON を更新し、同じフォルダーをプレーヤーが存在するすべてのシステムにコピーします。

### ポリシー属性 {#policy-attributes}

次の表に、参照用のポリシー JSON の例と共にポリシー属性を示します。

| **ポリシー名** | **目的** |
|---|---|
| server | Adobe Experience Manager（AEM） サーバーの URL。 |
| resolution | デバイスの解像度。 |
| rebootSchedule | プレーヤーを再起動するスケジュール。 |
| enableAdminUI | サイト上でデバイスを設定するための Admin UI を有効にします。完全に設定されて実稼動になったら、false に設定します。 |
| enableOSD | デバイスのチャネルを切り替えるための、ユーザー用のチャネルスイッチャー UI を有効にします。完全に設定されて実稼動になったら、false に設定することを検討します。 |
| enableActivityUI | 有効にすると、ダウンロードや同期などのアクティビティの進行状況を表示します。トラブルシューティング用に有効にし、完全に設定されて実稼動になったら無効にします。 |

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

Windows playerを展開する場合は、Kioskモードを有効にして、他のアプリケーションやタスクバーがWindowsデスクトップに表示されないようにすることが重要です。

>[!CAUTION]
>
>Windows版Kioskを有効にするには、デバイス管理ソリューションを使用することをお勧めします。 以下の手順に従って、キオスクモードを有効にするデバイス管理ソリューションがない場合に行います。 この方法では、Windows 10 EnterpriseおよびEduで使用可能なシェルランチャー機能を使用します。 UWP以外のアプリケーションに対してMicrosoftが推奨するその他の方法は、特にWindowsの他のエディションでKioskを有効にする場合にも適用できます。

以下の手順に従ってキオスクモードを有効にします。

>[!NOTE]
>
>次の手順に従う前に、Windows 10 EnterpriseまたはEducationを使用していることを確認してください。

1. シェルランチャーを有効にします。

   詳細については、Microsoft Windowsサ ***ポートの「***** Shell Launcher [**」ページの「Configure Shell Launcher](https://docs.microsoft.com/en-us/windows-hardware/customize/enterprise/shell-launcher)」を参照してください。

1. Kioskで使用する管理者以外のユーザーを作成します（まだ存在しない場合）。 ローカルユーザーまたはドメインユーザーを指定できます。
1. AEM Screens playerのダウンロードページから、そのKioskユーザー用のWindowsプ [レイヤーをインストールします](https://download.macromedia.com/screens/) 。
1. 詳細につい [ては、「Windows 10キオスクを作成するには](https://docs.microsoft.com/en-us/windows/configuration/kiosk-shelllauncher) 、Shell Launcherを使用します。」を参照してください。

   PowerShellスクリプトを変更して、ユーザー名を作成したユーザー名に置き換えます。 アプリケーションの実行可能ファイルへのパスが正しいことを確認します。 これにより、カスタムシェルがキオスクユーザーのWindowsプレーヤーアプリケーションとして設定され、他のユーザーのデフォルトがexplorer.exeに設定されます。

1. PowerShellスクリプトを管理者として実行します。
1. 再起動して、Kioskユーザーとプレイヤーアプリケーションを起動し、ログインします。

### トラブルシューティング {#troubleshooting}

Kioskユーザーとしてログインする際に黒い画面が表示された場合は、Windows Playerの実行可能ファイルへのパスが正しく指定されていない可能性があります。 管理者として再度ログインし、スクリプトを確認して再実行します。

Windowsプレーヤーのデフォルトのインストールパスは次のとおりです。

***C:\Users\&amp;lt;your user&gt;\AppData\Local\Programs\@aem-screens-player-electron\AEM Screens Player.exe***

リンク内のサンプルスクリプトは、カスタムシェルを有効または無効にします。 したがって、スクリプトを2つに分割し、次の該当行を有効または無効にする必要がある場合があります。

>[!NOTE]
>
>一部のWindows環境では、PowerShellスクリプトはポリシー（特に未署名のスクリプト）によって制限されている場合があります。 スクリプトを実行するには、スクリプトを実行する際に、この制限を一時的に無効にして再び有効にする必要がある場合があります。 PowerShellウィンドウを開き、次のコマンドを使用します。
>
>*set-executionpolicy unrestricted* — 制限を一時的に削除します。
>
>*set-executionpolicy restricted* — スクリプトの実行後に制限を再度有効にします。

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```

