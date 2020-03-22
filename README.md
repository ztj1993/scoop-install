# Scoop 索引

## 日志
```
git init
git commit --only --allow-empty -m init
git submodule add --depth 1 https://gitee.com/zhangtianjie/scoop-lukesampson apps/scoop/current
git submodule add --depth 1 https://github.com/ScoopInstaller/Main buckets/main
git submodule add --depth 1 https://github.com/lukesampson/scoop-extras buckets/extras
git submodule add --depth 1 https://github.com/ScoopInstaller/Java buckets/java
git submodule add --depth 1 https://github.com/TheRandomLabs/scoop-nonportable buckets/nonportable
git submodule add --depth 1 https://github.com/Ash258/Scoop-JetBrains buckets/jetbrains
git submodule add --depth 1 https://github.com/ScoopInstaller/PHP buckets/php
git submodule add --depth 1 https://github.com/ScoopInstaller/Versions buckets/versions
```

## 安装
```
git clone --depth 1 https://github.com/ztj1993/scoop-index
git submodule init
git submodule update --depth 1
```

## 重装
```
cd $env:SCOOP
Remove-Item .\apps\scoop -Force -Recurse -Confirm:$false
Remove-Item .\buckets -Force -Recurse -Confirm:$false
Remove-Item .\.git -Force -Recurse -Confirm:$false

cd $env:TMP
git clone --depth 1 https://github.com/ztj1993/scoop-index
cd .\scoop-index
git submodule init
git submodule update --depth 1

Copy-Item $env:TMP\scoop-index\* $env:SCOOP -Recurse -Force
```
