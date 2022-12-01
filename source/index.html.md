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

> RESPONSE 

```json

{
  "AUTH-TOKEN": "xxxx.xxxxx.xxxxx",
  "R-AUTH-TOKEN": "xxxxx.xxxxxx.xxxxxx"
}

```
Fandom Sprots BE에서의 인증/인가는 Jwt 토큰을 사용합니다.

- Jwt 토큰은 `access token`과 `refresh token`을 사용하고 `access token`이 만료된 경우 `refresh token`을 사용하여 `access token`을 재발급합니다.

- 재발급하는 과정에서 Client가 관여하는/해야할 부분은 없습니다. 

- 토큰은 `Cookie`에 담아 사용합니다.
- `cookie`의 key값에 해당하는 token-key는 애플리케이션 프로파일(로컬/개발/운영) 별로 상이합니다. 


### 토큰 형식
<code>
  AUTH-TOKEN : xxxx.xxxx.xxxx

  R-AUTH-TOKEN : xxxx.xxxx.xxxx
</code>


### Jwt 토큰 발급




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

