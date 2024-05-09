---
title: '[!UICONTROL AEM Screens] の前提条件'
description: AEM Screens プロジェクトを開始する前に、前提条件を確認してください。
exl-id: ff305a6c-02cb-4c06-a457-9a22f525fab5
source-git-commit: 2a51258ffe7b969962378dcd0558bd001b616ba1
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 88%

---

# 前提条件 {#prerequisites}

AEM Screens プロジェクトの実装の詳細を掘り下げる前に、具体的なチュートリアルや資料に目を通すことをお勧めします。

## AEM（Adobe Experience Manager）の学習 {#learning-aem}

AEM Screens を使用してデジタルサイネージプロジェクトの作業を開始するには、Adobe Experience Manager（AEM）の知識が必要で、AEM Screens プロジェクトに取り組む前に知識を習得しておく必要があります。

Adobe Experience Manager 6.5 について学ぶには、次のチュートリアルとリソースを参照してください。

* **[Adobe Experience Manager の概要](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/overview/introduction)**：Adobe Experience Manager の入門記事やビデオチュートリアルが含まれています。

* **[AEM 6.5 のチュートリアルとビデオ](https://experienceleague.adobe.com/ja/docs/experience-manager-tutorials)**：AEM 6.5 のリリースに伴いう AEM Sites、AEM Assets、AEM Forms、AEM Screens、AEM Foundation の新機能と更新機能について重点的に解説する一連のチュートリアルとビデオです。

* **[作成者が行う最初の手順](https://experienceleague.adobe.com/ja/docs/experience-manager-65/content/sites/authoring/essentials/first-steps)**：この節では、Adobe Experience Manager（AEM）でコンテンツのオーサリングを開始する際に使用できる主なタスクの概要について説明します。

* **[AEM の中心概念](https://experienceleague.adobe.com/ja/docs/experience-manager-65/content/implementing/developing/introduction/the-basics)**：AEM の構造に関する中心概念と、それを基にした開発方法の概要（JCR、Sling、OSGi、Dispatcher、ワークフロー、MSM の解説を含む）です。

## AEM Screens の製品機能とペルソナの学習 {#product-features}

AEM Screens プロジェクトの基本を学ぶには、以下のリソースを参照してください。

* **[AEM Screens ユーザーガイド](https://experienceleague.adobe.com/ja/docs/experience-manager-screens/user-guide/aem-screens-introduction)**：AEM Screens プロジェクトで使用される様々なペルソナの機能に関する詳細なドキュメントです。

* **[AEM Screens 実装の初期設定](https://experienceleague.adobe.com/?launch=AEM-7a#recommended/solutions/experience-manager)**：AEM Screens 実装の最も重要な側面を重点的に解説するガイド付きチュートリアルです。

* **[デジタルサイネージネットワークの基礎知識に関するビデオ](https://experienceleague.adobe.com/ja/docs/experience-manager-screens/user-guide/aem-screens-introduction)**：オーディオビデオ、デジタルサイネージハードウェア、サイネージネットワーク、オーディオビデオインテグレーターとの連携に関する主要な要素を重点的に解説する 5 つの基本ビデオです。
   * *[第 1 部：プロジェクト上の役割と責務](https://experienceleague.adobe.com/ja/docs/experience-manager-screens/user-guide/digital-signage-network/project-roles-responsibilities)*：5 部構成のシリーズの第 1 部は、チームメンバーが役割、責務、タイムラインをより深く理解できる内容になっています。これらは、デジタルサイネージプロジェクトのセールスおよびプロジェクトのライフサイクル中に必要です。Adobe、AEM実装担当者、音声ビデオインテグレーターのプロジェクト上の役割と責務を大まかに説明します。
   * *[パート 2：プロジェクト範囲を定義する際の検討事項](https://experienceleague.adobe.com/ja/docs/experience-manager-screens/user-guide/digital-signage-network/project-considerations)*：5 部構成のシリーズの第 2 部で、AEM Screens の導入を成功に導くためのプリセールス面の検討事項をチームメンバーがより深く理解できる内容になっています。プロジェクトの洗い出し作業で特定する必要がある要素と、プロジェクトを評価し適切な設計を準備するための関係者のアドバイスについて説明します。
   * *[第 3 部：テスト、POC、パイロットとロールアウト](https://experienceleague.adobe.com/ja/docs/experience-manager-screens/user-guide/digital-signage-network/testing-pocs-pilots-rollouts)*：5 部構成のシリーズの第 3 部は、チームメンバーが主要用語をより深く理解できる内容になっています。これらの用語は、ロールアウト前にソリューションの開発を成功に導くうえで重要です。ハードウェアのラボテストおよびパフォーマンス検証、概念実証（POC）、パイロットプログラムに関するアクションについて説明します。
   * *[第 4 部：プロジェクト管理とデプロイメント](https://experienceleague.adobe.com/ja/docs/experience-manager-screens/user-guide/digital-signage-network/project-management-and-deployment)*：5 部構成のシリーズの第 4 部では、プロジェクト管理とデプロイメントの準備について説明します。また、プロジェクトの管理とデプロイメントの準備に関して、オーディオビデオインテグレーターが責任を負う重要な要因も定義します。 プロジェクトのプリプロダクション、プロジェクトの開始、プロジェクトの進行について説明します。
   * *[第 5 部：サポートに関する検討事項](https://experienceleague.adobe.com/ja/docs/experience-manager-screens/user-guide/digital-signage-network/support-considerations)*：5 部構成のシリーズの第 5 部は、チームメンバーがハードウェア、ソフトウェア、接続の問題に対処する方法を学べる内容となっています。このフェーズでは、オンサイトサポートのコスト見積りとフレームワークを確認します。また、SLA パラメーター、運用予算、NOC ハンドオフの管理方法についても説明します。
