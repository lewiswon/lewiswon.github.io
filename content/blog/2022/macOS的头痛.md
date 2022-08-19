+++
title = "macOS的头痛问题"
date = 2022-08-19
+++

## 0x00 
我的电脑不算是配置低, i7 处理器，32GB 内存，但是自从更新 macOS Ventura 之后，卡的生活不能自理，idea 写代码的时候，恨不的一个字母一个字母的往出来崩，虽然说是 beta 系统吧，但是也严重怀疑是不是厨子按下了桌子下面的按钮，要彻底抛弃我们这些 intel chip 了。

## 0x01 powerd cpu 异常的高

就算是不使用,刚开机，风扇也是狂转，抽风一样，一看活动监视器，powerd，cpu 的 usage 就是 100多。

```bash
# 列出 powerd 的计划任务
pmset -g sched
# 关闭 powerd 的计划任务
sudo pmset schedule cancelall
```