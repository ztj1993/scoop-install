# Scoop 索引

## 构建方法
```
git init
git commit --only --allow-empty -m init
git submodule add --depth 1 https://github.com/lukesampson/scoop apps/scoop/current
git submodule add --depth 1 https://github.com/ScoopInstaller/Main buckets/main
git submodule add --depth 1 https://github.com/lukesampson/scoop-extras buckets/extras
git submodule add --depth 1 https://github.com/ScoopInstaller/Java buckets/java
git submodule add --depth 1 https://github.com/TheRandomLabs/scoop-nonportable buckets/nonportable
git submodule add --depth 1 https://github.com/Ash258/Scoop-JetBrains buckets/jetbrains
git submodule add --depth 1 https://github.com/ScoopInstaller/PHP buckets/php
git submodule add --depth 1 https://github.com/ScoopInstaller/Versions buckets/versions
```

## 安装方式
```
git clone --depth 1 https://github.com/ztj1993/scoop-index $env:USERPROFILE\scoop
git -C $env:USERPROFILE\scoop submodule init
git -C $env:USERPROFILE\scoop submodule update --depth 1
git -C $env:USERPROFILE\scoop\apps\scoop\current am $env:USERPROFILE\scoop\patch\disable-automatic-update.patch

. $env:USERPROFILE\scoop\apps\scoop\current\lib\core.ps1
$dir = ensure (versiondir 'scoop' 'current')
shim "$dir\bin\scoop.ps1" $false
ensure_scoop_in_path

scoop help
```

## 更新环境
```
git clone --depth 1 https://github.com/ztj1993/scoop-index .
git submodule init
git submodule update --depth 1
git submodule foreach git checkout master
git submodule foreach git pull --depth 1 origin master
```
