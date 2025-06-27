# ShortX Repo

这是ShortX发现页面的在线指令数据仓库，指令更新时，通过Github Action自动创建PR更新Index文件。

[![Update index](https://github.com/cmyyx/ShortX-Files/actions/workflows/update_index.yml/badge.svg)](https://github.com/cmyyx/ShortX-Files/actions/workflows/update_index.yml)


## 如何贡献

1. 通过ShortX app分享功能，保存为文件
2. 按需修改文件中版本号`versionCode`字段
3. 检查文件中`id`字段是否和上个版本一致（此步骤仅在更新指令时需要）
4. 将指令文件放到指定目录下，注意，不需要手动修改index文件
5. 往主分支提交PR

> PR合并之后，Index文件会通过Github action自动更新，因此可能需要一段时间才能在App上看到最新数据。

## 文件目录

`index.json`

这是指令的索引文件，记录了所有一键指令和自动指令的基础信息以及其url

`da`

这是放一键指令的目录，每个指令对应一个文件，可以通过App分享功能直接生成文件。

`rules`

这是放自动指令的目录，每个指令对应一个文件，可以通过App分享功能直接生成文件。


## 版本控制

`versionCode`属性表示版本号，`id`用于不用的指令；以一条一键指令为例，

```json
{
  "actions": [],
  "id": "DA9122b14f-a902-48f5-8dcb-f2b98881519d",
  "lastUpdateTime": "1689414154622",
  "createTime": "1688871810016",
  "title": "IP查询",
  "versionCode": 1,
  "description": "查询归属地并用弹幕通知",
  "author": {
    "name": "Genicur"
  }
}
```

上面例子里的`id`，建议使用UUID，同一条指令请用同一个`id`，更新指令时，需要增加版本号`versionCode`;
因此，如果你要上传一个指令到仓库，通过ShortX的分享功能导出指令后，需要手动修改一下版本号，以及确认下id是否一致。


## 指令要求

1. 禁止涉及用户数据安全隐私
2. 禁止动态加载可执行逻辑

## 指令建议

1. 标题和描述都写清楚
2. 给一些动作添加备注


## Fork 本仓库并开启自动更新

如果你想拥有自己独立的在线指令仓库，可以直接 Fork 本仓库。

得益于最新的 Github Action 配置，你无需进行任何额外设置。Fork 之后，仓库内的 Action 已经拥有足够的权限来自动处理更新。
(***记得手动开启仓库的 Action,fork仓库默认关闭***)

**工作流程如下：**

1.  将你制作或修改的指令文件推送到 Fork 后的仓库的 `main` 分支。
2.  Github Action 将会自动被触发。
3.  Action 会根据你的文件变更，创建一个用于更新 `index.json` 的 Pull Request。
4.  该 Pull Request 会被**自动合并**。

整个过程全自动，无需手动创建 Personal Access Token (PAT) 或进行其他设置。

**也许你还需要更新一下README中的两个链接(修改用户名为你的即可)**