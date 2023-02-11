# Scoop

Scoop 是一个 Windows 便携软件管理器，可以通过命令行的方式安装软件，以及更新软件时保留配置。

## 项目构建
```
cd $env:USERPROFILE

git clone --depth 1 https://github.com/ztj1993/scoop scoop
git clone --depth 1 https://github.com/ScoopInstaller/Scoop scoop/apps/scoop/current
git clone --depth 1 https://github.com/ScoopInstaller/Main scoop/buckets/main
git clone --depth 1 https://github.com/ScoopInstaller/Extras.git scoop/buckets/extras
git clone --depth 1 https://github.com/ScoopInstaller/Java scoop/buckets/java
git clone --depth 1 https://github.com/ScoopInstaller/Nonportable scoop/buckets/nonportable
git clone --depth 1 https://github.com/ScoopInstaller/PHP scoop/buckets/php
git clone --depth 1 https://github.com/ScoopInstaller/Versions scoop/buckets/versions
git clone --depth 1 https://github.com/Ash258/Scoop-JetBrains scoop/buckets/jetbrains

zip -qr scoop-$(date "+%Y%m%d").zip ./scoop
```

## 更新环境
```
cd $env:USERPROFILE/scoop

git pull
git -C apps/scoop/current pull
git -C buckets/main pull
git -C buckets/extras pull
git -C buckets/java pull
git -C buckets/nonportable pull
git -C buckets/jetbrains pull
git -C buckets/php pull
git -C buckets/versions pull
git -C buckets/ztj1993 pull
```

## 项目安装
```
cd $env:USERPROFILE/scoop
.\apps\scoop\current\bin\refresh.ps1
scoop help
```

## 项目卸载
```
cd $env:USERPROFILE/scoop
.\apps\scoop\current\bin\uninstall.ps1
```
