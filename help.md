## 版本检查

```ps
$PSVersionTable.PSVersion
```

## 重要概念
- output is object-based
- the command family is extensible
- use some c-sharp syntax
- Cmdlets use verb-noun names (try gcm -Verb Get, gcm -Noun Service)
- Cmdlets use standard params
- Common params: WhatIf, Confirm, Verbose, Debug, Warn, ErrorAction, ErrorVariable, OutVariable, OutBuffer.

## help 文档

- get-help get-childitem   等价于 Get-ChildItem -? 等价于 man ls 等价于 help ls
- man ls -Full 可以看更全的文档
- man ls -Online 在线看文档
- man ls -Examples
- man man
- man about_*  查看conceptual articles
- update-help  更新 help 文档
- Get-Help -Category Cmdlet  查看所有的help文档
  
#### 查看script的help文档

- Get-Help c:\ps-test\TestScript.ps1

#### 查看function的help文档

- Get-Help Disable-PSRemoting

## 查看 cmd

- gcm Get-Help -Syntax  查看Get-Help 的语法
- gcm *  查看所有命令
- gcm -CommandType Alias/Function/Script  查看指定类型的cmd
- gcm *-Service 查看Service结尾的cmd


## alias
- Get-ChildItem = ls = dir
- Get-Command = gcm
- Get-Service = gsv
- Get-Member = gm 

#### create new alias

```ps
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

## variable

```ps
$loc = ls
$loc | gm -MemberType Property
如何操作variable:   Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue     清除所有variable
get-variable // gv  获取variable

# 如何查看环境变量
env  或者 ls env:
环境变量
$env:SystemRoot
可以直接通过赋值来创建或修改variable  ,比如 $env:LIB_PATH='/usr/local/lib'
```

## 管道 和 流水线  pipe and pipeline

```ps
ls C:\WINDOWS\System32 | oh -Paging
ls | gm
gsv | gm
```

