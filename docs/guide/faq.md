---
title: 常见问题
icon: question-circle
---

### 支持的QQ版本

- 版本 `8.9.68`，`8.9.70`，`8.9.73`，`8.9.75`，`8.9.78`，`8.9.80`，`8.9.81`，`8.9.83`， `9.0.15`, `9.0.8`
- 理论上支持上述说明未提到的更高版本，如遇问题请提交 `issue`

### 反检测

`Shamrock` 内部已经做了对应处理，无需再进行任何操作。

::: warning 注意
禁止使用隐藏应用列表等其他方法对 `QQ` 隐藏 `Shamrock` ，否则会出现 `框架未激活` 等异常。
:::

### 模拟器部署成功后电脑无法访问？

部分模拟器采用的是 `NAT` 网络，请使用

```shell
adb forward xxx
```

将模拟器内的端口监听转发到电脑，别和我说为什么别人的模拟器可以在外面直接访问，你的不行就不行！

> 执行这个命令前，请注意adb是安卓调试桥工具包内的东西，请确保你的环境中有这个玩意，否则请前往谷歌官网或者刷机论坛之类的地方获取。

### 修改了配置文件，但没有生效？

`Shamrock` 的部分配置需要重新启动 `QQ` （请确保100%杀死QQ），然后在保证 `Shamrock` 存活的情况下启动 `QQ` ， `Shamrock` 的 `WebSocket` 相关的所有配置都需要重新启动生效。

::: warning 注意
如果启用了 实验功能->免死金牌 在更新配置或更新模块后需重启系统，否则更新可能不会生效。
:::

### 某些事件/消息/操作不支持？

提交 `issue` ，我们会实现。

### QQ闪退(每隔一段时间)怎么办？

勾选 `Shamrock` 的自动唤醒，或者使用某些框架自带QQ死亡自动唤醒的XP, MAGISK...插件。你要习以为常这个操作，请安装一些软件进行按时重启或者闪退重启，同时QQ有时也会有概率杀死他自己。

### 真机息屏状态，API会变慢/无响应？

断网式：这个操作源自于 `MIUI` 的 `息屏省电` ，请保证关闭锁屏后断开数据，这个选项，关闭睡眠模式。

缓慢式：使用某些息屏挂机软件，为 `QQ` 附加一个息屏挂机状态。安装息屏挂机软件 `extinguish` ，或者使用 `MIUI游戏助手` `息屏挂机` 。

### 模拟器部署，QQ闪退？

QQ修复了登录响应超时的问题，经测试(逍遥,夜神,MuMu)模拟器可正常使用，去QQ官网下载最新版本即可。

> 其次，模拟器部署请使用Shamrock的ALL版本，不要使用WSA(Windows安卓子系统)部署(有兼容问题)。

### 模拟器部署，外部无法访问接口？

参考 [模拟器部署成功后电脑无法访问？](#模拟器部署成功后电脑无法访问)

### Docker部署支持？

目前依旧在计划中，主要是不太会 `docker` 。

### 一定要保证Shamrock主APP在后台运行吗？

不需要，因为 `OneBot` 服务运行在 `QQ` 主进程中，无需 `Shamrock` 主进程运行(当然第一次使用 `Shamrock` ，请启动 `Shamrock` ，推送配置要求 `Shamrock` 和 `QQ` 都在运行)。

### 云手机支持哪些？

目前允许在中国移动云手机(`Magisk`)和红手指云手机(`Lspatch`)使用 `Shamrock` ，其它平台未测试。

### Shamrock的日志怎么导出？

`Shamrock` 的日志文件，按照时间和进程名称，保存在 `/sdcard/Android/data/com.tencent.mobileqq/Tencent/Shamrock/log` 文件夹内，请查看，提交 `issue` 时可以使用它们，注意请不要提交超过 `50kb` 的日志文件。
