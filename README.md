*NP manager*

在原版的脚本基础上修改。
增加了v6显示等；
重命名成：npMan (npMananger)

v1.0更新：
- 增加的“旧配置嗅探”功能，还会自动读取你旧的端口、API 前缀和 TLS 模式，并在安装时作为默认值推荐（来自旧的 .gob 数据库文件）。
- 增加 将api url和key写入/etc/nodepass/api.txt。
- 解除已安装np的情况下， 不能使用-i参数；现在可以选择4. reconfigure/install 或-i参数 覆盖安装（不改变原来的api配置）；需要修改的话可以用-k参数。
- 修正原来的ipv6地址在单栈机上会显示两次的bug。


下载安装--会显示原配置的API、运行状态
curl
```
sudo bash <(curl -sL https://raw.githubusercontent.com/2tof/npMan/main/npman.sh)
```

wget

```
wget -qO npman.sh https://raw.githubusercontent.com/2tof/npMan/main/npman.sh && sudo bash npman.sh
```

直接安装 （参数-i）【⚡️ 推荐 reconfigure/reinstall会覆盖旧脚本，而不该动原api url/key】

```
curl -sL https://raw.githubusercontent.com/2tof/npMan/main/npman.sh | sudo bash -s -- -i
```



## 菜单
  
1.Stop API (np -o)

2.Change KEY (np -k)

3.Upgrade core (np -v)

4.Reconfigure/Install (np -i)

5.Uninstall (np -u)

6.Exit

NodePass 一键安装与管理脚本
兼容主流 Linux 发行版与轻量级环境。

## ✨ Features / 核心特性

- **Cross-Platform Compatibility / 跨平台兼容**: 
  - 🐧 Systemd support: Debian 9-13, Ubuntu 18-24, CentOS 7-9, Arch Linux.
  - 🏔️ Daemonless support: Alpine Linux, Docker containers (auto fallback to background processes).
- **Smart Configuration Sniffer / 智能配置继承**: Automatically detects and inherits old configurations (Port, Prefix, TLS, API Key) during reinstall/upgrade. 无损覆盖安装，自动继承原有 API Key 和端口配置。
- **Dual-Stack Network Ready / 单双栈智能侦测**: Perfectly handles pure IPv4, pure IPv6, and Dual-Stack VPS. 完美识别纯 IPv6 机器，自动调整绑定策略。
- **Interactive Global Menu / 全局交互菜单**: Manage everything simply by typing `np` from anywhere in your terminal. 随时随地输入 `np` 呼出管理面板。
- **Auto Dependency Management / 自动环境修复**: Automatically resolves missing packages (curl, wget, tar, ps) and runtime libraries (glibc compat for Alpine).

## 🧰 Usage / 常用命令 (CLI)

Once installed, you can use the global shortcut `np` to bring up the management menu, or use the following quick flags:
安装完成后，你可以在终端任何位置输入 `np` 呼出主菜单，或者使用以下快捷命令：

| Command | Description | 功能说明 |
| --- | --- | --- |
| `np` | Show interactive menu | 呼出可视化管理面板 |
| `np -i` | Install or Reconfigure | 安装或覆盖重配 (保留原有密钥) |
| `np -s` | Show API URL and Key | 查看当前的 API 链接与密钥 |
| `np -o` | Start / Stop service | 启动或停止 NodePass 核心 |
| `np -v` | Upgrade NodePass core | 一键更新 NodePass 核心程序 |
| `np -k` | Rotate / Change API Key | 强制轮换生成新的 API 密钥 |
| `np -u` | Completely Uninstall | 彻底卸载清理 (会删除密钥数据) |

## 📁 File Structure / 目录结构

All related files and data are safely stored in a single directory:
所有文件和数据均安全地隔离存放在专属目录中：

* `/etc/nodepass/` : Main working directory (工作主目录)
* `/etc/nodepass/nodepass` : The core executable binary (核心程序)
* `/etc/nodepass/np.sh` : This management script (管理脚本源文件)
* `/etc/nodepass/gob/` : Persistent database and API Key storage (数据库与密钥存储)
* `/etc/nodepass/api.txt` : Auto-generated API info backup (安装后自动生成的配置备忘录)
* `/usr/bin/np` : Global shortcut command (全局快捷指令)

---

*Disclaimer: This is a community-driven management script. NodePass core project belongs to the original developers.*

原nodepass项目链接：
Nodepass Project

https://github.com/NodePassProject

https://nodepass.eu/

NPsh脚本
https://github.com/NodePassProject/npsh
