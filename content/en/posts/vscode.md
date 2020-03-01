+++
title = "VSCode"
categories = ["VSCode"]
tags = ["Tools", "VSCode", "tips"]
+++

## 一、 使用技巧

### 1. windows 上配置 git-bash 为默认的 bash

1. 确保已经安装 git-bash
2. 配置文件 settings.json 加入以下内容即可
   "terminal.integrated.shell.windows": "D:\\Program Files\\Git\\bin\\bash.exe"

### 2. 一次编辑多行

选好位置，比如行首，按 Ctrl+F2 进入列模式

## 二、 配置 VSCode 远程开发

### 1. 在 Win10 上运行 git-bash 执行以下命令

```bash
REMOTEHOST=root@172.x.y.z

scp $USERPROFILE/.ssh/id_rsa.pub $REMOTEHOST:~/tmp.pub

ssh $REMOTEHOST "mkdir -p ~/.ssh && chmod 700 ~/.ssh && cat ~/tmp.pub >> ~/.ssh/authorized_keys && chmod 600 ~/.ssh/authorized_keys && rm -f ~/tmp.pub"
```

### 2. 在~/.ssh/vscode-remote-config 文件里添加远程主机的 ip 等信息，例子如下

```config
Host CentOSxxx
    User root
    HostName 172.x.y.z
```

### 3. 在 VSCode 中按 F1 选择 Remote-SSH: Connect to Host...命令，选择之前添加的 CentOSxxx 即可

### 4.未尽事项详见官方文档 <https://code.visualstudio.com/docs/remote/troubleshooting#_configuring-key-based-authentication>

## 三、launch.json 例子

### 1. 调试 js 配置

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "node",
      "request": "launch",
      "name": "Launch Program",
      "program": "${workspaceFolder}/app.js",
      "args": ["--port", "800", "--debug", "yes", "--flags", "w"],
      "env": {
        "NODE_ENV": "development"
      },
      "skipFiles": [
        "<node_internals>/**",
        "async_hooks.js",
        "inspector_async_hook.js"
      ],
      "console": "integratedTerminal",
      "preLaunchTask": "eslint"
    },
    {
      "type": "node",
      "request": "launch",
      "name": "Mocha All",
      "program": "${workspaceFolder}/node_modules/mocha/bin/_mocha",
      "args": [
        "--timeout",
        "999999",
        "--colors",
        "${workspaceFolder}/test",
        "--port",
        "800",
        "--debug",
        "yes",
        "--flags",
        "w"
      ],
      "env": {
        "NODE_ENV": "development"
      },
      "skipFiles": [
        "<node_internals>/**",
        "async_hooks.js",
        "inspector_async_hook.js"
      ],
      "console": "integratedTerminal",
      "internalConsoleOptions": "neverOpen"
    },
    {
      "type": "node",
      "request": "launch",
      "name": "Mocha Current File",
      "program": "${workspaceFolder}/node_modules/mocha/bin/_mocha",
      "args": [
        "--timeout",
        "999999",
        "--colors",
        "${file}",
        "--port",
        "800",
        "--debug",
        "yes",
        "--flags",
        "w"
      ],
      "env": {
        "NODE_ENV": "development"
      },
      "skipFiles": [
        "<node_internals>/**",
        "async_hooks.js",
        "inspector_async_hook.js"
      ],
      "console": "integratedTerminal",
      "internalConsoleOptions": "neverOpen"
    }
  ]
}
```

### 2. 调试 bash 脚本（需要安装 Bash Debug 插件）

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "bashdb",
      "request": "launch",
      "name": "Bash-Debug (select script from list of sh files)",
      "cwd": "${workspaceFolder}",
      "program": "${command:SelectScriptName}",
      "args": []
    }
  ]
}
```
