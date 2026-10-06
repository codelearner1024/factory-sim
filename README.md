# 食品饮料工厂模拟 · 源码管理仓库（镜像）

这是工件「食品饮料工厂模拟 MVP」（space: mvp）的**源码版本管理仓库**。

## 为什么是镜像仓库
工件本体存放在平台管理目录（ts-spaces/mvp），只能通过工件构建工具修改，本身没有 git 历史。
本仓库在每轮构建交付后，把当时的 `index.html` + `assets/` + `space.json` 同步进来并提交，
于是获得完整的 git 提交记录、diff 与标签；它就是这个项目的版本账本。

## 结构
- `index.html` — 全部业务代码（单文件：CONFIG 配置层 / 仿真内核 / Three.js 场景 / 相机 / UI，分节与交接文档也在其中，页面数据抽屉内有内嵌版交接文档）
- `assets/three.min.js` — 自托管的 Three.js
- `space.json` — 工件元信息

## 版本与标签
- 每轮交付 = 一个 commit，提交信息写明该轮改了什么；稳定版打 tag（如 `v0.1.0`）。
- 基线：`v0.1.0` = 2026-10-05 控制台可隐藏版（3 小时优化马拉松开始前的稳定版），与
  `~/workspace/factory-sim-versions/v01-20261005-2222-stable-console-hide/` 快照为同一份源码（sha256 f44d07f0…）。

## 回滚
1. `git log --oneline` 找到目标版本，`git checkout <tag或commit> -- index.html assets` 取出那一版源码（或直接打开看）。
2. 让工件本体回滚：把取出的那一版作为依据，走一轮工件恢复构建恢复到该版，再把恢复结果作为新 commit 提交（回滚本身也留痕）。
3. 临时先用旧版：打开 factory-sim-versions 对应快照目录里的 exported-standalone.html（需与 assets 同目录）。

## 远程
目前仅本地仓库。需要多人协作/异地备份时可再接 GitHub 远程（私有仓库），push 后本仓库照常逐轮同步提交。
