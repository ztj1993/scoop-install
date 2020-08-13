# Scoop 索引

## 项目构建
```
git clone --no-checkout --depth 1 https://github.com/ztj1993/scoop-index scoop

cd scoop

git clone --depth 500 https://github.com/lukesampson/scoop apps/scoop/current
git clone --depth 500 https://github.com/ScoopInstaller/Main buckets/main
git clone --depth 500 https://github.com/lukesampson/scoop-extras buckets/extras
git clone --depth 500 https://github.com/ScoopInstaller/Java buckets/java
git clone --depth 500 https://github.com/TheRandomLabs/scoop-nonportable buckets/nonportable
git clone --depth 500 https://github.com/Ash258/Scoop-JetBrains buckets/jetbrains
git clone --depth 500 https://github.com/ScoopInstaller/PHP buckets/php
git clone --depth 500 https://github.com/ScoopInstaller/Versions buckets/versions

git -C apps/scoop/current am ../../../patch/disable-automatic-update.patch
```

## 更新环境
```
git -C apps/scoop/current pull
git -C buckets/main pull
git -C buckets/extras pull
git -C buckets/java pull
git -C buckets/nonportable pull
git -C buckets/jetbrains pull
git -C buckets/php pull
git -C buckets/versions pull
```

## 项目锁定
```
git -C buckets/main rev-parse HEAD
git -C buckets/main reset --hard d7ff2d94261b22a9901e8e08a009dd05f6b85497
git -C buckets/extras rev-parse HEAD
git -C buckets/extras reset --hard 31a5242463208798cfe8187b5c060694079c4181
git -C buckets/java rev-parse HEAD
git -C buckets/java reset --hard 30c9f331ba759f479d7d5e971049322f429c177b
git -C buckets/nonportable rev-parse HEAD
git -C buckets/nonportable reset --hard e0141b2a14004bff79af035aa0cfa1503ea9550a
git -C buckets/jetbrains rev-parse HEAD
git -C buckets/jetbrains reset --hard 6f4c8337599abdc6150cd4cc08174d763c5361b0
git -C buckets/php rev-parse HEAD
git -C buckets/php reset --hard 6ceb36a70072d94c9eb5bc5138f7118ce41fee9e
git -C buckets/versions rev-parse HEAD
git -C buckets/versions reset --hard 93c3a96a1fb58ba5155dd849926374df64d0473b
```

## 项目安装
```
mkdir $env:USERPROFILE\scoop -force
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
