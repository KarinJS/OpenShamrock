---
title: 资源相关
icon: video-camera
---

::: warning 注意
对于 Shamrock 尚未实现的 API，会在标题添加标记 <Badge text="未实现" type="danger" vertical="baseline" />
:::

## 获取图片

该接口用于获取图片，只能获取已缓存的图片。

### API 端点

`/get_image`

### 参数

| 字段 | 类型   | 必须 | 说明     |
| ---- | ------ | ---- | -------- |
| file | string | 是   | 文件 MD5 |

### 响应

| 字段     | 类型   | 说明      |
| -------- | ------ | --------- |
| size     | int64  | 文件大小  |
| url      | string | 文件 URL  |
| filename | string | 文件 名称 |

## 检查是否可以发送图片 <Badge text="未实现" type="danger" />

该接口用于检查是否可以发送图片。

### API 端点

`/can_send_image`

### 参数

::: tip 提示
该 API 无需参数
:::

### 响应

| 字段名 | 数据类型 | 说明   |
| ------ | -------- | ------ |
| yes    | boolean  | 是或否 |

## 图片 OCR <Badge text="未实现" type="danger" />

该接口用于图片 OCR。

### API 端点

`/ocr_image`

### 参数

| 字段  | 类型   | 说明   |
| ----- | ------ | ------ |
| image | string | 图片ID |

### 响应

| 字段     | 类型                                  | 说明    |
| -------- | ------------------------------------- | ------- |
| texts    | List<[TextDetection](#textdetection)> | OCR结果 |
| language | string                                | 语言    |

#### TextDetection

| 字段        | 类型      | 说明               |
| ----------- | --------- | ------------------ |
| text        | string    | 文本               |
| confidence  | int32     | 置信度             |
| coordinates | vector2[] | 二维数组表示的坐标 |

## 获取语音

该接口用于获取语音。

### API 端点

`/get_record`

### 参数

| 字段       | 类型   | 必须 | 说明     |
| ---------- | ------ | ---- | -------- |
| file       | string | 是   | 文件 MD5 |
| out_format | string | 是   | 输出格式 |

### 响应

| 字段 | 类型   | 说明     |
| ---- | ------ | -------- |
| file | string | 文件路径 |
| url  | string | 文件 URL |
| md5 | string | 文件md5,get_file的时候用这个较稳定，然后你程序如果是反向ws，可以用这个作为record的等待ident |

## 检查是否可以发送语音 <Badge text="未实现" type="danger" />

该接口用于检查是否可以发送语音。

### API 端点

`/can_send_record`

### 参数

::: tip 提示
该 API 无需参数
:::

### 响应

| 字段名 | 数据类型 | 说明   |
| ------ | -------- | ------ |
| `yes`  | boolean  | 是或否 |

### API 端点

`/get_record`

::: tip 提示
要使用此接口, 通常需要安装 ffmpeg, 请参考 OneBot 实现的相关说明。
:::

### 参数

| 字段名     | 数据类型 | 默认值 | 说明                                                                                 |
| ---------- | -------- | ------ | ------------------------------------------------------------------------------------ |
| file       | string   | -      | 收到的语音文件名（消息段的 `file` 参数）, 如 `0B38145AA44505000B38145AA4450500.silk` |
| out_format | string   | -      | 要转换到的格式, 目前支持 `mp3`、`amr`、`wma`、`m4a`、`spx`、`ogg`、`wav`、`flac`     |

### 响应

| 字段名 | 数据类型 | 说明                                                                                              |
| ------ | -------- | ------------------------------------------------------------------------------------------------- |
| file   | string   | 转换后的语音文件路径, 如 `/home/somebody/cqhttp/data/record/0B38145AA44505000B38145AA4450500.mp3` |

## 获取文件

该接口用于获取语音，哦当然，这个接口目前使用的是base64返回，主要为了照顾使用反向websocket的用户，如果是正向用户或者getpost用户，直接用/res/去拿数据更方便

如果你选择压缩，目前文本压缩性能较好，如果是音频或者视频，压缩率只有95.7%左右，大概只能节省5%的带宽，是否使用压缩获取可以自行考虑


### API 端点

`/get_file`

### 参数

| 字段       | 类型   | 必须 | 说明     |
| ---------- | ------ | ---- | -------- |
| file       | string | 是   | 文件 MD5 |
| file_type | string | 是   | 输出格式,支持base64|gzip,如果获取大文件，可以选择压缩 |

### 响应

| 字段 | 类型   | 说明     |
| ---- | ------ | -------- |
| file | string | 文件路径,和get_record一样 |
| base64String  | string | 文件 URL |
| md5 | string | 文件md5 |

## 获取视频 <Badge text="未实现" type="danger" />

该接口用于获取视频。

## 获取缩略图 <Badge text="未实现" type="danger" />

该接口用于获取缩略图。
