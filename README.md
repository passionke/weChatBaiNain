# weChatBaiNian
weChatBaiNain

```python
# -*- coding: utf-8 -*-

from wxpy import *
import time

# 初始化机器人，扫码登陆
bot = Bot()

group = bot.friends()

visitGroup = open("v.log").readlines()

vg = []
for v in visitGroup:
    vg.append(v.strip())

for frend in group:
    reMarkName = frend.raw['RemarkName']
    if reMarkName.strip() != '':
        print(frend.raw)
        if (reMarkName in vg):
            print("已经发送消息，跳过")
        else:
            try:
                time.sleep(5)
                frend.send("hi " + reMarkName + " 平时联系少，千万不要恼。各有各的事，推也推不了。如今狗年到，忙碌要丢掉。心情要美妙，快乐自己找。轻松又逍遥，愿你过得好！xxx 祝你狗年快乐，旺旺旺")
                f = open('v.log','a')
                f.write(reMarkName+"\n")
                f.close()
                time.sleep(5)
                frend.send_image('keji.jpeg')
            except Exception:
                print("opps")
```

## 使用说明


- 本机有python3环境
- 安装依赖 wxpy

python3 weChatBaiNian.py

## 原理

- 依赖微信中大家使用的备注的功能，只要备注正确，就可以循环的向所有的朋友发送祝福语。


