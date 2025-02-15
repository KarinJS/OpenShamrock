---
title: 文件相关
icon: file
---

::: warning 注意
对于 Shamrock 尚未实现的 API，会在标题添加标记 <Badge text="未实现" type="danger" vertical="baseline" />
:::

## 上传私聊文件

该接口用于上传私聊文件。

::: warning 注意
只能上传本地文件, 需要上传 `http` 文件的话请先下载至本地
:::

### API 端点

`/upload_private_file`

### 参数

| 字段    | 类型   | 说明         |
| ------- | ------ | ------------ |
| user_id | int64  | 目标         |
| file    | string | `本地文件路径` 或 `文件base64` 或 `文件url` |
| name    | string | 文件名称     |

::: warning 注意
本地文件路径为绝对路径，文件base64为`base64://`开头，文件url则应该是正确的http请求地址。
:::

### 响应

::: tabs

@tab 响应字段

| 字段    | 类型   | 说明     |
| ------- | ------ | -------- |
| msg_id  | int32  | 消息id   |
| bizid   | int32  |          |
| md5     | string | MD5      |
| file_id | string | 文件uuid |

@tab 响应示例

```json
{
  "status": "ok",
  "retcode": 0,
  "data": {
    "msg_id": 286479341,
    "bizid": 102,
    "md5": "6742327a8b0147eebd6e1d4018626082",
    "sha": "",
    "sha3": "",
    "file_id": "/c65b7c5c-50e0-47c6-951f-4e3377505f7f"
  },
  "echo": ""
}
```

:::

## 上传群文件

该接口用于上传群文件。

::: warning 注意
只能上传本地文件, 需要上传 `http` 文件的话请先下载至本地
:::

### API 端点

`/upload_group_file`

### 参数

| 字段     | 类型   | 说明         |
| -------- | ------ | ------------ |
| group_id | int64  | 群号         |
| file    | string | `本地文件路径` 或 `文件base64` 或 `文件url` |
| name    | string | 文件名称     |

::: warning 注意
本地文件路径为绝对路径，文件base64为`base64://`开头，文件url则应该是正确的http请求地址。
:::

### 响应

::: tabs

@tab 响应字段

| 字段    | 类型   | 说明     |
| ------- | ------ | -------- |
| msg_id  | int32  | 消息id   |
| bizid   | int32  |          |
| md5     | string | MD5      |
| file_id | string | 文件uuid |

@tab 响应示例

```json
{
  "status": "ok",
  "retcode": 0,
  "data": {
    "msg_id": 286479341,
    "bizid": 102,
    "md5": "6742327a8b0147eebd6e1d4018626082",
    "sha": "",
    "sha3": "",
    "file_id": "/c65b7c5c-50e0-47c6-951f-4e3377505f7f"
  },
  "echo": ""
}
```

:::

::: warning 注意
参数 `folder`在Shamrock不受支持。
:::

## 删除群文件

该接口用于删除群文件。

### API 端点

`/delete_group_file`

### 参数

| 字段     | 类型   | 说明                             |
| -------- | ------ | -------------------------------- |
| group_id | int64  | 群号                             |
| file_id  | string | 文件ID 参考 [File](#file) 对象   |
| busid    | int32  | 文件类型 参考 [File](#file) 对象 |

::: tip 提示
该 API 无响应数据
:::

## 创建群文件文件夹

该接口用于创建群文件文件夹。

::: warning 注意
仅能在根目录创建文件夹
:::

### API 端点

`/create_group_file_folder`

### 参数

| 字段     | 类型   | 说明         |
| -------- | ------ | ------------ |
| group_id | int64  | 群号         |
| name     | string | 群文件夹名字 |

### 响应示例

```json
{
  "status": "ok",
  "retcode": 0,
  "data": {
    "folder_id": "/ad86c100-031d-4139-8cab-c6c661a413ba",
    "parent_folder_id": "/",
    "folder_name": "测试",
    "create_time": 1706269735,
    "modify_time": 1706269735,
    "creator_uin": 1650114384,
    "modifier_uin": 1650114384
  },
  "message": "成功",
  "echo": 111
}
```

## 重命名群文件夹

把已经存在的群文件夹改个名字。

### API 端点

`/rename_group_folder`

| 字段      | 类型   | 说明         |
| --------- | ------ | ------------ |
| group_id  | int64  | 群号         |
| folder_id | string | 群文件夹ID   |
| name      | string | 群文件夹名字 |

### 响应解释

可通过返回的状态码判断重命名是否成功。

## 删除群文件文件夹

该接口用于删除群文件文件夹。

### API 端点

`/delete_group_folder`

### 参数

| 字段      | 类型   | 说明                                 |
| --------- | ------ | ------------------------------------ |
| group_id  | int64  | 群号                                 |
| folder_id | string | 文件夹ID 参考 [Folder](#folder) 对象 |

### 响应解释

可通过返回的状态码判断删除是否成功。

## 获取群文件系统信息

该接口用于获取群文件系统信息。

### API 端点

`/get_group_file_system_info`

### 参数

| 字段     | 类型  | 说明 |
| -------- | ----- | ---- |
| group_id | int64 | 群号 |

### 响应

| 字段        | 类型  | 说明       |
| ----------- | ----- | ---------- |
| file_count  | int32 | 文件总数   |
| limit_count | int32 | 文件上限   |
| used_space  | int64 | 已使用空间 |
| total_space | int64 | 空间上限   |

## 获取群根目录文件列表

该接口用于获取群根目录文件列表。

### API 端点

`/get_group_root_files`

### 参数

| 字段     | 类型  | 说明 |
| -------- | ----- | ---- |
| group_id | int64 | 群号 |

### 响应

| 字段    | 类型                    | 说明       |
| ------- | ----------------------- | ---------- |
| files   | List<[File](#file)>     | 文件列表   |
| folders | List<[Folder](#folder)> | 文件夹列表 |

#### File

| 字段           | 类型   | 说明                    |
| -------------- | ------ | ----------------------- |
| group_id       | int32  | 群号                    |
| file_id        | string | 文件ID                  |
| file_name      | string | 文件名                  |
| busid          | int32  | 文件类型                |
| file_size      | int64  | 文件大小                |
| upload_time    | int64  | 上传时间                |
| dead_time      | int64  | 过期时间，永久文件恒为0 |
| modify_time    | int64  | 最后修改时间            |
| download_times | int32  | 下载次数                |
| uploader       | int64  | 上传者ID                |
| uploader_name  | string | 上传者名字              |
| md5            | string | md5                     |
| sha            | string | sha                     |
| sha3           | string | sha3 可能获取不到       |

#### Folder

| 字段             | 类型   | 说明       |
| ---------------- | ------ | ---------- |
| group_id         | int32  | 群号       |
| folder_id        | string | 文件夹ID   |
| folder_name      | string | 文件名     |
| create_time      | int64  | 创建时间   |
| creator          | int64  | 创建者     |
| creator_name     | string | 创建者名字 |
| total_file_count | int32  | 子文件数量 |

## 获取群子目录文件列表

该接口用于获取群子目录文件列表。

### API 端点

`/get_group_files_by_folder`

### 参数

| 字段      | 类型   | 说明                                 |
| --------- | ------ | ------------------------------------ |
| group_id  | int64  | 群号                                 |
| folder_id | string | 文件夹ID 参考 [Folder](#folder) 对象 |

### 响应

| 字段    | 类型     | 说明       |
| ------- | -------- | ---------- |
| files   | File[]   | 文件列表   |
| folders | Folder[] | 文件夹列表 |

## 获取群文件资源链接

该接口用于获取群文件资源链接。

### API 端点

`/get_group_file_url`

### 参数

| 字段     | 类型   | 说明                             |
| -------- | ------ | -------------------------------- |
| group_id | int64  | 群号                             |
| file_id  | string | 文件ID 参考 [File](#file) 对象   |
| busid    | int32  | 文件类型 参考 [File](#file) 对象 |

### 响应

| 字段 | 类型   | 说明         |
| ---- | ------ | ------------ |
| url  | string | 文件下载链接 |
