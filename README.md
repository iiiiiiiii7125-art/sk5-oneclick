# SK5 / SOCKS5 一键搭建

基于 gost v2.11.5 单二进制的 SOCKS5 一键安装脚本：账号密码认证、支持 TCP + UDP、systemd 开机自启。

支持：Debian / Ubuntu / CentOS / Rocky / Alma / Fedora，x86_64 与 ARM64（armv8）。必须用 root 运行。

## 一键安装

```bash
bash <(curl -sL https://raw.githubusercontent.com/iiiiiiiii7125-art/sk5-oneclick/main/sk5.sh)
```

不带参数时全自动随机生成：**随机端口（20000–60000，自动避开已占用端口）、随机用户名、16 位随机密码**，并注册 systemd 服务开机自启（随系统重启自动启动）。装完直接打印连接信息（同时保存在服务器 `/etc/sk5/info.txt`）。

指定端口和账号密码：

```bash
bash <(curl -sL https://raw.githubusercontent.com/iiiiiiiii7125-art/sk5-oneclick/main/sk5.sh) --port 1080 --user myuser --pass mypass123
```

## 查看状态

```bash
bash sk5.sh --status
```

## 卸载

```bash
bash sk5.sh --uninstall
```

## 注意

- 云厂商控制台的安全组要另外放行所用端口的 **TCP + UDP**，脚本只能放行服务器本机防火墙。
- 用户名/密码只允许字母、数字、`_`、`-`（会拼进代理 URL，特殊字符会拼坏）。
