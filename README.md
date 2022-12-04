# kb容器云部署Xy 

### 可用1 https://github.com/juhytfen/bbdcp
### 可用2 https://github.com/wgp-2020/KX


## 部署步骤

1. fork某仓库

2. 在`Dockerfile`内第3-5行修改自定义设置，说明如下：

`AUUID`：UUID，可在(https://www.uuidgenerator.net/) 生成

`CADDYIndexPage`：伪装站首页文件，如 www.baidu.com

`ParameterSSENCYPT`：ShadowSocks加密协议

3. 去(https://hub.docker.com/)注册一个账号

4. 编辑Actions文件`docker-image.yml`，

按照“name: Docker_Hub_ID/自定义镜像名称”格式修改第13行

5. 添加Actions的Secrets变量，变量说明如下

`DOCKER_USERNAME`：Docker_Hub_ID 用户名

`DOCKER_PASSWORD`：Docker_Hub 登录密码

启动action

6. 打开某容器云主页，新建一个应用

7. 应用配置如下所示

`Docker Image`：Docker Hub镜像地址，

格式为“Docker_Hub_ID/自定义镜像名称”

Environment variables：
`Name`：PORT，

`Type`：plaintext

`Value`：80

Exposing your service:
Port：80
Path：/

`App_Name`：自己定义,

如YYYY, ID为XXXX，则地址为YYYY-XXXX.koyeb.app


8. 客户端配置如下所示

V2ray

```
地址：YYYY-XXXX.koyeb.app
端口：443
默认UUID：24b4b1e1-7a89-45f6-858c-242cf53b5bdb
vmess额外id：0
加密：none
传输协议：ws
伪装类型：none
伪装域名：xxx.prod-glb.koyeb.app
路径：/24b4b1e1-7a89-45f6-858c-242cf53b5bdb-vless
vless使用(/自定义UUID码-vless)，vmess使用(/自定义UUID码-vmess)
底层传输安全：tls
跳过证书验证：false
```

Trojan-go

```bash
{
    "run_type": "client",
    "local_addr": "127.0.0.1",
    "local_port": 1080,
    "remote_addr": "YYYY-XXXX.koyeb.app",
    "remote_port": 443,
    "password": [
        "24b4b1e1-7a89-45f6-858c-242cf53b5bdb"
    ],
    "websocket": {
        "enabled": true,
        "path": "/24b4b1e1-7a89-45f6-858c-242cf53b5bdb-trojan",
        "host": "xxx.prod-glb.koyeb.app"
    }
}
```

ShadowSocks

```bash
服务器地址: YYYY-XXXX.koyeb.app
端口: 443
密码：24b4b1e1-7a89-45f6-858c-242cf53b5bdb
加密：chacha20-ietf-poly1305
插件程序：xray-plugin_windows_amd64.exe
说明：需将插件 https://github.com/shadowsocks/xray-plugin/releases 下载解压后放至shadowsocks同目录
插件选项: tls;host=xxx.prod-glb.koyeb.app;path=/24b4b1e1-7a89-45f6-858c-242cf53b5bdb-ss
```

## 注意

请勿滥用本仓库

## 赞助我们

![afdian-MisakaNo.jpg](https://s2.loli.net/2021/12/25/SimocqwhVg89NQJ.jpg)

## 交流群
[Telegram](https://t.me/misakanetcn)
