---
title: AEM Screens でのビデオのサムネールサポート
description: AEM Screens にビデオのサムネールサポートを追加する方法を説明します。
exl-id: d2d87807-1699-47e3-b241-07c5b7e56f15
TQID: https://experienceleague.adobe.com/VlgvGuLabotRAwprPRl4UFIAycPi7M1oqz47nQZIpVU
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 442
ht-degree: 89%

---

# ビデオのサムネールサポート {#thumbnail-support-videos}

>[!IMPORTANT]
>このコンテンツは、AEM オンプレミス/AMS （AEM 6.5LTSおよびAEM 6.5）に対して有効です。 AEM as a Cloud Service Screensの内容については、[AEM as a Cloud Service ガイド &#x200B;](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)を参照してください。

## はじめに {#introduction}

コンテンツ作成者は、画像がプレースホルダーとして使用されるように、ビデオのサムネールを定義できます。 担当のチームが実際のビデオに仕上げる間に、コンテンツの再生とターゲティングを適切にテストできます。 その画像は、ビデオの再生に失敗した場合でも使用できます。

ビデオコンポーネントにサムネール画像のサポートを追加すると、ユーザーは実際のコンテンツと共に有効なコンポーネントをチャネルに適切に追加し、ビデオが実際に配信される前にターゲティング設定を実行できます。

>[!NOTE]
>サムネール画像は、ビデオコンポーネントに設定されている場合、プレーヤーでビデオの再生が失敗した場合に再生されます。 このフォールバックにより、コンテンツを完全にスキップするのではなく、（コンテンツを再生して）オーディエンスに適切なメッセージを配信できます。

サムネールのサポートにより、次のことが可能になります。

* ビデオがまだ準備できていない場合や、プレーヤーに大きなアセットをダウンロードしてテストする必要がない場合に、チャネルエクスペリエンスを準備する

* デバイスで再生の問題が発生した場合に備えて、フォールバックメカニズムを設定する

## ビデオでのサムネールの使用 {#using-thumbnails}

ビデオでサムネールを使用するには、次の手順に従います。

1. 既存の AEM Screens チャネルに移動するか、チャネルを作成します。

1. チャネルをクリックし、アクションバーの「**編集**」をクリックします。

   ![画像](/help/user-guide/assets/thumbnails/thumbnail-1.png)

1. 既存のビデオコンポーネントを追加または編集します（下図を参照）。

   ![画像](/help/user-guide/assets/thumbnails/thumbnail-2.png)

1. ビデオをクリックし、*レンチ*&#x200B;アイコンをクリックします。

   ![画像](/help/user-guide/assets/thumbnails/thumbnail-3.png)

1. **ビデオ**&#x200B;ダイアログボックスが開き、**サムネール**&#x200B;ドロップゾーンが表示されます。

   ![画像](/help/user-guide/assets/thumbnails/thumbnail-4.png)

1. アセットピッカーから&#x200B;**サムネール**&#x200B;ドロップゾーンに画像をドラッグ＆ドロップし、「**完了**」をクリックします。

   ![画像](/help/user-guide/assets/thumbnails/thumbnail-5.png)

1. **プレビュー**&#x200B;をクリックします。

1. コンポーネントにビデオが設定されている場合は、ビデオが再生されます。 ビデオが設定されておらず、サムネールが設定されている場合は、サムネールが再生されます。 それ以外の場合、コンポーネントは未設定と見なされ、スキップされます。

## ビデオでサムネールを使用する際にサポートされているユースケース {#understand-use-case}

ビデオ内のサムネールでは、次のユースケースをサポートしています。

* 何も設定されていないビデオコンポーネントはスキップされます。

* サムネールのみ設定されているビデオコンポーネントでは、サムネールを再生します。

* ビデオ（正しいレンディションがあるもの）とサムネールの両方が設定されているビデオコンポーネントでは、ビデオを再生します。

* ビデオが設定されているビデオコンポーネントでは、再生エラーが発生した場合はサムネールを再生し、サムネールが設定されていない場合は次の項目までスキップします。
