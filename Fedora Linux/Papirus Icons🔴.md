### The fullest icon pack for Linux
![[Pasted image 20240120133813.png]]

>[!NOTE] Installing icon pack
>```shell
>sudo dnf install papirus-icon-theme
>```

>[!reqv]
>To change active icon pack you need to install ***gnome-tweaks*** with command
>```shell
>sudo dnf install gnome-tweaks
>```

---
#### Colored Folders
![[Pasted image 20240120133607.png]]

Papirus has icons for all default [$HOME](Change%20default%20$HOME%20directories.md) directories and another folders out of [$HOME](Change%20default%20$HOME%20directories.md)

>[!NOTE] **INSTALLATION OF papirus-folders**
>```shell
>wget -qO- https://git.io/papirus-folders-install | sh
>```

To apply these themes you need to execute some commands in Terminal

>[!NOTE] Changing folder colors
>```shell
>papirus-folders -C "theme" "icon-set"
>```

>[!NOTE] What style used right now
>```shell
>papirus-folders -l --theme "icon-set"
>```

>[!NOTE] Restore defaults
>```shell
>papirus-folders -D --theme "icon-set"
>```

##### Available folder styles sheet
![](Pasted%20image%2020240120134859.jpg)


