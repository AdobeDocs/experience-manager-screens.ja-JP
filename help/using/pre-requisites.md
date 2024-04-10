---
title: '[!UICONTROL AEM Screens] の前提条件'
description: AEM Screens プロジェクトを開始する前に必要な前提条件について説明します。
exl-id: ff305a6c-02cb-4c06-a457-9a22f525fab5
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 37%

---

# 前提条件 {#prerequisites}

AEM Screens プロジェクトの実装の詳細を掘り下げる前に、具体的なチュートリアルや資料に目を通すことをお勧めします。

## AEMの学習（Adobe Experience Manager） {#learning-aem}

AEM Screensを使用してデジタルサイネージプロジェクトへの取り組みを開始する前に、Adobe Experience Manager（AEM）に関する知識が必要です。この知識は、AEM Screens プロジェクトに取り組む前に完了しておく必要があります。

Adobe Experience Manager 6.5 について学ぶには、次のチュートリアルとリソースを参照してください。

* **[Adobe Experience Manager の概要](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/overview/introduction)**：Adobe Experience Manager の入門記事やビデオチュートリアルが含まれています。

* **[AEM 6.5 のチュートリアルとビデオ](https://experienceleague.adobe.com/en/docs/experience-manager-tutorials)**：AEM 6.5 のリリースに伴いう AEM Sites、AEM Assets、AEM Forms、AEM Screens、AEM Foundation の新機能と更新機能について重点的に解説する一連のチュートリアルとビデオです。

* **[作成者がおこなう最初の手順](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/sites/authoring/essentials/first-steps)**：ここでは、Adobe Experience Manager（AEM）でコンテンツのオーサリングを開始する際に使用できる主なタスクの概要について説明します。

* **[AEMの中心概念](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/developing/introduction/the-basics)**:AEMの構造に関する中心概念と、それを基にした開発方法（JCR、Sling、OSGi、Dispatcher、ワークフロー、MSM の解説を含む）の概要。

## AEM Screensの製品機能とペルソナの学習 {#product-features}

AEM Screens プロジェクトの基本については、以下のリソースを参照してください。

* **[AEM Screens ユーザーガイド](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/aem-screens-introduction)**：AEM Screens プロジェクトで使用される様々なペルソナの機能に関する詳細なドキュメントです。

* **[AEM Screensの実装の初期設定](https://experienceleague.adobe.com/?launch=AEM-7a#recommended/solutions/experience-manager)**:AEM Screens実装の最も重要な側面を重点的に解説するガイド付きチュートリアルです。

* **[デジタルサイネージネットワークの基本に関するビデオ](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/aem-screens-introduction)**：AV、デジタルサイネージハードウェア、サイネージネットワーク、AV インテグレーターとの連携に関する主要な要素を重点的に解説する 5 つの基本ビデオです。
   * *[第 1 部：プロジェクト上の役割と責務](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/digital-signage-network/project-roles-responsibilities)*:5 部構成のシリーズの第 1 部で、チームメンバーが役割、責務、タイムラインをより深く理解できる内容になっています。 これらは、デジタルサイネージプロジェクトのセールスおよびプロジェクトのライフサイクルで必要です。 Adobe、AEM実装担当者、AV インテグレーターのプロジェクト上の役割と責務を大まかに説明します。
   * *[パート 2：プロジェクト範囲を定義する際の検討事項](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/digital-signage-network/project-considerations)*：5 部構成のシリーズの第 2 部で、AEM Screens の導入を成功に導くためのプリセールス面の検討事項をチームメンバーがより深く理解できる内容になっています。プロジェクトの洗い出し作業で特定する必要がある要素と、プロジェクトを評価し適切な設計を準備するための関係者のアドバイスについて説明します。
   * *[第 3 部：テスト、POC、パイロット、ロールアウト](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/digital-signage-network/testing-pocs-pilots-rollouts)*:5 部構成のシリーズの第 3 部で、チームメンバーが主要用語をより深く理解できる内容になっています。 これらの用語は、ロールアウト前にソリューションの開発を成功に導くうえで非常に重要です。 ハードウェアのラボテストおよびパフォーマンス検証、概念実証（POC）、パイロットプログラムに関するアクションについて説明します。
   * *[第 4 部：プロジェクトの管理とデプロイメント](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/digital-signage-network/project-management-and-deployment)*:5 部構成のシリーズの第 4 部で、プロジェクトの管理とデプロイメントの準備について説明します。 また、プロジェクトの管理とデプロイメントの準備に関して、AV インテグレーターが責任を負う重要な要因も定義します。 プロジェクトのプリプロダクション、プロジェクトの開始、プロジェクトの進行について説明します。
   * *[第 5 部：サポートに関する考慮事項](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/digital-signage-network/support-considerations)*:5 部構成のシリーズの第 5 部で、ハードウェア、ソフトウェア、接続の問題に対処する方法をチームメンバーが学ぶうえで役に立つ内容になっています。 このフェーズでは、オンサイトサポートのコスト見積りとフレームワークを調べます。また、SLA パラメータ、運用予算、NOC ハンドオフの管理方法についても説明します。
