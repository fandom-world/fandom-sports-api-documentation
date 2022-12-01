---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - http

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Kittn API
---
# Documentation version
- V0.1

# Introduction

Fandom Sports BE에서 제공하는 REST API 문서입니다.

Client-Server 간  API 명세서이자 API의 버전를 관리하는 문서입니다.

문서 제공자는 REST API를 만드는 BE 개발자이며, 문서 사용자는 해당 REST API를 호출하는 FE개발자 입니다.

프로젝트는 [fandom/slate](https://github.com/fandom-world/fandom-sports-api-documentation)에서 다운로드 받을 수 있습니다. 권한이 없을 경우 `이재근`님께 권한요청바랍니다.

| 문서작성은 [컨플루언스](https://fandom-proj.atlassian.net/wiki/spaces/FANDOM/pages/23068676/API)와 Guide 탭을 참조해주세요.

# Authentication

> 테스트 시 JWT 토큰을 발급받는 방법입니다. 

```HTTP
GET /jwt
```
> 발급받은 JWT 토큰을 Header에 추가하여 사용합니다.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Guide

## Request without parameter 


어떤 파라미터도 포함하지 않은 API 호출 방식입니다.

### HTTP Request

`GET http://{{host}}/health`

### Query Parameters

Parameter | Type | Default |Description
--------- |---------|---------|-----------
- | -    | -       | -
- | -    | -       | -

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```http
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```


> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```http
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

