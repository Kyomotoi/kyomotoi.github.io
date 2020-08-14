## ATRI | アトリ 部署教程
此Bot的框架为 Mirai/OPQBot，启动界面均为Shell，并不存在UI一说。在此推荐Bot的运行环境为 Linux，如果你想用Windows也行。

OPQBot 的部署教程日后更新

Stp.1 
  请安装以下必要软件/工具：
    - Python3.8: <https://www.python.org/downloads/>
    - Mirai download: （本库文件夹内带Mirai一键包，根据你的系统打开即可）
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
  
  对于 Python3.8 安装：
  
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
      - python -V
    
    如提示关键词中带`Python3.8.x`字样，则说明安装成功，输入`exit()`以回到 Shell 界面。
  
