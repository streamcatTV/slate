---
title: API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Streamcat.TV API.

# Authentication


## Registration

Streamcat uses API keys to allow access to the API. You can register a new Streamcat API key at our [developer portal](http://streamcat.tv/developers).

Once you have an API Key and Secret, you'll need to create an authentication token.

### HTTP Request

```shell
curl "api_endpoint_here"
  -H "Authorization: Basic meowmeowmeow"
```

`GET https://api.streamcat.tv/authorize`

`Authorization: Basic meowmeowmeow`

You must replace <code>meowmeowmeow</code> with your API Key and Secret in a base64 encoded string in the following format:

`Authorization: Basic <base64 encoded api_key:api_secret>`.

<aside class="notice">
JWT tokens expire in 72 hours, please cache and store the token accordingly.
</aside>

### Making Authenticated Requests
> To authorize, use this code:


```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

> Make sure to replace `meowmeowmeow` with your API key.

Streamcat expects the auth token to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer <token>`

<aside class="notice">
You must replace <code>token</code> with the auth token.
</aside>

# Streams

## Get All Streams

```shell
curl "https://api.streamcat.tv/v1/streams"
  -H "Authorization: Bearer <token>"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "title": "testing",
    "type": "gaming",
    "description": "test desc",
    "private": false,
    "stream_name": "alf123",
    "stream_url": "http://streamcat.tv/alf123",
    "stream_rtmp_url": "rtmp://live.streamcat.tv:8080/stream",
    "video_url": "http://live.streamcat.tv:8080/live/alf123.m3u8",
    "thumbnail": "http://live.streamcat.tv:8080/live/alf123.png"
  }
]
```

This endpoint retrieves all streams.

### HTTP Request

`GET https://api.streamcat.tv/v1/streams`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Stream

```shell
curl "https://api.streamcat.tv/v1/alf123"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
  {
    "id": 1,
    "title": "testing",
    "type": "gaming",
    "description": "test desc",
    "private": false,
    "stream_name": "alf123",
    "stream_url": "http://streamcat.tv/alf123",
    "stream_rtmp_url": "rtmp://live.streamcat.tv:8080/stream",
    "video_url": "http://live.streamcat.tv:8080/live/alf123.m3u8",
    "thumbnail": "http://live.streamcat.tv:8080/live/alf123.png"
  }
```

This endpoint retrieves a specific stream.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET https://api.streamcat.tv/v1/<stream_name>`

### URL Parameters

Parameter | Description
--------- | -----------
stream_name | The stream name of the stream.
