---
title: Windows 10 プレーヤーの実装
seo-title: Windows 10 プレーヤーの実装
description: このページでは、AEM Screens Windows 10 プレーヤーの設定について説明します。
seo-description: このページでは、AEM Screens Windows 10 プレーヤーの設定について説明します。
uuid: da7e88bf-c251-481e-9029-f8fc4768b309
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 4228e8a1-9749-49a6-a1bb-365492bc2a3d
docset: aem65
translation-type: ht
source-git-commit: 66c741bb73bd5deb2bb5b06dd46f2e407d9c4b7e

---


# Windows 10 プレーヤーの実装 {#implementing-windows-player}

ここでは、AEM Screens Windows 10 プレーヤーの設定について説明します。使用可能な設定ファイルやオプションと、開発およびテストに使用する設定に関する推奨事項について説明します。

## Windows プレーヤーのインストール {#installing-windows-player}

AEM Screens 用の Windows プレーヤーを実装するには、同プレーヤーをインストールしてください。

[**AEM Screens Player のダウンロード**](https://download.macromedia.com/screens/) ページにアクセスします。

### アドホック方式 {#ad-hoc-method}

アドホック方式を使用すると、最新の Windows プレーヤー（**.exe）をインストールできます。[**AEM Screens Player のダウンロード**](https://download.macromedia.com/screens/) ページにアクセスします。

アプリケーションをダウンロードしたら、以下の手順に従ってプレイヤーのアドホックインストールを完了します。

1. 左上隅を長押しして、管理パネルを開きます。
1. 左のアクションメニューから「**設定**」に移動し、接続する AEM インスタンスの場所（アドレス）を入力して、「**保存**」をクリックします。
1. 左側のアクションメニューから「**デバイスの****登録**」リンクに移動して、デバイス登録プロセスのステータスを確認します。

>[!NOTE]
>
>「**状態**」が「**登録済み**」の場合は、「**デバイス ID**」フィールドに値が入力されます。
>
>「**状態**」が「**未登録**」の場合は、**トークン**&#x200B;を使用してデバイスを登録できます。

### サーバーの一括設定：1 つの設定を使用した複数の Windows 10 プレーヤーの登録 {#bulk-server-configuration-registering-multiple-windows-players-with-one-configuration}

Windows プレーヤーをインストールしたら、1 つの設定で複数のプレーヤーを登録できます。

>[!NOTE]
>
>**Windows プレーヤーの一括登録**
>
>Windows プレーヤーを実装する場合、すべてのプレーヤーを個別に手動で設定する必要はありません。テスト済みで導入の準備ができた設定 JSON ファイルを更新することで、すべてのプレーヤーを設定できます。
>
>設定では、すべてのプレーヤーが設定ファイルで指定された同じサーバーに接続されていることが確認されます。プレーヤーの登録は個別に手動でおこなう必要があります。

Windows 10 プレーヤーを設定するには、次の手順を実行します。

1. Windows プレーヤーをインストールします。
1. 設定ファイルは ***%appdata%\com.adobe.aem.screens.player\config.json*** の下にあります。
1. 後述の情報を使用して設定 JSON を更新し、同じフォルダーをプレーヤーが存在するすべてのシステムにコピーします。

### ポリシー属性   {#policy-attributes}

次の表に、参照用のポリシー JSON の例と共にポリシー属性を示します。

| **ポリシー名** | **目的** |
|---|---|
| server | Adobe Experience Manager（AEM） サーバーの URL。 |
| resolution | デバイスの解像度。 |
| rebootSchedule | プレーヤーを再起動するスケジュール。 |
| enableAdminUI | サイト上でデバイスを設定するための Admin UI を有効にします。完全に設定されて実稼動になったら、false に設定します。 |
| enableOSD | デバイスのチャネルを切り替えるための、ユーザー用のチャネルスイッチャー UI を有効にします。完全に設定されて実稼動になったら、false に設定することを検討します。 |
| enableActivityUI | 有効にすると、ダウンロードや同期などのアクティビティの進行状況を表示します。トラブルシューティング用に有効にし、完全に設定されて実稼動になったら無効にします。 |

#### ポリシー JSON ファイルの例{#example-policy-json-file}

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

Windows プレーヤーをデプロイする際は、他のアプリケーションやタスクバーが Windows デスクトップに表示されないように、キオスクモードを有効にすることが重要です。

>[!CAUTION]
>
>Windows のキオスクモードを有効にするには、デバイス管理ソリューションを使用することをお勧めします。キオスクモードを有効にするためのデバイス管理ソリューションがない場合は、以下の手順に従います。この方法では、Windows 10 Enterprise および Windows 10 Education のシェルランチャー機能を使用します。非 UWP アプリ向けに Microsoft が推奨する他の方法もキオスクモードの有効化、特に、Windows の他のエディションでキオスクモードを有効にする場合に適用できます。

キオスクモードを有効にするには、以下の手順に従います。

>[!NOTE]
>
>以下の手順を実行する前に、Windows 10 Enterprise または Windows 10 Education を使用していることを確認してください。

1. シェルランチャーを有効にします。

   詳しくは、Microsoft Windows サポートによる&#x200B;**[シェルランチャー](https://docs.microsoft.com/ja-JP/windows-hardware/customize/enterprise/shell-launcher)**&#x200B;ページの&#x200B;***シェルランチャーの構成***&#x200B;の節を参照してください。

1. キオスクモードに使用する管理者以外のユーザーを作成します（まだ存在しない場合）。ローカルユーザーでもドメインユーザーでも構いません。
1. [AEM Screens Player のダウンロード](https://download.macromedia.com/screens/) ページから、そのキオスクユーザー用の Windows プレーヤーをインストールします。
1. PowerShell スクリプトの編集について詳しくは、[シェルランチャーを使って Windows 10 キオスクを作成する](https://docs.microsoft.com/ja-JP/windows/configuration/kiosk-shelllauncher)を参照してください。

   PowerShell スクリプトを編集して、ユーザー名を上記で作成したユーザー名に置き換えます。アプリケーションの実行可能ファイルへのパスが正しいことを確認します。これにより、カスタムシェルがキオスクユーザーの Windows プレーヤーアプリケーションとして設定され、他のユーザーには explorer.exe がデフォルトとして設定されます。

1. PowerShell スクリプトを管理者として実行します。
1. 再起動してキオスクユーザーとしてログインすると、プレーヤーアプリケーションが起動します。

### トラブルシューティング {#troubleshooting}

キオスクユーザーとしてログインしたときに黒い画面が表示された場合は、Windows プレーヤーの実行可能ファイルへのパスが正しく指定されていない可能性があります。管理者としてログインし直し、スクリプトを確認してから再実行します。

Windows プレーヤーのデフォルトのインストールパスは次のとおりです。

***C:\Users\&amp;lt;your user&gt;\AppData\Local\Programs\@aem-screensscreens-player-electron\AEM Screens Player.exe***

リンク内のサンプルスクリプトでは、カスタムシェルを有効および無効にします。したがって、場合によっては、スクリプトを 2 つに分割し、それぞれで、該当する以下の行を有効または無効にする必要があります。

>[!NOTE]
>
>一部の Windows 環境では、PowerShell スクリプト（特に未署名のスクリプト）の実行はポリシーによって制限されている場合があります。その場合は、この制限を一時的に無効にしてスクリプトを実行したあと、制限を再び有効にする必要があります。PowerShell ウィンドウを開き、次のコマンドを使用します。
>
>*set-executionpolicy unrestricted* - 制限を一時的に解除する
>
>*set-executionpolicy restricted* - スクリプトの実行後に制限を再度有効にする

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```

