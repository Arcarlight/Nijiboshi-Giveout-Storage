# Nijiboshi-Giveout-Storage

《想要飞的始祖小鸟》（TBTAK）的**公开素材库**——点阵图、角色立绘、MIDI、UI 素材都放这里。

主站（<https://arcarlight.github.io/BlogStand/>）不直接存这些文件，只存一份素材清单；
图片和音频通过 **jsDelivr CDN** 从这里取，省主站仓库体积、也不占 GitHub Pages 带宽。

素材分发页：<https://arcarlight.github.io/BlogStand/resources/>

## 授权

本仓库所有素材以 **CC BY 4.0**（知识共享 署名 4.0 国际）授权，见 [LICENSE](LICENSE)。

你可以自由地：

- **共享** —— 以任何媒介或格式复制、发行本素材
- **演绎** —— 修改、转换或以本素材为基础进行创作
- 包括**商业用途**

唯一条件是**署名**。推荐写法：

```
素材：Fliegen-sprite-cut.png — 虹星（Nijiboshi）
来源：https://github.com/Arcarlight/Nijiboshi-Giveout-Storage
许可：CC BY 4.0
```

在游戏、视频、网站里用的话，把上面三行写进致谢名单或说明文档就够了。

## 目录约定

```
tbtak/
  sprite/     点阵图（角色行走图、战斗图，按固定格切）
  portrait/   敌人 / 角色的小型立绘（约 500×500）
  ui/         UI 素材（图标、窗框、按钮底图等）
audio/
  midi/       MIDI 文件
```

目录变了要同步改主站的 `data/resources.toml`（下面讲）。

## 主站怎么引用

主站读 `data/resources.toml`，条目里的 `file` 是**这个仓库里的相对路径**，页面自动拼成：

```
https://cdn.jsdelivr.net/gh/Arcarlight/Nijiboshi-Giveout-Storage@main/<file>
```

例如 `tbtak/sprite/Fliegen-sprite-cut.png` →
<https://cdn.jsdelivr.net/gh/Arcarlight/Nijiboshi-Giveout-Storage@main/tbtak/sprite/Fliegen-sprite-cut.png>

### 注意 jsDelivr 的缓存

jsDelivr 会把文件缓存在 CDN 上（通常几小时）。两种情况：

- **新加文件**：一般几分钟内就能访问到；
- **覆盖同名文件**：CDN 可能还给你旧的那份。

覆盖后想立刻生效，把 `@main` 换成某个 tag（例如 `@v1`），或者到
<https://www.jsdelivr.com/tools/purge> 贴 URL 清一下缓存。
最稳的办法是**不要覆盖**：新版本换个文件名（`xxx-v2.png`）。

## 上传素材

```bash
git add tbtak/sprite/新文件.png
git commit -m "点阵图：新增 xxx"
git push
```

然后在主站仓库的 `data/resources.toml` 里加一条，提交推送即可出现在分发页上。

## 体积约定

- 单文件别超过 **20 MB**（超过的话 jsDelivr 不保证能服，GitHub 也是 100 MB 硬上限）
- 整包下载走本仓库的 **Release**（单文件上限 2 GB），页面里的「整包下载」就指向那里
- 大图建议先压一压：立绘 500×500 的 PNG 一般 100–300 KB 就够
