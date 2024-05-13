---
title: 機能パック 202109 のリリースノート
description: 2021年9月23日にリリースされた AEM Screens 機能パック 202109 について説明します。
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: e1794013-59ce-4ddc-93c0-601668c75cd1
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 63%

---

# 機能パック 202109 のリリースノート {#release-notes-for-feature-pack}

>[!CAUTION]
>Adobeでは、最新バージョンのAdobe Experience Manager（AEM）にアップグレードすることをお勧めします。 AEM Screensは、AEM 6.3 Screens プラットフォームのメンテナンスサポートを提供します。

## 入手方法 {#availability}

AEM Screens は、AEM 6.5 機能パック 9 をリリースしました。

AEM Screens 6.5.9 リリースの最新の機能パックは、からダウンロードできます。 [ソフトウェア配布ポータル](https://experience.adobe.com/#/downloads/content/software-distribution/ja/aem.html) Adobe IDを使用する。 に移動します。 **Adobe Experience Manager** タブで「」を検索 **スクリーン** というタイトルの最新の機能パックを取得するには **AEM 6.5 Screens FP9**.

## リリース日 {#release-date}

AEM Screens 機能パック 202109 のリリース日は 2021 年 9 月 23 日（PT）です。

### 新機能 {#what-is-new}

* **ビデオのサムネールサポート**

  ビデオのサムネールが AEM Screens でサポートされるようになりました。コンテンツ作成者は、画像がプレースホルダーとして使用されるように、ビデオのサムネールを定義します。 また、適切なチームが実際のビデオに仕上げる間に、コンテンツの再生とターゲティングも適切にテストします。 その画像は、ビデオの再生に失敗した場合でも使用できます。
詳しくは、[ビデオのサムネールサポート](/help/user-guide/thumbnail-support.md)を参照してください。

* **基本的な再生モニタリング**

  AEM Screens では、基本的な再生モニタリングをサポートするようになりました。プレーヤーでは、各 ping（デフォルトは 30 秒）で様々な再生指標がレポートされるようになりました。指標に基づいて、様々なエッジケース（動きのないエクスペリエンス、空白の画面、スケジュールの問題など）を検出します。この機能を使用すると、プレーヤーがコンテンツを適切に再生しているかどうかをチームがリモートで監視でき、空白の画面やフィールド内のエクスペリエンスの不具合に対する反応が向上します。不具合のあるエクスペリエンスがエンドユーザーに表示されるリスクも軽減されます。
詳しくは、[基本的な再生モニタリング](https://experienceleague.adobe.com/ja/docs/experience-manager-screens/user-guide/administering/installing-screens-player#playback-monitoring)を参照してください。

* **コンテンツ割り当てレポートの更新**

  コンテンツ割り当てレポートが最適化され、ユーザーエクスペリエンスが向上しました。 ダウンロード可能なレポートには、改善されたプレーヤー関連のエンティティが表示されます。 このようなエンティティには、場所、ディスプレイ、デバイスが 1 つのスプレッドシートタブに含まれます。 また、他のタブにあるチャネルやアセットなどのコンテンツプロバイダー情報も含まれます。
詳しくは、[コンテンツ割り当てレポート](/help/user-guide/content-assignment-report.md)を参照してください。

* **アダプティブレンディション**

  アダプティブレンディションを使用すると、顧客定義のルールに基づいて、デバイスに最適なレンディションをデバイスで自動的にクリックできます。

  AEM Screens 開発者は、すべてのコンテンツバリエーションを手動で作成しなくても、デバイス固有のアセットレンディションが自動的にダウンロードされて再生されるように設定できるようになりました。詳しくは、[アダプティブレンディション：アーキテクチャ概要と設定](/help/user-guide/adaptive-renditions.md)を参照してください。

  また、AEM Screens コンテンツ作成者は、アダプティブレンディションを使用するようにアセットを設定することができます。また、デバイスを大規模なネットワークに移行して、AEM Screens チャネルでこの機能を使用することもできます。詳しくは、[AEM Screens でのアダプティブレンディションの使用](/help/user-guide/using-adaptive-renditions.md)を参照してください。

* **V3 マニフェストのサポート**

  マニフェストバージョン v3 に対応するように Dispatcher を設定できるようになりました。v3 マニフェストを有効にするには、次の手順を実行します。

   * オーサーとパブリッシュ環境の両方で、保留中オフラインコンテンツジョブを消去します。

      * オーサーとパブリッシュで CRXDE Lite に移動します。

      * ツール／クエリをクリックします。

      * クエリで `/jcr:root/var/eventing/jobs/assgined//element(*,slingevent:Job)[\@event.job.topic='screens/offline_content_update']` を使用します。

      * これにより、現在実行中またはキューで保留中のオフラインコンテンツジョブが一覧表示されます。

      * クエリから返されるオフラインコンテンツジョブがなくなるまで待ちます。

   * `/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag` でコンテンツ同期を無効にします。

   * `/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl` でスマート同期を有効にします。

   * Dispatcher を更新します。

   * カスタムコンポーネントを更新します。


   * 詳しくは、[マニフェストバージョン v3 に対応した Dispatcher の設定](https://experienceleague.adobe.com/ja/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens#configuring-dispatcherv3)を参照してください。
   * さらに、カスタムコンポーネントを v3 マニフェストの一部として使用する場合は、[カスタムハンドラーのテンプレート](https://experienceleague.adobe.com/ja/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop#custom-handlers)を参照してください。


### バグ修正 {#bug-fixes}

**プレーヤー側**

* アセットをレンディションに置き換えることで、ファイルキャッシュエラーを解決しました。

* レンディションマッピングが存在する場合、プレーヤーはアセットレンディションのみを表示するようになりました。

* 応答が有効な JSON でない場合に再認証するための ping を強化しました。

* チャネル名／役割が数値の場合、画面が空白になります。

* 最適化されたレンディションをスマート同期でダウンロードします。

* マッピングをレンディションキーのリストに変換しました。

* がへのアクセスを削除しました `cmd.exe` および `reg.exe` Windows プレーヤーで調整します。

* プレーヤーは、最後に成功した再生イベントを報告する必要があります。

* プレーヤーは、再生ステータスを報告する必要があります。

* `ALL` キャッシュがクリアされると、プレーヤーがアセットを再ダウンロードしません。

* プレーヤー管理者は、プレーヤー名を選択できるようになりました。

* ディスプレイからチャネル割り当てを削除しても、プレーヤーに反映されません。

* チャネルアップデートのダウンロード中にプレーヤーをリロードすると、プレーヤーはアップデートを無視します。

* 埋め込みページコンポーネントは、タッチイベントに従うようになりました。

* Tizen プレーヤーのリモートプロビジョニングがサポートされるようになりました。

**サーバー側**

* ターゲットビデオが表示されません。
* 後続シーケンスへの表示データのブロードキャスト時に競合状態が発生します。

* チャネルプレビューが、ビデオを含んだチャネルで機能しません。

* 分割画面チャネルのプレビューモードで表示が空白になります。

* アダプティブレンディションを有効にすると、ビデオサムネールが空白にレンダリングされる。

* 参照先のページが公開された場合、チャネルマニフェストを自動的に更新します。

* 削除されたデバイスで、Screens レプリケーションキューがブロックされなくなりました。

* マニフェストにターゲットコンテンツまたは Sites の埋め込みページが含まれていませんでした。 このバグは修正されました。

* 新しいコア画像コンポーネントがチャネルマニフェストに追加されました。

* スマート同期を介した最適化されたレンディションのダウンロードがサポートされるようになりました。

* すべてのアセットで最適化されたレンディションが再生されるようになりました。

* 複数のコンテンツプロバイダータイプがサポートされるようになりました。

* 埋め込みシーケンスの再生方法が機能しませんでしたが、このバグが修正されました。

* リクエストパラメーター `wcmmode` を HTML エントリに使用したオフラインマニフェストはキャッシュできなくなります。

* 空の動的埋め込みシーケンスが原因で画面が空白になることがありました。

* プレーヤーが再生ステータスをレポートするようになりました。

* ビデオが `Tiny mode` で再生されても、デバイスで全画面表示ビデオとして再生されない問題がありましたが、現在は修正されました。

### リリースされている AEM Screens Player

AEM Screens 6.5 機能パック 9 向けに、次の AEM Screens Player がリリースされています。

* Chrome OS
* Windows
* Tizen
* Android™
* Linux®

#### AEM Screens Player のダウンロード

最新のAEM Screens Player のダウンロードとバグ修正について詳しくは、以下を参照してください。 **[AEM Screens Player のダウンロード](https://download.macromedia.com/screens/index.html)**.
