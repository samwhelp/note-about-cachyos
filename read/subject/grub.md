---
title: GRUB
nav_order: 3060
has_children: false
---


# GRUB


## 主題

* [如何更改GRUB佈景主題](#如何更改grub佈景主題)
* [完整腳本](#完整腳本)
* [下載安裝](#下載安裝)
* [設定採用](#設定採用)
* [相關筆記](#相關筆記)




## 如何更改GRUB佈景主題

> 以下以「[grub-theme-glass-remix](https://samwhelp.github.io/grub-theme-glass-remix/)」這個「GRUB 佈景主題」為例。




## 完整腳本

| 完整腳本 |
| --- |
| [grub-theme-glass-remix](https://github.com/samwhelp/cachyos-adjustment/tree/main/prototype/main/grub-config/grub-theme/grub-theme-glass-remix) |




## 下載安裝

``` sh

## 產生暫時資料夾
mkdir -p "./tmp"


## 下載
wget -c "https://github.com/samwhelp/grub-theme-glass-remix/archive/refs/heads/main.tar.gz" -O "./tmp/grub-theme-glass-remix-main.tar.gz"


## 解壓縮
tar xf "./tmp/grub-theme-glass-remix-main.tar.gz" -C "./tmp"


## 確保有「/boot/grub/themes」這個「資料夾」
sudo mkdir -p "/boot/grub/themes"


## 將剛剛解開的「佈景主題」，安裝到「/boot/grub/themes/grub-theme-glass-remix」這個路徑。
sudo cp -rf "./tmp/grub-theme-glass-remix-main/." "/boot/grub/themes/grub-theme-glass-remix"

```

> 以上的步驟，就已經將「GRUB 佈景主題」安裝完成了。

> 接著要執行「設定採用」的步驟。




## 設定採用

可以編輯「`/etc/default/grub`」這個檔案，內容如下

``` sh
GRUB_BACKGROUND='/boot/grub/themes/grub-theme-glass-remix/background.jpg'
GRUB_THEME='/boot/grub/themes/grub-theme-glass-remix/theme.txt'
```

或是產生「`/etc/default/grub.d/theme.cfg`」這個檔案, 執行

``` sh

## 確保有「/etc/default/grub.d」這個「資料夾」
sudo mkdir -p /etc/default/grub.d


## 產生「`/etc/default/grub.d/theme.cfg`」這個檔案
cat << EOF | sudo tee /etc/default/grub.d/theme.cfg
GRUB_BACKGROUND='/boot/grub/themes/grub-theme-glass-remix/background.jpg'
GRUB_THEME='/boot/grub/themes/grub-theme-glass-remix/theme.txt'

EOF

```

> 為何要同時設定「`GRUB_THEME`」和「`GRUB_BACKGROUND`」，請參考「[另一篇](https://samwhelp.github.io/note-about-grub/read/howto/use_background_image.html)」的說明。

> 接著上面的步驟完成後，一定要執行下面的步驟，

執行下面的指令，重新產生「`/boot/grub/grub.cfg`」這個檔案。

``` sh
sudo update-grub
```

若是沒有「`update-grub`」這個指令，可以改執行下面的指令

``` sh
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

接著重新開機，就可以看到效果了。




## 更多的佈景主題

> 其他更多的「[GRUB 佈景主題](https://samwhelp.github.io/note-about-grub/read/theme.html)」。




## 相關筆記

| Link | GitHub |
| ---- | ------ |
| [GRUB 探索筆記](https://samwhelp.github.io/note-about-grub/) | [GitHub](https://github.com/samwhelp/note-about-grub) |
