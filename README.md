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
git clone --no-checkout --depth 1 https://github.com/ztj1993/scoop-index $env:USERPROFILE\scoop\tmp
Copy-Item $env:USERPROFILE\scoop\tmp\.git -Destination $env:USERPROFILE\scoop\.git -Recurse
Remove-Item $env:USERPROFILE\scoop\tmp -Force -Recurse

git -C $env:USERPROFILE\scoop checkout master
git -C $env:USERPROFILE\scoop submodule init
git -C $env:USERPROFILE\scoop submodule update --depth 1

git -C $env:USERPROFILE\scoop\apps\scoop\current am $env:USERPROFILE\scoop\patch\disable-automatic-update.patch

. $env:USERPROFILE\scoop\apps\scoop\current\lib\core.ps1
$dir = ensure (versiondir 'scoop' 'current')
shim "$dir\bin\scoop.ps1" $false
ensure_scoop_in_path

scoop help
```

## 删除环境
```
Remove-Item $env:USERPROFILE\scoop\.git -Force -Recurse

Remove-Item $env:USERPROFILE\scoop\apps\scoop -Recurse

Remove-Item $env:USERPROFILE\scoop\buckets\main -Force -Recurse
Remove-Item $env:USERPROFILE\scoop\buckets\extras -Force -Recurse
Remove-Item $env:USERPROFILE\scoop\buckets\java -Force -Recurse
Remove-Item $env:USERPROFILE\scoop\buckets\nonportable -Force -Recurse
Remove-Item $env:USERPROFILE\scoop\buckets\jetbrains -Force -Recurse
Remove-Item $env:USERPROFILE\scoop\buckets\php -Force -Recurse
Remove-Item $env:USERPROFILE\scoop\buckets\versions -Force -Recurse

Remove-Item $env:USERPROFILE\scoop\patch -Force -Recurse
Remove-Item $env:USERPROFILE\scoop\.gitignore -Force -Recurse
Remove-Item $env:USERPROFILE\scoop\.gitmodules -Force -Recurse
Remove-Item $env:USERPROFILE\scoop\README.md -Force -Recurse
```
