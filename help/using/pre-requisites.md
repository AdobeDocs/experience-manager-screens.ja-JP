---
title: '[!UICONTROL AEM Screens] の前提条件'
seo-title: '[!UICONTROL AEM Screens] プロジェクトの前提条件'
description: このガイドでは、AEM Screens プロジェクトを開始する前の前提条件について説明します。
seo-description: このガイドでは、AEM Screens プロジェクトを開始する前の前提条件について説明します。
translation-type: tm+mt
source-git-commit: 599eb98dff8040fd169499fca2894530fd8a42e8
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 100%

---


# 前提条件 {#prerequisites}

AEM Screens プロジェクトの実装の詳細を掘り下げる前に、具体的なチュートリアルや資料に目を通すことをお勧めします。

## AEM（Adobe Experience Manager）の学習 {#learning-aem}

AEM Screens を使用してデジタルサイネージプロジェクトの作業を開始するには、Adobe Experience Manager（AEM）の知識が必要で、AEM Screens プロジェクトに取り組む前に知識を習得しておく必要があります。

Adobe Experience Manager 6.5 については、以下のチュートリアルとリソースを参照してください。

* **[Adobe Experience Manager の概要](https://helpx.adobe.com/jp/experience-manager/get-started.html)**：Adobe Experience Manager の入門記事やビデオチュートリアルが含まれています。

* **[AEM 6.5 のチュートリアルとビデオ](https://helpx.adobe.com/jp/experience-manager/kt/index/aem-6-5-videos.html)**：AEM 6.5 のリリースに伴う AEM Sites、AEM Assets、AEM Forms、AEM Screens、AEM Foundation の新機能と更新された機能について重点的に解説する一連のチュートリアルとビデオです。

* **[作成者がおこなう最初の手順](https://helpx.adobe.com/jp/experience-manager/6-5/sites/authoring/using/first-steps.html)**：Adobe Experience Manager（AEM）でコンテンツのオーサリングを開始する際に使用する主なタスクの概要について説明します。

* **[AEM の中心概念](https://helpx.adobe.com/jp/experience-manager/6-5/sites/developing/using/the-basics.html)**：AEM の構造に関する中心概念と、それを基にした開発方法の概要（JCR、Sling、OSGi、ディスパッチャー、ワークフロー、MSM の解説を含む）です。

## AEM Screens の製品機能とペルソナの学習 {#product-features}

AEM Screens プロジェクトの基本を学ぶには、以下のリソースを参照してください。

* **[AEM Screens ユーザーガイド](https://helpx.adobe.com/jp/experience-manager/6-5/screens/user-guide.html)**：AEM Screens プロジェクトで使用される様々なペルソナの機能に関する詳細なドキュメントです。

* **[AEM Screens 実装の要点](https://experienceleague.adobe.com/?launch=AEM-7a#recommended/solutions/experience-manager)**:AEM Screens の実装に関する基本事項を重点的に解説するガイド付きチュートリアルです。

* **[デジタルサイネージネットワークの基本に関するビデオ](https://helpx.adobe.com/jp/experience-manager/6-5/screens/user-guide.html?topic=/experience-manager/6-5/screens/morehelp/digital-signage-networks-basics.ug.js)**：AV、デジタルサイネージハードウェア、サイネージネットワーク、AV インテグレーターとの連携に関する主要な要素を重点的に解説する 5 つの基本ビデオです。
   * *[パート 1：プロジェクト上の役割と責務](https://helpx.adobe.com/jp/experience-manager/6-5/screens/using/project-roles-responsibilities.html)*：5 部構成のシリーズの第 1 部で、デジタルサイネージプロジェクトのセールスおよびプロジェクトライフサイクル中に必要な役割、責務、タイムラインをチームメンバーがより深く理解できる内容になっています。アドビ、AEM 実装担当者、AVインテグレーターのプロジェクト上の役割と責務を大まかに説明します。
   * *[パート 2：プロジェクト範囲を定義する際の検討事項](https://helpx.adobe.com/jp/experience-manager/6-5/screens/using/project-considerations.html)*：5 部構成のシリーズの第 2 部で、AEM Screens の導入を成功に導くためのプリセールス面の検討事項をチームメンバーがより深く理解できる内容になっています。プロジェクトの洗い出し作業で特定する必要がある要素と、プロジェクトを評価し適切な設計を準備するための関係者のアドバイスについて説明します。
   * *[パート 3：テスト、POC、パイロット、ロールアウト](https://helpx.adobe.com/jp/experience-manager/6-5/screens/using/testing-pocs-pilots-rollouts.html)*：5 部構成のシリーズの第 3 部で、展開前にソリューションの開発を成功に導くうえで非常に重要な主要用語をチームメンバーがより深く理解できる内容になっています。ハードウェアのラボテストおよびパフォーマンス検証、概念実証（POC）、パイロットプログラムに関するアクションについて説明します。
   * *[パート 4：プロジェクトの管理と導入](https://helpx.adobe.com/jp/experience-manager/6-5/screens/using/project-management-and-deployment.html)*：5 部構成のシリーズの第 4 部で、プロジェクトの管理と導入準備について説明し、プロジェクトの管理と導入準備に関して AV インテグレーターが責任を負う重要な要素を定義します。プロジェクトのプリプロダクション、プロジェクトの開始、プロジェクトの進行について説明します。
   * *[パート 5：サポートに関する検討事項](https://helpx.adobe.com/jp/experience-manager/6-5/screens/using/support-considerations.html)*：5 部構成のシリーズの第 5 部で、ハードウェア、ソフトウェア、接続の問題に対処する方法をチームメンバーが学ぶうえで役に立つ内容になっています。このフェーズでは、オンサイトサポートのコスト見積りとフレームワークを調べます。さらに、SLA パラメーター、運用予算、NOC ハンドオフの管理方法についても説明します。
