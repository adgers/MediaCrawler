> **免责声明：**
> 
> 大家请以学习为目的使用本仓库，爬虫违法违规的案件：https://github.com/HiddenStrawberry/Crawler_Illegal_Cases_In_China  <br>
>
>本仓库的所有内容仅供学习和参考之用，禁止用于商业用途。任何人或组织不得将本仓库的内容用于非法用途或侵犯他人合法权益。本仓库所涉及的爬虫技术仅用于学习和研究，不得用于对其他平台进行大规模爬虫或其他非法行为。对于因使用本仓库内容而引起的任何法律责任，本仓库不承担任何责任。使用本仓库的内容即表示您同意本免责声明的所有条款和条件。

> 点击查看更为详细的免责声明。[点击跳转](#disclaimer)
# 仓库描述

**小红书爬虫**，**抖音爬虫**， **快手爬虫**， **B站爬虫**， **微博爬虫**...。  
目前能抓取小红书、抖音、快手、B站、微博的视频、图片、评论、点赞、转发等信息。

原理：利用[playwright](https://playwright.dev/)搭桥，保留登录成功后的上下文浏览器环境，通过执行JS表达式获取一些加密参数
通过使用此方式，免去了复现核心加密JS代码，逆向难度大大降低


## 功能列表
> 下面不支持的项目，相关的代码架构已经搭建好，只需要实现对应的方法即可，欢迎大家提交PR


| 平台  | 关键词搜索 | 指定帖子ID爬取 | 二级评论 | 指定创作者主页 | 登录态缓存 | IP代理池 | 生成评论词云图 |
|-----|-------|----------|-----|--------|-------|-------|-------|
| 小红书 | ✅     | ✅        | ✅   | ✅      | ✅     | ✅     | ✅    |
| 抖音  | ✅     | ✅        | ✅    | ✅       | ✅     | ✅     | ✅    |
| 快手  | ✅     | ✅        | ✅   | ✅      | ✅     | ✅     | ✅    |
| B 站 | ✅     | ✅        | ✅   | ✅      | ✅     | ✅     | ✅    |
| 微博  | ✅     | ✅        | ❌   | ❌      | ✅     | ✅     | ✅    |


## 使用方法

### 创建并激活 python 虚拟环境
   ```shell   
   # 进入项目根目录
   cd MediaCrawler
   
   # 创建虚拟环境
   # 注意python 版本需要3.7 - 3.9 
   python -m venv venv
   
   # macos & linux 激活虚拟环境
   source venv/bin/activate

   # windows 激活虚拟环境
   venv\Scripts\activate

   ```

### 安装依赖库

   ```shell
   pip3 install -r requirements.txt
   ```

### 安装 playwright浏览器驱动

   ```shell
   playwright install
   ```

### 运行爬虫程序

   ```shell
   ### 项目默认是没有开启评论爬取模式，如需评论请在config/base_config.py中的 ENABLE_GET_COMMENTS 变量修改
   ### 一些其他支持项，也可以在config/base_config.py查看功能，写的有中文注释
   
   # 从配置文件中读取关键词搜索相关的帖子并爬取帖子信息与评论
   python main.py --platform xhs --lt qrcode --type search
   
   # 从配置文件中读取指定的帖子ID列表获取指定帖子的信息与评论信息
   python main.py --platform xhs --lt qrcode --type detail
  
   # 打开对应APP扫二维码登录
     
   # 其他平台爬虫使用示例，执行下面的命令查看
   python main.py --help    
   ```

### 数据保存
- 支持保存到关系型数据库（Mysql、PgSQL等）
    - 执行 `python db.py` 初始化数据库数据库表结构（只在首次执行）
- 支持保存到csv中（data/目录下）
- 支持保存到json中（data/目录下）


## 开发者服务
- 知识星球：沉淀高质量常见问题、最佳实践文档、多年编程+爬虫经验分享，提供付费知识星球服务，主动提问，作者会定期回答问题
  <p>
  <img alt="xingqiu" src="https://nm.zizhi1.com/static/img/8e1312d1f52f2e0ff436ea7196b4e27b.15555424244122T1.webp" style="width: auto;height: 400px" >
  <img alt="xingqiu_yhq" src="https://nm.zizhi1.com/static/img/c14da73f0dd9351e7169a36368d5037b.yhq.webp" style="width: auto;height: 400px" >
  </p>
  
  星球精选文章： 
  - [【独创】使用Playwright获取某音a_bogus参数流程（包含加密参数分析）](https://articles.zsxq.com/id_u89al50jk9x0.html)
  - [【独创】使用Playwright低成本获取某书X-s参数流程分析（当年的回忆录）](https://articles.zsxq.com/id_u4lcrvqakuc7.html)
  - [ MediaCrawler-基于抽象类设计重构项目缓存](https://articles.zsxq.com/id_4ju73oxewt9j.html)
  - [ 手把手带你撸一个自己的IP代理池](https://articles.zsxq.com/id_38fza371ladm.html)
  
  
  
- MediaCrawler视频课程：
  > 如果你想很快入门这个项目，或者想了具体实现原理，我推荐你看看这个视频课程，从设计出发一步步带你如何使用，门槛大大降低，同时也是对我开源的支持，如果你能支持我的课程，我将会非常开心～<br>
  > 课程售价非常非常的便宜，几杯咖啡的事儿.<br>
  > 课程介绍飞书文档链接：https://relakkes.feishu.cn/wiki/JUgBwdhIeiSbAwkFCLkciHdAnhh



## 感谢下列Sponsors对本仓库赞助
- 感谢 [JetBrains](https://www.jetbrains.com/?from=gaowei-space/markdown-blog) 对本项目的支持！
<a href="https://www.jetbrains.com/?from=NanmiCoder/MediaCrawler" target="_blank">
    <img src="https://resources.jetbrains.com/storage/products/company/brand/logos/jb_beam.png" width="100" height="100">
</a>
<br>
- <a href="https://sider.ai/ad-land-redirect?source=github&p1=mi&p2=kk">通过注册这个款免费的GPT助手，帮我获取GPT4额度作为支持。也是我每天在用的一款chrome AI助手插件</a>

成为赞助者，展示你的产品在这里，联系作者：relakkes@gmail.com



## MediaCrawler爬虫项目交流群：
> 7天有效期，自动更新, 如果人满了可以加作者wx拉进群: yzglan，备注来自github.

<div style="max-width: 200px">  
<p><img alt="11群二维码" src="static/images/11群二维码.JPG" style="width: 200px;height: 100%" ></p>
</div>


## 打赏
免费开源不易，如果项目帮到你了，可以给我打赏哦，您的支持就是我最大的动力！
<div style="display: flex;justify-content: space-between;width: 100%">
    <p><img alt="打赏-微信" src="static/images/wechat_pay.jpeg" style="width: 200px;height: 100%" ></p>
    <p><img alt="打赏-支付宝" src="static/images/zfb_pay.png"   style="width: 200px;height: 100%" ></p>
</div>

## 爬虫入门课程
我新开的爬虫教程Github仓库 [CrawlerTutorial](https://github.com/NanmiCoder/CrawlerTutorial) ，感兴趣的朋友可以关注一下，持续更新，主打一个免费.


## 运行报错常见问题Q&A
> 遇到问题先自行搜索解决下，现在AI很火，用ChatGPT大多情况下能解决你的问题 [免费的ChatGPT](https://sider.ai/ad-land-redirect?source=github&p1=mi&p2=kk)  

➡️➡️➡️ [常见问题](docs/常见问题.md)

抖音使用Playwright登录现在会出现滑块验证 + 短信验证，手动过一下


## 项目代码结构
➡️➡️➡️ [项目代码结构说明](docs/项目代码结构.md)

## 手机号登录说明
➡️➡️➡️ [手机号登录说明](docs/手机号登录说明.md)

## 项目贡献者
<!-- readme: contributors -start -->
<table>
	<tbody>
		<tr>
            <td align="center">
                <a href="https://github.com/NanmiCoder">
                    <img src="https://avatars.githubusercontent.com/u/47178017?v=4" width="100;" alt="NanmiCoder"/>
                    <br />
                    <sub><b>程序员阿江-Relakkes</b></sub>
                </a>
            </td>
            <td align="center">
                <a href="https://github.com/leantli">
                    <img src="https://avatars.githubusercontent.com/u/117699758?v=4" width="100;" alt="leantli"/>
                    <br />
                    <sub><b>leantli</b></sub>
                </a>
            </td>
            <td align="center">
                <a href="https://github.com/BaoZhuhan">
                    <img src="https://avatars.githubusercontent.com/u/140676370?v=4" width="100;" alt="BaoZhuhan"/>
                    <br />
                    <sub><b>Bao Zhuhan</b></sub>
                </a>
            </td>
            <td align="center">
                <a href="https://github.com/nelzomal">
                    <img src="https://avatars.githubusercontent.com/u/8512926?v=4" width="100;" alt="nelzomal"/>
                    <br />
                    <sub><b>zhounan</b></sub>
                </a>
            </td>
            <td align="center">
                <a href="https://github.com/Hiro-Lin">
                    <img src="https://avatars.githubusercontent.com/u/40111864?v=4" width="100;" alt="Hiro-Lin"/>
                    <br />
                    <sub><b>HIRO</b></sub>
                </a>
            </td>
            <td align="center">
                <a href="https://github.com/PeanutSplash">
                    <img src="https://avatars.githubusercontent.com/u/98582625?v=4" width="100;" alt="PeanutSplash"/>
                    <br />
                    <sub><b>PeanutSplash</b></sub>
                </a>
            </td>
		</tr>
		<tr>
            <td align="center">
                <a href="https://github.com/Ermeng98">
                    <img src="https://avatars.githubusercontent.com/u/55784769?v=4" width="100;" alt="Ermeng98"/>
                    <br />
                    <sub><b>Ermeng</b></sub>
                </a>
            </td>
            <td align="center">
                <a href="https://github.com/Rosyrain">
                    <img src="https://avatars.githubusercontent.com/u/116946548?v=4" width="100;" alt="Rosyrain"/>
                    <br />
                    <sub><b>Rosyrain</b></sub>
                </a>
            </td>
            <td align="center">
                <a href="https://github.com/henryhyn">
                    <img src="https://avatars.githubusercontent.com/u/5162443?v=4" width="100;" alt="henryhyn"/>
                    <br />
                    <sub><b>Henry He</b></sub>
                </a>
            </td>
            <td align="center">
                <a href="https://github.com/Akiqqqqqqq">
                    <img src="https://avatars.githubusercontent.com/u/51102894?v=4" width="100;" alt="Akiqqqqqqq"/>
                    <br />
                    <sub><b>leonardoqiuyu</b></sub>
                </a>
            </td>
            <td align="center">
                <a href="https://github.com/jayeeliu">
                    <img src="https://avatars.githubusercontent.com/u/77389?v=4" width="100;" alt="jayeeliu"/>
                    <br />
                    <sub><b>jayeeliu</b></sub>
                </a>
            </td>
            <td align="center">
                <a href="https://github.com/ZuWard">
                    <img src="https://avatars.githubusercontent.com/u/38209256?v=4" width="100;" alt="ZuWard"/>
                    <br />
                    <sub><b>ZuWard</b></sub>
                </a>
            </td>
		</tr>
		<tr>
            <td align="center">
                <a href="https://github.com/Zzendrix">
                    <img src="https://avatars.githubusercontent.com/u/154900254?v=4" width="100;" alt="Zzendrix"/>
                    <br />
                    <sub><b>Zendrix</b></sub>
                </a>
            </td>
            <td align="center">
                <a href="https://github.com/chunpat">
                    <img src="https://avatars.githubusercontent.com/u/19848304?v=4" width="100;" alt="chunpat"/>
                    <br />
                    <sub><b>zhangzhenpeng</b></sub>
                </a>
            </td>
            <td align="center">
                <a href="https://github.com/tanpenggood">
                    <img src="https://avatars.githubusercontent.com/u/37927946?v=4" width="100;" alt="tanpenggood"/>
                    <br />
                    <sub><b>Sam Tan</b></sub>
                </a>
            </td>
            <td align="center">
                <a href="https://github.com/xbsheng">
                    <img src="https://avatars.githubusercontent.com/u/56357338?v=4" width="100;" alt="xbsheng"/>
                    <br />
                    <sub><b>xbsheng</b></sub>
                </a>
            </td>
            <td align="center">
                <a href="https://github.com/yangrq1018">
                    <img src="https://avatars.githubusercontent.com/u/25074163?v=4" width="100;" alt="yangrq1018"/>
                    <br />
                    <sub><b>Martin</b></sub>
                </a>
            </td>
            <td align="center">
                <a href="https://github.com/zhihuiio">
                    <img src="https://avatars.githubusercontent.com/u/165655688?v=4" width="100;" alt="zhihuiio"/>
                    <br />
                    <sub><b>zhihuiio</b></sub>
                </a>
            </td>
		</tr>
		<tr>
            <td align="center">
                <a href="https://github.com/renaissancezyc">
                    <img src="https://avatars.githubusercontent.com/u/118403818?v=4" width="100;" alt="renaissancezyc"/>
                    <br />
                    <sub><b>Ren</b></sub>
                </a>
            </td>
            <td align="center">
                <a href="https://github.com/Tianci-King">
                    <img src="https://avatars.githubusercontent.com/u/109196852?v=4" width="100;" alt="Tianci-King"/>
                    <br />
                    <sub><b>Wang Tianci</b></sub>
                </a>
            </td>
            <td align="center">
                <a href="https://github.com/Styunlen">
                    <img src="https://avatars.githubusercontent.com/u/30810222?v=4" width="100;" alt="Styunlen"/>
                    <br />
                    <sub><b>Styunlen</b></sub>
                </a>
            </td>
            <td align="center">
                <a href="https://github.com/Schofi">
                    <img src="https://avatars.githubusercontent.com/u/33537727?v=4" width="100;" alt="Schofi"/>
                    <br />
                    <sub><b>Schofi</b></sub>
                </a>
            </td>
            <td align="center">
                <a href="https://github.com/Klu5ure">
                    <img src="https://avatars.githubusercontent.com/u/166240879?v=4" width="100;" alt="Klu5ure"/>
                    <br />
                    <sub><b>Klu5ure</b></sub>
                </a>
            </td>
            <td align="center">
                <a href="https://github.com/keeper-jie">
                    <img src="https://avatars.githubusercontent.com/u/33612777?v=4" width="100;" alt="keeper-jie"/>
                    <br />
                    <sub><b>Kermit</b></sub>
                </a>
            </td>
		</tr>
		<tr>
            <td align="center">
                <a href="https://github.com/kexinoh">
                    <img src="https://avatars.githubusercontent.com/u/91727108?v=4" width="100;" alt="kexinoh"/>
                    <br />
                    <sub><b>KEXNA</b></sub>
                </a>
            </td>
            <td align="center">
                <a href="https://github.com/aa65535">
                    <img src="https://avatars.githubusercontent.com/u/5417786?v=4" width="100;" alt="aa65535"/>
                    <br />
                    <sub><b>Jian Chang</b></sub>
                </a>
            </td>
            <td align="center">
                <a href="https://github.com/522109452">
                    <img src="https://avatars.githubusercontent.com/u/16929874?v=4" width="100;" alt="522109452"/>
                    <br />
                    <sub><b>tianqing</b></sub>
                </a>
            </td>
		</tr>
	<tbody>
</table>
<!-- readme: contributors -end -->

## star 趋势图
- 如果该项目对你有帮助，star一下 ❤️❤️❤️

[![Star History Chart](https://api.star-history.com/svg?repos=NanmiCoder/MediaCrawler&type=Date)](https://star-history.com/#NanmiCoder/MediaCrawler&Date)




## 参考

- xhs客户端 [ReaJason的xhs仓库](https://github.com/ReaJason/xhs)
- 短信转发 [参考仓库](https://github.com/pppscn/SmsForwarder)
- 内网穿透工具 [ngrok](https://ngrok.com/docs/)



## 免责声明
<div id="disclaimer"> 

### 1. 项目目的与性质
本项目（以下简称“本项目”）是作为一个技术研究与学习工具而创建的，旨在探索和学习网络数据采集技术。本项目专注于自媒体平台的数据爬取技术研究，旨在提供给学习者和研究者作为技术交流之用。

### 2. 法律合规性声明
本项目开发者（以下简称“开发者”）郑重提醒用户在下载、安装和使用本项目时，严格遵守中华人民共和国相关法律法规，包括但不限于《中华人民共和国网络安全法》、《中华人民共和国反间谍法》等所有适用的国家法律和政策。用户应自行承担一切因使用本项目而可能引起的法律责任。

### 3. 使用目的限制
本项目严禁用于任何非法目的或非学习、非研究的商业行为。本项目不得用于任何形式的非法侵入他人计算机系统，不得用于任何侵犯他人知识产权或其他合法权益的行为。用户应保证其使用本项目的目的纯属个人学习和技术研究，不得用于任何形式的非法活动。

### 4. 免责声明
开发者已尽最大努力确保本项目的正当性及安全性，但不对用户使用本项目可能引起的任何形式的直接或间接损失承担责任。包括但不限于由于使用本项目而导致的任何数据丢失、设备损坏、法律诉讼等。

### 5. 知识产权声明
本项目的知识产权归开发者所有。本项目受到著作权法和国际著作权条约以及其他知识产权法律和条约的保护。用户在遵守本声明及相关法律法规的前提下，可以下载和使用本项目。

### 6. 最终解释权
关于本项目的最终解释权归开发者所有。开发者保留随时更改或更新本免责声明的权利，恕不另行通知。
</div>





