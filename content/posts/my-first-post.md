+++
title = "配置VSCode远程开发"
+++



# 注意在Win10上运行git-bash执行以下命令

REMOTEHOST=root@172.16.87.31

scp $USERPROFILE/.ssh/id_rsa.pub $REMOTEHOST:~/tmp.pub

ssh $REMOTEHOST "mkdir -p ~/.ssh && chmod 700 ~/.ssh && cat ~/tmp.pub >> ~/.ssh/authorized_keys && chmod 600 ~/.ssh/authorized_keys && rm -f ~/tmp.pub"

## 最后一步，在以下文件里添加远程主机的ip等信息
~/.ssh/vscode-remote-config

### 详见 https://code.visualstudio.com/docs/remote/troubleshooting#_configuring-key-based-authentication