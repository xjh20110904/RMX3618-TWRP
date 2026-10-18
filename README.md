# 真我V30T (RMX3618) TWRP 3.7.x

基于 TWRP 3.7.x（twrp-12.1 源码）编译的 recovery 镜像。
本机为 A/B 设备，recovery 集成在 boot 分区，产物为 **boot.img 格式**。

## 文件说明
- `twrp-RMX3618-boot.img` — TWRP 恢复镜像（boot格式，64MB）
  - 内核/DTB 提取自原厂 boot.img（未修改）
  - ramdisk 为全新编译的 TWRP 3.7.x

## 使用方法（二选一）
### 1. 临时启动（推荐，不写入分区，重启恢复原样）
```
fastboot boot twrp-RMX3618-boot.img
```
### 2. 永久刷入 boot 分区
```
fastboot flash boot twrp-RMX3618-boot.img
```
> ⚠️ A/B 设备没有独立 recovery 分区，**不要刷 recovery 分区**！
> 永久刷入会覆盖原厂 boot（包含 root 组件），root 会丢失。

## 前置条件
- Bootloader 已解锁（真我官方"深度测试"申请，约7天审核）
- 已备份全部数据
- 刷机有风险，操作不当可能变砖

## 常见问题
- 触摸无反应：连接 OTG 鼠标操作
- 刷入后无法开机：重新刷回原厂 boot.img
- 如需 root：请使用原厂 boot.img 修补（APatch/KernelSU），不要用本镜像修补

## 构建信息
- 设备树：twrpdtgen 自动生成（device/oplus/ossi）+ 修复
- 源码：minimal-manifest-twrp (twrp-12.1)
- 内核：原厂 prebuilt (4.19.191+)
