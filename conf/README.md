# 🌊 Surge 高级定制配置文件

一份追求极致灵活性、高度自动化与清晰可维护性的 Surge 配置方案。

---

## 核心特性

### ✨ 智选 + 手选 + 故障转移 (故转)
这套配置的核心是名为 **“故转”** 的策略。您可以为常用地区**固定一个节点**来保持 IP 稳定；当该节点意外失效时，系统将**自动无缝切换**到延迟最低的备用节点，确保网络永不中断；待您手动选择的节点恢复后，又会**自动切回**。这套机制兼顾了 IP 的稳定性与连接的可靠性。

### ✨ 区域化节点分组
配置会自动将您机场订阅中的所有节点，按照 **香港、美国、日本、台湾、韩国、新加坡** 等主要地区，以及 **亚洲其它、低价购买区、欧洲其它** 等特殊用途进行分类，让您在选择节点时清晰明了。

### ✨ 精细化应用分流
我们为几乎所有常用 App（如 GitHub、人工智能、网飞视频、油管视频等）都创建了独立的策略组。这意味着您可以单独控制每个 App 的出口策略，实现“让AI走美国，让网飞走日本”的精细化操作，彼此互不干扰。

### ✨ 强大的广告拦截与隐私保护
集成了社区优选的高质量拦截规则，可以在网络底层高效屏蔽各类网页广告、App内置广告、恶意软件、追踪脚本以及钓鱼网站，同时还能优化特定软件（如Adobe）的网络请求行为，防止内存泄漏。

### ✨ 智能兜底策略
**🐟 漏网之鱼** 是一个特殊的“收容所”，所有未被精确规则匹配到的流量，最终都会被导向这里。您可以通过手动选择它的出口，来应对各种临时的、未知的网络访问需求（例如访问一个规则库里没有的土耳其网站）。

**🪄 手动选择** 则是配置的“总开关”或“遥控器”。大部分应用的默认出口都设置为跟随它，让您可以一键改变多数应用的全局出口区域，方便快捷。

---

## 策略组设计理念

本配置的策略组经过精心设计，形成了一个清晰的四层依赖结构，就像盖房子一样，从地基到屋顶，层层递进。

### ① 底层 - 节点池 🏊‍♂️
这是所有策略的基础，包含了您的 **`✈️ 主力机场`** 和 **`🚀 备用机场`** 订阅，以及从中筛选出来的 **`🇭🇰 香港-手动`** 和 **`🇭🇰 香港-智选`** 等最基础的节点列表。

### ② 逻辑层 - 故转核心 🔄
这一层构建了我们独特的 **`🇭🇰 香港-故转`** 策略。它组合了“手动”和“智选”两个节点池，实现了“首选手动，失效自动切换”的核心逻辑。

### ③ 控制层 - 核心开关 🕹️
这一层定义了上面提到的 **`🪄 手动选择`** 和 **`🐟 漏网之鱼`** 两个核心控制策略组。它们是您日常操作最常接触的“遥控器”，负责调度下面所有的“故转”策略组。

### ④ 应用层 - 具体服务 📱
这是最顶层的应用策略，例如 **`🤖 人工智能`**、**`🎬 网飞视频`**、**`💻 GitHub`** 等。您可以让它们默认跟随 **`🪄 手动选择`** 的全局设定，也可以在需要时，为它们单独指定一个出口（比如强制“网飞视频”走“日本-故转”）。

---

## 如何使用

### 1. 下载与配置
首先，下载本仓库中的 `.conf` 配置文件。用任意文本编辑器打开它，找到 `[Proxy Group]` 部分的 `✈️ 主力机场` 和 `🚀 备用机场` 这两行，将 `policy-path=` 后面的链接替换为您自己的机场订阅链接。

### 2. 导入 Surge
对于 **macOS** 用户，可以直接将修改后的 `.conf` 文件拖入 Surge 的主窗口。
对于 **iOS** 用户，可以通过隔空投送（AirDrop）、iCloud Drive 或其他文件共享方式将 `.conf` 文件导入到手机中，然后在 Surge App 内选择“从本地导入配置”。

### 3. 开始使用
导入成功后，建议您进行如下初始设置以获得最佳体验：
* **设置全局出口**: 在 Surge 的策略组菜单中，找到 **`🪄 手动选择`**，选择您偏好的默认出口区域，例如选择 **`🇭🇰 香港-故转`**。
* **固定常用节点**: 在您选择的区域策略组中，例如 **`🇭🇰 香港-手动`**，选择一个您最常用且稳定的节点。
* **按需单独设置**: 对于有特殊需求的应用（如 **`🎬 网飞视频`**），可以单独进入其策略组，选择指定的区域出口。

现在，一套为您深度定制的、强大且稳定的 Surge 配置已经准备就绪。

希望它能为您带来稳定、流畅、自由的网络体验！
