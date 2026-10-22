[English](README.en.md)

# susfs4ksu-lkm

SUSFS 的可加载内核模块（LKM）移植，面向三星 RKP/KDP/DEFEX 设备：不重编译内核即可获得 susfs 隐藏，
配合 late-load 的 KernelSU 使用。

基于 [inforcqb/susfs4ksu-lkm](https://github.com/inforcqb/susfs4ksu-lkm) ，
功能源头 [susfs4ksu](https://gitlab.com/simonpunk/susfs4ksu)。

## 使用

Release 提供：

- `susfs_samsung_lkm-<kmi>.ko` —— 按内核 KMI 三选一（android13-5.15 / android14-6.1 / android15-6.6）
- `susfs-lkm-module-<tag>-arm64.zip` —— KernelSU 模块包：管理器刷入后**软重启**，`late-load.sh`
  按 `/proc/sys/kernel/osrelease` 自动选 ko 加载（`expose_proc=1`，只加载、不设 susfs 规则；
  系统已有 susfs 则跳过）。硬重启后两个模块都不在，需重跑 late-load 流程。

手动加载 / 卸载：

```sh
insmod susfs_samsung_lkm.ko   # 非 KernelSU 设备用 release 自带的 bin/susfs_insmod
rmmod susfs_samsung_lkm
```

`/proc/susfs_*` 控制节点见 [PROC_INTERFACES.md](PROC_INTERFACES.md)。

## License

GPL-3.0。仅用于技术研究与学习，风险自担。
