# 短信转发 随身wifi
基于https://gitee.com/jiu-xiao/ufi-message魔改而来

# 功能
- 定时转发
- 多渠道通知
- 超小占用
- 稳定运行

# 依赖
- Python3
- requests
- cron

# 开始设置


## 设置notify文件
在通知服务下输入相关的token来支持推送。更多请百度搜索 实例‘青龙 微信通知’  #本文件基于青龙面板notify魔改



## 设置cron定时

```
#编辑root用户的cron任务
crontab -u root -e
```
填入一下内容
```
#每5分钟进行一次同步并在结束后清空短信
*/5  * * * * sh /root/msg.py forward && sh /root/msg.py clean
```

## 记录LOG
在notify的目录下 'log' 文件
