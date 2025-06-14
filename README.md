# Surge 配置与资源整合

## 项目概述

本仓库汇集了 Surge 相关的实用配置、规则集及模块资源，旨在为 iOS/macOS 平台的网络代理与开发提供便捷的整合方案。Surge 作为强大的网络工具，支持代理接管、规则分流、HTTPS 解密等功能，适用于开发者调试与网络优化场景。

## 核心资源链接

### 官方文档与指南

- **Surge 官方使用手册**  
  📚 [https://surge.mitsea.com/overview](https://surge.mitsea.com/overview)  
  涵盖核心工作流（接管、处理、转发、拦截）及跨平台特性（Mac/iOS 专属功能）。

- **Surge 官方中文指引**  
  📖 [https://manual.nssurge.com/book/understanding-surge/cn](https://manual.nssurge.com/book/understanding-surge/cn)  
  深入解析原理，包括代理接管方式、规则系统、TLS 与 MITM 机制等。

### 配置与规则集

- **深港有喵自用配置**  
  🐇 [https://github.com/Rabbit-Spec/Surge](https://github.com/Rabbit-Spec/Surge)  
  - 包含分流策略组（如 Netflix/YouTube 香港节点、OpenAI 代理）
  - 模块与脚本集合，支持流媒体解锁检测

- **SukkaW 规则集**  
  🌐 [https://github.com/SukkaW/Surge](https://github.com/SukkaW/Surge)  
  - 分类规则组（广告拦截、流媒体、AI 服务、Telegram 等）
  - 支持 Surge/Clash Meta/sing-box 多平台适配

### 规则与模块库

- **Sukka Ruleset Server**  
  🧩 [https://ruleset.skk.moe](https://ruleset.skk.moe)  
  - 域名规则集（domainset）、IP 规则集（ip）、非 IP 规则集（non_ip）
  - 包含 Apple/Google/Microsoft 等厂商 CDN 直连规则

- **Surge 模块集合**  
  ⚙️ [https://whatshub.top/surge](https://whatshub.top/surge)  
  - 去开屏广告、流媒体字幕优化、应用解锁模块（如 bilibili/Spotify）
  - 系统工具类模块（网速测试、节点信息面板）

## 功能特性

### 核心功能概览

1. **智能分流策略**  
   - 基于域名/IP CIDR/GeoIP 的规则匹配
   - 策略组动态选择（URL Test 测速、SSID 切换、负载均衡）

2. **HTTPS 解密与 MITM**  
   - 中间人攻击技术解密加密流量
   - 自定义 CA 证书生成与系统信任配置

3. **DNS 优化**  
   - 并发解析与乐观解析（Optimistic DNS）
   - 本地 DNS 映射与域名劫持防御

### 推荐使用场景

- 开发者网络调试与请求拦截
- 流媒体服务区域解锁（Netflix/Disney+/YouTube）
- 广告拦截与隐私保护
- 跨国服务代理加速（如 OpenAI/GitHub）

## 快速开始

### 配置导入指南

1. **Surge 配置文件结构**  
   ```
   Surge/
   ├── Conf/              # 主配置文件
   ├── Module/            # 功能模块
   └── Script/            # 脚本规则
   ```

2. **使用步骤**  
   - 在 Surge 中导入 `Conf` 目录下的配置文件
   - 在「模块」选项中加载 `Module` 目录下的 .sgmodule 文件
   - 调整策略组节点配置，匹配个人网络环境

### 规则优先级说明

1. **规则匹配顺序**  
   - 自上而下依次匹配，建议将高频规则（如国内域名直连）置于顶部
   - IP 规则会触发 DNS 解析，建议将非 IP 规则（non_ip）优先配置

2. **SukkaW 规则组最佳实践**  
   ```markdown
   # 推荐规则顺序
   - RULE-SET,https://ruleset.skk.moe/List/domainset/reject.conf,REJECT
   - RULE-SET,https://ruleset.skk.moe/List/non_ip/direct.conf,DIRECT
   - RULE-SET,https://ruleset.skk.moe/List/ip/china_ip.conf,DIRECT
   - FINAL,Proxy              # 最终代理策略
   ```

## 免责声明

1. 本仓库资源仅供学习研究，请勿用于商业或非法用途。
2. 机场服务存在合规风险，建议自行评估网络使用场景。
3. 规则集可能涉及第三方服务解析，作者不对内容合法性负责。
4. 使用 MITM 功能可能影响部分应用安全性，建议仅在开发环境启用。

## 特别致谢

- [Rabbit-Spec](https://github.com/Rabbit-Spec) 提供的分流配置框架
- [SukkaW](https://github.com/SukkaW) 维护的开源规则集
- Surge 官方团队的技术文档支持

## 版权声明

本仓库整合资源遵循原作者版权协议：
- 深港有喵配置：MIT 许可证
- SukkaW 规则集：AGPL-3.0 许可证
- 官方文档：NSSurge 版权所有

如需商业使用，请联系原作者获取授权。
