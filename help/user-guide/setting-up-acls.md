---
title: ACL の設定
description: ACL を使用してプロジェクトを分離し、個々またはチームが独自のプロジェクトを処理できるようにする方法を説明します。
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: b40bcc9f-307c-422c-8abb-5c15965772d4
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 26%

---

# ACL の設定 {#setting-up-acls}

ここでは、各個人またはチームが独自のプロジェクトを処理できるように、ACL を使用してプロジェクトを区別する方法について説明します。

AEM管理者は、プロジェクトのチームメンバーが他のプロジェクトに干渉せず、各ユーザーにプロジェクト要件に従って特定の役割が割り当てられることを確認する必要があります。

## 権限の設定 {#setting-up-permissions}

次に、プロジェクト用の ACL の設定手順の概要を示します。

1. AEM にログインして、**ツール**／**セキュリティ**&#x200B;に移動します。

   ![screen_shot_2018-02-16at10156pm](assets/screen_shot_2018-02-16at10156pm.png)

1. 「**グループ**」をクリックして、ID（例：Acme）を入力します。

   または、このリンク（`http://localhost:4502/libs/granite/security/content/groupadmin.html`）を使用します。

   次に、 **保存**.

   ![screen_shot_2018-02-16at12648pm](assets/screen_shot_2018-02-16at12648pm.png)

1. クリック **投稿者** リストで、ダブルクリックします。

   ![screen_shot_2018-02-18at33938pm](assets/screen_shot_2018-02-18at33938pm.png)

1. を追加 **アクメ** （作成したプロジェクト） **グループにメンバーを追加**. 「**保存**」をクリックします。

   ![screen_shot_2018-02-18at35630pm](assets/screen_shot_2018-02-18at35630pm.png)

   >[!NOTE]
   >
   >プロジェクトチームメンバーにプレーヤーを登録させる場合（各プレーヤー用のユーザーの作成を伴う）、グループのユーザー管理者を見つけて、ACME グループをユーザー管理者に追加します。

1. に取り組んでいるすべてのユーザーを追加 **アクメ** にプロジェクト **アクメ** グループ。

   ![screen_shot_2018-02-18at41320pm](assets/screen_shot_2018-02-18at41320pm.png)

1. グループの権限の設定 **アクメ** これを使用 `(http://localhost:4502/useradmin)`.

   グループをクリックします **アクメ** をクリックし、 **権限**.

   ![screen_shot_2018-02-18at41534pm](assets/screen_shot_2018-02-18at41534pm.png)

### 権限 {#permissions}

次の表に、プロジェクトレベルの権限を持つパスの概要を示します。

| **パス** | **権限** | **説明** |
|---|---|---|
| `/apps/<project>` | 読み取り | 必要に応じて、プロジェクト ファイルにアクセスできます。 |
| `/content/dam/<project>` | すべて | 画像やビデオなどのプロジェクトアセットを DAM に保存するためのアクセス権を提供します。 |
| `/content/screens/<project>` | すべて | /content/screens の下にあるその他すべてのプロジェクトへのアクセスを削除します。 |
| `/content/screens/svc` | 読み取り | 登録サービスにアクセスできます。 |
| `/libs/screens` | 読み取り | DCC へのアクセスを提供します。 |
| `/var/contentsync/content/screens/` | すべて | プロジェクトのオフラインコンテンツを更新できます。 |

>[!NOTE]
>
>オーサー機能（アセットの管理やチャネルの作成など）と管理機能（プレーヤーの登録など）を分離できる場合があります。 このようなシナリオでは、2 つのグループを作成し、作成者グループを投稿者に、管理者グループを投稿者とユーザー管理者の両方に追加します。

### グループの作成 {#creating-groups}

プロジェクトを作成する際は、基本的な権限セットが割り当てられたデフォルトのユーザーグループも作成する必要があります。 権限をAEM Screensで定義された一般的な役割に拡張します。

例えば、次のプロジェクト固有のグループを作成できます。

* Screens プロジェクト管理者
* Screens プロジェクトオペレーター（プレーヤーの登録、場所とデバイスの管理）
* Screens プロジェクトユーザー（チャネル、スケジュール、チャネル割り当てを操作する）

次の表に、AEM Screens プロジェクトの説明と権限を含むグループをまとめます。

<table>
 <tbody>
  <tr>
   <td><strong>グループ名</strong></td>
   <td><strong>説明</strong></td>
   <td><strong>権限</strong></td>
  </tr>
  <tr>
   <td>Screens 管理者<br /> <em><code>screens-admins</code></em></td>
   <td>AEM Screens機能の管理レベルアクセス</td>
   <td>
    <ul>
     <li>Member Of Contributors</li>
     <li>ユーザー管理者のメンバー</li>
     <li>すべての/content/screens</li>
     <li>すべての/content/dam</li>
     <li>すべての/content/experience-fragments</li>
     <li>すべての/etc/design/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Screens ユーザー<br /> <em><code>screens-users</code></em></td>
   <td>AEM Screensで、チャネルとスケジュールを作成および更新し、場所を割り当てる</td>
   <td>
    <ul>
     <li>Member Of Contributors</li>
     <li><code>&lt;project&gt; /content/screens</code></li>
     <li><code>&lt;project&gt; /content/dam</code></li>
     <li><code>&lt;project&gt; /content/experience-fragments</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td>Screens オペレーター<br /> <em><code>screens-operators</code></em></td>
   <td>場所構造を作成および更新し、AEM Screensにプレーヤーを登録する</td>
   <td>
    <ul>
     <li>Member Of Contributors</li>
     <li><code>jcr:all /home/users/screens</code></li>
     <li><code>jcr:all /home/groups/screens</code></li>
     <li><code>&lt;project&gt; /content/screens</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td>Screens Player<br /> <em><code>screens-&lt;project&gt;-devices</code></em></td>
   <td>グループすべてのプレーヤーとすべてのプレーヤー/デバイスは、自動的に投稿者のメンバーになります。</td>
   <td><p> 寄稿者のメンバー</p> </td>
  </tr>
 </tbody>
</table>
