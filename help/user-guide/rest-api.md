---
title: REST API
seo-title: REST API
description: AEM Screens には、Siren の仕様に準拠する単純な RESTful API が用意されています。このページの説明に従って、コンテンツ構造内を移動する方法と環境内のデバイスにコマンドを送信する方法を学習します。
seo-description: AEM Screens には、Siren の仕様に準拠する単純な RESTful API が用意されています。このページの説明に従って、コンテンツ構造内を移動する方法と環境内のデバイスにコマンドを送信する方法を学習します。
uuid: 5988fdcb-cda5-4d3e-a2ab-f9ee4179e568
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: c07b6e4f-c0a4-4151-a543-76dabd6d5146
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# REST API{#rest-apis}

AEM Screens provides a simple RESTful API that follows the [Siren](https://github.com/kevinswiber/siren) specification. この API により、コンテンツ構造内を移動したり、環境内のデバイスにコマンドを送信したりできるようになります。

The API is accessible at [*http://localhost:4502/api/screens.json*](http://localhost:4502/api/screens.json).

## コンテンツ構造内での移動 {#navigating-content-structure}

API 呼び出しで返される JSON によって、現在のリソースに関連するエンティティが表示されます。リストに示した自己リンクに従って、これらの各エンティティは再びRESTリソースとしてアクセスできます。

例えば、デモの重要な場所での表示にアクセスするには、次の呼び出しをおこないます。

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship.json HTTP/1.1
Host: http://localhost:4502
```

または、curlを使用します。

```xml
curl -u admin:admin http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship.json
```

結果は以下のようになります。

```xml
{
  "class": [
    "aem-io/screens/location"
  ],
  "links": [
    {
      "rel": [
        "self"
      ],
      "href": "http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship.json"
    },
    {
      "rel": [
        "parent"
      ],
      "href": "http://localhost:4502/api/screens/content/screens/we-retail/locations/demo.json"
    }
  ],
  "properties": {…},
  "entities": [
    {
      "class": [
        "aem-io/screens/display"
      ],
      "links": [
        {
          "rel": [
            "self"
          ],
          "href": "http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json"
        }
      ],
      "rel": [
        "child"
      ],
      "properties": {
        "title": "Single Screen Display",
        "height": 1440,
        "description": "Demo location of a single screen display.",
        "name": "single",
        "width": 2560,
        "idletimeout": 300,
        "layoutrows": 1,
        "layoutcols": 1
      }
    },
    …
  ]
}
```

その後、単一画面表示にアクセスするには、次を呼び出します。

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502
```

## リソースに対するアクションの実行 {#executing-actions-on-the-resource}

API 呼び出しで返される JSON には、リソースに対して使用可能なアクションのリストを含めることができます。

The display, for instance, lists a *broadcast-command* action that allows to send a command to all the devices assigned to that display.

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502
```

または、curlを使用します。

```xml
curl -u admin:admin http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json
```

***結果：***

```xml
{
  "class": [
    "aem-io/screens/display"
  ],
  "links": […],
  "properties": {…},
  "entities": […],
  "actions": [
    {
      "title": "",
      "name": "broadcast-command",
      "method": "POST",
      "href": "/api/screens/content/screens/we-retail/locations/demo/flagship/single",
      "fields": [
        {
          "name": ":operation",
          "value": "broadcast-command",
          "type": "hidden"
        },
        {
          "name": "msg",
          "type": "text"
        }
      ]
    }
  ]
}
```

このアクションを呼び出すには、次の呼び出しをおこないます。

```xml
POST /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502

:operation=broadcast-command&msg=reboot
```

または、curlを使用します。

```xml
curl -u admin:admin -X POST -d ':operation=broadcast-command&msg=reboot' http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json
```

