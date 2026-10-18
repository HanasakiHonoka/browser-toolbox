# browser-toolbox

统一的浏览器插件 / 油猴脚本仓库：这里存放日常使用的 Chrome 扩展与 Tampermonkey 脚本，按类型分目录管理。

## 目录结构

```
browser-toolbox/
├── scripts/                    # 油猴脚本（Tampermonkey / Violentmonkey，*.user.js）
│   ├── h5mota-toolbox.user.js          # H5 魔塔工具箱
│   ├── sukebei-preview.user.js         # Sukebei 悬停封面预览
│   ├── sukebei-batch-preview.user.js   # Sukebei 列表页批量预览
│   └── sukebei-size-highlighter.user.js# Sukebei Size 列体积高亮
├── chrome-fetch-img-plugin/    # Chrome 扩展（MV3）：Sukebei 悬停预览
└── data/                       # 站点离线快照（本地参考，不入库）
```

## 油猴脚本

| 脚本 | 版本 | 作用 |
| --- | --- | --- |
| [H5 魔塔工具箱](scripts/h5mota-toolbox.user.js) | 2.2.7 | 血瓶拾取/使用倍率、实时查看并增减钥匙数量、楼层传送器无视楼梯限制、扣血转加血、回春触发计算、楼层敌人统计、撤销悬浮按钮、楼传滚动条。配置按魔塔独立存储，新塔默认全关。适配 HTML5 魔塔引擎（土豆魔塔） |
| [Sukebei Preview](scripts/sukebei-preview.user.js) | 1.3 | 鼠标悬停在 sukebei 种子链接上时显示封面预览，与 Batch Preview 共用封面缓存 |
| [Sukebei Batch Preview](scripts/sukebei-batch-preview.user.js) | 1.4 | 列表页插入封面缩略图列与多选列，支持批量复制磁力链接、按需加载封面 |
| [Sukebei Size Highlighter](scripts/sukebei-size-highlighter.user.js) | 1.3 | 按相对大小高亮 Size 列，数值越大颜色越醒目 |

主站与镜像域名（`sukebei.nyaa.si` / `sukebei.nyaa.mom`）均已适配。

**安装 / 更新**：直接安装下面的 raw 链接，Tampermonkey 会按脚本内的 `@updateURL` 自动检查更新。

```
https://raw.githubusercontent.com/HanasakiHonoka/browser-toolbox/main/scripts/<脚本文件名>.user.js
```

## Chrome 扩展

[chrome-fetch-img-plugin](chrome-fetch-img-plugin/README.md) —— Manifest V3 扩展，功能与 Sukebei Preview 脚本重叠；一般优先用脚本版，扩展版作为需要后台/跨页缓存时的替代。

本地加载：`chrome://extensions` → 开启「开发者模式」→「加载已解压的扩展程序」→ 选择 `chrome-fetch-img-plugin/` 目录。

## 约定

- 油猴脚本统一放 `scripts/`，文件名用 kebab-case，必须以 `.user.js` 结尾才能被 Tampermonkey 识别。
- 同一目标站点的多个小功能应合并进一个工具箱脚本，不再按功能拆分新脚本。
- 每次功能变更同步提升 `@version`，否则用户端检测不到更新。
- 新增 Chrome 扩展时放在仓库根目录的独立文件夹内，附 `manifest.json` 与说明。
