[](https://cloud.tencent.com/developer/user/8492898)

[星哥玩云

](https://cloud.tencent.com/developer/user/8492898)

星哥带你玩飞牛NAS-7：手把手教你免费内网穿透-Cloudflare tunnel
------------------------------------------

原创

关注作者

[_腾讯云_](https://cloud.tencent.com/?from=20060&from_column=20060)

[_开发者社区_](https://cloud.tencent.com/developer)

[文档](https://cloud.tencent.com/document/product?from=20702&from_column=20702)[建议反馈](https://cloud.tencent.com/voc/?from=20703&from_column=20703)[控制台](https://console.cloud.tencent.com/?from=20063&from_column=20063)

登录/注册

[首页](https://cloud.tencent.com/developer)

学习

活动

专区

圈层

工具

[MCP广场![](https://qccommunity.qcloudimg.com/image/new.png)](https://cloud.tencent.com/developer/mcp)

文章/答案/技术大牛搜索

搜索关闭

发布

星哥玩云

[社区首页](https://cloud.tencent.com/developer) >[专栏](https://cloud.tencent.com/developer/column) >星哥带你玩飞牛NAS-7：手把手教你免费内网穿透-Cloudflare tunnel

星哥带你玩飞牛NAS-7：手把手教你免费内网穿透-Cloudflare tunnel
==========================================

![作者头像](https://developer.qcloudimg.com/http-save/10011/7ad9ef0a09832775d23628895639c4b0.jpg)

星哥玩云

关注

发布于 2025-12-13 14:43:20

发布于 2025-12-13 14:43:20

10.6K0

举报

概述

大家好，我是星哥。一直以来，我都在折腾各种云服务和NAS玩法，目标就是让家庭和工作环境更高效、更有趣。很多朋友问我：没有公网IP，怎么才能在外网访问家里的NAS？ 这其实是个常见痛点。如何让外网安全访问内网NAS服务？

文章被收录于专栏：[NAS](https://cloud.tencent.com/developer/column/106641)[NAS](https://cloud.tencent.com/developer/article/2600529)

原创声明：本文系作者授权腾讯云开发者社区发表，未经许可，不得转载。

如有侵权，请联系 [cloudcommunity@tencent.com](mailto:cloudcommunity@tencent.com) 删除。

[腾讯技术创作特训营S16](https://cloud.tencent.com/developer/tag/18203)

原创声明：本文系作者授权腾讯云开发者社区发表，未经许可，不得转载。

如有侵权，请联系 [cloudcommunity@tencent.com](mailto:cloudcommunity@tencent.com) 删除。

[腾讯技术创作特训营S16](https://cloud.tencent.com/developer/tag/18203)

[#nas](https://cloud.tencent.com/developer/search/article-nas)

评论

登录后参与评论

0 条评论

热度

最新

登录 后参与评论

推荐阅读

相关产品与服务

域名注册

[产品介绍](https://cloud.tencent.com/product/domain?from=21341&from_column=21341)[产品文档](https://cloud.tencent.com/document/product/242?from=21342&from_column=21342)

[热销域名限时优惠，新客首年免费！](https://cloud.tencent.com/act/pro/domain?from=21344&from_column=21344)

领券

*   ### 社区
    
    *   [技术文章](https://cloud.tencent.com/developer/column)
    *   [技术问答](https://cloud.tencent.com/developer/ask)
    *   [技术沙龙](https://cloud.tencent.com/developer/salon)
    *   [技术视频](https://cloud.tencent.com/developer/video)
    *   [学习中心](https://cloud.tencent.com/developer/learning)
    *   [技术百科](https://cloud.tencent.com/developer/techpedia)
    *   [技术专区](https://cloud.tencent.com/developer/zone/list)
    
*   ### 活动
    
    *   [自媒体同步曝光计划](https://cloud.tencent.com/developer/support-plan)
    *   [邀请作者入驻](https://cloud.tencent.com/developer/support-plan-invitation)
    *   [自荐上首页](https://cloud.tencent.com/developer/article/1535830)
    *   [技术竞赛](https://cloud.tencent.com/developer/competition)
    
*   ### 圈层
    
    *   [腾讯云最具价值专家](https://cloud.tencent.com/tvp)
    *   [腾讯云架构师技术同盟](https://cloud.tencent.com/developer/program/tm)
    *   [腾讯云创作之星](https://cloud.tencent.com/developer/program/tci)
    *   [腾讯云TDP](https://cloud.tencent.com/developer/program/tdp)
    
*   ### 关于
    
    *   [社区规范](https://cloud.tencent.com/developer/article/1006434)
    *   [免责声明](https://cloud.tencent.com/developer/article/1006435)
    *   [联系我们](mailto:cloudcommunity@tencent.com)
    *   [友情链接](https://cloud.tencent.com/developer/friendlink)
    *   [MCP广场开源版权声明](https://cloud.tencent.com/developer/article/2537547)
    

### 腾讯云开发者

![扫码关注腾讯云开发者](https://qcloudimg.tencent-cloud.cn/raw/a8907230cd5be483497c7e90b061b861.png?imageView2/2/w/200)

扫码关注腾讯云开发者

领取腾讯云代金券

### 热门产品

*   [域名注册](https://cloud.tencent.com/product/domain?from=20064&from_column=20064)
*   [云服务器](https://cloud.tencent.com/product/cvm?from=20064&from_column=20064)
*   [区块链服务](https://cloud.tencent.com/product/tbaas?from=20064&from_column=20064)
*   [消息队列](https://cloud.tencent.com/product/message-queue-catalog?from=20064&from_column=20064)
*   [网络加速](https://cloud.tencent.com/product/ecdn?from=20064&from_column=20064)
*   [云数据库](https://cloud.tencent.com/product/tencentdb-catalog?from=20064&from_column=20064)
*   [域名解析](https://cloud.tencent.com/product/dns?from=20064&from_column=20064)
*   [云存储](https://cloud.tencent.com/product/cos?from=20064&from_column=20064)
*   [视频直播](https://cloud.tencent.com/product/css?from=20064&from_column=20064)

### 热门推荐

*   [人脸识别](https://cloud.tencent.com/product/facerecognition?from=20064&from_column=20064)
*   [腾讯会议](https://cloud.tencent.com/product/tm?from=20064&from_column=20064)
*   [企业云](https://cloud.tencent.com/act/pro/enterprise2022?from=20064&from_column=20064)
*   [CDN加速](https://cloud.tencent.com/product/cdn?from=20064&from_column=20064)
*   [视频通话](https://cloud.tencent.com/product/trtc?from=20064&from_column=20064)
*   [图像分析](https://cloud.tencent.com/product/imagerecognition?from=20064&from_column=20064)
*   [MySQL 数据库](https://cloud.tencent.com/product/cdb?from=20064&from_column=20064)
*   [SSL 证书](https://cloud.tencent.com/product/ssl?from=20064&from_column=20064)
*   [语音识别](https://cloud.tencent.com/product/asr?from=20064&from_column=20064)

### 更多推荐

*   [数据安全](https://cloud.tencent.com/solution/data_protection?from=20064&from_column=20064)
*   [负载均衡](https://cloud.tencent.com/product/clb?from=20064&from_column=20064)
*   [短信](https://cloud.tencent.com/product/sms?from=20064&from_column=20064)
*   [文字识别](https://cloud.tencent.com/product/ocr?from=20064&from_column=20064)
*   [云点播](https://cloud.tencent.com/product/vod?from=20064&from_column=20064)
*   [大数据](https://cloud.tencent.com/product/bigdata-class?from=20064&from_column=20064)
*   [小程序开发](https://cloud.tencent.com/solution/la?from=20064&from_column=20064)
*   [网站监控](https://cloud.tencent.com/product/tcop?from=20064&from_column=20064)
*   [数据迁移](https://cloud.tencent.com/product/cdm?from=20064&from_column=20064)

Copyright © 2013 - 2026 Tencent Cloud. All Rights Reserved. 腾讯云 版权所有 

[深圳市腾讯计算机系统有限公司](https://qcloudimg.tencent-cloud.cn/raw/986376a919726e0c35e96b311f54184d.jpg) ICP备案/许可证号：[粤B2-20090059](https://beian.miit.gov.cn/#/Integrated/index) ![](https://qcloudimg.tencent-cloud.cn/raw/eed02831a0e201b8d794c8282c40cf2e.png)[粤公网安备44030502008569号](https://beian.mps.gov.cn/#/query/webSearch?code=44030502008569)

[腾讯云计算（北京）有限责任公司](https://qcloudimg.tencent-cloud.cn/raw/a2390663ee4a95ceeead8fdc34d4b207.jpg) 京ICP证150476号 |  [京ICP备11018762号](https://beian.miit.gov.cn/#/Integrated/index)

[问题归档](https://cloud.tencent.com/developer/ask/archives.html)[专栏文章](https://cloud.tencent.com/developer/column/archives.html)[快讯文章归档](https://cloud.tencent.com/developer/news/archives.html)[关键词归档](https://cloud.tencent.com/developer/information/all.html)[开发者手册归档](https://cloud.tencent.com/developer/devdocs/archives.html)[开发者手册 Section 归档](https://cloud.tencent.com/developer/devdocs/sections_p1.html)

Copyright © 2013 - 2026 Tencent Cloud.

All Rights Reserved. 腾讯云 版权所有

登录 后参与评论

000

推荐

if (!String.prototype.replaceAll) { String.prototype.replaceAll = function (str, newStr) { // If a regex pattern if (Object.prototype.toString.call(str).toLowerCase() === '\[object regexp\]') { return this.replace(str, newStr); } // If a string return this.replace(new RegExp(str, 'g'), newStr); }; } {"props":{"isMobile":false,"currentDomain":"cloud.tencent.com","baseUrl":"https://cloud.tencent.com","reqId":"-DZhtgEvOdZ4fyPNUPi7G","query":{"articleId":"2600529"},"platform":"other","env":"production","\_\_N\_SSP":true,"pageProps":{"fallback":{"#url:\\"/api/article/detail\\",params:#articleId:2600529,,":{"articleData":{"articleId":2600529,"codeLineNum":3,"readingTime":500,"wordsNum":2293},"articleInfo":{"articleId":2600529,"channel":0,"commentNum":0,"content":"# 星哥带你玩飞牛NAS-7：手把手教你免费内网穿透-Cloudflare tunnel\\n\\n\\n## 前言\\n\\n大家好，我是星哥。一直以来，我都在折腾各种云服务和NAS玩法，目标就是让家庭和工作环境更高效、更有趣。很多朋友问我：\*\*没有公网IP，怎么才能在外网访问家里的NAS？\*\* 这其实是个常见痛点。\\n\*\*如何让外网安全访问内网NAS服务？\*\* \\n1. 内网则访问IP+端口（192.168.1.3:5667）\\n2. 飞牛官方的FN Connect (基础版 2Mbps 无限流量）\\n3. DDNS（ipv4无效、ipv6有效）\\n4. 如果有独立服务器和域名，可以使用frp客户端内网穿透。\\n5. 第三方服务，如节小宝\\n6. 今天的教程则使用Cloudflare Tunnel\\n\\n今天我就带大家实战一把，用 \*\*Cloudflare Tunnel\*\* 来实现免费内网穿透，让飞牛NAS轻松走向公网。\\n传统方案要么依赖公网IP，要么借助第三方付费内网穿透工具。今天星哥带你玩一个\*\*零成本、稳定可靠的方案 —— Cloudflare Tunnel\*\*。\\nCloudflare是一家总部位于美国旧金山的跨国科技公司，主要提供网站加速与安全服务，包括CDN、DDoS防护、Web应用防火墙和域名解析等功能，Cloudflare（本文都用CF代替）被广大网友冠以“赛博大善人”、“赛博活佛”等戏称，这是因为很多别人家收费的服务，它都免费提供。\\n## Cloudflare Tunnel优点\\n\\n- \*\*免费\*\*：无需购买公网IP或额外服务。\\n- \*\*安全\*\*：基于 Cloudflare 的全球节点，自动加密传输、自动配置 SSL 证书（HTTPS）。\\n- \*\*简单\*\*：几条命令即可完成配置。\\n- \*\*灵活\*\*：支持多端口、多服务映射，适合NAS场景。\\n- \*\*支持CDN\*\*：且支持 CDN 加速\\n\\n!\[img\](https://developer.qcloudimg.com/http-save/yehe-8492898/6a990788310c209782b331836a8cc17c.png)\\n## 实战\\n\\n## 注册 Cloudflare 账号\\n\\n- 前往 \[Cloudflare 官网\](https://www.cloudflare.com/) \`https://dash.cloudflare.com/\` 注册账号。\\n- 添加你的域名（如果没有域名，可以考虑购买一个便宜的 \`.xyz\` 或 \`.top\` 域名）。\\n- 当然也可以申请一个免费域名。\\n- 把我是其他平台购买的域名，可以把这个域名加入到CF中。\\n\\n注册登录\\n## 加入域名\\n\\n如果你有域名已经加入到CF中，此步可以忽略\\n### 1.点击“加入域”\\n\\n!\[img\](https://developer.qcloudimg.com/http-save/yehe-8492898/cbe0f6b1cdc210fe599d8ceecc96f0bf.png)\\n### 2.输入域名\\n\\n输入你的域名，点击继续\\n!\[img\](https://developer.qcloudimg.com/http-save/yehe-8492898/09e38eac5d839d5e3ebda876695f2ccd.png)\\n### 3.修改dns\\n\\n!\[img\](https://developer.qcloudimg.com/http-save/yehe-8492898/e610a858a772052cfd550f53c122b54e.png)\\n\\n### 4.修改域名的dns\\n\\n进入到你的域名管理后台，修改dns\\n!\[img\](https://developer.qcloudimg.com/http-save/yehe-8492898/4a9c980e8fc455e0ff1f4283018b0152.png)\\n### 5.域名添加成功\\n\\n!\[img\](https://developer.qcloudimg.com/http-save/yehe-8492898/f9c8524b115b6aa6884ef83d62edf627.png)\\n\\n## 安装 Cloudflare Tunnel 客户端\\n\\n### 1.开通Zero Trust\\n\\n在Cloudflare首页的左侧栏目中点击\`Zero Trust\`进入详情页面。\\n!\[img\](https://developer.qcloudimg.com/http-save/yehe-8492898/48f5857eee667173e5e5d06c557c9d99.png)\\n\\n选择您的团队名称，不要点下一步，选择取消。\\n!\[img\](https://developer.qcloudimg.com/http-save/yehe-8492898/ce4ad1eca2200d0374a1dfbb07810dbc.png)\\n\\n!\[img\](https://developer.qcloudimg.com/http-save/yehe-8492898/feec610058755a487450889e7dfb1800.png)\\n\\n### 2.创建隧道\\n\\n进入页面后，在左侧栏目中找到网络/network，并点击其中的Tunnels，首次使用需要激活。 点击创建隧道\\n!\[img\](https://developer.qcloudimg.com/http-save/yehe-8492898/3749b5585b28ce8200fb8bc0fc7eedad.png)\\n### 3.选择隧道类型\\n\\n选择cloudflared方式创建隧道\\n!\[img\](https://developer.qcloudimg.com/http-save/yehe-8492898/7a68fe83589108d8e826bba5128e2f85.png)\\n### 4.填写隧道类型\\n\\n隧道名称可以随意填写，考虑到方便记忆，例如home\_fnas\\n!\[img\](https://developer.qcloudimg.com/http-save/yehe-8492898/bcb53ecb2c1653fa0b41164e4a359798.png)\\n### 5.安装软件\\n\\n选择对应的软件并安装。选择Debian、64位。随后使用SSH登录飞牛系统，运行下图中的命令，最后，运行下图中的内容设置为开机自启。几秒后将完整隧道链接，在页面下方将显示此设备。\\n!\[img\](https://developer.qcloudimg.com/http-save/yehe-8492898/78a8560c612921ca5928d11d3dbef5d8.png)\\n执行命令\\n再到飞牛中FntermX\\n!\[img\](https://developer.qcloudimg.com/http-save/yehe-8492898/909074b3a7d14cd086b7e64c128af06e.png)\\n输入命令\\n!\[img\](https://developer.qcloudimg.com/http-save/yehe-8492898/e11c9c38847bd6ca82320affce564bc3.png)\\n\\n开机启动\\n\`\`\`\\nstar@star-fnas:~$ sudo cloudflared service install 你的密钥\\n2025-11-25T10:29:35Z INF Using Systemd\\n\`\`\`点击下一步\\n### 6.设置域名\\n\\n进入此隧道，在设置中找到\`公共机名\`并点击添加。详细说明如下：\\n- \`子域\`为网址前缀，比如我希望实现\`fnas.example.com\`，那么此处填写\`fnas\`，如果不填写，最终的域名就是\`example.com\`\\n- \`域\`需要选择一个托管在Cloudflare的域名，即上述的\`example.com\`，如果没有，可以在\[Cloudflare domains\](https://domains.cloudflare.com/)注册一个6位或者9位数字的xyz域名，一年仅需要0.83美元。\\n- \`路径\`留空，不填写\\n- \`类型\`选择http\\n- \`URL\`填入\`localhost:5666\`\\n\\n!\[img\](https://developer.qcloudimg.com/http-save/yehe-8492898/a9f83ef10d28be7c1bee84e954da7cea.png)\\n\\n### 测试是否成功\\n\\n如图到飞牛的登录界面，说明CF的 Tunnel搭建成功\\n!\[img\](https://developer.qcloudimg.com/http-save/yehe-8492898/bbcfa78f9105f4460e3ea38b1144b600.png)\\n\\n\\n### 安全与优化建议\\n\\n- 使用 \*\*HTTPS 域名访问\*\*，避免明文传输。\\n- 配合 \*\*Cloudflare Access\*\* 做身份验证，防止NAS暴露在公网。\\n- 建议将 Tunnel 服务纳入 systemd，保证开机自启与稳定性。\\n\\n增加安全认证\\n!\[img\](https://developer.qcloudimg.com/http-save/yehe-8492898/cf06619780bf1fec6f2e97c8a1150773.png)\\n## 其他文章\\n\\n- \[星哥带你玩飞牛NAS-1：安装飞牛NAS\](https://mp.weixin.qq.com/s/QMaWJ8E9cd4-y5p02NWqzg)\\n- \[星哥带你玩飞牛NAS-2：飞牛配置RAID磁盘阵列\](https://mp.weixin.qq.com/s/R6Qw9sO5sNlQ2CdwE4wUkg)\\n- \[星哥带你玩飞牛NAS-3：安装飞牛NAS后的很有必要的操作\](https://mp.weixin.qq.com/s/Xc0Qci70aug6Hry7QCzXDg)\\n- \[星哥带你玩飞牛NAS-4：飞牛NAS安装istore旁路由，家庭网络升级的最佳实践\](https://mp.weixin.qq.com/s/UL4StiG40OxwGQ5IQTlYYg)\\n- \[星哥带你玩飞牛NAS-5：飞牛NAS中的Docker功能介绍\](https://mp.weixin.qq.com/s/Wqv3Iusu\_\_Ugrb\_LbLtfMQ)\\n- \[星哥带你玩飞牛NAS-6：抖音视频同步工具，视频下载自动下载保存\](https://mp.weixin.qq.com/s/BeGhw0cF7R1goS\_lUPBQZw)\\n- \[云服务器配置frp实现内网穿透\](https://mp.weixin.qq.com/s/4NwzAvh1F3eRWK0dwMwfpw)\\n- \[飞牛NAS玩转Frpc并且配置，随时随地直连你的私有云\](https://mp.weixin.qq.com/s/Cdf5m0DCU2TecS6rkM64Uw)\\n\\n## 总结\\n\\n写文不易，如果你都看到了这里，请点个赞和在看，分享给更多的朋友；也别忘了关注星哥玩云！这里有满满的干货分享，还有轻松有趣的技术交流～点个赞、分享给身边的小伙伴，一起成长，一起玩转技术世界吧！ 😊\\n实测使用Cloudflare Tunnel网速在2-3MB/s\\n!\[img\](https://developer.qcloudimg.com/http-save/yehe-8492898/cc8fb74b79ab40a7397f393014f822e6.png)\\n\\n通过 Cloudflare Tunnel，我们可以轻松实现：\\n- \*\*零成本的内网穿透\*\*\\n- \*\*安全可靠的远程访问\*\*\\n- \*\*灵活的多服务映射\*\*\\n\\n不仅可以设置飞牛，其他的内网设备也可以做内网穿透。\\n以上就是我这次的实战分享。通过 Cloudflare Tunnel，我们不仅能零成本解决内网穿透，还能享受到 Cloudflare 提供的安全与加速服务。对我来说，这不只是一个技术方案，更是一种“玩云”的乐趣：用最简单的方式，把复杂问题优雅地解决。","createTime":1765608200,"ext":{"closeTextLink":0,"comment\_ban":0,"description":"","focusRead":0},"favNum":1,"html":"","isOriginal":0,"likeNum":3,"pic":"https://developer.qcloudimg.com/http-save/yehe-8492898/7d9da8fb5f638d7e3fcf3cfd2205d8f6.jpg","plain":"星哥带你玩飞牛NAS-7：手把手教你免费内网穿透-Cloudflare tunnel\\n前言\\n大家好，我是星哥。一直以来，我都在折腾各种云服务和NAS玩法，目标就是让家庭和工作环境更高效、更有趣。很多朋友问我：没有公网IP，怎么才能在外网访问家里的NAS？ 这其实是个常见痛点。\\n如何让外网安全访问内网NAS服务？ 内网则访问IP+端口（192.168.1.3:5667）\\n飞牛官方的FN Connect (基础版 2Mbps 无限流量）\\nDDNS（ipv4无效、ipv6有效）\\n如果有独立服务器和域名，可以使用frp客户端内网穿透。\\n第三方服务，如节小宝\\n今天的教程则使用Cloudflare Tunnel 今天我就带大家实战一把，用 Cloudflare Tunnel 来实现免费内网穿透，让飞牛NAS轻松走向公网。\\n传统方案要么依赖公网IP，要么借助第三方付费内网穿透工具。今天星哥带你玩一个零成本、稳定可靠的方案 —— Cloudflare Tunnel。\\nCloudflare是一家总部位于美国旧金山的跨国科技公司，主要提供网站加速与安全服务，包括CDN、DDoS防护、Web应用防火墙和域名解析等功能，Cloudflare（本文都用CF代替）被广大网友冠以“赛博大善人”、“赛博活佛”等戏称，这是因为很多别人家收费的服务，它都免费提供。\\nCloudflare Tunnel优点 免费：无需购买公网IP或额外服务。\\n安全：基于 Cloudflare 的全球节点，自动加密传输、自动配置 SSL 证书（HTTPS）。\\n简单：几条命令即可完成配置。\\n灵活：支持多端口、多服务映射，适合NAS场景。\\n支持CDN：且支持 CDN 加速 实战\\n注册 Cloudflare 账号 前往 Cloudflare 官网 注册账号。\\n添加你的域名（如果没有域名，可以考虑购买一个便宜的 或 域名）。\\n当然也可以申请一个免费域名。\\n把我是其他平台购买的域名，可以把这个域名加入到CF中。 注册登录\\n加入域名\\n如果你有域名已经加入到CF中，此步可以忽略\\n1.点击“加入域” 2.输入域名\\n输入你的域名，点击继续 3.修改dns 4.修改域名的dns\\n进入到你的域名管理后台，修改dns 5.域名添加成功 安装 Cloudflare Tunnel 客户端\\n1.开通Zero Trust\\n在Cloudflare首页的左侧栏目中点击进入详情页面。 选择您的团队名称，不要点下一步，选择取消。 2.创建隧道\\n进入页面后，在左侧栏目中找到网络/network，并点击其中的Tunnels，首次使用需要激活。 点击创建隧道 3.选择隧道类型\\n选择cloudflared方式创建隧道 4.填写隧道类型\\n隧道名称可以随意填写，考虑到方便记忆，例如home\_fnas 5.安装软件\\n选择对应的软件并安装。选择Debian、64位。随后使用SSH登录飞牛系统，运行下图中的命令，最后，运行下图中的内容设置为开机自启。几秒后将完整隧道链接，在页面下方将显示此设备。 执行命令\\n再到飞牛中FntermX 输入命令 开机启动","showReadNum":10592,"sourceDetail":null,"sourceType":1,"status":2,"summary":"大家好，我是星哥。一直以来，我都在折腾各种云服务和NAS玩法，目标就是让家庭和工作环境更高效、更有趣。很多朋友问我：没有公网IP，怎么才能在外网访问家里的NAS？ 这其实是个常见痛点。如何让外网安全访问内网NAS服务？","tagIds":\[18203\],"title":"星哥带你玩飞牛NAS-7：手把手教你免费内网穿透-Cloudflare tunnel","uid":8492898,"updateTime":1765608296,"userSummary":"大家好，我是星哥。一直以来，我都在折腾各种云服务和NAS玩法，目标就是让家庭和工作环境更高效、更有趣。很多朋友问我：没有公网IP，怎么才能在外网访问家里的NAS？ 这其实是个常见痛点。如何让外网安全访问内网NAS服务？","userUpdateTime":1765608200,"contentType":"markdown","isNewArticle":true},"authorInfo":{"articleNum":0,"avatarUrl":"https://developer.qcloudimg.com/http-save/10011/7ad9ef0a09832775d23628895639c4b0.jpg","company":"传趣网络","introduce":"","isProfessionVerified":1,"nickname":"星哥玩云","privilege":1,"title":"运维经理","uid":8492898},"authorType":{"isBlogMoveAuthor":0,"isCoCreator":1,"isInternalAuthor":0,"isOriginalAuthor":1},"classify":\[{"id":1,"name":"云计算"},{"id":12,"name":"运维"},{"id":14,"name":"网络与通信"}\],"columnInfo":{"columnAvatar":"https://cloudcache.tencent-cloud.com/qcloud/developer/images/release/column-icons/7.png","columnDesc":"nas","columnId":106641,"columnName":"NAS","createTime":1764603052,"createUid":8492898,"memberNum":1,"showArticleNum":41,"showConcernNum":0},"columnList":\[{"columnAvatar":"https://cloudcache.tencent-cloud.com/qcloud/developer/images/release/column-icons/7.png","columnDesc":"nas","columnId":106641,"columnName":"NAS","createTime":1764603052,"createUid":8492898,"memberNum":1,"showArticleNum":41,"showConcernNum":0}\],"editTime":0,"grayWords":\[\],"isTencent":false,"longtailTags":\["nas"\],"publishTime":1765608200,"sourceDetail":{"blogType":2,"blogUrl":"https://www.xgss.net/","channelSource":"","originalTime":"","sourceAuthor":"","sourceLink":"","wechatNickName":"","wechatUserName":""},"tags":\[{"categoryId":99,"createTime":"2025/11/12 22:48:17","groupId":0,"groupName":"","tagId":18203,"tagName":"腾讯技术创作特训营S16"}\],"tdk":{"description":"免费实现飞牛NAS内网穿透！使用Cloudflare Tunnel零成本搭建安全远程访问，无需公网IP。教程详解注册账号、创建隧道、配置域名全过程，支持HTTPS加密和多服务映射。实测网速2-3MB/s，适合NAS玩家解决外网访问难题。","keywords":\["内网穿透","CloudflareTunnel","飞牛NAS","远程访问"\]},"textLink":\[{"ext":{"categoryId":0,"categoryName":"","desc":"","kpCount":0,"name":"","pCategoryId":0,"termId":0},"id":173,"link":"https://cloud.tencent.com/product/waf","sources":\[1\],"text":"Web应用防火墙"},{"ext":{"categoryId":1004,"categoryName":"云产品 - 计算","desc":"云服务器（Cloud Virtual Machine，CVM）提供安全可靠的弹性计算服务。 您可以实时扩展或缩减计算资源，适应变化的业务需求，并只需按实际使用的资源计费。使用 CVM 可以极大降低您的软硬件采购成本，简化 IT 运维工作。","kpCount":458,"name":"云服务器","pCategoryId":1000,"termId":1000},"id":2,"link":"https://cloud.tencent.com/developer/techpedia/1000","sources":\[1,2\],"text":"云服务器"},{"ext":{"categoryId":0,"categoryName":"","desc":"","kpCount":0,"name":"","pCategoryId":0,"termId":0},"id":10,"link":"https://cloud.tencent.com/product/dns","sources":\[1\],"text":"域名解析"},{"ext":{"categoryId":1030,"categoryName":"通用技术 - 安全","desc":"身份验证（Authentication）是指确认用户的身份是否合法的过程。在计算机系统中，身份验证是指通过一系列的安全机制来确认用户或程序的身份是否是合法的，以控制对系统资源的访问权限。","kpCount":7,"name":"身份验证","pCategoryId":1002,"termId":1769},"id":1096,"link":"https://cloud.tencent.com/developer/techpedia/1769","sources":\[1,2\],"text":"身份验证"},{"ext":{"categoryId":0,"categoryName":"","desc":"","kpCount":0,"name":"","pCategoryId":0,"termId":0},"id":823,"link":"https://cloud.tencent.com/product/cdn","sources":\[1\],"text":"网站加速"},{"ext":{"categoryId":0,"categoryName":"","desc":"","kpCount":0,"name":"","pCategoryId":0,"termId":0},"id":150,"link":"https://cloud.tencent.com/product/ddos","sources":\[1\],"text":"DDoS防护"},{"ext":{"categoryId":0,"categoryName":"","desc":"","kpCount":0,"name":"","pCategoryId":0,"termId":0},"id":821,"link":"https://cloud.tencent.com/product/cdn","sources":\[1\],"text":"CDN加速"},{"ext":{"categoryId":1020,"categoryName":"通用技术 - 云计算","desc":"服务器是一种计算机硬件和软件系统，其主要功能是为其他计算机（通常称为客户端）提供服务、资源和数据。服务器可以处理来自客户端的请求，例如文件共享、应用程序访问、数据存储和检索、网络服务等。服务器通常具有较高的处理能力、内存和存储容量，以便能够同时处理多个客户端的请求。\\n\\n服务器可以分为不同类型，如文件服务器、数据库服务器、Web服务器、邮件服务器等，根据其提供的服务和功能而有所不同。服务器可以部署在本地数据中心、企业内部网络或云计算环境中，以满足不同的业务需求和应用场景。","kpCount":13,"name":"服务器","pCategoryId":1002,"termId":2248},"id":374,"link":"https://cloud.tencent.com/developer/techpedia/2248","sources":\[1,2\],"text":"服务器"},{"ext":{"categoryId":0,"categoryName":"","desc":"","kpCount":0,"name":"","pCategoryId":0,"termId":0},"id":96,"link":"https://cloud.tencent.com/product/ssl","sources":\[1\],"text":"SSL证书"},{"ext":{"categoryId":1020,"categoryName":"通用技术 - 云计算","desc":"私有云（Private Cloud）是一种基于云计算技术的云服务模式，由企业或组织自己搭建和管理，用于提供计算资源和服务。私有云通常是单租户的，即只有一个用户使用，用户可以在私有云上创建和管理虚拟机、存储、网络、安全等资源和服务，以满足自己的业务需求。","kpCount":3,"name":"私有云","pCategoryId":1002,"termId":1512},"id":2185,"link":"https://cloud.tencent.com/developer/techpedia/1512","sources":\[1,2\],"text":"私有云"},{"ext":{"categoryId":1030,"categoryName":"通用技术 - 安全","desc":"防火墙（Firewall）是一种网络安全设备，用于保护网络免受未经授权的访问和攻击。它通过监控和控制网络流量，筛选并阻止非法或不必要的访问，从而保护网络的安全性和完整性。防火墙可以根据预定的规则和策略，过滤入站和出站数据包，防止未经授权的访问和攻击者的入侵。防火墙可以是硬件设备、软件程序或两者的组合，通常安装在网络中的边界处，如路由器、交换机、服务器等。","kpCount":10,"name":"防火墙","pCategoryId":1002,"termId":1671},"id":3398,"link":"https://cloud.tencent.com/developer/techpedia/1671","sources":\[1,2\],"text":"防火墙"},{"ext":{"categoryId":0,"categoryName":"","desc":"","kpCount":0,"name":"","pCategoryId":0,"termId":0},"id":810,"link":"https://cloud.tencent.com/product/eip","sources":\[1\],"text":"公网IP"},{"ext":{"categoryId":0,"categoryName":"","desc":"","kpCount":0,"name":"","pCategoryId":0,"termId":0},"id":1565,"link":"https://cloud.tencent.com/product/domain","sources":\[1\],"text":"域名"},{"ext":{"categoryId":1031,"categoryName":"通用技术 - 网络与通信","desc":"路由是指在计算机网络中，将数据包从源节点传输到目标节点的过程。在互联网中，路由是指在多个网络之间传递数据包的过程。","kpCount":6,"name":"路由","pCategoryId":1002,"termId":1612},"id":3350,"link":"https://cloud.tencent.com/developer/techpedia/1612","sources":\[1,2\],"text":"路由"},{"ext":{"categoryId":1026,"categoryName":"通用技术 - 操作系统","desc":"Debian操作系统是一种自由开源的Linux操作系统，它是由全球志愿者组成的社区开发团队开发和维护的。它的目标是提供一个稳定、安全、可靠的操作系统，以及广泛的软件库，可以满足各种需求。","kpCount":11,"name":"Debian","pCategoryId":1002,"termId":1965},"id":3662,"link":"https://cloud.tencent.com/developer/techpedia/1965","sources":\[1,2\],"text":"Debian"},{"ext":{"categoryId":0,"categoryName":"","desc":"","kpCount":0,"name":"","pCategoryId":0,"termId":0},"id":14,"link":"https://cloud.tencent.com/product/cdn","sources":\[1\],"text":"CDN"}\]},"#url:\\"/api/tag/products\\",params:#tagIds:@18203,,objectType:1,objectId:2600529,,":\[{"adActivity":{"id":5762,"lightSpotLabel":"HOT","pageUrl":"https://cloud.tencent.com/act/pro/domain","priority":1,"startTime":"2023/12/13 17:13:15","title":"热销域名限时优惠，新客首年免费！\\n"},"cnName":"域名注册","desc":"","docURL":"https://cloud.tencent.com/document/product/242","hasActivity":false,"icon":"https://main.qcloudimg.com/image/product/2312/32\_32/blue.svg","introURL":"https://cloud.tencent.com/product/domain","name":"domain","productId":10422,"shortDesc":"提供域名注册、域名查询、域名购买到移动解析一站式满足超百万用户的整体需求","tagId":0},{"adActivity":{"id":5746,"lightSpotLabel":"HOT","pageUrl":"https://cloud.tencent.com/act/pro/video\_freetrial","priority":1,"startTime":"2023/12/12 18:27:50","title":"CDN免费试用\\n"},"cnName":"内容分发网络 CDN","desc":"内容分发网络（Content Delivery Network，CDN）通过将站点内容发布至遍布全球的海量加速节点，使其用户可就近获取所需内容，避免因网络拥堵、跨运营商、跨地域、跨境等因素带来的网络不稳定、访问延迟高等问题，有效提升下载速度、降低响应时间，提供流畅的用户体验。","docURL":"https://cloud.tencent.com/document/product/228","hasActivity":false,"icon":"https://main.qcloudimg.com/raw/9976b423c023ff3c87e3a8e4cad67807.svg","introURL":"https://cloud.tencent.com/product/cdn","name":"cdn","productId":10410,"shortDesc":"快速、稳定、智能、可靠的内容加速服务，支持图片、音视频等多元内容分发","tagId":0},{"adActivity":{"id":5738,"lightSpotLabel":"HOT","pageUrl":"https://cloud.tencent.com/act/pro/warmup-202606","priority":4,"startTime":"2023/12/12 17:58:46","title":"2026年中大促 | AI 领航 智绘未来"},"cnName":"弹性公网 IP","desc":"弹性公网 IP（Elastic IP，EIP）是可以独立购买和持有，且在某个地域下固定不变的公网 IP 地址，可以与 CVM、NAT 网关、弹性网卡和高可用虚拟 IP 等云资源绑定，提供访问公网和被公网访问能力；还可与云资源的生命周期解耦合，单独进行操作；同时提供多种计费模式，您可以根据业务特点灵活选择，以降低公网成本。","docURL":"https://cloud.tencent.com/document/product/1199","hasActivity":false,"icon":"https://main.qcloudimg.com/image/product/2394/32\_32/blue.svg","introURL":"https://cloud.tencent.com/product/eip","name":"eip","productId":11044,"shortDesc":"稳定、独立的公网 IP 资源，可灵活管理，满足您的网络通信需求","tagId":0},{"adActivity":{"id":5766,"lightSpotLabel":"HOT","pageUrl":"https://cloud.tencent.com/act/pro/dnsbigsales","priority":0,"startTime":"2023/12/13 18:31:40","title":"DNS解析新购特惠59元起，续费优惠低至5.3折！"},"cnName":"云解析 DNS","desc":"云解析 DNS 提供快速、稳定且高可用的 DNS 解析服务，支持智能解析、流量调度、安全防护。","docURL":"https://cloud.tencent.com/document/product/302","hasActivity":false,"icon":"https://main.qcloudimg.com/image/product/2162/32\_32/blue.svg","introURL":"https://cloud.tencent.com/product/dns","name":"dns","productId":11524,"shortDesc":"向全网域名提供稳定、安全、快速的智能解析服务","tagId":0},{"adActivity":{"id":5738,"lightSpotLabel":"HOT","pageUrl":"https://cloud.tencent.com/act/pro/warmup-202606","priority":4,"startTime":"2023/12/12 17:58:46","title":"2026年中大促 | AI 领航 智绘未来"},"cnName":"SSL 证书","desc":"腾讯云 SSL 证书（SSL Certificates）为您提供 SSL 证书的申请、管理、部署等服务，为您提供一站式 HTTPS 解决方案。","docURL":"https://cloud.tencent.com/document/product/400","hasActivity":false,"icon":"https://main.qcloudimg.com/image/product/2164/32\_32/blue.svg","introURL":"https://cloud.tencent.com/product/ssl","name":"ssl","productId":10427,"shortDesc":"数字证书一站式管理，快速接入 HTTPS 安全","tagId":0},{"adActivity":{"id":5738,"lightSpotLabel":"HOT","pageUrl":"https://cloud.tencent.com/act/pro/warmup-202606","priority":4,"startTime":"2023/12/12 17:58:46","title":"2026年中大促 | AI 领航 智绘未来"},"cnName":"DDoS 防护","desc":"DDoS 防护（Anti-DDoS）具有全面、高效、专业的 DDoS 防护能力，为企业组织提供 DDoS 高防包、DDoS 高防 IP 等多种 DDoS 解决方案，应对 DDoS 攻击问题。通过充足、优质的 DDoS 防护资源，结合持续进化的“自研+AI 智能识别”清洗算法，保障用户业务的稳定、安全运行。防护场景覆盖游戏、互联网、视频、金融、政府等行业。","docURL":"https://cloud.tencent.com/document/product/297","hasActivity":false,"icon":"https://main.qcloudimg.com/image/product/2075/32\_32/blue.svg","introURL":"https://cloud.tencent.com/product/ddos","name":"ddos","productId":11061,"shortDesc":"拥有可信赖的 DDoS 防护体系，可为不同行业提供多种安全解决方案","tagId":0}\]},"tdk":{"title":"星哥带你玩飞牛NAS-7：手把手教你免费内网穿透-Cloudflare tunnel-腾讯云开发者社区-腾讯云","keywords":"内网穿透,CloudflareTunnel,飞牛NAS,远程访问","description":"免费实现飞牛NAS内网穿透！使用Cloudflare Tunnel零成本搭建安全远程访问，无需公网IP。教程详解注册账号、创建隧道、配置域名全过程，支持HTTPS加密和多服务映射。实测网速2-3MB/s，适合NAS玩家解决外网访问难题。"},"meta":{"subject":"其他-空类-腾讯技术创作特训营S16","subjectTime":"2025-12-13 14:43:20","articleSource":"O","magicSource":"N","authorType":"G,O","productSlug":"domain,cdn,eip","authorUID":8492898},"link":{"canonical":"https://cloud.tencent.com/developer/article/2600529"},"cssName":\["Article","DraftMaster","Player","Katex"\],"rbConfigKeys":\["groupQRKeywords"\],"pvId":"-DZhtgEvOdZ4fyPNUPi7G","clientIp":"49.232.17.144","globalAnnounce":{"announceId":0},"rbConfig":{"groupQRKeywords":{"AI":{"keywords":\[\],"img":"https://qcloudimg.tencent-cloud.cn/raw/89b22f53dc3d4e0516d0a4f74ab01a30.png"}},"versionUpdateTipList":\[{"id":1008,"title":"一站式MCP教程库，解锁AI应用新玩法","description":"涵盖代码开发、场景应用、自动测试全流程，助你从零构建专属AI助手","start\_time":"2025/09/08 00:00:00","end\_time":"2025/10/08 23:59:59","url":"https://cloud.tencent.com/developer/special/mcp?from=28419\\u0026from\_column=28419"},{"id":1009,"title":"社区富文本\\u0026Markdown编辑器全新改版上线，欢迎大家体验!","description":"聚焦“写作效率、视觉美观与运行性能”三方面进行全面升级，为您提供更高效、稳定的创作环境","start\_time":"2025/11/17 00:00:00","end\_time":"2025/11/20 23:59:59","url":"https://cloud.tencent.com/developer/article/write?fromchannel=update\_notice"},{"id":1010,"title":"社区新版编辑器体验调研","description":"诚挚邀请您参与本次调研，分享您的真实使用感受与建议。您的反馈至关重要，感谢您的支持与参与！","start\_time":"2025/12/01 00:00:00","end\_time":"2025/12/05 23:59:59","url":"https://doc.weixin.qq.com/forms/AJEAIQdfAAoAVIAoAZxAL0CN9ODn0Xvaf?page=1"}\],"navList":\[{"text":"学习","menuList":\[{"iconName":"article","title":"文章","desc":"技术干货聚集地","href":"/developer/column?from=19154"},{"iconName":"ask","title":"问答","desc":"技术问题讨论区","href":"/developer/ask?from=19155"},{"iconName":"video","title":"视频","desc":"技术视频记录区","href":"/developer/video?from=19156"},{"iconName":"https://qccommunity.qcloudimg.com/icons/%E6%8A%80%E6%9C%AF%E5%AD%A6%E4%B9%A0.svg","title":"教程","desc":"技术学习实践区","href":"/developer/tutorial/practice"},{"iconName":"learn","title":"学习中心","desc":"一站式学习平台","href":"/developer/learning"},{"iconName":"lab","title":"腾讯云实验室","desc":"体验腾讯云产品功能","href":"/lab/labslist?from=20154\\u0026from\_column=20154\\u0026channel=c1004\\u0026sceneCode=dev"}\]},{"text":"活动","menuList":\[{"iconName":"living","title":"直播","desc":"技术大咖面对面","href":"/developer/salon?from=19161"},{"iconName":"competition","title":"竞赛","desc":"秀出你的技术影响力","href":"/developer/competition?from=19162"}\]},{"text":"专区","menuList":\[{"iconName":"https://qccommunity.qcloudimg.com/icons/demo-analyze.svg","title":"腾讯云代码分析专区","desc":"关注每行代码迭代","href":"/developer/zone/tencentcloudcodeanalysis"},{"iconName":"https://qccommunity.qcloudimg.com/icons/ioa.svg","title":"腾讯iOA零信任安全管理系统专区","desc":"腾讯自研自用的办公安全一体化平台","href":"/developer/zone/zerotrustsecuritymanagement"},{"iconName":"https://qccommunity.qcloudimg.com/icons/tm-zone.svg","title":"腾讯云架构师技术同盟交流圈","desc":"架构行家智汇，海量一线案例","href":"/developer/zone/tm"},{"iconName":"https://qcloudimg.tencent-cloud.cn/raw/1deae15bfe2dcdd1036f601852df7dd2.svg","title":"腾讯云数据库专区","desc":"数据智能管理专家","href":"/developer/zone/tencentdb"},{"iconName":"https://qccommunity.qcloudimg.com/icons/cloud\_assistant.svg","title":"腾讯云智能顾问专区","desc":"实现便捷、灵活的一站式云上治理","href":"/developer/zone/tencentcloudsmartadvisor"},{"iconName":"cloudnative","title":"腾讯云原生专区","desc":"助力业务降本增效","href":"/developer/zone/cloudnative?from=19164"},{"iconName":"https://qccommunity.qcloudimg.com/icons/tencenthunyuan.svg","title":"腾讯混元专区","desc":"具备强大的中文创作、逻辑推理、任务执行能力","href":"/developer/zone/tencenthunyuan"},{"iconName":"https://qcloudimg.tencent-cloud.cn/raw/1d60f881ef280ea992e2e4b6490d974b.svg","title":"腾讯云TCE专区","desc":"私有化云解决方案","href":"/developer/zone/tce"},{"iconName":"https://qccommunity.qcloudimg.com/community/image/lighthouse.svg","title":"腾讯云Lighthouse专区","desc":"新一代开箱即用、面向轻量应用场景的云服务器","href":"/developer/zone/lighthouse"},{"iconName":"https://qccommunity.qcloudimg.com/community/image/HAi.svg","title":"腾讯云HAI专区","desc":"提供即插即用的高性能云服务","href":"/developer/zone/hai"},{"iconName":"https://cloudcache.tencent-cloud.com/qcloud/ui/static/static\_source\_business/b3e1b483-be77-4e08-827f-ef0e5cda26cf.svg","title":"腾讯云Edgeone专区","desc":"下一代CDN—EdgeOne，不止加速","href":"/developer/zone/tencentcloudedgeone"},{"iconName":"https://qccommunity.qcloudimg.com/community/image/cos.svg","title":"腾讯云存储专区","desc":"安全稳定的海量分布式存储服务","href":"/developer/zone/cos"},{"iconName":"https://qccommunity.qcloudimg.com/community/image/ai.svg","title":"腾讯云智能专区","desc":"数实融合，云上智能","href":"/developer/zone/ai"},{"iconName":"https://qccommunity.qcloudimg.com/community/image/ipass.svg","title":"腾讯轻联专区 ","desc":"新一代应用与数据集成平台","href":"/developer/zone/ipaas"},{"iconName":"https://qccommunity.qcloudimg.com/image/cloudbase.svg","title":"腾讯云开发专区","desc":"云原生一体化开发平台","href":"/developer/zone/tencentcloudbase"},{"iconName":"https://qccommunity.qcloudimg.com/image/TAPD.svg","title":"TAPD专区","desc":"让协作更敏捷","href":"/developer/zone/tapd"},{"iconName":"https://qccommunity.qcloudimg.com/icons/game.svg","title":"腾讯轻量云游戏服专区","desc":"一键开服，畅快开玩，稳定可靠的游戏服务器","href":"/developer/zone/lightgame"},{"iconName":"https://cloudcache.tencent-cloud.com/qcloud/ui/static/static\_source\_business/b3e1b483-be77-4e08-827f-ef0e5cda26cf.svg","title":"EdgeOne AI 安全实战专区","desc":"免费开启安全防护","href":"/developer/zone/edgeoneaisecurity"}\]},{"text":"圈层","menuList":\[{"iconName":"https://qccommunity.qcloudimg.com/community/image/sphereExpert.svg","title":"腾讯云最具价值专家","desc":"汇聚行业顶级技术专家，用科技影响世界","href":"/tvp"},{"iconName":"https://qccommunity.qcloudimg.com/community/image/sphereAlliance.svg","title":"腾讯云架构师技术同盟","desc":"同盟共创，关注每位架构师成长","href":"/developer/program/tm"},{"iconName":"https://qccommunity.qcloudimg.com/community/image/sphereStar.svg","title":"腾讯云创作之星","desc":"做知识摆渡人，共造技术普惠加速度","href":"/developer/program/tci"},{"iconName":"https://qccommunity.qcloudimg.com/community/image/spherePioneer.svg","title":"腾讯云开发者先锋","desc":"聚技术先锋之力，携开发者共拓产品新界","href":"/developer/program/tdp"}\]},{"text":"工具","menuList":\[{"iconName":"https://qccommunity.qcloudimg.com/icons/ai-assistant.svg","title":"腾讯云代码助手","desc":"辅助编码工具，使研发提效增质","href":"/product/acc?from=22178"},{"iconName":"https://qccommunity.qcloudimg.com/icons/CNB.svg","title":"云原生构建","desc":"帮助开发者以更酷的方式构建软件","href":"/product/cnb?Is=sdk-topnav"},{"iconName":"https://qccommunity.qcloudimg.com/image/TAPD.svg","title":"TAPD 敏捷项目管理","desc":"让协作更敏捷","href":"/product/tapd?Is=sdk-topnav"},{"iconName":"studio","title":"Cloud Studio","desc":"随时随地在线协作开发","href":"https://cloudstudio.net/"},{"iconName":"sdk","title":"SDK中心","desc":"开发者语言与SDK","href":"/document/sdk?from=20154\\u0026from\_column=20154"},{"iconName":"api","title":"API中心","desc":"API 助力快捷使用云产品","href":"/document/api?from=20154\\u0026from\_column=20154"},{"iconName":"tool","title":"命令行工具","desc":"可快速调用管理云资源","href":"/document/product/440/6176?from=20154\\u0026from\_column=20154"}\]}\],"activity-popup":{"mImgUrl":"https://qccommunity.qcloudimg.com/mp/images/11-11mobile.jpg","imgUrl":"https://qccommunity.qcloudimg.com/mp/images/11-11pc.jpg","beginTime":"2024/10/24 00:00:00","endTime":"2024/10/31 23:59:59"},"header-advertisement":{"imageUrl":"https://qccommunity.qcloudimg.com/image/2024-11-01-18-15.png","link":"https://cloud.tencent.com/act/pro/double11-2024?from=22374\\u0026from\_column=22374#miaosha"}},"session":{"isLogined":false,"isQCloudLogined":false,"isQCommunityLogined":false,"isDifferentUin":false,"editMode":"rich"}}},"page":"/article/\[articleId\]","query":{"articleId":"2600529"},"buildId":"okEiaj8-fh7uI1IdIRHlo","assetPrefix":"https://qccommunity.qcloudimg.com/community","isFallback":false,"gssp":true,"appGip":true,"scriptLoader":\[\]}

  

本文转自 [https://cloud.tencent.com/developer/article/2600529](https://cloud.tencent.com/developer/article/2600529)，如有侵权，请联系删除。