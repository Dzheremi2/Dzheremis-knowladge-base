#### https://github.com/jeffshee/gnome-ext-hanabi#troubleshooting

##### Installation

1. Clone the repo
>```
>git clone https://github.com/jeffshee/gnome-ext-hanabi.git`
>```

2. Run the installation script
>```
>cd gnome-ext-hanabi
>```
>```
>./run.sh install
>```

3. Restart the shell
4. Enable extension
>[!reqv]
>For enabling the extensions you need to install **Extension Manager** from **[[FlatHub]]**
>```
>flatpak install flathub com.mattjakeman.ExtensionManager
>```

5. Choose your video wallpaper inte the extension preferences window

##### Optimization

Hanabi extension can utilize ```calppersink``` from *[Clapper](https://github.com/Rafostar/clapper)* for the best performance if installed

>[!IMPRT] Important
>For this to work, Clapper must be installed **from the package manager and not from Flatpak/Snap**.
>>[!reqv]
>>```shell
>>sudo dnf install clapper
>>```
---
tags:
#customization 
---