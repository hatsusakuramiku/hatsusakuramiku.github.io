---
title: 【zhenxun_bot】Bot部署教程
cover: 'https://cdn.hatsusakuramiku.cn/hexo/img/gallery/post/81677882.webp'
top_img: 'https://cdn.hatsusakuramiku.cn/hexo/img/gallery/post/81677882.webp'
tag:
  - 学习
category: zhenxun_bot
swiper_index: 1
description: 在windows 与 云服务器等平台部署 zhenxun_bot 的简单教程
abbrlink: 61cbfabc
comments: false
---
>**zhenxun_bot相关导航**
>
>1. [【zhenxun_bot】可爱的绪山真寻Bot部署教程](/posts/61cbfabc.html)⇦当前位置🪂

{% note info flat %}封面图片PID:[81677882](https://www.pixiv.net/artworks/81677882){% endnote %}

{% note warning flat %}阅前须知：本教程与此项目仅用于学习交流，不存在任何盈利目的，请勿用于非法或盈利用途！！！{% endnote %}
![小真寻](https://cdn.hatsusakuramiku.cn/hexo/img/gallery/post/zhenxun.png "xiaozhenxun")

目前已实现的功能
![功能介绍](https://cdn.hatsusakuramiku.cn/hexo/img/post/zhenxun/opionts.png "opionts")
关于[小真寻](https://zh.moegirl.org.cn/%E7%BB%AA%E5%B1%B1%E7%9C%9F%E5%AF%BB)（[绪山真寻](https://zh.moegirl.org.cn/%E7%BB%AA%E5%B1%B1%E7%9C%9F%E5%AF%BB)）
更多更详细的介绍请移步:[[使用文档]](https://hibikier.github.io/zhenxun_bot/about)|[[项目地址]](https://github.com/HibiKier/zhenxun_bot)

## 注意事项

1. 保证系统的相同，环境的相同，是尽量减少麻烦的最有效的途径
2. 遇到麻烦先不要慌，先看看你是不是漏看了亿步
3. 实在解决不了，带上你的完整的报错，和自己所做过的行为去群里问问。QQ群：「[是真寻酱哒](https://jq.qq.com/?_wv=1027&k=u8PgBkMZ)」或「[真寻酱的技术群](https://qm.qq.com/q/YYYt5rkMYc)」

## 必要的准备

1. 一定的基础，包括但不限于稍微熟悉linux或windows cmd命令行
2. 一台还凑合的{% span red, 电脑或云服务器 %}，推荐部署系统: [Ubuntu20.04 LTS](https://cn.ubuntu.com/blog/ubuntu-20-04-lts-arrives-cn)
3. 一个可以用的脑子
4. 善于百度谷歌的双手

## 简要说明

>真寻Bot基于 `Nonebot2` 开发，以`tortoise-orm`作为`ORM`，支持`Postgresql`、`MySQL`、`SQLite`等数据库，使用以`OneBot`协议为准的框架的由[HibiKier](https://github.com/HibiKier)开发的非常可爱的绪山真寻Bot。
>推荐的部署系统为`Linux`，可以使用 `Ubuntu` 等，`Windows`也可以获得很好的支持。本文就分别以 `Ubuntu 20.04 LTS` 和 `Windows 10 x64` 作为部署系统，简要介绍部署教程。

## `Windows` 部署教程

{% note info flat %}
下文中提到的命令个人推荐使用`Windows Terminal` 或者`PowerShell`运行，当然你也可以使用`cmd`。
{% endnote %}

### 1 必要工具/环境安装

#### 1.1 `git` 和 `python`

>由于`zhenxun_bot`的源码存储在`GitHub`上，后续安装bot本体时需要从`GitHub`上拉取源码，因此需要安装`git`。此外`zhenxun_bot`的运行也依赖`python`，因此也需要安装`python`。

| 工具/环境  | 版本要求                                                                    | 官方下载地址                                                                       | 快速下载地址                                                                                                                    |
|--------|-------------------------------------------------------------------------|------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------|
| git    | 最新稳定版即可                                                                 | [git - Git for Windows (git-scm.com)](https://git-scm.com/downloads/win)     | [Git-2.47.0-64-bit.exe](https://github.com/git-for-windows/git/releases/download/v2.47.0.windows.1/Git-2.47.0-64-bit.exe) |
| python | `3.9.x`及以上，建议`3.10.x`或`3.11.x`，若使用`3.9.x`需要将`pyproject.toml`中的版本改为`3.9` | [python - Official Download Page](https://www.python.org/downloads/windows/) | [python-3.11.6-amd64.exe](https://www.python.org/ftp/python/3.11.6/python-3.11.6-amd64.exe)                               |

#### 1.2 数据库

>`zhenxun_bot`原先仅支持`PostgreSQL`，近期重构后支持的数据库包括`PostgreSQL`、`MySQL`、`SQLite`，用户可依需选择数据库。

{% tabs, -1 %}
<!-- tab SQLite-->
`zhenxun_bot`已内置`SQLite`数据库，开箱即用。若使用`SQLite`数据库，可直接跳过此步骤。
<!-- endtab-->

<!-- tab PostgreSQL-->
| 数据库        | 版本要求      | 官方下载地址                                                                                                | 快速下载地址                                                                                              |
|------------|-----------|-------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
| PostgreSQL | 大于`9.x`即可 | [PostgreSQL: Download the official PostgreSQL database](https://www.postgresql.org/download/windows/) | [PostgreSQL 15.1 64-bit](https://get.enterprisedb.com/postgresql/postgresql-15.1-1-windows-x64.exe) |

**1 安装**:

1. 双击安装程序，点击`Next`
![install_1](https://cdn.hatsusakuramiku.cn/hexo/img/zhenxun_bot/install_1-1f165d5abfd31080a8f2e3a922ca0a6d.png)
2. 选择安装路径（没有特殊情况一般默认即可），继续`Next`
{% note warning flat %}
安装路径请不要出现中文！
{% endnote %}
![install_2](https://cdn.hatsusakuramiku.cn/hexo/img/zhenxun_bot/install_2-8040d2de330e79007f3b6405de9f509b.png)
3. 去掉`Stack Builder`即可，不影响使用，`Next`
![install_3](https://cdn.hatsusakuramiku.cn/hexo/img/zhenxun_bot/install_3-b6df95bf1241b5d7bfe0486542f3d642.png)
4. 数据存储路径（没有特殊情况一般默认即可），`Next`
![install_4](https://cdn.hatsusakuramiku.cn/hexo/img/zhenxun_bot/install_4-42b3b83409ee53accc7d2390978e7d48.png)
5. 设置postgres用户的密码，例如: `zhenxun`
![install_5](https://cdn.hatsusakuramiku.cn/hexo/img/zhenxun_bot/install_5-7cce2171b0bdbb91556ec9b19a6f2fdb.png)
6. 默认端口，`Next`
![install_6](https://cdn.hatsusakuramiku.cn/hexo/img/zhenxun_bot/install_6-ac64f448a7a2f0100248ae4af0833327.png)
7. 接下来一路`Next`直到进入安装进度条
![install_7](https://cdn.hatsusakuramiku.cn/hexo/img/zhenxun_bot/install_7-53fb02ef47d6f1d40d0faf9c2d44fbb9.png)
8. ✨✨ 安装完成 ✨✨
![install_8](https://cdn.hatsusakuramiku.cn/hexo/img/zhenxun_bot/install_8-a2209de26879f552269e3ea2b3f9ad61.png)

**2 配置连接**:

1. 找到安装的pgAdmin，直接启动！
![create_1](https://cdn.hatsusakuramiku.cn/hexo/img/zhenxun_bot/install_9.png)
{% note info flat %}
是英文界面？别急，已[百度](https://www.baidu.com/baidu?tn=monline_3_dg&ie=utf-8&wd=pgadmin4%E8%AE%BE%E7%BD%AE%E4%B8%AD%E6%96%87)
{% endnote %}
2. 新建连接
左侧栏右键点击`Servers`后选择`Register`，再点击`服务器`
![create_2](https://cdn.hatsusakuramiku.cn/hexo/img/zhenxun_bot/setup_2-a909dfe1b4e8835efc1a19d02564d2b6.png)
3. 为服务器{% del 随便 %}起一个响亮的名字
![create_3](https://cdn.hatsusakuramiku.cn/hexo/img/zhenxun_bot/setup_3-115b55bee755cbad13796f21017d0714.png)
4. 填写配置
填写`主机名称/地址`，如果是连接远程服务器的话对应的服务器IP，本地的话可以直接填写`127.0.0.1`
`端口`就是安装时配置的端口，没有修改的话默认`5432`
`密码`就是安装时配置的密码
![create_4](https://cdn.hatsusakuramiku.cn/hexo/img/zhenxun_bot/setup_4-de9d15356c324a5810c2d6bf124e30fc.png)
5. ✨✨ 点击保存 ✨✨
左侧栏会出现一头🐘
![create_5](https://cdn.hatsusakuramiku.cn/hexo/img/zhenxun_bot/download.png)

**3 创建数据库**:

1. 展开🐘🐘
右击`数据库`，选择`创建`后点击`数据库`
![create_6](https://cdn.hatsusakuramiku.cn/hexo/img/zhenxun_bot/create_1-0a53a879241a5a4c1b0d035107a1c054.png)
2. ✨✨ 直接创建！ ✨✨
设置数据库名称后点击`保存`
![create_7](https://cdn.hatsusakuramiku.cn/hexo/img/zhenxun_bot/create_2-7bd737416af883beab28fbdd0f7a52b7.png)
<!-- endtab-->

<!-- tab MySQL-->
| 数据库   | 版本要求    | 官方下载地址                                                                            | 快速下载地址                                                                                          |
|-------|---------|-----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------|
| MySQL | 较新稳定版即可 | [MySQL : Download MySQL Community Server](https://dev.mysql.com/downloads/mysql/) | [MySQL LTS 8.4.2-winx64.msi](https://cdn.mysql.com//Downloads/MySQL-8.4/mysql-8.4.2-winx64.msi) |

{% psw 好麻烦懒得写 %}请自行寻找安装教程，建议使用`SQLite`与`PostgreSQL`数据库。

<!-- endtab-->
{% endtabs %}

#### 1.3 无头QQ安装

>无头QQ作为前端用于真寻Bot与QQ服务器之间的通信。无头QQ负责接收QQ消息并转发给真寻Bot，真寻Bot处理消息后返回给无头QQ，无头QQ再将消息发送给QQ用户。之前，旧版真寻Bot的默认前端是[go-cqhttp](https://github.com/Mrs4s/go-cqhttp)，但`go-cqhttp`的风险性实在较高，已基本宣告死亡，因此推荐使用[NapCat](https://github.com/NapNeko/NapCatQQ), [LLOneBot](https://github.com/LLOneBot/LLOneBot), [Lagrange.Core](https://github.com/LagrangeDev/Lagrange.Core)等。这些前端均支持`HTTP`、`WebSocket`、`TCP`等多种协议，并且均支持`OneBot`协议，因此可以无缝对接真寻Bot。

{% tabs, -1 %}
<!-- tab NapCat-->
|项目地址|平台|核心作者|文档|备注|
|----|----|----|----|----|
|[NapCat](https://github.com/NapNeko/NapCatQQ)|NTQQ|[NapNeko](https://github.com/NapNeko)|[文档](https://napneko.github.io/)|部署简单，可以不使用{% span red, GUI %}，方便内存较小不支持图形界面的服务器部署；可以与手机同时在线；无法使用{% span red, 戳一戳 %}功能|

{% note info flat %}
请移步[官方文档](https://napneko.github.io/)。
{% endnote %}
<!-- endtab-->

<!-- tab LLOneBot-->
|项目地址|平台|核心作者|文档|备注|
|----|----|----|----|----|
|[LLOneBot](https://github.com/LLOneBot/LLOneBot)|NTQQ|[linyuchen](https://github.com/linyuchen)|[文档](https://llob.napneko.com/zh-CN/)|部署简单，需要使用 {% span red, GUI %}；可以与手机同时在线；可以使用{% span red, 戳一戳 %}功能|

{% note info flat %}
请移步[官方文档](https://llob.napneko.com/zh-CN/)。
{% endnote %}
<!-- endtab-->

<!-- tab Lagrange.Core-->
|项目地址|平台|核心作者|文档|备注|
|----|----|----|----|----|
|[Lagrange.Core](https://github.com/LagrangeDev/Lagrange.Core)||LagrangeDev/Linwenxuan04|[文档](https://github.com/LagrangeDev/Lagrange.Core/blob/master/README_zh.md)||

{% note warning info %}
未使用过此前端，请自行查阅[官方文档](https://github.com/LagrangeDev/Lagrange.Core/blob/master/README_zh.md)。
{% endnote %}
<!-- endtab-->
{% endtabs %}

### 2 安装真寻Bot

#### 2.1 下载Bot文件并安装依赖

>1.使用 `git` 拉取真寻源码

  ```bash
  git clone https://github.com/HibiKier/zhenxun_bot.git # 拉取源码 
  # 国内下载速度较慢也可使用
  # git clone https://ghproxy.com/github.com/HibiKier/zhenxun_bot.git
  ```

>2.安装依赖
>真寻使用`poetry`管理依赖，在安装依赖之前，需要先安装 `poetry`。当出现异常情况导致环境配置出错时，只需删除对应的`poetry包`重新安装即可，不需要回滚系统。

  ```bash
  cd zhenxun_bot # 进入项目目录
  pip install -y poetry # 如果没有安装poetry，请先安装
  poetry install # 安装依赖
  ```

#### 2.2 修改相关配置

>1.设置超级用户，打开`~/zhenxun_bot/.env.dev`，在 **`SUPERUSERS`** 和 **`qq`** 中添加你的 `QQ`号。

```config
SUPERUSERS=["123456789"] # 将 123456789 替换为你的 QQ 号

PLATFORM_SUPERUSERS = '
  {
    "qq": ["123456789"], # 将 123456789 替换为你的 QQ 号
    "dodo": [],
    "kaiheila": [],
    "discord": []
  }
'
```

>2.设置数据库连接，打开`~/zhenxun_bot/.env.dev`，在 **`DB_URL`** 中添加你的数据库连接地址。

{% tabs, -1 %}
<!-- tab PostgreSQL-->
建议的数据库，嫌麻烦请使用 `SQLite`。

```config
# 示例: "postgres://user:password@127.0.0.1:5432/database"

DB_URL = "postgres://用户名:密码@127.0.0.1:端口/数据库名称"

# 如果你是与教程一模一样的命令代码，可以直接复制以下URL

DB_URL = "postgres://postgres:zhenxun_bot@127.0.0.1:5432/zhenxun_bot"
```
<!-- endtab-->

<!-- tab SQLite-->
Sqlite可以放置在任何位置，`sqlite:`之后为存放路径，但建议在`data`文件夹下新建`db`文件夹后使用。

```config
# 示例: "sqlite:data/db/zhenxun.db"

DB_URL = "sqlite:data/db/zhenxun.db"
<!-- endtab-->

<!-- tab MySQL-->
# 示例: "mysql://user:password@127.0.0.1:3306/database"

DB_URL = "mysql://用户名:密码@127.0.0.1:端口/数据库名称"
```
<!-- endtab-->

<!-- tab MySQL-->
与`Postgresql`相同。

```config
# 示例: "mysql://user:password@127.0.0.1:3306/database"

DB_URL = "mysql://用户名:密码@127.0.0.1:端口/数据库名称"
```
<!-- endtab-->
{% endtabs %}

{% note info flat %}
文件保存在 `~/zhenxun_bot/data/config.yaml`，所有真寻相关插件都在使用该配置文件，按需修改
{% endnote %}

#### 2.3 启动真寻Bot

> 真寻必须在`poetry`环境下运行，启动Bot前请先进入`poetry`环境。

```bash
# cd zhenxun_bot # 进入项目目录
poetry shell # 进入poetry环境
python bot.py # 启动Bot
# python3 bot.py # 可以使用python3启动
```

>当你的控制台出现以下日志，说明你已经成功了🎉🎉

```bash
08-14 23:18:44 [INFO] zhenxun | CMD[Web UI] API启动成功
08-14 23:18:44 [INFO] uvicorn | Application startup complete.
08-14 23:18:44 [INFO] uvicorn | Uvicorn running on http://127.0.0.1:8080 (Press CTRL+C to quit)
```

{% note warning flat %}
启动成功后，请勿关闭终端窗口，否则Bot会停止运行。
{% endnote %}

### 3 插件安装

>当前版本真寻本体与插件库分离，你可以在以下获取插件或其他相关，或通过与真寻的对话命令安装插件（插件商店）

|项目名称|主要用途|仓库作者|备注|
|---|---|---|---|
|[插件库](https://github.com/zhenxun-org/zhenxun_bot_plugins)|插件库|[zhenxun-org](https://github.com/zhenxun-org)|原 plugins 文件夹插件|
|[插件索引库](https://github.com/zhenxun-org/zhenxun_bot_plugins_index)|插件|[zhenxun-org](https://github.com/zhenxun-org)|扩展插件索引库|
|[真寻一键安装脚本](https://github.com/soloxiaoye2022/zhenxun_bot-deploy)|一键安装脚本|[soloxiaoye2022](https://github.com/soloxiaoye2022)|第三方|
|[WbeUi](https://github.com/HibiKier/zhenxun_bot_webui)|管理面板|[HibiKier](https://github.com/HibiKier)|基于真寻 WebApi 的 webui 实现|
|[安卓 app(WebUi)](https://github.com/YuS1aN/zhenxun_bot_android_ui)|安卓 app|[YuS1aN](https://github.com/YuS1aN)|第三方|

## `Ubuntu` 部署教程

