---
title: 如何安裝「新酷音輸入法」
nav_order: 3101
has_children: false
parent: fcitx5
grand_parent: 輸入法
---


# 如何安裝「新酷音輸入法」




## 主題

* [微調腳本](#微調腳本)
* [指令安裝](#指令安裝)
* [Environment Variables](#environment-variables)
* [加入輸入法](#加入輸入法)
* [備註](#備註)




## 微調腳本

| 微調腳本 | 中文輸入法 |
| -------- | ---------- |
| [fcitx5-chewing 安裝設定腳本](https://github.com/samwhelp/cachyos-adjustment/tree/main/prototype/main/im-config/fcitx5/fcitx5-chewing) | 新酷音輸入法 |




## 指令安裝

執行下面指令，安裝「fcitx5」和「fcitx5-chewing」。

``` sh
sudo pacman -Sy --needed fcitx5 fcitx5-chewing
```

執行下面指令，確保安裝支援「GTK」和「QT」環境所需要的「Package」。

``` sh
sudo pacman -Sy --needed fcitx5-gtk fcitx5-qt
```

執行下面指令，安裝「圖形設定介面」的「輔助工具」。

``` sh
sudo pacman -Sy --needed fcitx5-configtool
```

> 可以參考我的「[package-list.txt](https://github.com/samwhelp/cachyos-adjustment/blob/main/prototype/main/im-config/fcitx5/fcitx5-chewing/package-list.txt)」。


## Arch Package Group

| Arch Package Group |
| --- |
| [fcitx5-im](https://archlinux.org/groups/x86_64/fcitx5-im/) |


## Arch Package

| Arch Package |
| --- |
| [fcitx5](https://archlinux.org/packages/extra/x86_64/fcitx5/) |
| [fcitx5-configtool](https://archlinux.org/packages/extra/x86_64/fcitx5-configtool/) |
| [fcitx5-gtk](https://archlinux.org/packages/extra/x86_64/fcitx5-gtk/) |
| [fcitx5-qt](https://archlinux.org/packages/extra/x86_64/fcitx5-qt/) |
| [fcitx5-chewing](https://archlinux.org/packages/extra/x86_64/fcitx5-chewing/) |


> 上面的安裝指令，可以合併在一起如下

``` sh
sudo pacman -Sy --needed \
	fcitx5 \
	fcitx5-chewing \
	fcitx5-gtk \
	fcitx5-qt \
	fcitx5-configtool

```




### Environment Variables

* [Fcitx5](https://wiki.archlinuxcn.org/zh-tw/Fcitx5)

| Config File Path |
| --- |
| /etc/environment |

``` sh
GTK_IM_MODULE=fcitx
QT_IM_MODULE=fcitx
XMODIFIERS=@im=fcitx
SDL_IM_MODULE=fcitx
INPUT_METHOD=fcitx
GLFW_IM_MODULE=ibus
```

or

| Config File Path |
| --- |
| [/etc/profile.d/input-method.sh](./asset/overlay/etc/profile.d/input-method.sh) |

``` sh
export GTK_IM_MODULE=fcitx
export QT_IM_MODULE=fcitx
export XMODIFIERS=@im=fcitx
export SDL_IM_MODULE=fcitx
export INPUT_METHOD=fcitx
export GLFW_IM_MODULE=ibus
```


> 重新登出，然後登入，就會生效。




## 加入輸入法

透過「圖形操作介面程式(`fcitx5-configtool`)」，

加入「新酷音輸入法(`fcitx5-chewing`)」這個「輸入法」。

這個設定會被儲存在「[~/.config/fcitx5/profile](https://github.com/samwhelp/cachyos-adjustment/blob/main/prototype/main/im-config/fcitx5/fcitx5-chewing/asset/overlay/etc/skel/.config/fcitx5/profile#L15-L19)」這個檔案。
