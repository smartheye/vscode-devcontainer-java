# VScode devcontainer for Java

## Environment
- Java: OpenJDK 21
- Maven: 3.9.6

## Memo
### 1. 绑定本地的ssh证书和m2目录
打开.devcontainer/devcontainer.json，


找到mounts下面的这段注释

```json
    //"type=bind,source=/home/${localEnv:USER}/.ssh,target=/home/vscode/.ssh,readonly",
    //"type=bind,source=/home/${localEnv:USER}/.m2,target=/home/vscode/.m2",
```

分别改为
#### Mac
```
    "type=bind,source=/Users/${localEnv:USER}/.ssh,target=/home/vscode/.ssh,readonly",
    "type=bind,source=/Users/${localEnv:USER}/.m2,target=/home/vscode/.m2",
```

#### Linux
```
    "type=bind,source=/home/${localEnv:USER}/.ssh,target=/home/vscode/.ssh,readonly",
    "type=bind,source=/home/${localEnv:USER}/.m2,target=/home/vscode/.m2",
```

然后删除

```json
    "source=devc-java-m2,target=/home/vscode/.m2,type=volume"
```