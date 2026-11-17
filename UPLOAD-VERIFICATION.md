# GitHub 上传验收记录

验收日期：2026-11-17。

后续状态：所有者已明确要求公开仓库并删除本地文件，操作已完成。下文保留初次私有上传验收时的记录；当前状态见 [公开访问与本地清理记录](CLEANUP-VERIFICATION.md)。

- 仓库：https://github.com/Wuliang1236/fate-dice-duel
- 仓库所有者：Wuliang1236。
- 可见性：Private，网页标识与 GitHub 仓库元数据的 private=true 一致；未启用 Pages。
- 压缩包提交：09b7b1217aca0a85812dd65aa67a1aec4a6df851。
- 两个 ZIP 均已实际从仓库下载，而非仅根据上传界面的文件名或成功提示判断。

## 下载与本地逐一比对

| 文件 | 下载字节数 | 包内文件数 | 下载 SHA-256 与本地 |
| --- | --- | --- | --- |
| releases/fate-dice-sites-version-1.zip | 3,696,274 | 133 | 一致 |
| releases/fate-dice-final-2026-11-17.zip | 3,724,713 | 167 | 一致 |

```text
44954509dcb7d1abcea81885a8518f25a135aed69cd43b9ed74d06f2d01c2036  fate-dice-sites-version-1.zip
ee558b0ed109e3e86e2816a60cbaeccf55196daed833ec35dd8839c9a99064e3  fate-dice-final-2026-11-17.zip
```

重新打开下载的两个 ZIP，对照各自 FILE_MANIFEST.json 检查每一个文件的路径、字节数与 SHA-256，合计 300 个文件通过；没有发现所检查的私钥和访问令牌模式。中文路径使用 UTF-8，已通过标准 ZIP 读取验证。

GitHub 内容目录另确认两个 ZIP 的字节数与下载结果一致。其 Git blob SHA 为：历史版 8d4a92f33ecc5165455320e9546ec89d685ea087；最终版 68a389f5f000eb73750ca668f9cd57c44235abfc。Git blob SHA 与整文件 SHA-256 是不同算法与用途，不应混用。

## 源码和资源范围

历史版从已发布版本 1 的固定原始提交还原；最终版含 Node.js / Sites 两套完整源码、数据库迁移、依赖锁文件、动画音效、测试、原始参考图、截图、部署文档、systemd 示例和原始部署 TAR。完整源码保存于 ZIP 内，仓库顶层文档供直接查看。

根 README、VERSIONS.md、ARCHIVE-CONTENTS.md、DEPLOYMENT-UBUNTU.md、VERIFICATION.md、ZIP-VERIFICATION.json 及 releases/README.md 提供详细文件描述、运行方式、版本来源和已知限制；releases/CHECKSUMS.sha256 提供下载校验值。

## 保留与验证边界

- 本地原项目、参考资料、两个 ZIP、整理目录和下载核验副本均保留；没有执行删除。
- 源工程原有未提交修改没有被自动提交或推送；本次提交仅用于新建 GitHub 归档仓库。
- 本次没有连接、修改或重启阿里云服务器和已有 Sites 站点，没有更改它们的访问权限。
- 上传完整性验证不等于新增手机真机、音效听感、Docker 构建或公网游戏验收；这些限制见 VERIFICATION.md。
- 只有用户之后明确授权删除，再核对实际文件与路径范围进行清理。
