---
title: プレーヤーの自動登録
description: このページでは、AMS／オンプレミス Screens でのプレーヤーの自動登録について説明します。
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 28449523-a44d-4260-9771-f1987686cbb6
TQID: https://experienceleague.adobe.com/uvCRS49L6CQbah4AKFwRdhGN-pvKnTWtNMN8CnFojIQ
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 388
ht-degree: 88%

---

# プレーヤーの自動登録 {#auto-registration}

>[!IMPORTANT]
>このコンテンツは、AEM オンプレミス/AMS （AEM 6.5LTSおよびAEM 6.5）に対して有効です。 AEM as a Cloud Service Screensの内容については、[AEM as a Cloud Service ガイド ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)を参照してください。

何千ものプレーヤーを手動で一括登録するのは面倒で、時間とコストが余計にかかります。 このプロセスを簡単にするために、一括登録機能では、AEM で事前に共有されたキーを指定し、設定ファイルまたはモバイルデバイス管理（MDM）ソリューションを通じてプレーヤーにプロビジョニングできます。

## プレーヤーの自動登録の実装 {#bulk-registering-implementation}

プレーヤーの自動登録を実装するには、次の手順に従います。

1. AEM インスタンスにログインし、AEM Screens プロジェクトをクリックして、アクションバーの「**プロパティ**」をクリックします。
1. 「**詳細**」タブをクリックすれば、「**デバイスの登録**」の節を表示できます。

1. **一括登録コード**&#x200B;フィールドで自動登録コードを指定します。 次に、オプションのデフォルトディスプレイを「**デフォルトのディスプレイ割り当て**」で指定して、自動登録されているプレーヤーに割り当てます。

   >[!NOTE]
   >任意のコードを入力し、必要に応じてデフォルトのディスプレイをクリックします。

   ![画像](/help/user-guide/assets/auto-registration/auto-register1.png)
1. MDM または設定 JSON ファイルを使用して、適切なサーバー URL と登録コードをプレーヤーにプロビジョニングします。

   >[!NOTE]
   >詳しくは、ご使用のオペレーティングシステム（OS）に固有のプレーヤーの実装ページを参照してください。 また、登録コードの入力には、管理 UI を使用することもできます。

1. `registrationKey` 属性が AEM に設定された値と一致する場合、プレーヤーは自動的に登録されます。さらに、デフォルトのディスプレイが設定されている場合は、そのコンテンツがダウンロードされ再生されます。

   ![画像](/help/user-guide/assets/auto-registration/auto-register2.png)

## セキュリティのベストプラクティス {#security-best-practices}

この節では、セキュリティのベストプラクティスをいくつか紹介します。

* 登録コードが侵害されていないことを確認する：一括登録を開始する直前に AEM にコードを設定し、登録が完了したら、登録コードのフィールドをクリアして AEM に保存します。

* パス `/bin/screens/registration` は、できるだけ既知の IP 範囲からのみアクセス可能なように設定できます。

* MDM を使用してプレーヤーに設定をプロビジョニングすることを検討します。

* プレーヤーと AEM の通信には、`HTTP` ではなく `HTTPS` を常に使用します。

  >[!NOTE]
  >デフォルトのディスプレイ割り当ては、現在、一括登録でのみ機能します。 登録コードが入手できない場合、手動登録では機能しません。
