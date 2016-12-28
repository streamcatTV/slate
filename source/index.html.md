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

> To authorize, use this code:


```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

> Make sure to replace `meowmeowmeow` with your API key.

Streamcat uses API keys to allow access to the API. You can register a new Streamcat API key at our [developer portal](http://streamcat.tv/developers).

Streamcat expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Streams

## Get All Streams

```shell
curl "https://api.streamcat.tv/v1/streams"
  -H "Authorization: meowmeowmeow"
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
