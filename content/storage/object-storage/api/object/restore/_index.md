---
title: "Restore Object"
date: 2020-11-26T10:08:56+09:00
collapsible: false
draft: false
weight: 3
---

# Restore Object

从冷存储中取回 object。可以指定缓存天数，在缓存到期前，object 可以读取。

> 如果存储空间被设置为对匿名用户可写，则请求不需要携带认证信息。然而如果携带了认证信息，但是认证用户不拥有该存储空间的可写权限，则请求该接口会返回权限错误。

## Request Syntax

```http
POST /<object-name>?restore HTTP/1.1
Host: <bucket-name>.<zone-id>.qingstor.com
Date: <date>
Authorization: <authorization-string>
```

## Request Parameters

没有请求参数

## Request Headers

参见[公共请求头](../common/common_header.html#请求头字段-request-header)

## Request Body

Json 消息体
| Name | Type | Description | Required |
| --- | --- | --- | --- |
| days | Integer | 如果是正整数，指定取回 object 缓存的天数。如果是 0，则表示删除缓存中的 object。

## Response Headers

参见[公共响应头](../common/common_header.html#响应头字段-request-header)


## Status Code

成功返回 200, 失败的返回码参考[错误码列表](../common/error_code.html)

## Response Body

正常情况下没有响应消息体, 错误情况下会有返回码对应的 Json 消息, 参考[错误码列表](../common/error_code.html)

## Example

### Example Request

```http
POST /test-0/1?restore HTTP/1.1
Host: example.stor.qingstor.me
Date: Mon, 07 Dec 2020 12:21:41 GMT
Content-Length: 13
Authorization: authorization string

{
    "days": 1
}
```

### Example Response

```http
HTTP/1.1 200 OK
Server: QingStor
Date: Mon, 07 Dec 2020 12:21:41 GMT
Content-Length: 0
Connection: close
x-qs-request-id: 585238a4fcce5469
```
