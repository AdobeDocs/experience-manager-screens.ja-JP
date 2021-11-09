---
title: Screens レプリケーションエージェントの設定
description: このページでは、Screens レプリケーションエージェントの設定方法について説明します。
role: Developer
level: Intermediate
source-git-commit: 9f0beddf87d9f5473fdedc292d3c24e96b85cdd4
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 10%

---


# Screens レプリケーションエージェントの設定 {#configuring-screens-replication-agent}

ここでは、Screens レプリケーションエージェントの設定方法について説明します。

## ユーザーの有効化とパスワードの更新 {#enable-users}

次の手順に従います。

1. AEM インスタンスに移動します。

1. ツール/ **セキュリティ** —> **ユーザー**.

   ![画像](/help/user-guide/assets/screens-replication/screens-replication1.png)

1. を検索 **screens-receiver-user**.

1. を選択します。 **screens-receiver-user** をクリックし、 **有効にする** をクリックします。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication2.png)

1. クリック **OK** をクリックして確定します。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication3.png)

   ユーザーを有効にすると、 **screens-receiver-user** as **有効** の下に **ステータス** フィールドに入力します。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication4.png)

1. を選択します。 **screens-receiver-user** をクリックし、 **プロパティ** をクリックします。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication5.png)

1. クリック **パスワードを変更** under **アカウント設定** から **詳細** 」タブに表示されます。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication6.png)

1. 新しいパスワードを **パスワードを変更** ダイアログボックスを開き、 **保存**.

   >[!NOTE]
   >次を入力してください： **admin** in **パスワード** フィールドに入力します。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication7.png)

1. クリック **保存して閉じる**.

1. を選択します。 **screens-receiver-user** をクリックし、 **有効化** をクリックします。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication8.png)

1. クリック **OK** をクリックして確定します。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication9.png)

1. を選択します。 **screens-receiver-user** をクリックし、 **無効にする** をクリックします。

   >[!IMPORTANT]
   > 無効化 **screens-receiver-user** は、このユーザーをオーサーインスタンスから無効にするだけで、パブリッシュインスタンスのすべてのユーザーはアクティブなままです。 クリックしない **無効化** アクティベートを解除すると、ユーザーがパブリッシュインスタンスからも削除されるので、アクションバーから。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication10.png)

1. クリック **OK** をクリックして確定します。

## Screens レプリケーションエージェントの更新 {#replicate-agent}

以下の節に従って、Screens レプリケーションエージェントの設定を更新します。

1. AEM インスタンスに移動します。

1. ツール/ **導入** —> **レプリケーション**.

   ![画像](/help/user-guide/assets/screens-replication/screens-replication1a.png)
