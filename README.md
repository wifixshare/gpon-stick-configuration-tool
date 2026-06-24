# 猫棒助手 gpon stick configuration tool

![猫棒助手软件海报](猫棒助手软件海报.png)

猫棒助手是一款用于通过 SSH 配置 GPON 猫棒 / GPON SFP Stick 的桌面工具。它可以帮助你读取和写入原光猫认证信息、设置 VLAN、查看 PON 注册状态、测试拨号、获取日志并执行固件维护操作。

> This tool is a GPON stick configuration assistant for Windows and macOS. It focuses on SSH-based setup, status checks, VLAN configuration, logging, and maintenance.

## 下载

| 系统 | 文件 |
| --- | --- |
| Windows | [猫棒助手gpon_onu_config.exe](猫棒助手gpon_onu_config.exe) |
| macOS | [猫棒助手gpon_onu_config_macos.zip](猫棒助手gpon_onu_config_macos.zip) |

macOS 用户下载 zip 后解压，打开 `gpon_onu_config.app`。如果系统提示来自未知开发者，可以在“系统设置 > 隐私与安全性”中允许打开，或右键选择“打开”。

## 适用场景

- 写入原光猫的 GPON SN、LOID、LOID CheckCode 或 PLOAM Password。
- 设置上网 VLAN、IPTV 组播 VLAN、VLAN 转换和兼容规则。
- 查看 PON 状态、光功率、温度、固件版本、设备型号和 OMCID 信息。
- 在 Windows 上进行 PPPoE 拨号测试。
- 获取调试日志、恢复出厂、维护双 IP 管理入口。
- 按设备型号检测和刷写在线固件，或刷写本地 `.image` 固件。

## 快速使用

1. 从原光猫后台或标签记录 GPON SN、LOID、LOID 密码 / CheckCode、PLOAM Password、上网 VLAN 和 IPTV VLAN。
2. 将电脑连接到猫棒管理网络，默认管理地址通常为 `192.168.1.10`。
3. 打开猫棒助手，顶部连接区填写 Host、Port、User 和 Password，点击“连接”，再点击“读取”。
4. 进入“快速设置”，填写原光猫认证信息和关键 VLAN。
5. 点击“保存并应用”，等待约 8 秒后点击“重启”，然后等待猫棒重启完成。
6. 重新连接后点击“刷新状态”，PON 状态显示 `O5` 通常代表注册成功。
7. 注册成功后，在路由器中设置 PPPoE 拨号上网，或在 Windows 版里先做拨号测试。

完整图文说明请看：[使用说明教程.md](使用说明教程.md)

## 重要安全提醒

GPON SFP ONT / 猫棒会接入运营商的共享光网络。错误的认证信息、固件、VLAN、OMCI 或高级参数可能导致无法注册、反复重启、业务中断，甚至影响同一 PON 口下的其他用户。

- 只填写来自自己原光猫或运营商授权的信息。
- 不确定的高级参数不要随意修改，尤其是 MIB、OMCID、OMCC 和固件刷写相关功能。
- 刷写固件前确认设备型号、固件版本和 MD5。
- 刷写或重启过程中不要断电、不要拔出猫棒。
- 光功率过强可能损坏设备，做下行光相关测试时尤其要谨慎。
- 本项目只提供通用配置工具和使用说明，不提供运营商专用配置、绕过认证或未授权接入指导。

## 常见判断

| 现象 | 优先检查 |
| --- | --- |
| PON 状态为 `O5` | 认证成功，可继续检查拨号、VLAN 和路由器设置 |
| PON 状态非 `O5` | GPON SN、LOID、PLOAM Password、光纤信号、OMCI 兼容 |
| 有光功率但无法 `O5` | 认证信息、运营商绑定、MIB/OMCI 参数 |
| 已经 `O5` 但无法拨号 | PVID、强制 ME 规则、宽带账号密码、运营商绑定 |
| 软件连接不上 | 电脑网段、猫棒 IP、SSH 开启状态、账号密码 |

## 项目文件

- `猫棒助手gpon_onu_config.exe`：Windows 程序。
- `猫棒助手gpon_onu_config_macos.zip`：macOS 程序压缩包。
- `使用说明教程.md`：完整使用教程。
- `猫棒助手软件海报.png`：软件海报。
- `icon_128x128@2x.png` / `app_icon_size_preview.png`：项目图标素材。

## 图标

![猫棒助手图标](icon_128x128@2x.png)

## 致谢

README 的安全提醒和结构参考了 [Anime4000/RTL960x](https://github.com/Anime4000/RTL960x) 对 xPON/GPON 配置风险的说明。请始终在合法、授权和不影响他人的前提下使用本工具。
