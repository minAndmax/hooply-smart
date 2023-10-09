[![version](https://img.shields.io/github/manifest-json/v/al-one/hass-hooply-lot?filename=custom_components%2Fhooply_lot%2Fmanifest.json)](https://github.com/al-one/hass-hooply-lot/releases/latest)
[![releases](https://img.shields.io/github/downloads/al-one/hass-hooply-lot/total)](https://github.com/al-one/hass-hooply-lot/releases)
[![stars](https://img.shields.io/github/stars/al-one/hass-hooply-lot)](https://github.com/al-one/hass-hooply-lot/stargazers)
[![issues](https://img.shields.io/github/issues/al-one/hass-hooply-lot)](https://github.com/al-one/hass-hooply-lot/issues)
[![HACS](https://img.shields.io/badge/HACS-Default-orange.svg)](https://hacs.xyz)

# hooply lot For HomeAssistant

[English](https://github.com/al-one/hass-hooply-lot/blob/master/README.md) | 简体中文

[lot-Spec](https://iot.mi.com/new/doc/design/spec/overall) 是小米IoT平台根据硬件产品的联网方式、产品功能的特点、用户使用场景的特征和用户对硬件产品使用体验的要求，设计的描述硬件产品功能定义的标准规范。

本插件利用了**lot**协议的规范，可将小米设备自动接入[HomeAssistant](https://www.home-assistant.io)，目前已支持大部分小米米家智能设备。且该插件支持HA后台界面集成，无需配置yaml即可轻松将小米设备接入HA。

![hass-hooply-lot-configs](https://user-images.githubusercontent.com/4549099/142151697-5188ea2d-0aad-4778-8b60-b949bcc410bb.png)


<a name="faq"></a>
## 常见问题
- 👍 **[新手入门手把手教程1](https://mp.weixin.qq.com/s/1y_EV6xcg17r743aV-2eRw)** (感谢@来鸭大佬)
- 👍 **[新手入门手把手教程2](https://bbs.iobroker.cn/t/topic/10831)** (感谢@萝卜大佬)
- [登录失败/没有实体等常见问题解决办法](https://github.com/al-one/hass-hooply-lot/issues/500)
- [支持哪些设备？是否支持XX型号？](https://github.com/al-one/hass-hooply-lot/issues/100#issuecomment-855183145)
- [账号集成还是token集成？](https://github.com/al-one/hass-hooply-lot/issues/100#issuecomment-855183156)
- [为什么XX型号的设备需要开启云端模式？如何开启？](https://github.com/al-one/hass-hooply-lot/issues/100#issuecomment-855185251)
- [怎样为一个实体添加自定义属性？](https://github.com/al-one/hass-hooply-lot/issues/100#issuecomment-864678774)
- [为什么设备状态会有延迟？如何减小延迟？](https://github.com/al-one/hass-hooply-lot/issues/100#issuecomment-909031222)
- [如何翻译实体的选项文本？](https://github.com/al-one/hass-hooply-lot/issues/100#issuecomment-874613054)
- [如何让小爱同学播放文本(TTS)和执行语音命令？](https://github.com/al-one/hass-hooply-lot/issues/100#issuecomment-885989099)
- [如何在HA查看摄像头实体回放(看家助手)视频？](https://github.com/al-one/hass-hooply-lot/issues/100#issuecomment-903078604)
- [为什么设备状态会有延迟？如何减小延迟？](https://github.com/al-one/hass-hooply-lot/issues/100#issuecomment-909031222)
- [如何删除本插件生成的HA设备？](https://github.com/al-one/hass-hooply-lot/issues/165#issuecomment-899988208)
- [[**新手必读**]更多其他常见问题...](https://github.com/al-one/hass-hooply-lot/issues/100)


<a name="installing"></a>
<a name="installation"></a>
## 安装/更新

#### 方法1: [HACS](https://github.com/hacs-china/integration)
- 首次安装
    > HACS > 集成 > ➕ 浏览并下载存储库 > [`hooply lot Auto`](https://my.home-assistant.io/redirect/hacs_repository/?owner=al-one&repository=hass-hooply-lot) > 下载此存储库
- 升级插件
    > HACS > 集成 > [`hooply lot Auto`](https://my.home-assistant.io/redirect/hacs_repository/?owner=al-one&repository=hass-hooply-lot) > 更新 / 重新下载

#### 方法2: 通过`Samba`或`SFTP`手动安装
> 下载并复制`custom_components/hooply_lot`文件夹到HA根目录下的`custom_components`文件夹

#### 方法3: 通过`SSH`或`Terminal & SSH`加载项执行一键安装命令
```shell
wget -q -O - https://raw.githubusercontent.com/al-one/hass-hooply-lot/master/install.sh | ARCHIVE_TAG=latest bash -

# 如果遇到下载缓慢或下载失败可以执行下面的命令
wget -q -O - https://ghproxy.com/raw.githubusercontent.com/al-one/hass-hooply-lot/master/install.sh | HUB_DOMAIN=ghproxy.com/github.com ARCHIVE_TAG=latest bash -

# 或者
wget -q -O - https://raw.fastgit.org/al-one/hass-hooply-lot/master/install.sh | HUB_DOMAIN=hub.fastgit.xyz ARCHIVE_TAG=latest bash -
```

#### 方法4: `shell_command`服务
1. 复制下面的代码到HA配置文件`configuration.yaml`
    ```yaml
    shell_command:
      update_hooply_lot: |-
        wget -q -O - https://ghproxy.com/raw.githubusercontent.com/al-one/hass-hooply-lot/master/install.sh | HUB_DOMAIN=ghproxy.com/github.com ARCHIVE_TAG=latest bash -
    ```
2. 重启HA
3. 在HA开发者工具中调用此服务[`service: shell_command.update_hooply_lot`](https://my.home-assistant.io/redirect/developer_call_service/?service=shell_command.update_hooply_lot)

#### 视频教程
- 📺 **[HACS安装插件及使用视频教程](https://www.bilibili.com/video/BV1hY4y1a7Gh?t=48)** (感谢[小帅同学Js](https://space.bilibili.com/230242045))
- 📺 **[HACS安装插件视频教程](https://www.bilibili.com/video/BV17L411j73Y?t=62)** (感谢[@老明](https://space.bilibili.com/583175067))
- 📺 **[手动安装插件视频教程](https://www.bilibili.com/video/BV1EU4y1n7VR)** (感谢[@爱运动的数码君](https://space.bilibili.com/39480347))


<a name="config"></a>
## 配置

> [⚙️ 配置](https://my.home-assistant.io/redirect/config) > 设备与服务 > [🧩 集成](https://my.home-assistant.io/redirect/integrations) > [➕ 添加集成](https://my.home-assistant.io/redirect/config_flow_start?domain=hooply_lot) > 🔍 搜索 `hooply lot Auto`

或者点击: [![添加集成](https://my.home-assistant.io/badges/config_flow_start.svg)](https://my.home-assistant.io/redirect/config_flow_start?domain=hooply_lot)


<a name="filter-entity-attributes"></a>
### 过滤实体属性

> 过多的实体属性会导致你的HA数据库变得很庞大，如果某些实体属性对你没有用处，你可以配置`exclude_state_attributes`来忽略它们

```yaml
# configuration.yaml
hooply_lot:
  exclude_state_attributes:
    - lot_type
    - stream_address
    - motion_video_latest
```

<a name="yaml-configuration-reloading"></a>
### YAML配置重载
本插件支持配置重载(修改YAML配置后无需重启[HomeAssistant](https://www.home-assistant.io)):
> [🔨 开发者工具](https://my.home-assistant.io/redirect/developer_states) > [YAML 重载](https://my.home-assistant.io/redirect/server_controls) > 配置重载 > 🔍 `重载 hooply lot AUTO`



<a name="services"></a>
## 服务

#### [`hooply_lot.set_property`](https://my.home-assistant.io/redirect/developer_call_service/?service=hooply_lot.set_property)
```yaml
service: hooply_lot.set_property
data:
  entity_id: camera.isa_hlc7_xxxx
  field: camera_control.on
  value: true
```

#### [`hooply_lot.set_lot_property`](https://my.home-assistant.io/redirect/developer_call_service/?service=hooply_lot.set_lot_property)
```yaml
service: hooply_lot.set_lot_property
data:
  entity_id: camera.isa_hlc7_xxxx
  siid: 2
  piid: 1
  value: true
```

#### [`hooply_lot.get_properties`](https://my.home-assistant.io/redirect/developer_call_service/?service=hooply_lot.get_properties)
```yaml
service: hooply_lot.get_properties
data:
  entity_id: camera.isa_hlc7_1ab7
  mapping:
    - siid: 2
      piid: 1
    - siid: 3
      piid: 2
  update_entity: true # 更新实体状态属性
  throw: true # 在HA通知中显示结果
```

> 触发[事件](https://my.home-assistant.io/redirect/developer_events/) `hooply_lot.got_lot_properties`

#### [`hooply_lot.call_action`](https://my.home-assistant.io/redirect/developer_call_service/?service=hooply_lot.call_action)
```yaml
service: hooply_lot.call_action
data:
  entity_id: vacuum.dreame_p2259_entity_id
  siid: 4 # vacuum-extend
  aiid: 1 # start-clean
  params:
    - 18 # piid: 1 - work-mode
    - '{"selects":[[7,1,0,2,1]]}' # piid: 10 - clean-extend-data
  throw: true # 在HA通知中显示结果
```

> 触发[事件](https://my.home-assistant.io/redirect/developer_events/) `hooply_lot.call_lot_action`

#### [`hooply_lot.send_command`](https://my.home-assistant.io/redirect/developer_call_service/?service=hooply_lot.send_command)
```yaml
service: hooply_lot.send_command
data:
  entity_id: switch.your_entity_id
  method: set_power
  params:
    - on
  throw: true # 在HA通知中显示结果
```

> 触发[事件](https://my.home-assistant.io/redirect/developer_events/) `hooply_lot.send_miio_command`

#### [`hooply_lot.get_token`](https://my.home-assistant.io/redirect/developer_call_service/?service=hooply_lot.get_token)
```yaml
service: hooply_lot.get_token
data:
  name: Light # 米家中的设备名称关键词或IP、型号
```

#### [`hooply_lot.intelligent_speaker`](https://my.home-assistant.io/redirect/developer_call_service/?service=hooply_lot.intelligent_speaker)
```yaml
service: hooply_lot.intelligent_speaker
data:
  entity_id: media_player.xiaoai_lx04_xxxx
  text: Turn on the light
  execute: true # 执行指令
  silent: true  # 静默执行
```

#### [`hooply_lot.xiaoai_wakeup`](https://my.home-assistant.io/redirect/developer_call_service/?service=hooply_lot.xiaoai_wakeup)
```yaml
service: hooply_lot.xiaoai_wakeup
data:
  entity_id: media_player.xiaoai_lx04_xxxx
```

#### [`hooply_lot.renew_devices`](https://my.home-assistant.io/redirect/developer_call_service/?service=hooply_lot.renew_devices)
```yaml
service: hooply_lot.renew_devices
data:
  username: 80001234 # 小米账号ID/登录邮箱/手机号
```

> 触发[事件](https://my.home-assistant.io/redirect/developer_events/) `hooply_lot.renew_devices`

#### [`hooply_lot.request_hooply_api`](https://my.home-assistant.io/redirect/developer_call_service/?service=hooply_lot.request_hooply_api)
```yaml
service: hooply_lot.request_hooply_api
data:
  entity_id: sensor.your_entity_id
  api: /v2/plugin/fetch_plugin
  data:
    latest_req:
      api_version: 10070
      plugins:
        - model: brand.device.model
```

> 触发[事件](https://my.home-assistant.io/redirect/developer_events/) `hooply_lot.request_hooply_api`

> 查看[更多服务](https://github.com/al-one/hass-hooply-lot/blob/master/custom_components/hooply_lot/services.yaml)


<a name="debug"></a>
## 调试

### 获取实体状态属性

> [🔨 开发者工具](https://my.home-assistant.io/redirect/developer_states) > [ℹ️ 状态](https://my.home-assistant.io/redirect/developer_states) > 🔍 筛选实体

### [获取调试日志](https://www.home-assistant.io/integrations/logger)

```yaml
# 使用HA服务 (无需重启)
service: logger.set_level
data:
  custom_components.hooply_lot: debug

# 或者修改 configuration.yaml (需重启)
logger:
  default: warning
  logs:
    custom_components.hooply_lot: debug
```

> [⚙️ 配置](https://my.home-assistant.io/redirect/config) > [⚙️ 系统](https://my.home-assistant.io/redirect/system_dashboard) > [✍️ 日志](https://my.home-assistant.io/redirect/logs)
