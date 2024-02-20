BApp - is an alternative [package](Packages.md) manager for [QOS](QOS⚛️.md). Its designed for providing better experience of installing custom packages which is not presented in default QOS's package manager  `appx`

BApp is declared as "Build App"

## BApp repositories
1. [GitHub](https://github.com)
2. BApp Trusted Repo
3. AlloidRepo
4. AllTheAppsRepo

>[!INFO] GitHub
>BApp can install packages from [GitHub](https://github.com). It uses specific algorithm that can parse all of github repos and automatically determine repos with QOS-compatible software and automatically generate compilation instructions, if it is not provided by repo developer.

>[!INFO] BApp Trusted Repo
>BApp Trusted Repo - BApp's own packages which is tested and ***100% debugged***, no installation problems possible

>[!INFO] AlloidRepo
>AlloidRepo is 3rd party repository hosted by independent company, but their repo is tested by BApp team and included into default BApp's repolist

>[!INFO] AllTheAppsRepo
>AllTheAppsRepo is the same as [AlloidRepo](#^d39b14)

## How to use BApp
>[!Reqv] Installation
>BApp is not provided by appx, so you need to download and [compile](OBJQcomp%20complete%20guide) it by yourself.
>1. Go to https://bapp.org/download/ and download the installation archive
>2. Unpack this archive by GUI utilities or by command line
>`unpack -zip <name_of_downloaded_archive>`
>3. Go to `bapp` directory
>4. Open terminal in this folder
>5. Write `objqcomp compiler compile --compile-executable-type=.app --support-custom-cores=True compile.objqcomp`, press Enter and wait for [OBJQcomp](OBJQcomp%20complete%20guide.md) to complete your task
>6. After all is done, go to `build` directory and run `appx install -from-file local:/<builded_file>` and you are all done
>
>Now BApp is listed in your apps and available in terminal as command.

>[!INFO] How to use BApp
>BApp has its own GUI app, but i won't describe its usage here, instead i'll tell you about terminal `bapp` utility 
>
>How to install an application
>>To install app you need to execute `bapp install <package_name if target app is in one of official repos or reponame/author/package_name if not in official repo or if app is on GitHub>`
>
>How to remove a package
>>`bapp remove <package_name or author/package_name>`

## Why BApp is better than [appx](appx.md)?
Just because here you can find fore useful software from GitHub from another self-added repos, here, for example, you can find cracked Adobe Products, instead of licensed from appx.

Software can be not signed with digital key → more developers can publish their products to BApp than the appx

Developers don't need to write any compilation instructions for their packages, BApp will do it automatically for them.

## If BApp so better than appx, why appx is more popular for developers, especially commercial?
BApp is hard to install for basic user than appx, appx installed for their system by default, and BApp needs to be installed manually with compilation process, which is scaring basic users

True QOS enjoyers installing their system with BApp pre-installed instead of appx, leaving only appx's installation components because BApp can install all apps from appx, so you don't need to have appx installed at all to manage your packages, BApp can do it all.