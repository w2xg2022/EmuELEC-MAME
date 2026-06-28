# EmuELEC-MAME

预编译 EmuELEC 的 MAME 系 libretro 核心（mame2003-plus、mame2010），供 [w2xg2022/EmuELEC](https://github.com/w2xg2022/EmuELEC) 主建置直接下载安装，避免在主建置（尤其云端 CI）中重新编译这些重量级核心，节省磁盘空间与建置时间。

## 为什么需要这个仓库

MAME 系核心（尤其完整版 mame）编译耗时长、耗磁盘/内存巨大，是云端 CI（GitHub Actions 免费 runner 磁盘上限约 146GB）建置失败的主要原因之一。把这些核心的编译工作拆到独立仓库单独处理，主仓库的 package.mk 改为直接下载这里发布的预编译 `.so`，从根本上避开主建置的资源瓶颈。

## Release 命名规则

每个 release 标签格式：`cores-<EmuELEC主仓库commit短hash>`，对应该次编译时使用的 EmuELEC 工具链版本（ABI 兼容性以此为准）。

## 包含核心

- `mame2003_plus_libretro.so`（[libretro/mame2003-plus-libretro](https://github.com/libretro/mame2003-plus-libretro)）
- `mame2010_libretro.so`（[libretro/mame2010-libretro](https://github.com/libretro/mame2010-libretro)）
