# Windows系统下使用雨云VPS搭建Minecraft 1.19.4服务器完整指南

## 服务端选择与准备

本教程采用**Mohist 1.19.4**服务端，该服务端完美兼容Forge模组和Bukkit/Spigot/Paper插件体系。无论您想创建模组服还是插件服，都能获得稳定流畅的游戏体验。

### Mohist核心优势
- **卓越性能**：整合Paper核心优化，即使加载大量模组/插件也能保持流畅运行
- **完美兼容**：同时支持Forge模组和Bukkit系插件，扩展性极强
- **持续更新**：活跃的开发社区确保及时适配最新Minecraft版本

👉 [【点击查看】2025年最新雨云优惠码及特价云服务器方案汇总](https://bit.ly/RainYun)

## 服务器配置指南

### 硬件选择建议
- **推荐配置**：4核CPU/8GB内存起步（Windows系统本身占用较大资源）
- **系统选择**：Windows Server 2019
- **网络配置**：NAT模式可开通15个端口，完全满足MC服务器需求

### 环境准备步骤
1. 关闭防火墙（或仅开放25565等必要端口）
2. 设置端口映射（NAT用户需将25565端口映射到公网）
3. 安装适配的JDK版本：
   - 1.12.2及以下：Java 8
   - 1.16.5：Java 11
   - 1.17+：推荐Java 17（建议使用阿里Dragonwell优化版）

## 服务端部署流程

### 快速启动方案
1. 创建专用文件夹存放服务端文件
2. 下载Mohist官方服务端jar包
3. 创建启动脚本run.bat：
bash
java -Xms128M -XX:MaxRAMPercentage=95.0 -Dfile.encoding=UTF-8 -Duser.country=CN -jar mohist-1.19.4-192-server.jar
pause

### 参数解析
- `-Xms128M`：设置JVM初始内存为128MB
- `-XX:MaxRAMPercentage=95.0`：限制JVM最大使用95%系统内存
- `-Dfile.encoding=UTF-8`：避免中文乱码问题
- `-Duser.country=CN`：自动使用国内镜像源加速资源下载

## 服务器管理技巧

### 基础配置优化
- 修改server.properties文件：
  - `online-mode=false` 关闭正版验证
  - 调整view-distance视距参数
  - 设置max-players最大玩家数

### 运维建议
1. 使用`stop`命令安全关闭服务端
2. 定期备份world文件夹
3. 通过OP指令管理玩家权限：
   - `/op [玩家名]` 授予管理员权限
   - `/deop [玩家名]` 撤销权限

## 客户端连接指南

在游戏客户端中添加服务器时，输入格式为：`映射公网地址:端口号`。成功连接后即可与好友共同探索您打造的专属Minecraft世界！

通过本教程，您已掌握从零开始搭建Minecraft服务器的完整流程。如需更高性能的服务器方案，可随时升级雨云VPS配置，获得更流畅的游戏体验。