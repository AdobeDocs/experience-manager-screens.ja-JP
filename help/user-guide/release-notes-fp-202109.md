---
title: 機能パック 202109 のリリースノート
description: 2021 年 9 月 23 日にリリースされたAEM Screens機能パック 202109 について説明します。
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: e1794013-59ce-4ddc-93c0-601668c75cd1
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '897'
ht-degree: 59%

---

# 機能パック 202109 のリリースノート {#release-notes-for-feature-pack}

>[!CAUTION]
>最新バージョンの Adobe Experience Manager（AEM）にアップグレードすることをお勧めします。AEM Screensは、AEM 6.3 Screens プラットフォームのメンテナンスサポートを提供します。

## 可用性 {#availability}

AEM Screens は、AEM 6.5 機能パック 9 をリリースしました。

Adobe ID を使用して、AEM Screens 6.5.9 リリースの最新の機能パックを[ソフトウェア配布ポータル](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)からダウンロードできます。「**Adobe Experience Manager**」タブに移動し、「**Screens**」を検索して「**AEM 6.5 Screens FP9**」というタイトルが付いた最新の機能パックを入手します。

## リリース日 {#release-date}

AEM Screens 機能パック 202109 のリリース日は 2021 年 9 月 23 日（PT）です。

### 新機能 {#what-is-new}

* **ビデオのサムネールサポート**

  ビデオのサムネールが AEM Screens でサポートされるようになりました。コンテンツ作成者は、画像がプレースホルダーとして使用されるように、ビデオのサムネールを定義します。 また、適切なチームによって実際のビデオに関する最終決定が下される間に、コンテンツの再生とターゲティングのテストも適切におこなわれます。 この画像は、ビデオの再生に失敗した場合にも使用できます。
詳しくは、[ビデオのサムネールサポート](/help/user-guide/thumbnail-support.md)を参照してください。

* **基本的な再生モニタリング**

  AEM Screens では、基本的な再生モニタリングをサポートするようになりました。現在は、各 ping で様々な再生指標がレポートされます（デフォルトは 30 秒）。 指標に基づいて、様々なエッジケース（動きのないエクスペリエンス、空白の画面、スケジュールの問題など）を検出します。 この機能を使用すると、プレーヤーがコンテンツを適切に再生しているかどうかをチームがリモートで監視でき、空白の画面やフィールド内のエクスペリエンスの不具合に対する反応性が向上します。 また、不具合のあるエクスペリエンスがエンドユーザーに表示されるリスクの軽減にもつながります。
詳しくは、[基本的な再生モニタリング](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/installing-screens-player#playback-monitoring)を参照してください。

* **コンテンツ割り当てレポートの更新**

  コンテンツ割り当てレポートが最適化され、ユーザーエクスペリエンスが向上しました。ダウンロード可能なレポートでは、ロケーション、ディスプレイ、デバイスなどの改善されたプレーヤー関連のエンティティが一方のスプレッドシートタブに表示され、チャネルやアセットなどのコンテンツプロバイダー情報がもう一方のタブに表示されます。
詳しくは、[コンテンツ割り当てレポート](/help/user-guide/content-assignment-report.md)を参照してください。

* **アダプティブレンディション**

  アダプティブレンディションを使用すると、顧客定義のルールに基づいて、デバイスに最適なレンディションをデバイスで自動的に選択できます。

  AEM Screens 開発者は、すべてのコンテンツバリエーションを手動で作成しなくても、デバイス固有のアセットレンディションが自動的にダウンロードされて再生されるように設定できるようになりました。詳しくは、[アダプティブレンディション：アーキテクチャ概要と設定](/help/user-guide/adaptive-renditions.md)を参照してください。

  また、AEM Screens コンテンツ作成者は、アダプティブレンディションを使用するようにアセットを設定することができます。 また、デバイスを大規模なネットワークに移行して、AEM Screens チャンネルでこの機能を使用することもできます。 詳しくは、[AEM Screens でのアダプティブレンディションの使用](/help/user-guide/using-adaptive-renditions.md)を参照してください。

* **V3 マニフェストのサポート**

  マニフェストバージョン v3 に対応するように Dispatcher を設定できるようになりました。v3 マニフェストを有効にするには、次の操作を行う必要があります。

   * オーサーとパブリッシュ環境の両方で、保留中オフラインコンテンツジョブを消去します。

      * オーサーとパブリッシュのCRXDE Liteーに移動します。

      * ツール/クエリをクリックします。

      * クエリで、を使用します `/jcr:root/var/eventing/jobs/assgined//element(*,slingevent:Job)[\@event.job.topic='screens/offline_content_update']`.

      * これにより、現在実行中またはキューで保留中のオフラインコンテンツジョブが一覧表示されます。

      * クエリから返されるオフラインコンテンツジョブがなくなるまで待ちます。

   * `/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag` でコンテンツ同期を無効にします。

   * `/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl` でスマート同期を有効にします。

   * Dispatcher を更新します。

   * カスタムコンポーネントを更新します。


   * 詳しくは、[マニフェストバージョン v3 に対応した Dispatcher の設定](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens#configuring-dispatcherv3)を参照してください。
   * さらに、カスタムコンポーネントを v3 マニフェストの一部として使用する場合は、[カスタムハンドラーのテンプレート](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop#custom-handlers)を参照してください。


### バグ修正 {#bug-fixes}

**プレーヤー側**

* アセットをレンディションに置き換えることで、ファイルキャッシュエラーを解決しました。

* レンディションマッピングが存在する場合、プレーヤーはアセットレンディションのみを表示するようになりました。

* 応答が有効な JSON でない場合に再認証するための ping を強化しました。

* チャネル名／役割が数値の場合、画面が空白になります。

* スマート同期を使用して、最適化されたレンディションがダウンロードされるようになりました。

* マッピングをレンディションキーのリストに変換しました。

* Windows プレーヤーでの `cmd.exe` および `reg.exe` へのアクセスを解除しました。

* プレーヤーは、最後に成功した再生イベントを報告する必要があります。

* プレーヤーは、再生ステータスを報告する必要があります。

* 次の場合、プレーヤーがアセットを再ダウンロードしない `ALL` キャッシュがクリアされます。

* プレーヤー管理者は、プレーヤー名を選択できるようになりました。

* ディスプレイからチャネル割り当てを削除しても、プレーヤーに反映されません。

* チャネル更新のダウンロード中にプレーヤーが再読み込みされると、プレーヤーは更新を無視します。

* 埋め込みページコンポーネントは、タッチイベントに従うようになりました。

* Tizen プレーヤーのリモートプロビジョニングがサポートされるようになりました。

**サーバー側**

* ターゲットビデオが表示されません。
* 後続シーケンスへの表示データのブロードキャスト時に競合状態が発生する。

* チャネルプレビューが、ビデオを含んだチャネルで機能しません。

* 分割画面チャネルのプレビューモードで表示が空白になります。

* アダプティブレンディションを有効にすると、ビデオのサムネールが空白にレンダリングされます。

* 参照先のページが公開された場合、チャネルマニフェストを自動的に更新します。

* 削除されたデバイスで、Screens レプリケーションキューがブロックされなくなりました。

* マニフェストにターゲットコンテンツも Sites の埋め込みページも含まれていませんでした。現在は修正されました。

* 新しいコア画像コンポーネントがチャネルマニフェストに追加されました。

* スマート同期による最適化されたレンディションのダウンロードがサポートされるようになりました。

* すべてのアセットで最適化されたレンディションが再生されるようになりました。

* 複数のコンテンツプロバイダータイプがサポートされるようになりました。

* 埋め込みシーケンスの再生方法が機能しませんでしたが、現在は修正されました。

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
