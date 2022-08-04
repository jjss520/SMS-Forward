# 短信转发 随身wifi
msg.py 基于 https://gitee.com/jiu-xiao/ufi-message 魔改而来
notify 基于 https://github.com/whyour/qinglong 魔改而来

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
在通知服务下输入相关的token来支持推送。更多请百度搜索 实例‘青龙 微信通知’

## 设置cron定时

```
#编辑cron任务
vi /etc/crontab
```
填入以下内容
```
#每5分钟进行一次同步并在结束后清空短信  python3后面为msg.py目录 forward 转发功能
*/5 * * * *   root    python3 /root/msg.py forward && python3 /root/msg.py clean
```
检查状态
```
service cron status
#查看执行状态和运行状态
```

## 记录LOG
在notify的目录下 'sms_log' 文件

# 错误ERROR

Cron: pam_unix (cron:session): session opened/closed for user root by (uid=0)

编辑 /etc/pam.d/common-session-noninteractive 在 session required pam_unix.so 上方添加```session [success=1 default=ignore] pam_succeed_if.so service in cron quiet use_uid``` 保存并重启服务 ```service cron restart```

