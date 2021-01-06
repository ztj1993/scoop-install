# Scoop 索引

## 项目构建
```
mkdir scoop

git clone --depth 1 https://github.com/ztj1993/scoop-index scoop
git clone --depth 1 https://github.com/lukesampson/scoop scoop/apps/scoop/current
git clone --depth 1 https://github.com/ScoopInstaller/Main scoop/buckets/main
git clone --depth 1 https://github.com/lukesampson/scoop-extras scoop/buckets/extras
git clone --depth 1 https://github.com/ScoopInstaller/Java scoop/buckets/java
git clone --depth 1 https://github.com/TheRandomLabs/scoop-nonportable scoop/buckets/nonportable
git clone --depth 1 https://github.com/Ash258/Scoop-JetBrains scoop/buckets/jetbrains
git clone --depth 1 https://github.com/ScoopInstaller/PHP scoop/buckets/php
git clone --depth 1 https://github.com/ScoopInstaller/Versions scoop/buckets/versions

git -C scoop/apps/scoop/current am ../../../patch/disable-automatic-update.patch
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

## 项目安装
```
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Force

$env:SCOOP="$(Get-Location)"
[Environment]::SetEnvironmentVariable('SCOOP', $env:SCOOP, 'User')

. "$(Get-Location)\apps\scoop\current\lib\core.ps1"
$dir = ensure (versiondir 'scoop' 'current')
shim "$dir\bin\scoop.ps1" $false
ensure_scoop_in_path

scoop help
```

## 删除环境
```
scoop uninstall scoop

Remove-Item .git -Force -Recurse

Remove-Item apps\scoop -Recurse

Remove-Item buckets\main -Force -Recurse
Remove-Item buckets\extras -Force -Recurse
Remove-Item buckets\java -Force -Recurse
Remove-Item buckets\nonportable -Force -Recurse
Remove-Item buckets\jetbrains -Force -Recurse
Remove-Item buckets\php -Force -Recurse
Remove-Item buckets\versions -Force -Recurse

Remove-Item patch -Force -Recurse
Remove-Item .gitignore -Force -Recurse
Remove-Item README.md -Force -Recurse
```
