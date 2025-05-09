---
title: AEM Screens での Dispatcher 設定
description: このページでは、AEM Screens プロジェクトの Dispatcher を設定する際のガイドラインについて説明します。
feature: Administering Screens
role: Developer, User
level: Intermediate
exl-id: 8b281488-f54d-4f8a-acef-ca60fa2315ed
source-git-commit: df41a8794683e241b6f12b58d39c01e069187435
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 100%

---

# AEM Screens での Dispatcher 設定{#dispatcher-configurations-for-aem-screens}

Dispatcher は、Adobe Experience Manager のキャッシュ、ロードバランシングツールまたはその両方です。

次のページでは、AEM Screens プロジェクトの Dispatcher を設定する際のガイドラインを説明します。

>[!NOTE]
>
>Dispatcher が使用可能な場合は、Dispatcher ルールでフィルタリングすると、登録サーブレットへの接続を防ぐことができます。
>
>Dispatcher がない場合は、OSGi コンポーネントリストで登録サーブレットを無効にします。

AEM Screens プロジェクトの Dispatcher を設定する前に、Dispatcher に関する事前の知識が必要です。
詳しくは、[Dispatcher の設定](https://experienceleague.adobe.com/ja/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration)を参照してください。

## Manifest バージョン v2 用 Dispatcher の設定 {#configuring-dispatcher}

>[!IMPORTANT]
>次の Dispatcher 設定は、Manifest バージョン v2 にのみ適用されます。Manifest バージョン v3 については、[Manifest バージョン v3 の Dispatcher 設定](#configuring-dispatcherv3)を参照してください。

AEM Screens Player／デバイスは、パブリッシュインスタンスのリソースにアクセスする際にも、認証済みセッションを使用します。複数のパブリッシュインスタンスがある場合、AEM Screens Player またはデバイスから送られるすべてのリクエストで認証済みセッションが有効になるよう、常に同じパブリッシュインスタンスにリクエストを送信する必要があります。

以下の手順に従って、AEM Screens プロジェクトの Dispatcher を設定します。

### スティッキーセッションの有効化 {#enable-sticky-session}

1 つの Dispatcher を経由して複数のパブリッシュインスタンスを使用する場合は、`dispatcher.any` ファイルを更新してスティッキー機能を有効にします。

```xml
/stickyConnections {
  /paths
  {
    "/"
  }
 }
```

1 つの Dispatcher を経由して 1 つのパブリッシュインスタンスを使用する場合、ロードバランサーが各リクエストを Dispatcher に送信してしまうため、Dispatcher でスティッキー機能を有効にしても役に立ちません。この場合、次の図に示すように、「**スティッキー機能**」フィールドの「**有効にする**」をクリックして、ロードバランサーレベルで有効化します。

![画像](/help/user-guide/assets/dispatcher/dispatcher-enable.png)

例えば、AWS ALB を使用している場合、ALB レベルでのスティッキー機能の有効化については、[アプリケーションロードバランサーのターゲットグループ](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html)を参照してください。1 日間、スティッキー機能を有効にします。

### 手順 1：クライアントヘッダーの設定 {#step-configuring-client-headers}

`/clientheaders` セクションに次の内容を追加します。

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### 手順 2：Screens フィルターの設定 {#step-configure-screens-filters}

Screens フィルターを設定するには、以下の内容を ***`/filter`*** に追加します。

```
## AEM Screens Filters
## # Login, Ping and Device Configurations
/0200 { /type "allow" /method "POST" /url "/libs/granite/core/content/login.validate/j_security_check" }
/0201 { /type "allow" /method "GET" /url "/libs/granite/csrf/token.json" }
/0202 { /type "allow" /method "GET" /url "/content/screens/svc.json" }
/0203 { /type "allow" /method "GET" /url "/content/screens/svc.ping.json" }
/0204 { /type "allow" /method "GET" /url "/content/screens/svc.config.json" }
## # Device Dashboard Configurations
/0210 { /type "allow" /method '(GET|POST)' /url "/home/users/screens/*/devices/*/profile_screens.preferences.json" }
/0211 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.logs.json" }
/0212 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.statusinfo.json" }
/0213 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.screenshot.json" }
## # Content Configurations
/0220 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*" }
/0221 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*/jcr:content/*/offline-config_*.zip" }
/0222 { /type "allow" /method '(GET|HEAD)' /url '/var/contentsync/content/screens/.+/jcr:content/.+/offline-config_.*\.[0-9]+\.zip' }
```

### 手順 3：Dispatcher キャッシュの無効化 {#step-disabling-dispatcher-cache}

***/content/screens path*** の Dispatcher キャッシュを無効にします。

Screens Player は認証済みセッションを使用するので、Dispatcher は、`channels/assets` に対する Screens Player のリクエストをキャッシュしません。

アセットが Dispatcher キャッシュから提供されるようにするには、アセットのキャッシュを有効にし、次の手順を実行します。

* `/allowAuthorization 1` を `/cache` セクションに追加
* `/cache` の `/rules` セクションに以下の規則を追加

```xml
/0000
    {
        /glob "*"
        /type "allow"
    }   

/0001
    {
        # Disable Dispatcher Cache for Screens channels
        /glob "/content/screens/*.html"
        /type "deny" 
    }

/0002
    {
    # Disable Dispatcher Cache for Screens offline manifests
    /glob "/content/screens/*.json"
    /type "deny"
    }

/0003
    { # Disable Dispatcher Cache for Screens devices json 
    /glob "/home/users/screens/*.json"
    /type "deny"
    }
```

## Manifest バージョン v3 用の Dispatcher の設定 {#configuring-dispatcherv3}

Screens を機能させるには、パブリッシュインスタンスの前にある Dispatcher で、これらのフィルターとキャッシュルールを許可してください。

### Manifest バージョン v3 の前提条件{#prerequisites3}

AEM Screens の Dispatcher（Manifest バージョン v3）を設定する前に、次の 2 つの前提条件に従ってください。

* `v3 manifests` を使用していることを確認します。`https://<server:port>/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag` に移動し、`Enable ContentSync Cache` がオフになっていることを確認します。

* パブリッシュインスタンスの `/etc/replication/agents.publish/dispatcher1useast1Agent` に Dispatcher フラッシュエージェントが設定されていることを確認します。

  ![画像](/help/user-guide/assets/dispatcher/dispatcher-1.png)

  ![画像](/help/user-guide/assets/dispatcher/dispatcher-3.png)

### フィルター {#filter-v3}

```
## AEM Screens Filters
## # Login, Ping and Device Configurations
/0200 { /type "allow" /method "POST" /url "/libs/granite/core/content/login.validate/j_security_check" }
/0201 { /type "allow" /method "GET" /url "/libs/granite/csrf/token.json" }
/0202 { /type "allow" /method "GET" /url "/content/screens/svc.json" }
/0203 { /type "allow" /method "GET" /url "/content/screens/svc.ping.json" }
/0204 { /type "allow" /method "GET" /url "/content/screens/svc.config.json" }
 
## # Device Dashboard Configurations
/0210 { /type "allow" /method '(GET|POST)' /url "/home/users/screens/*/devices/*/profile_screens.preferences.json" }
/0211 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.logs.json" }
/0212 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.statusinfo.json" }
/0213 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.screenshot.json" }
 
## # Content Configurations
/0220 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*" }
#/0221 { /type "allow" /method '(GET|HEAD)' /url "/content/experience-fragments/*" } ## uncomment this, if you're using experience-fragments
/0222 { /type "allow" /extension '(css|eot|gif|ico|jpeg|jpg|js|gif|pdf|png|svg|swf|ttf|woff|woff2|html|mp4|mov|m4v)' /path "/content/dam/*" } ## add any other formats required for your project here
 
## # Enable clientlibs proxy servlet
/0230 { /type "allow" /method "GET" /url "/etc.clientlibs/*" }
```

### キャッシュルール {#cache-rules-v3}

* `/allowAuthorized "1"` を `publish_farm.any` の `/cache` のセクションに追加します。

* すべての AEM Screens Player は、認証済みセッションを使用して AEM（オーサー／パブリッシュ）に接続します。標準の Dispatcher は、これらの URL をキャッシュしないよう設定されているので、有効にする必要があります。

* `publish_farm.any` の `statfileslevel "10"` を `/cache` セクションに追加
このルールはすべてを無効化するのではなく、キャッシュドキュメントルートから最大 10 レベルのキャッシュがサポートされ、コンテンツが公開されたときに応じて無効になります。コンテンツ構造の深さに基づいて、このレベルを自由に変更できます。

* `/invalidate section in publish_farm.any` に次の内容を追加します

  ```
  /0003 {
      /glob "*.json"
      /type "allow"
  }
  ```

* `publish_farm.any` にある `/cache` の `/rules` セクション、または `publish_farm.any` からインクルードされるファイルに、次のルールをセクションに追加します。

  ```
  ## Don't cache CSRF login tokens
  /0001
      {
      /glob "/libs/granite/csrf/token.json"
      /type "deny"
      }
  ## Allow Dispatcher Cache for Screens channels
  /0002
      {
          /glob "/content/screens/*.html"
          /type "allow"
      }
  ## Allow Dispatcher Cache for Screens offline manifests
  /0003
      {
      /glob "/content/screens/*.manifest.json"
      /type "allow"
      }
  ## Allow Dispatcher Cache for Assets
  /0004
      {
  
      /glob "/content/dam/*"
      /type "allow"
      }
  ## Disable Dispatcher Cache for Screens devices json
  /0005
      {
      /glob "/home/users/screens/*.json"
      /type "deny"
      }
  ## Disable Dispatcher Cache for Screens svc json
  /0006
      {
      /glob "/content/screens/svc.json"
      /type "deny"
      }
  ```

### segments.js の無効化ルールの追加 {#invalidsegmentjs}

AEM Screens でターゲットキャンペーンを使用している場合は、AEM で新しいセグメントを追加して公開する際に、Dispatcher から提供される `segments.js file` を無効にする必要があります。この無効化ルールがないと、新しいターゲットキャンペーンは AEM Screens Player で機能しません（代わりにデフォルトコンテンツが表示されます）。

* 無効化ルールを `/etc/httpd/conf.dispatcher.d/available_farms/999_ams_publish_farm.any` に追加します。 追加するルールは次のとおりです。

```
    /invalidate {
                        .
                        .
                        /0004 {
                               /glob "conf/<project-name>/settings/wcm/.js"
                               /type "allow"
                        }
                }
```

* このルールにより、`segments.js` ファイルが無効化され、変更時に最新のファイルが取得されます。
