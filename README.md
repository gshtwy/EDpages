# edgetunnel
这是一个基于 CF Worker 平台的脚本，在原版的基础上修改了显示 VLESS 配置信息转换为订阅内容。使用该脚本，你可以方便地将 VLESS 配置信息使用在线配置转换到 Clash 或 Singbox 等工具中。

- 基础部署视频教程：https://www.youtube.com/watch?v=LeT4jQUh8ok
- 快速部署视频教程：https://www.youtube.com/watch?v=59THrmJhmAw ***最佳推荐!!!***
- 进阶使用视频教程：https://www.youtube.com/watch?v=s91zjpw3-P8

Telegram交流群：[@CMLiussss](https://t.me/CMLiussss)，**感谢[Alice Networks](https://alicenetworks.net/)提供的云服务器维持[CM订阅转换服务](https://sub.fxxk.dedyn.io/)！**

# 免责声明

本免责声明适用于 GitHub 上的 “edgetunnel” 项目（以下简称“该项目”），项目链接为：https://github.com/cmliu/edgetunnel

### 用途
该项目被设计和开发仅供学习、研究和安全测试目的。它旨在为安全研究者、学术界人士和技术爱好者提供一个了解和实践网络通信技术的工具。

### 合法性
使用者在下载和使用该项目时，必须遵守当地法律和规定。使用者有责任确保他们的行为符合其所在地区的法律、规章以及其他适用的规定。

### 免责
1. 作为该项目的作者，我（以下简称“作者”）强调该项目应仅用于合法、道德和教育目的。
2. 作者不鼓励、不支持也不促进任何形式的非法使用该项目。如果发现该项目被用于非法或不道德的活动，作者将强烈谴责这种行为。
3. 作者对任何人或团体使用该项目进行的任何非法活动不承担责任。使用者使用该项目时产生的任何后果由使用者本人承担。
4. 作者不对使用该项目可能引起的任何直接或间接损害负责。
5. 通过使用该项目，使用者表示理解并同意本免责声明的所有条款。如果使用者不同意这些条款，应立即停止使用该项目。

作者保留随时更新本免责声明的权利，且不另行通知。最新的免责声明版本将会在该项目的 GitHub 页面上发布。

## 风险提示
- 通过提交虚假的节点配置给订阅服务，避免节点配置信息泄露。
- 另外，您也可以选择自行部署 [WorkerVless2sub 订阅生成服务](https://github.com/cmliu/WorkerVless2sub)，这样既可以利用订阅生成器的便利。
   
## Workers 部署方法 [视频教程](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=83s)
1. 部署 CF Worker：
   - 在 CF Worker 控制台中创建一个新的 Worker。
   - 将 [worker.js](https://github.com/cmliu/edgetunnel/blob/main/_worker.js) 的内容粘贴到 Worker 编辑器中。
   - 将第 7 行 `userID` 修改成你自己的 **UUID** 。

2. 访问订阅内容：
   - 访问 `https://[YOUR-WORKERS-URL]/[UUID]` 即可获取订阅内容。
   - 例如 `https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10` 就是你的通用自适应订阅地址。
   - 例如 `https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub` Base64订阅格式，适用PassWall,SSR+等。
   - 例如 `https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash` Clash订阅格式，适用OpenClash等。
   - 例如 `https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb` singbox订阅格式，适用singbox等。

3. 给 workers绑定 自定义域： 
   - 在 workers控制台的 `触发器`选项卡，下方点击 `添加自定义域`。
   - 填入你已转入 CF 域名解析服务的次级域名，例如:`vless.google.com`后 点击`添加自定义域`，等待证书生效即可。
   - **如果你是小白，你现在可以直接起飞，不用再往下看了！！！**

<details>
<summary><code><strong>「 我不是小白！我真的真的不是小白！我要玩花活！我要开启高端玩法！ 」</strong></code></summary>

4. 使用自己的`优选域名`/`优选IP`的订阅内容：
   - 如果你想使用自己的优选域名或者是自己的优选IP，可以参考 [WorkerVless2sub GitHub 仓库](https://github.com/cmliu/WorkerVless2sub) 中的部署说明自行搭建。
   - 打开 [worker.js](https://github.com/cmliu/edgetunnel/blob/main/_worker.js) 文件，在第 12 行找到 `sub` 变量，将其修改为你部署的订阅生成器地址。例如 `let sub = 'sub.cmliussss.workers.dev';`，注意不要带https等协议信息和符号。
   - 注意，如果您使用了自己的订阅地址，要求订阅生成器的 `sub`域名 和 `[YOUR-WORKER-URL]`的域名 不同属一个顶级域名，否则会出现异常。您可以在 `sub` 变量赋值为 workers.dev 分配到的域名。

</details>

## Pages 上传 部署方法 **最佳推荐!!!** [视频教程](https://www.youtube.com/watch?v=59THrmJhmAw)
1. 部署 CF Pages：
   - 下载 [worker.zip](https://raw.githubusercontent.com/cmliu/edgetunnel/main/worker.zip) 文件，并点上 Star !!!
   - 在 CF Pages 控制台中选择 `上传资产`后，为你的项目取名后点击 `创建项目`，然后上传你下载好的 [worker.zip](https://raw.githubusercontent.com/cmliu/edgetunnel/main/worker.zip) 文件后点击 `部署站点`。
   - 部署完成后点击 `继续处理站点` 后，选择 `设置` > `环境变量` > **制作**为生产环境定义变量 > `添加变量`。
     变量名称填写**UUID**，值则为你的UUID，后点击 `保存`即可。
   - 返回 `部署` 选项卡，在右下角点击 `创建新部署` 后，重新上传 [worker.zip](https://raw.githubusercontent.com/cmliu/edgetunnel/main/worker.zip) 文件后点击 `保存并部署` 即可。

2. 访问订阅内容：
   - 访问 `https://[YOUR-PAGES-URL]/[YOUR-UUID]` 即可获取订阅内容。
   - 例如 `https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10` 就是你的通用自适应订阅地址。
   - 例如 `https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub` Base64订阅格式，适用PassWall,SSR+等。
   - 例如 `https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash` Clash订阅格式，适用OpenClash等。
   - 例如 `https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb` singbox订阅格式，适用singbox等。

<details>
<summary><code><strong>「 我自己有域名！我要绑定自己的域名！我已经熟练的掌握域名解析！ 」</strong></code></summary>
   
3. 给 Pages绑定 CNAME自定义域：[视频教程](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=851s)
   - 在 Pages控制台的 `自定义域`选项卡，下方点击 `设置自定义域`。
   - 填入你的自定义次级域名，注意不要使用你的根域名，例如：
     您分配到的域名是 `fuck.cloudns.biz`，则添加自定义域填入 `lizi.fuck.cloudns.biz`即可；
   - 按照 CF 的要求将返回你的域名DNS服务商，添加 该自定义域 `lizi`的 CNAME记录 `edgetunnel.pages.dev` 后，点击 `激活域`即可。
   - **如果你是小白，那么你的 pages 绑定`自定义域`之后即可直接起飞，不用再往下看了！！！**
   - 
</details>
<details>
<summary><code><strong>「 我不是小白！我真的真的不是小白！我要玩花活！我要开启高端玩法！ 」</strong></code></summary>
   
4. 使用自己的`优选域名`/`优选IP`的订阅内容：
   - 如果你想使用自己的优选域名或者是自己的优选IP，可以参考 [WorkerVless2sub GitHub 仓库](https://github.com/cmliu/WorkerVless2sub) 中的部署说明自行搭建。
   - 在 Pages控制台的 `设置`选项卡，选择 `环境变量`> `制作`> `编辑变量`> `添加变量`；
   - 变量名设置为`SUB`，对应的值为你部署的订阅生成器地址。例如 `sub.cmliussss.workers.dev`，后点击 **保存**。
   - 之后在 Pages控制台的 `部署`选项卡，选择 `所有部署`> `最新部署最右的 ...`> `重试部署`，即可。
   - 注意，如果您使用了自己的订阅地址，要求订阅生成器的 `SUB`域名 和 `[YOUR-PAGES-URL]`的域名 不同属一个顶级域名，否则会出现异常。您可以在 `SUB` 变量赋值为 Pages.dev 分配到的域名。

</details>

## Pages GitHub 部署方法 [视频教程](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=560s)
1. 部署 CF Pages：
   - 在 Github 上先 Fork 本项目，并点上 Star !!!
   - 在 CF Pages 控制台中选择 `连接到 Git`后，选中 `edgetunnel`项目后点击 `开始设置`。
   - 在 `设置构建和部署`页面下方，选择 `环境变量（高级）`后并 `添加变量`
     变量名称填写**UUID**，值则为你的UUID，后点击 `保存并部署`即可。

2. 访问订阅内容：
   - 访问 `https://[YOUR-PAGES-URL]/[YOUR-UUID]` 即可获取订阅内容。
   - 例如 `https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10` 就是你的通用自适应订阅地址。
   - 例如 `https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub` Base64订阅格式，适用PassWall,SSR+等。
   - 例如 `https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash` Clash订阅格式，适用OpenClash等。
   - 例如 `https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb` singbox订阅格式，适用singbox等。

3. 给 Pages绑定 CNAME自定义域：[视频教程](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=851s)
   - 在 Pages控制台的 `自定义域`选项卡，下方点击 `设置自定义域`。
   - 填入你的自定义次级域名，注意不要使用你的根域名，例如：
     您分配到的域名是 `fuck.cloudns.biz`，则添加自定义域填入 `lizi.fuck.cloudns.biz`即可；
   - 按照 CF 的要求将返回你的域名DNS服务商，添加 该自定义域 `lizi`的 CNAME记录 `edgetunnel.pages.dev` 后，点击 `激活域`即可。
   - **如果你是小白，那么你的 pages 绑定`自定义域`之后即可直接起飞，不用再往下看了！！！**

<details>
<summary><code><strong>「 我不是小白！我真的真的不是小白！我要玩花活！我要开启高端玩法！ 」</strong></code></summary>

4. 使用自己的`优选域名`/`优选IP`的订阅内容：
   - 如果你想使用自己的优选域名或者是自己的优选IP，可以参考 [WorkerVless2sub GitHub 仓库](https://github.com/cmliu/WorkerVless2sub) 中的部署说明自行搭建。
   - 在 Pages控制台的 `设置`选项卡，选择 `环境变量`> `制作`> `编辑变量`> `添加变量`；
   - 变量名设置为`SUB`，对应的值为你部署的订阅生成器地址。例如 `sub.cmliussss.workers.dev`，后点击 **保存**。
   - 之后在 Pages控制台的 `部署`选项卡，选择 `所有部署`> `最新部署最右的 ...`> `重试部署`，即可。
   - 注意，如果您使用了自己的订阅地址，要求订阅生成器的 `SUB`域名 和 `[YOUR-PAGES-URL]`的域名 不同属一个顶级域名，否则会出现异常。您可以在 `SUB` 变量赋值为 Pages.dev 分配到的域名。

</details>

## 变量说明
| 变量名 | 示例 | 必填 | 备注 | YT |
|--------|---------|-|-----|-----|
| UUID | 90cd4a77-141a-43c9-991b-08263cfe9c10 |√| Powershell -NoExit -Command "[guid]::NewGuid()"| [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=72s) |
| PROXYIP | proxyip.fxxk.dedyn.io |×| 备选作为访问CFCDN站点的代理节点(支持多ProxyIP, ProxyIP之间使用`,`或 换行 作间隔) | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=166s) |
| SOCKS5  | user:password@127.0.0.1:1080 |×| 优先作为访问CFCDN站点的SOCKS5代理 | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=826s) |
| ADD | icook.tw:2053#官方优选域名 |×| 本地优选TLS域名/优选IP(支持多元素之间`,`或 换行 作间隔) ||
| ADDAPI | [https://raw.github.../addressesapi.txt](https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressesapi.txt) |×| 不解释, 懂得都懂 ||
| ADDNOTLS | icook.hk:8080#官方优选域名 |×| 本地优选noTLS域名/优选IP(支持多元素之间`,`或 换行 作间隔) ||
| ADDNOTLSAPI | [https://raw.github.../addressesapi.txt](https://raw.githubusercontent.com/cmliu/CFcdnVmess2sub/main/addressesapi.txt) |×| 不解释, 懂得都懂 ||
| ADDCSV | [https://raw.github.../addressescsv.csv](https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressescsv.csv) |×| 不解释, 懂得都懂 ||
| DLS | 8 |×| 不解释, 懂得都懂 ||
| TGTOKEN | 6894123456:XXXXXXXXXX0qExVsBPUhHDAbXXX |×| 发送TG通知的机器人token | 
| TGID | 6946912345 |×| 接收TG通知的账户数字ID | 
| SUB | VLESS.fxxk.dedyn.io | × | 内建域名、IP节点信息的订阅生成器地址 | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1193s) |
| SUBAPI | subapi.fxxk.dedyn.io |×| clash、singbox等 订阅转换后端 | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1446s) |
| SUBCONFIG | [https://raw.github.../ACL4SSR_Online_Full_MultiMode.ini](https://raw.githubusercontent.com/cmliu/ACL4SSR/main/Clash/config/ACL4SSR_Online_Full_MultiMode.ini) |×| clash、singbox等 订阅转换配置文件 | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1605s) |
| RPROXYIP | false |×| 设为 true 即可强制获取订阅器分配的ProxyIP(需订阅器支持)| [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1816s) |
| URL302 | https://t.me/CMLiussss |×| 主页302跳转(支持多url, url之间使用`,`或 换行 作间隔, 小白别用) |  |
| URL | https://t.me/CMLiussss |×| 主页伪装(支持多url, url之间使用`,`或 换行 作间隔, 乱设容易触发反诈) |  |
| CFEMAIL | admin@gmail.com |×| CF账户邮箱(与`CFKEY`都填上后, 订阅信息将显示请求使用量, 小白别用) |  |
| CFKEY | c6a944b5c956b6c18c2352880952bced8b85e |×| CF账户Global API Key(与`CFEMAIL`都填上后, 订阅信息将显示请求使用量, 小白别用) |  |

**注意: 填入`SOCKS5`后将不再启用`PROXYIP`！请二选一使用！！！**

**注意: 填入`SUB`后将不再启用`ADD*`类变量生成的订阅内容！请二选一使用！！！**

**注意: 同时填入`CFEMAIL`和`CFKEY`才会启用显示请求使用量，但是不推荐使用！没必要给一个Worker项目这么高的权限！后果自负！！！**

## 实用小技巧

**该项目部署的节点可通过节点PATH(路径)的方式，使用指定的`PROXYIP`或`SOCKS5`!!!**

- 指定 `PROXYIP` 案例
   ```url
   /proxyip=proxyip.fxxk.dedyn.io
   /?proxyip=proxyip.fxxk.dedyn.io
   /proxyip.fxxk.dedyn.io (仅限于域名开头为'proxyip.'的域名)
   ```

- 指定 `SOCKS5` 案例
   ```url
   /socks5=user:password@127.0.0.1:1080
   /?socks5=user:password@127.0.0.1:1080
   /socks://dXNlcjpwYXNzd29yZA==@127.0.0.1:1080
   /socks5://user:password@127.0.0.1:1080
   ```


## Star 星星走起
[![Stargazers over time](https://starchart.cc/cmliu/edgetunnel.svg?variant=adaptive)](https://starchart.cc/cmliu/edgetunnel)

## 已适配自适应订阅内容
   - [v2rayN](https://github.com/2dust/v2rayN)
   - clash.meta（[clash-verge-rev
](https://github.com/clash-verge-rev/clash-verge-rev)，[Clash Nyanpasu](https://github.com/keiko233/clash-nyanpasu)，~[clash-verge](https://github.com/zzzgydi/clash-verge/tree/main)~，ClashX Meta）
   - sing-box（SFI）



# 感谢
[zizifn](https://github.com/zizifn/edgetunnel)、[3Kmfi6HP](https://github.com/3Kmfi6HP/EDtunnel)、[Stanley-baby](https://github.com/Stanley-baby)、[ACL4SSR](https://github.com/ACL4SSR/ACL4SSR/tree/master/Clash/config)、[SHIJS1999](https://github.com/SHIJS1999/cloudflare-worker-vless-ip)、<a href="https://alicenetworks.net/"><img src="https://alicenetworks.net/templates/lagom2/assets/img/logo/logo_big.194980063.png" width="150" height="75" alt="Alice Networks LTD"/></a>，
