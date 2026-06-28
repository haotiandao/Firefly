---
title: 使用 NodeWarden部署
published: 2026-06-28
pinned: false
description: 博客示例。
tags: [演示]
category: 测试
draft: false
---


[](about:blank#NodeWarden "NodeWarden")NodeWarden
=================================================

想找免费的 Bitwarden 自建方案？这篇文章会手把手教你如何部署使用 NodeWarden，在 Cloudflare Workers 上 **零成本搭建一个属于自己的密码管理器** ，全程无需 VPS 服务器。

相比传统部署方式，这套方案不仅完全免费，还支持官方客户端同步、自动填充、云端备份以及 TOTP 双重验证，几乎可以替代官方付费功能，非常适合个人长期使用。

我们都知道，Bitwarden 是目前最受欢迎的开源密码管理器之一，但过去自建往往需要一台长期运行的 VPS 服务器，既麻烦又有成本。

而现在大佬更进一步用 NodeWarden 直接把 Bitwarden 服务端搬到了 “赛博大善人” Cloudflare 的 Workers 上，让我们可以用 **零服务器成本实现完整功能** 。

部署 NodeWarden 完成后，你就可以在手机、电脑、浏览器插件中无缝使用 Bitwarden，实现密码同步、自动填充等功能，在这里统统 **直接白嫖** 爽翻～

> **为什么选择 NodeWarden？**
> 
> *   **费用：** 0元（利用 Cloudflare Workers 免费额度）
> *   **性能：** 极速（部署在 CF 全球边缘节点）
> *   **安全：** 私有化部署，数据存储在自己的 CF D1/KV 数据库
> *   **兼容性：** 支持所有 Bitwarden 官方客户端（iOS/Android/Chrome/桌面端）
> *   **核心优势：** 比 Vaultwarden 更轻量，完全不需要购买 VPS 服务器。

[](about:blank#NodeWarden-%E4%B8%8E-Bitwarden-%E5%AE%98%E6%96%B9%E6%9C%8D%E5%8A%A1%E7%AB%AF%E8%83%BD%E5%8A%9B%E5%AF%B9%E6%AF%94 "NodeWarden 与 Bitwarden 官方服务端能力对比")NodeWarden 与 Bitwarden 官方服务端能力对比
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

在开搞之前，我们先看看这个 NodeWarden 版本，和官方版有什么区别。简单总结：**个人单用户使用完美，企业/多人协作功能精简。**

| 能力 | Bitwarden | NodeWarden | 说明 |
| --- | --- | --- | --- |
| 网页密码库 | ✅ | ✅ | **原创Web Vault界面** |
| 全量同步 `/api/sync` | ✅ | ✅ | 已针对官方客户端做兼容优化 |
| 附件上传 / 下载 | ✅ | ✅ | Cloudflare R2 或 KV |
| Send | ✅ | ✅ | 支持文本与文件 Send |
| 导入 / 导出 | ✅ | ✅ | 支持 Bitwarden JSON / CSV / **ZIP 导入（包括附件）** |
| **云端备份中心** | ❌ | ✅ | **支持 WebDAV / E3 定时备份** |
| 密码提示（网页端） | ⚠️ 有限 | ✅ | **无需发送邮件** |
| TOTP / Steam TOTP | ✅ | ✅ | 含 `steam://` 支持 |
| 多用户 | ✅ | ✅ | 支持邀请码注册 |
| 组织 / 集合 / 成员权限 | ✅ | ❌ | 未实现 |
| 登录 2FA | ✅ | ⚠️ 部分支持 | 当前仅支持用户级 TOTP |
| SSO / SCIM / 企业目录 | ✅ | ❌ | 未实现 |

可以看出，对于咱们个人日常使用，NodeWarden 的功能已经完全绰绰有余了！我甚至更喜欢这个，免费且能使用 **云端备份** 去掉了我之前的焦虑。

[](about:blank#NodeWarden-%E9%83%A8%E7%BD%B2%E5%89%8D%E5%87%86%E5%A4%87 "NodeWarden 部署前准备")NodeWarden 部署前准备
-----------------------------------------------------------------------------------------------------------

1.  **一个 Cloudflare 账号**
    *   需要拥有一个托管在 CF 上的 **域名**，没有域名可以查看 [最新免费域名资源汇总](https://blog.zrf.me/p/Free-Domains/)（因为 CF 默认的 `workers.dev` 域名在国内访问是被阻断的）。
    *   需要绑定信用卡或 PayPal（开通 R2储存桶 服务，免费额度对个人绝对够用，不会扣费）。
2.  **一个 GitHub 账号**
    *   用于 Fork 源码并授权一键部署。

[](about:blank#NodeWarden-%E9%83%A8%E7%BD%B2%E6%95%99%E7%A8%8B "NodeWarden 部署教程")NodeWarden 部署教程
------------------------------------------------------------------------------------------------

### [](about:blank#%E7%AC%AC%E4%B8%80%E6%AD%A5%EF%BC%9AFork-%E9%A1%B9%E7%9B%AE%E6%BA%90%E7%A0%81 "第一步：Fork 项目源码")第一步：Fork 项目源码

首先，我们需要把大佬的源码复刻到咱们自己的 GitHub 仓库里。

1.  打开 NodeWarden 的 GitHub 开源地址：[https://github.com/shuaiplus/NodeWarden](https://github.com/shuaiplus/NodeWarden)
    
2.  来到页面右上角，可以给大佬点个 **Star** ，然后 **Fork** 按钮，将项目复制到你自己的账号下。  
    ![NodeWarden GitHub 源码 Fork 步骤](https://blog.zrf.me/img/loading2.gif)
    
3.  项目同步更新（可选）
    
    *   本来我这里写的是建议开启，但是由于自动同步更新，导致我创建的二十多个号通行密钥全部失效，我全部转移到此项目上，费了我老半天劲呢，我很难受！！！原由：[重构：移除与密码相关的功能和类型](https://github.com/shuaiplus/nodewarden/commit/76623d72014efb994d390e9bcab019088fb219e3) **最新现已修复数据还在的，不难受了**
    *   自动：进入你的 Fork 仓库 ➜ `Actions` ➜ `Sync upstream` ➜ `Enable workflow`，会在每天凌晨 3 点自动同步上游。  
        ![NodeWarden GitHub 源码 项目同步更新1](https://blog.zrf.me/img/loading2.gif)  
        ![NodeWarden GitHub 源码 项目同步更新2](https://blog.zrf.me/img/loading2.gif)

### [](about:blank#%E7%AC%AC%E4%BA%8C%E6%AD%A5%EF%BC%9A%E4%B8%80%E9%94%AE%E9%83%A8%E7%BD%B2%E5%88%B0-Cloudflare "第二步：一键部署到 Cloudflare")第二步：一键部署到 Cloudflare

这步非常丝滑，不需要你敲任何代码。但是要明确你的 Cloudflare 是否开通 R2 存储功能。没有就先去开通一下，需要绑卡，功能是免费的，如开通过一直下一步就可以了。

| 储存 | 是否需绑卡 | 单个附件/Send文件上限 | 免费额度 |
| --- | --- | --- | --- |
| R2 | 需要 | 100 MB（软限制可更改） | 10 GB |
| KV | 不需要 | 25 MiB（Cloudflare限制） | 1 GB |

1.  打开 [Workers](https://dash.cloudflare.com/?to=/:account/workers-and-pages/create) ➜ `Continue with GitHub` ➜ 选择你 Fork 后的仓库（`NodeWarden`）➜ 下一步 ➜ （默认使用 R2 存储；若未开通，可用 KV 来代替，将**部署命令**改为 `npm run deploy:kv`）➜ 部署 ➜ 打开生成的链接

![Cloudflare Workers 部署 NodeWarden 部署设置1](https://blog.zrf.me/img/loading2.gif)  
![Cloudflare Workers 部署 NodeWarden 部署设置2](https://blog.zrf.me/img/loading2.gif)  
![Cloudflare Workers 部署 NodeWarden 部署设置3](https://blog.zrf.me/img/loading2.gif)

### [](about:blank#%E7%AC%AC%E4%B8%89%E6%AD%A5%EF%BC%9A%E5%88%9D%E5%A7%8B%E5%8C%96%E8%AE%BE%E7%BD%AE%E4%B8%8E%E7%BB%91%E5%AE%9A%E5%9F%9F%E5%90%8D "第三步：初始化设置与绑定域名")第三步：初始化设置与绑定域名

1.  部署成功后，Cloudflare 会为你分配一个类似 `nodewarden.xxx.workers.dev` 的域名地址。
    
    > **注意：**  
    > 由于国内网络环境，`.workers.dev` 通常是打不开的。来到设置，找到 **域和路由** ➜ **自定义域** ，绑定一个你自己的二级域名（例如 `nodewarden.zrf.me`）。我就使用默认的来教程，自用建议绑定。
    
    ![设置自定义域名](https://blog.zrf.me/img/loading2.gif)
    
2.  绑定好自定义域名后，用浏览器打开这个域名，你就会看到 NodeWarden 的页面。提示你 **设置 JWT\_SECRET**：这是用于加密你的会话 Token 的密钥，系统会随机生成，复制下来我们按照页面中的提示去添加这个变量。  
    ![Cloudflare Workers 部署 NodeWarden 部署 设置 JWT_SECRET 环境变量 1](https://blog.zrf.me/img/loading2.gif)
    
3.  回到 Cloudflare 面板刚刚的 `nodewarden` 项目页面，点击顶部的 **设置**，找到 **变量和机密**，点击添加。按照下图所示填写：
    
    *   **类型**：下拉选择 **密钥**（必须选 **密钥** 不然后期项目同步更新，变量：JWT\_SECRET 会失效，别问我怎么知道）。
    *   **变量名称**：填入 `JWT_SECRET`。
    *   **值**：**粘贴**你刚才在第 2 步网页上复制的那串密钥。
    *   填写完成后，点击**部署**保存即可。  
        ![Cloudflare Workers 部署 NodeWarden 部署 设置 JWT_SECRET 环境变量 2](https://blog.zrf.me/img/loading2.gif)
4.  刷新域名地址，我们就来到项目首页了，去创建 **主账号密码**：**关键！** 这是你以后登录 Bitwarden 客户端的唯一账号和主密码，千万别忘了！创建完登录即可。  
    ![NodeWarden 项目中 创建账户](https://blog.zrf.me/img/loading2.gif)
    
5.  到这里项目部署就全部完成了，非常的简单。
    

[](about:blank#NodeWarden-%E7%AE%80%E5%8D%95%E4%BD%BF%E7%94%A8%E6%95%99%E7%A8%8B "NodeWarden 简单使用教程")NodeWarden 简单使用教程
----------------------------------------------------------------------------------------------------------------------

### [](about:blank#1-%E8%AE%BE%E7%BD%AE%E4%BA%8C%E6%AC%A1%E9%AA%8C%E8%AF%81 "1. 设置二次验证")1\. 设置二次验证

1.  来到项目 **账户设置** ➜ **设置二次验证 (TOTP)** ：强烈建议开启！有些小伙伴可能对 TOTP 不太熟，其实它就是咱们常说的 **2FA 双重身份验证**，支持 **Google Authenticator (谷歌验证器)** 或微软验证器。赶紧绑定一下，或者使用本项目去保存，稍后会教，这里就不写了。
    
    *   不知道为啥我扫码添加失败了，如果你也遇到这情况，直接使用 **输入设置密钥** 就可以成功绑定了！
2.  保存 **恢复代码** ：千万别漏了这一步！ 顺手生成一下，找个安全的地方保存好。 万一哪天你手机丢了、或者验证器没法用进不去账号，这就是你登入账号的最后一把救命钥匙！  
    ![NodeWarden 项目中 设置二次验证](https://blog.zrf.me/img/loading2.gif)
    

### [](about:blank#2-%E8%BF%9E%E6%8E%A5Bitwarden%E5%AE%A2%E6%88%B7%E7%AB%AF "2. 连接Bitwarden客户端")2\. 连接Bitwarden客户端

项目服务端搞定了，接下来就是连接 Bitwarden 客户端！

1.  来到官方下载页面 [Bitwarden-点击前往](https://bitwarden.com/download/) 下载好的 **Bitwarden 客户端** ，我一般喜欢用浏览器插件，我以 Chrome 为例 [Chrome-Bitwarden 密码管理器-点击前往](https://chromewebstore.google.com/detail/bitwarden-free-password-m/nngceckbapebfimnlniiiahkandclblb?browser=chrome) 安装完成后，在浏览器的右上角 **扩展程序** 找到Bitwarden，点击图钉图标来固定Bitwarden扩展。  
    ![安装 Bitwarden 扩展程序](https://blog.zrf.me/img/loading2.gif)
    
2.  我发现这个插件页面登录UI有问题还是怎么，反正我这里是异常显示，可以点右上角的 **弹出新窗口** ，弹出后就可以自由拖动大小了，在登录界面，不要急着输入账号，点击最下方的 **“bitwarden.com”** 选择 **自托管** 选项，弹出的 **服务器URL** 中填写你的项目域名地址，如你设置了自定义域名就写自定义的。然后输入你的账户密码进行登录就行了，如果刚才开启了二次验证，系统会要求你输入 6 位动态验证码。  
    ![登录 Bitwarden 程序1](https://blog.zrf.me/img/loading2.gif)  
    ![登录 Bitwarden 程序2](https://blog.zrf.me/img/loading2.gif)
    

### [](about:blank#3-%E4%BB%8E%E6%B5%8F%E8%A7%88%E5%99%A8%E5%AF%BC%E5%87%BA%E5%AF%86%E7%A0%81 "3. 从浏览器导出密码")3\. 从浏览器导出密码

1.  从 Chrome 或 Edge 浏览器导出密码：
    
    *   打开浏览器的设置，然后导航到密码设置，例如 `chrome://password-manager/settings` 或 `edge://wallet/passwords`
    *   找到“导出密码”并点击“下载文件”。系统可能会提示您输入计算机密码进行验证。对于 Microsoft Edge 浏览器，此选项可能隐藏在“已保存密码”部分的菜单下。
    *   指定导出文件的保存位置，并确认格式为逗号分隔值( CSV )。
    *   选择“保存”完成导出。  
        ![从 Chrome 或 Edge 浏览器导出密码](https://blog.zrf.me/img/loading2.gif)
2.  将数据导入密码库：拿到导出的 CSV 文件后，你可以直接你部署的 NodeWarden 网页端导入，也可以在 Bitwarden 浏览器扩展插件进行导入。随便选一个就行，两边的数据都是云端实时同步的。  
    ![导入数据到 NodeWarden 或 Bitwarden](https://blog.zrf.me/img/loading2.gif)
    
3.  拿我自己来说，平时习惯把 Chrome 当主力大号用，Edge 当备用小号，结果两边浏览器存了大量重复或者交叉的账号密码。现在哪怕你导入了多个浏览器的多份数据，直接在网页端左侧菜单点击 「重复项」，项目就会自动帮你找出所有重复的账号密码。点击上方的「选择重复项」即可智能勾选，然后一键「删除」，这下整个密码库清爽了， **强迫症狂喜**  
    ![NodeWarden 项目中 去重复项](https://blog.zrf.me/img/loading2.gif)
    

### [](about:blank#4-%E4%BA%91%E7%AB%AF%E5%A4%87%E4%BB%BD%EF%BC%88%E6%8E%A8%E8%8D%90%EF%BC%89 "4. 云端备份（推荐）")4\. 云端备份（推荐）

1.  InfiniCLOUD：是日本的云存储服务，支持 WebDAV，只需邮箱即可注册免费 20 GB；填写推荐码后总计 25 GB，还不错我用了蛮久的了，当时搞了 45G 空间只用来存储数据根本用不完。
    
2.  你在[InfiniCLOUD-点击前往](https://infini-cloud.net/en/)注册后，在[My Page-点击前往](https://infini-cloud.net/en/modules/mypage/usage/)里输入邀请码: `DYZYJ`，就能额外再获得 5GB 永久免费空间，总共可到 25GB。  
    ![InfiniCLOUD](https://blog.zrf.me/img/loading2.gif)
    
3.  在左侧导航栏点击 「云端备份」，然后在「备份地点」区域点击 「+ 新增地点」，选择 WebDAV 类型。
    
    *   WebDAV 服务地址：输入 InfiniCLOUD 地址 [https://miya.teracloud.jp/dav](https://miya.teracloud.jp/dav) （替换为你的实际地址）
    *   WebDAV 用户名：输入你的 InfiniCLOUD 账号（如 zrfme）
    *   WebDAV 密码：输入你的 InfiniCLOUD 应用密码（不是登录密码）
    *   远程目录：输入备份存放目录（如 nodewarden，会自动创建）
    *   配置完成后，先点击「启用」开启自动备份计划,再点击「保存设置」；你也可以按需点击「手动执行」立即触发一次备份测试，或点击「删除」来移除该备份地点。

![NodeWarden 项目中 设置云端备份](https://blog.zrf.me/img/loading2.gif)

### [](about:blank#5-%E4%BD%BF%E7%94%A8-NodeWarden-%E4%B8%BA-%E8%B4%A6%E5%8F%B7-%E5%BC%80%E5%90%AF%E9%80%9A%E8%A1%8C%E5%AF%86%E9%92%A5-Passkeys-%E4%B8%8E-TOTP "5. 使用 NodeWarden 为 账号 开启通行密钥 (Passkeys) 与 TOTP")5\. 使用 NodeWarden 为 账号 开启通行密钥 (Passkeys) 与 TOTP

接下来的操作才是 **NodeWarden** 的真正魅力所在：我们要直接“白嫖”官方 Bitwarden 只有高级会员（Premium）才能享有的 **内置 TOTP 验证器** 和 **通行密钥 (Passkeys)** 功能。

很多大佬可能还习惯在手机上装个 Google Authenticator，每次登录都要翻手机找验证码，简直是“反人类”操作。（当然我把这个 NodeWarden 项目的 TOTP 在谷歌验证器与此项目都绑定了，以防这个项目出现了什么问题。导致后续验证出现问题。）

用了 NodeWarden 之后，咱们直接把这些全部集成到插件软件里面，电脑用插件手机端用客户端也是一样使用。

#### [](about:blank#5-1-%E9%85%8D%E7%BD%AE-Passkeys%EF%BC%88%E9%80%9A%E8%A1%8C%E5%AF%86%E9%92%A5%EF%BC%89 "5.1 配置 Passkeys（通行密钥）")5.1 配置 Passkeys（通行密钥）

Passkeys 是未来的趋势，不用背密码，安全性还爆表。下面我以 GitHub 为例，带大家感受一下什么叫真正的“丝滑”。

1.  **进入 GitHub 设置：** 登录你的 GitHub，点头像进入 `Settings` ➜ `Password and authentication`。
2.  **点击添加：** 在 **Passkeys** 栏目找到 `Add a passkey`，新添加需要收验证码验证身份。验证完成添加既可，然后叫你命名你就随便写，你知道这个用于哪里就行，方便后续记忆。  
    ![配置 Passkeys（通行密钥）](https://blog.zrf.me/img/loading2.gif)
3.  **插件接管：** 此时浏览器会进入等待界面，只要你安装并登录了 Bitwarden 插件，它会 **自动跳出** “保存通行密钥”的窗口。如我下面的截图所示，插件非常智能，它会自动匹配你库里现有的 GitHub 账号。
4.  **一键关联保存：** 在插件弹窗中，直接点击你那个 **对应的登录账号**（就是图中红框标出的账号）。如果你想存成一个新项目，也可以点右上角的 `+ 新增`。点完之后，这个 Passkey 就稳稳地存进你的 NodeWarden 数据库了。  
    ![谷歌插件接管 Passkeys 保存界面](https://blog.zrf.me/img/loading2.gif)

*   **爽点：** 下次你登录 GitHub 电脑端只要点一下“使用通行密钥”，手机端指纹或面容一刷，瞬间进后台，连账号密码都不用输入，安全又快捷！  
    ![Bitwarden 程序中 使用通行密钥 登录](https://blog.zrf.me/img/loading2.gif)

#### [](about:blank#5-2-%E5%BC%80%E5%90%AF%E5%86%85%E7%BD%AE-TOTP "5.2 开启内置 TOTP")5.2 开启内置 TOTP

大家注意，官方 Bitwarden 的内置 TOTP（就是那个 30 秒一变的 6 位验证码）是 **收费功能** 。但使用 NodeWarden ，**直接免费了！**

1.  **获取密钥：** 在 GitHub 的双因素认证（2FA）页面，选择 `Enable two-factor authentication`。你会看到一个 **二维码** 。  
    ![开启 Enable two-factor authentication](https://blog.zrf.me/img/loading2.gif)
2.  **编辑条目：** 打开 Bitwarden 插件，找到你的 GitHub 账号，点右侧的三个点，再点 `编辑`。
3.  **注入灵魂：** 找到 `验证器密钥 (TOTP)` 这一行：
    *   你可以点右边的 **相机图标** 直接对着屏幕扫。
    *   或者直接点击把二维码下方 **Setup Key** 的那一串字符，粘贴进去。  
        ![验证器密钥 (TOTP) 导入密钥 到 Bitwarden 程序中](https://blog.zrf.me/img/loading2.gif)
4.  **保存即用：** 保存后，使用 TOTP 进行验证一下。你会发现条目里出现了一个不断刷新的 6 位数字。  
    ![保存密钥 并 TOTP 验证](https://blog.zrf.me/img/loading2.gif)
5.  **附件保存：非常重要，如果丢失会导致你的账号无法登录** 我们可以把这些恢复代码直接保存到项目中，下载下来添加在`附件`中 或 添加复制到 `字段` 去保存，项目有自动备份功能。我并不担心数据丢失。  
    ![恢复代码 备份 很重要](https://blog.zrf.me/img/loading2.gif)

*   **强迫症狂喜：** 以后登录需要验证码，插件会自动帮你填充，或者点一下直接复制，再也不用满世界找手机了！

[](about:blank#%E5%AE%8C%E7%BB%93%E6%92%92%E8%8A%B1%EF%BC%81%E5%8F%91%E5%93%A5%E5%B0%8F%E6%8F%90%E7%A4%BA%EF%BC%81%EF%BC%88%E5%BF%85%E7%9C%8B%EF%BC%89 "完结撒花！发哥小提示！（必看）")完结撒花！发哥小提示！（必看）
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

至此，你拥有了一个完全属于自己、无需维护服务器、基于 Cloudflare 全球边缘节点加速，并且支持密码同步、自动填充、云端备份以及 TOTP 功能的满血版密码管理器！。

相比传统自建方案，这种基于 Cloudflare 的无服务器部署方式，不仅成本为 0，还兼顾了性能与可用性，可以说是目前个人用户最优雅的 Bitwarden 自建方案之一。

虽然“白嫖”很爽，但因为我们把“鸡蛋都放进了一个篮子”（账号密码、Passkey、TOTP）都集中在同一个 NodeWarden 系统中。因此，有两件事情你**必须认真对待**：

1.  **所有账号的 TOTP 必须额外备份：**  
    一定要确认 NodeWarden 主账号已开启 TOTP 双重验证。但请记住：不仅是 NodeWarden 本身，只要是被你放进密码管理器里的重要账号（如谷歌账户、Apple ID、域名服务商等），其 TOTP 都强烈建议在第三方验证器（如 Google Authenticator）或备用的旧手机中额外备份一份！
    
    > 就在写这篇教程不久之后，我之前设置好的 NodeWarden 的 TOTP 突然出现 Bug，不知道为什么项目无故显示“未启用”。我当时就重新设置了新的 TOTP，但忘记立刻将其备份到其他身份验证器上。结果到了第二天，我所有的设备突然全部掉线（退出登录状态）！
    > 
    > 因为登录需要 TOTP，而唯一的 TOTP 又锁在了我登不进去的 NodeWarden 项目里，给我直接吓出一身冷汗，还好之前设置了恢复代码！并且保存在了其他地方，所以成功恢复且登录，因此，记住无论何时重置 TOTP，**第一件事就是扫码备份到第三方验证器，且保存恢复代码！**
    
2.  **备份恢复代码：**  
    虽然 NodeWarden 已支持定时云端备份（如 WebDAV），在大多数情况下数据是安全的，但恢复代码依然建议保留一份离线备份。比如说 Cloudflare 崩了，刚好你这个时候要使用（小概率但是会发生）
    
    因为一旦出现设备丢失、TOTP 无法使用等情况，恢复代码可能是你重新访问账号的唯一方式。
    

最后记住一句话：  
**你可以忘记密码，但绝不能丢掉恢复代码。**

  

本文转自 [https://blog.zrf.me/p/NodeWarden-Bitwarden/](https://blog.zrf.me/p/NodeWarden-Bitwarden/)，如有侵权，请联系删除。