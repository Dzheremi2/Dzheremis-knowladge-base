#### Vivaldi Browser Intructions

You can install Vivaldi browser from [[FlatHub]]/[From their own site](https://vivaldi.com/download/)/From your distro repository, if it exists in these repo **OR** you can install it with my [fast install script](https://github.com/Dzheremi2/linux) for **Fedora**.

##### You can either use manually installation method by importing vivaldi's repo file for specific directory

> [!IMPRT] These method is for Fedora only!
> 
> ```shell
> sudo chown $USER vivaldi.repo
> sudo cp vivaldi.repo /etc/yum.repos.d/
> sudo dnf update
> 
> sudo dnf install vivaldi-stable
> ```

>[!INFO] Content of vivaldi.repo file
>```
>[vivaldi]
name=vivaldi
baseurl=https://repo.vivaldi.com/archive/rpm/x86_64
enabled=1
gpgcheck=1
gpgkey=https://repo.vivaldi.com/archive/linux_signing_key.pub
>```

### E.T.C
[[Fix GUI lag in Vivaldi caused by llvm-libs package]]