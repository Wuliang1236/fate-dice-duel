# 完整源码及资源 ZIP 下载

此目录保存两个独立 ZIP；全部内容为私有仓库资源，只有获授权的账号可下载。点击文件后使用 Download raw file，或点击下表的直接下载链接。

| 文件 | 内容 | 字节数 |
| --- | --- | --- |
| [fate-dice-sites-version-1.zip](fate-dice-sites-version-1.zip?raw=true) | Sites 2026-10-20 历史发布版本 1：固定 Git 提交的云端完整源码、迁移、锁文件、参考图及原始部署工件；133 个文件 | 3,696,274 |
| [fate-dice-final-2026-11-17.zip](fate-dice-final-2026-11-17.zip?raw=true) | 最终增强版快照：完整 Node.js 与 Sites 源码、动画音效、测试、图片截图、部署文档、systemd 示例和精简部署工件；167 个文件 | 3,724,713 |
| [CHECKSUMS.sha256](CHECKSUMS.sha256) | 两个 ZIP 的 SHA-256 校验值，下载后可用来核对完整性 | — |

## 校验值

```text
44954509dcb7d1abcea81885a8518f25a135aed69cd43b9ed74d06f2d01c2036  fate-dice-sites-version-1.zip
ee558b0ed109e3e86e2816a60cbaeccf55196daed833ec35dd8839c9a99064e3  fate-dice-final-2026-11-17.zip
```

Windows 可执行 `Get-FileHash -Algorithm SHA256 文件名.zip`；Linux 可执行 `sha256sum 文件名.zip`。ZIP 内 FILE_MANIFEST.json 另外记录逐文件大小及 SHA-256。

历史版直接来自提交 `396de04fb8552e28b2704733e9595948e33d2d4c`。final-2026-11-17 是日期快照，不是新游戏版本号。两个 ZIP 均含完整资源，最终版的音效由 Web Audio 代码合成，没有额外 MP3 / WAV。

ZIP 是完整交付源码与资源，不包含 node_modules、凭据或生产数据库；依赖可按锁文件安装。运行方式、功能限制和已验证范围请参阅仓库根目录说明及各 ZIP 内文档。

