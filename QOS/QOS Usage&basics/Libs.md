Libs - packages shared with all users and `app` packages

>[!EXAMPLE]
>Lib `QT-devel` used to build app with QT framework, but cannot be used to use in compiled [app](Apps.md)
>Contrariwise compiled apps builded with QT require just`QT` lib without devel

Requirement libs are listed in <app_name>.objqcomp file in project folder. Added by using 
```objqcomp
[smth]
...

[Depend]
depends on libQT : in file as QT
{prjlib:QT-devel ; applib:QT} 
```

Libs stored in [QRoot](QRoot.md)/sys/lib