! 此页面即将重写！

## 安装
* 本项目基于 [Nonebot](https://nonebot.cqp.moe/)，因此在尝试运行本项目之前，请先了解 Nonebot 的使用。
* 本项目部分功能需要梯子，最好让本项目在国外的服务器上运行。
* 本项目对python新手及其友好，初学者能看懂此源码的40%甚至全部。

```
# 克隆代码
git clone https://github.com/Kyomotoi/ATRI.git

# 安装依赖
pip install -r requirements.txt

# 运行
python run.py (这里需求python版本为3.7.x，请勿使用3.8运行本项目)
```


### 配置
第一次运行，请打开`AyaBot/config.py`并修改其配置:

```python
#配置监听的 IP 和端口(本地)
HOST = '127.0.0.1'
PORT = 8080

#咱的主人(QQ号)
SUPERUSERS = {}

#机器人赋名，替代@
NICKNAME = {}

#自定义命令开头
COMMAND_START = {}

#推送屏蔽群名单
bangroup = []

#LOLICONAPI url:https://api.lolicon.app/#/setu <<api申请网址
LOLICONAPI = ""

#腾讯ai url:https://ai.qq.com/ <<apikey申请网址
TX_APP_ID = ""
TX_APPKEY = ""
```


### 关于开源
![](https://www.gnu.org/graphics/gplv3-88x31.png)
本项目使用 [GPLv3](https://github.com/Kyomotoi/Aya/blob/master/LICENSE) 开源协议，这意味着你可以使用本项目运行你的机器人，并向你的用户提供服务，但如果你需要对项目的源码进行修改，则必须将你修改后的版本对你的用户开源。

由于本项目的特殊性，本项目的源码中出现在 NoneBot 文档的部分（例如作为其示例代码），不使用 AGPLv3 许可，而使用和 NoneBot 一样的 MIT 许可。



RCNB！
