---
title: 改变 Mac Launchpad 图标的大小
date: 2020-02-24 22:06:41
categories:
 - Mac
tags:
 - Mac
---

**记录重置 Mac Launchpad 的命令**
##### 行数
```
# 修改
defaults write com.apple.dock springboard-rows -int 6
# 恢复
defaults write com.apple.dock springboard-rows Default
```
<!--more-->

##### 列数
```
# 修改
defaults write com.apple.dock springboard-columns -int 8
# 恢复
defaults write com.apple.dock springboard-columns Default   
```

---
##### 重启Dock
```bash
killall Dock  
```