---
title: Screens レプリケーションエージェントの設定
description: Screens レプリケーションエージェントの設定方法について説明します。
role: Developer
level: Intermediate
exl-id: 40877547-5027-41eb-8d66-d4a2d7b9af70
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 32%

---

# Screens レプリケーションエージェントの設定 {#configuring-screens-replication-agent}

ここでは、Screens レプリケーションエージェントの設定方法について説明します。

## 目的 {#objective}

Screens レプリケーションエージェントは、*user*、*password*、*rebootSchedule*、*maxNumberOfLogFilesToKeep* などのコマンドデータをはじめ、さらに多くの値をパブリッシュからオーサーに渡す役目を担います。オーサーがデバイス ping を表示できるように設定する必要があります。

>[!NOTE]
>Screens レプリケーションエージェントについて詳しくは、[Screens レプリケーションエージェントとコマンド](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-publish-architecture-overview#screens-replication-agents-and-commands)を参照してください。

Screens レプリケーションエージェントの設定を完了する場合は、次の両方の節を完了してください。

1. [ユーザーの有効化とパスワードの更新](#enable-users)
1. [Screens レプリケーションエージェント設定の更新](#replicate-agent)

## ユーザーの有効化とパスワードの更新 {#enable-users}

次の手順に従って、ユーザーを有効にし、のパスワードを更新します `screens-receiver-user`:

>[!NOTE]
>セキュリティ上の理由から、次の場合は admin パスワードを使用しないことをお勧めします `screens-receiver-user`.

1. AEM オーサーインスタンスに移動します。

1. ツールを選択 > **セキュリティ** > **ユーザー**.

   ![画像](/help/user-guide/assets/screens-replication/screens-replication1.png)

1. **`screens-receiver-user`** を検索します。

1. 「」を選択します **`screens-receiver-user`** を選択して、 **Enable （有効）** アクションバーから。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication2.png)

1. を選択 **OK** を確認します。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication3.png)

   ユーザーを有効にすると、 **`screens-receiver-user`** as **Enabled** の下 **ステータス** フィールド。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication4.png)

1. 「」を選択します **`screens-receiver-user`** を選択して、 **プロパティ** アクションバーから。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication5.png)

1. を選択 **パスワードの変更** 未満 **アカウント設定** から **詳細** タブを付けます（下図を参照）。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication6.png)

1. に新しいパスワードを入力 **パスワードの変更** ダイアログボックスで「」を選択します。 **保存**.

   >[!NOTE]
   >既存の管理者ユーザーパスワードを次に入力します **パスワード** フィールド。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication7.png)

1. 「**保存して閉じる**」を選択します。

1. 「」を選択します **`screens-receiver-user`** を選択して、 **Activate** アクションバーから。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication8.png)

1. を選択 **OK** を確認します。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication9.png)

1. 「」を選択します **`screens-receiver-user`** を選択して、 **無効** アクションバーから。

   >[!IMPORTANT]
   > 無効化 **`screens-receiver-user`** は、このユーザーをオーサーインスタンスから無効にするだけで、パブリッシュインスタンスのすべてのユーザーはアクティブなままです。 選択しない **非アクティブ化** アクションバーから（非アクティブ化すると、パブリッシュインスタンスからもユーザーが削除されます）。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication10.png)

1. を選択 **OK** を確認します。

## Screens レプリケーションエージェント設定の更新 {#replicate-agent}

次の節に従って、AEM Screens レプリケーションエージェントの設定を更新します。

>[!IMPORTANT]
>既存のすべてのAEM Screens レプリケーションエージェントで、次の手順を実行します。

1. AEM インスタンスに移動します。
1. ツールを選択 > **デプロイメント** > **複製**.

   ![画像](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. を選択 **オーサー環境のエージェント**.

   ![画像](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. 次の図に示すように、オーサー環境のすべてのAEM Screens レプリケーションエージェントを検索し、リンクを選択します。

   >[!NOTE]
   >すべてのAEM Screens レプリケーションエージェントを検索します。 Screens レプリケーションエージェント名には文字が含まれます **S** のタイトルで。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. 「**編集**」を選択します。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. 「**設定**」タブから「**有効**」をチェックします。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. に移動します。 **0.48181894** tab キーを押して **エージェント設定** ダイアログボックスを更新し、 **ユーザー** 対象： **`screens-receiver-user`** と、手順（8）で以前に設定したパスワードを入力します [ユーザーの有効化とパスワードの更新](#enable-users).

   ![画像](/help/user-guide/assets/screens-replication/screens-replication1-f.png)

1. 「**OK**」を選択します。

1. 上記の手順を完了した後、 **接続をテスト** 接続を確認します。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   接続の検証が成功した場合は、Screens レプリケーションエージェントの設定は完了です。
