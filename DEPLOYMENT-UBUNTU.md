# Ubuntu 自有服务器部署说明

以下为独立恢复步骤和示例，不是自动执行脚本。实际目录、服务名和端口需先检查，避免覆盖其他业务。

## 前提和目录

需要 Node.js 22 或更新版本；主工程无第三方运行依赖。上传完整源码中的 Projects/命运之戏，或解压 distributions/fate-dice-server-20261028-222439.tar.gz 到新建的 /opt/fate-dice。后者仅含运行所需代码和网页资源，不含测试、云端和参考图。

先检查 node 的绝对路径、8088 端口是否空闲、/opt/fate-dice 和 fate-dice.service 是否已存在。不要把本说明的示例覆盖到现有服务。

## systemd 示例

deploy/fate-dice.service 保存了对话中使用的独立服务配置。示例使用 /usr/local/bin/node、/opt/fate-dice、PORT=8088 和 DynamicUser=yes；换服务器时必须先核对可执行文件位置及访问权限。

安装 unit 后，systemctl daemon-reload 重新读取配置，systemctl enable --now fate-dice 设置开机启动并启动游戏。这些命令会修改服务器并对外提供应用，需在所有者确认目录、端口及影响后执行。

## 验证与网络

systemctl status fate-dice --no-pager --full 查看服务；curl -sS --max-time 5 -o /dev/null -w 'HTTP %{http_code}\n' http://127.0.0.1:8088/ 验证服务器内部首页。此应用只提供 GET 静态资源，不能仅用 curl -I 的 HEAD 结果判断首页故障。

浏览器访问 http://服务器公网IP:8088/ 。超时时先检查实例关联安全组是否允许 TCP 8088 入方向、访问 IP 是否正确及服务器实际监听地址。游戏供公网玩家使用时才按需允许所有 IPv4 来源；安全组如关联多台实例，规则会影响它们相应端口。不要改变 SSH 或其他业务规则来处理此游戏。

域名和 HTTPS 尚未在对话中配置。可先按已批准范围用公网 IP 测试；后续配置反向代理与 HTTPS 需另行准备并确认。Node 版按连接地址限流，反向代理后的多个用户可能共享限流桶，扩容前应单独处理可信代理和限流策略。

## 对局和回退

用两台设备分别创建和加入同一房间，完成准备、投骰、保留、恩惠、结算和下一回合，再核对双方生命与记录。单独 HTTP 200 不代表完整对战验收。

systemctl disable --now fate-dice 会停止游戏并撤销开机启动；只针对本次独立服务，不删除源文件。停止、崩溃或重启游戏会清空内存房间。最终删除目录或配置需要单独核实并得到所有者明确批准。
