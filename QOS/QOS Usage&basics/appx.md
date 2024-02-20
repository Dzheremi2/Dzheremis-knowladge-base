appx - default [QOS](QOS⚛️.md)'s package manager which is build-in to [QTK](QTK.md).
appx managing all system's packages and used in the system update process, by this reason, you cannot remove appx at all, you can remove only user-side `appx` utility, but you cannot do that for appxInstallD, appxRemoveD, appxUpdateD, appxSysUpdD, because these packages declared as impossible dependencies of [QTK](QTK.md) 

appx has appxHandler process running in [QRoot](QRoot.md) not [rootBIN](rootBIN.md) in background for determining if packages has available updates and automatically download them
>[!NOTE]
>If auto-updates disabled, this handler wouldn't be loaded

>[!EXAMPLE] appx default commands
>`appx instal <package_name>` → install a package
>`appx remove <package_name>` → remove a package
>`appx add-repo <repo_link>` → add new repo to repolist
>`appx clean <package>` → remove all package dependencies with package
>`appx sys-upd LTS` → update system to latest release
>`appx sys-upd <specified_version>` → update or downgrade system to specified version