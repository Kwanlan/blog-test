WWW=URL+HTTP+HTML
IP 和端口缺一不可 (IP 提供机器 端口提供服务)
IP 分为内网和外网
#几个特殊的 IP

    127.0.0.1 表示自己
    localhost 通过 hosts 指定为自己
    0.0.0.0 不表示任何设备

端口 port

一台机器可以提供不同的服务

    要提供 http 服务最好使用 80 端口
    要提供 https (security)服务最好使用 443 端口
    要提供 FTP (文件传输)服务最好使用 21 端口
    一共有 65535 个端口(基本够用)

规则

    0 到 1023(2 的10 次方 -1)号端口是留给系统使用的
    拥有管理权后才能使用 1024 端口，其他端口可以给普通用户使用
    比如:http-server 默认使用 8080 端口
    一个端口如果被占用，只能换一个端口

域名

是对 IP 的别称 ping baidu.com 查看百度 IP 知识点

    一个域名可以对应不同 IP
    叫做均衡负载，防止一台机器扛不住
    一个 IP 可以对应不同域名
    这个叫共享主机，穷开发者会这么做

DNS 域名服务 Domain Name System 将域名和 IP 联系
www.xiedaimala.com 和 xiedaimala.com 不是同一个域名

    com 是顶级域名
    xiedaimala.com 是二级域名(俗称一级域名)
    www.xiedaimala.com 是三级域名(俗称二级)
    他们是父子关系
    github.io 把子域名 xxx.github.io 免费给你使用
    www 是多余的

URL 统一资源定位服务

    https 默认端口 443
    锚点不会传给服务器

curl 命令

curl 发送 http 请求

    curl -v www.baidu.com
    curl -s -v www.baidu.com

理解

    url 会被 curl 工具重写，先请求 DNS 获取 IP
    先进行 TCP 连接，TCP 连接成功后，开始发送 HTTP 请求
    响应结束后，关闭 TCP 连接
    真正结束