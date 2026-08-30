# Github-direct

[![Latest release](https://img.shields.io/github/v/release/FxxkLocation/Github-direct?style=flat-square)](https://github.com/FxxkLocation/Github-direct/releases/latest)
[![Source](https://img.shields.io/badge/source-FxxkLocation%2FGithub--direct-181717?style=flat-square&logo=github)](https://github.com/FxxkLocation/Github-direct)
[![LSPosed API](https://img.shields.io/badge/LSPosed_API-101%2B-6f42c1?style=flat-square)](https://github.com/LSPosed/LSPosed)

Github-direct 是 Android Root / LSPosed 环境中的选择性网络连通性模块。它将动态 DNS 处理、可信候选校验、透明 TCP 中继与故障开放机制组合为一个按应用启用的数据面；GitHub 是当前已完成真机验证的基线。

当前版本：**1.1.1**（`versionCode 3`）

## 主要能力

- 现代 LibXposed / LSPosed API 101+ 模块，按已选择的应用作用域生效。
- Root 透明后端在启动时探测 `su`、iptables、owner、REDIRECT 与可选 IPv6 能力；不满足条件时保持 fail-open，不遗留本模块规则。
- 基于可信来源和严格 TLS 校验维护候选，避免将未经验证的解析结果提升为上游目标。
- 支持 IPv4 透明中继；只有完整 IPv6 能力与监听器均就绪时才启用 IPv6 接管。
- 对显式授权的内置运行时宿主提供受限的 TCP/443 捕获；未知流量按原始目的地透传。
- 状态页显示 Root 服务、活动规则代次、候选数与失败阶段，便于自行排障。

## 1.1.1

- 修复部分 legacy/nft `iptables -S` 实现重排 owner、目标地址、协议参数时，Root 透明后端把已安装规则误判为缺失的问题。
- 防火墙启动校验与运行中健康检查改为按规则语义字段比较，不依赖厂商工具箱的文本排列。
- 不包含机型、厂商或 UID 特判；满足能力条件的设备自动适配。

## 要求

- Android 8.0+（API 26）
- LSPosed 或兼容现代 API 101+ 的框架
- Root 透明模式需要 Magisk / KernelSU 提供可用的 `su` 与 iptables；IPv6 接管需要额外通过完整能力探测

## 安装与配置

1. 从 [Github-direct 1.1.1](https://github.com/FxxkLocation/Github-direct/releases/tag/1.1.1) 下载 APK 并安装。
2. 在 LSPosed 中启用模块，只选择需要使用该模块的目标应用。
3. 打开 Github-direct，授予 Root 权限后，在应用内选择相同的 Root 作用域。
4. 启动服务并确认状态页没有失败阶段；能力或规则校验失败时，模块会回滚自己的规则并保持网络故障开放。

请勿对无关应用使用全量作用域，也不要把不受信任的证书安装为系统信任根。

## 下载与校验

- 主发布页：[FxxkLocation/Github-direct Releases](https://github.com/FxxkLocation/Github-direct/releases)
- 本版本 APK：`Github-direct-1.1.1.apk`
- SHA-256：`d4b372925751fbed2c128a2c14991bcf276750a5b26344621bbf63e5cdc8c330`

当前 APK 保持项目既有签名以确保已有安装可升级；正式发布密钥迁移会单独公告并提供证书指纹。

## 源码与反馈

- 源码：[FxxkLocation/Github-direct](https://github.com/FxxkLocation/Github-direct)
- 问题反馈：[GitHub Issues](https://github.com/FxxkLocation/Github-direct/issues)
