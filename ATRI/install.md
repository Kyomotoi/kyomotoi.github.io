## ATRI | アトリ 部署教程
此Bot的框架为 Mirai/OPQBot，启动界面均为Shell，并不存在UI一说，请根据自己能力选择部署平台。

在此推荐Bot的运行环境为 Linux，服务器地区为大陆外，防止某些功能无法正常启用。

OPQBot 的部署教程日后更新

### Stp.1 
 请安装以下必要软件/工具：
  - Python3.8: <https://www.python.org/downloads/>
  - Git：<https://git-scm.com/download/win> （Linux用户无需安装）
  - Mirai download: （本库内带Mirai一键包，根据系统打开即可）
  - CQHTTPMirai: <https://github.com/yyuueexxiinngg/cqhttp-mirai/releases>
  - Bot本体: <https://github.com/Kyomotoi/ATRI>

 如您是 Windows 用户，推荐安装此开发工具：<https://code.visualstudio.com/>
  
 如您部署Bot所在的环境由于配置的限制，推荐使用这个（Notepad++）：<https://notepad-plus-plus.org/downloads/>

  VisualStudio Code 一些必装的模块：
  - Chinese
  - Python

 在Linux系统中，安装Python难免会遇到一些困难：
  - Python3.8 版本难以直接安装
  - pip 指向版本为 Python3.6
  - Python 中一些库，例如：dlib难以直接安装
  
 此教程中会专门针对这些困难作出教程，以帮助入门者成功部署本Bot。
  
 Windows 用户：
  - 请跳过此，直至`Stp.2`
  
 Linux 用户：
  - 请继续往下阅读
  
 **关于Python3.8安装在Linux上**
  
 以root用户或具有sudo访问权限的用户身份运行以下命令，以更新软件包列表并安装必备组件：
  - sudo apt update
  - sudo apt install software-properties-common
  
 将deadsnakes PPA添加到系统的来源列表中：
  - sudo add-apt-repository ppa:deadsnakes/ppa
  
 出现提示时，按Enter继续：
  ```
  The package sources are available at:
  https://github.com/deadsnakes/
  更多信息： https://launchpad.net/~deadsnakes/+archive/ubuntu/ppa
  按 [ENTER] 继续或 Ctrl-c 取消安装。
  ```
  
 启用存储库后，请使用以下命令安装Python 3.8：
  - sudo apt install python3.8
  
 通过键入以下命令验证安装是否成功：
  - python3.8 -V
  
 如提示关键词中带`Python3.8.x`字样，则说明安装成功，输入`exit()`以回到 Shell 界面。
  
 以为这样就完了？并不！请继续往下看！
  
  - 我摸了我摸了！请看此：<https://www.linuxidc.com/Linux/2019-12/161629.htm>
  
 至此，您已经成功安装并设 Python3.8 为您 Linux 默认的 Python 版本了。
  
 安装完后，别急！还有 pip 的默认指向版本需要修改，请继续往下看
  
  - 我又摸了...摸了！！请看此：<https://blog.csdn.net/yiyu3344/article/details/90102410>
  
### Stp.2
  **Windows 用户**
  
  打开新鲜出炉的 Git，并输入以下指令：
  - git clone https://github.com/Kyomotoi/ATRI
  
  静坐等候即可
  
  选择一个风水极好的文件夹，最好全英文，将 Git clone 下来的东西解压至此文件夹
  
  打开文件夹中的`Mirai/windows`，并双击运行`miraiOK_windows_amd64.exe`，等正常开启并需要您登陆QQ账号后，关掉，将所下载的`CQHTTPMirai`拖入生成的`plugins`中。再次开启，   待出现`成功加载插件`类似字样后，关掉，打开所生成的配置文件，将以下内容复制进`setting.yml`：
  ```
  # Debug日志输出选项
  debug: true
  # 要进行配置的QQ号 (Mirai支持多帐号登录, 故需要对每个帐号进行单独设置)
  '123456789':
    # HTTP 相关配置
    http:
      # 可选，是否启用HTTP API服务器, 默认为不启用, 此项开始与否跟postUrl无关
      enable: false
      # 可选，HTTP API服务器监听地址, 默认为0.0.0.0
      host: 127.0.0.1
      # 可选，HTTP API服务器监听端口, 5700
      port: 5700
      # 可选，访问口令, 默认为空, 即不设置Token
      accessToken: ""
      # 可选，事件及数据上报URL, 默认为空, 即不上报
      postUrl: ""
      # 可选，上报消息格式，string 为字符串格式，array 为数组格式, 默认为string
      postMessageFormat: string
      # 可选，上报数据签名密钥, 默认为空
      secret: ""
    # 可选，反向客户端服务
    ws_reverse:
      # 可选，是否启用反向客户端，默认不启用
      - enable: true
        # 上报消息格式，string 为字符串格式，array 为数组格式
        postMessageFormat: string
        # 反向Websocket主机
        reverseHost: 127.0.0.1
        # 反向Websocket端口
        reversePort: 8080
        # 访问口令, 默认为空, 即不设置Token
        accessToken: ""
        # 反向Websocket路径
        reversePath: /ws
        # 可选, 反向Websocket Api路径, 默认为reversePath
        reverseApiPath: /api
        # 可选, 反向Websocket Event路径, 默认为reversePath
        reverseEventPath: /event
        # 是否使用Universal客户端 默认为true
        useUniversal: true
        # 反向 WebSocket 客户端断线重连间隔，单位毫秒
        reconnectInterval: 3000
      - enable: false # 这里是第二个连接, 相当于CQHTTP分身版
        postMessageFormat: string
        reverseHost: 127.0.0.1
        reversePort: 9222
        reversePath: /ws
        useUniversal: false
        reconnectInterval: 3000
    # 可选，正向Websocket服务器
    ws:
      # 可选，是否启用正向Websocket服务器，默认不启用
      enable: false
      # 可选，上报消息格式，string 为字符串格式，array 为数组格式, 默认为string
      postMessageFormat: string
      # 可选，访问口令, 默认为空, 即不设置Token
      accessToken: ""
      # 监听主机
      wsHost: "127.0.0.1"
      # 监听端口
      wsPort: 8080
  ```
  请将开头的`123456789`改为您Bot的QQ号。
  
  打开Bot目录下的config：
  ```
  #配置监听的 IP 和 端口
  HOST = '127.0.0.1'
  PORT = 8080

  # 机器人的主人（QQ号）即 超级用户
  SUPERUSERS = [123456789]
  def MASTER():
      return 123456789

  # 机器人名称，替代 @ 和 命令开头
  NICKNAME = {'ATRI'}

  # 自定义命令开头
  COMMAND_START = {''}

  BANGROUP = []

  # API url:https://api.lolicon.app/#/setu
  def LOLICONAPI():
      return ""

  # API url:https://api-cn.faceplusplus.com/
  def FACE_KEY():
      return ""

  def FACE_SECRET():
      return ""
  ```
  以上信息请务必补充完毕！
  
  打开Cmd，cd进Bot根目录，键入以下内容：
  ```
  python -3.8 -m pip install -r requirements.txt
  python BOT.py
  ```
  同时启动MiraiOK
  
  当你的Shell界面出现以下内容：
  ```
  [2020-08-14 22:39:03,985] INFO in __init__: received event: meta_event.lifecycle.connect
  ```
  则说明Bot已成功部署！
  
  至此，您已经完成主要的部署步骤。
  
  **Linux用户**
  
  直接：鸽了，明天更
  
  
  





  
