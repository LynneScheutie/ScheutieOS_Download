<div align="center">

# ScheutieOS

把 `chat.deepseek.com` 装进一个独立窗口

**重点是长对话导出** —— PDF、Markdown、纯文本，外加中英文分开的字数统计

**本仓库仅存放安装包，不包含源代码。**

</div>

---

## 为什么会有这个

**macOS 上没有本地的 DeepSeek 软件**——官方只有网页版和手机 App。在 Mac 上想用，只能开浏览器，在一堆标签页里翻找。这个客户端先解决的就是这件事：给网页一个独立窗口、独立图标、独立会话，让它像一款正经应用，而不是一个标签页。

**用久了真正离不开的，是网页端做不到的事：把对话导出来。** 一段几十轮的对话想留下来，只有两个办法：一张张截图，或者手动全选复制——后者会把侧边栏、按钮文字、时间戳一起带走，粘进文档还得逐行清理。

它把对话结构化提出来，三种格式任选，再补一个网页端没有的统计：这段对话多少字、其中中文多少、英文多少。

## 功能

**导出**

| 方式 | 适合 |
| --- | --- |
| **PDF**（⌘P） | 归档、打印。走系统打印管线，排版跟屏幕一致 |
| **Markdown** | 再编辑、放进笔记软件。保留标题、列表、代码块 |
| **纯文本** | 只要文字 |

另有三种复制粒度：复制全文、复制选中、复制为 Markdown（带格式）。

导出前会剥掉对话容器之外的界面元素，粘出来是干净的对话。

**字数统计**

```
共 12483 字符 · 中文 6821 字 · 英文 912 词
```

中文按字、英文按词，混排内容不会被算成一个笼统的字符数。

**其他**

- 外观强制：跟随系统 / 暗色 / 亮色
- 自定义 CSS：调字号、行距、代码块配色（用 `adoptedStyleSheets` 绕过页面 CSP）
- 多标签会话、八种界面语言

## 下载

| 文件 | 大小 | 说明 |
| --- | --- | --- |
| [ScheutieOS-8.4.2.pkg](https://github.com/LynneScheutie/ScheutieOS_Download/releases/download/macOS-v8.4.2/ScheutieOS-8.4.2.pkg) | 1.5 MB | **最省事**。双击一路「继续」，装完直接可用，不会被标记为「来自网络」 |
| [ScheutieOS-8.4.2.dmg](https://github.com/LynneScheutie/ScheutieOS_Download/releases/download/macOS-v8.4.2/ScheutieOS-8.4.2.dmg) | 1.6 MB | 有拖拽窗口，拖进「应用程序」那种熟悉的流程 |
| [ScheutieOS-8.4.2.zip](https://github.com/LynneScheutie/ScheutieOS_Download/releases/download/macOS-v8.4.2/ScheutieOS-8.4.2.zip) | 1.5 MB | 解压得到 app，自己拖到「应用程序」 |

三个内容一样，只是打包方式不同，**任选一个**即可。

> [!IMPORTANT]
> **仅支持 Apple Silicon（M1 / M2 / M3 / M4），需要 macOS 13.0 及以上。Intel Mac 用不了。**
> Windows 版目前只有源码，需要在 Windows 上自行构建，见[源码仓库](https://github.com/LynneScheutie/ScheutieOS)。

## 安装

1. 下载上面任意一个文件
2. `.pkg` 直接双击安装；`.dmg` 拖进「应用程序」；`.zip` 解压后拖进「应用程序」
3. 首次打开若提示「无法验证开发者」，到「系统设置 → 隐私与安全性」点「仍要打开」
4. 如果提示文件已损坏，终端执行：

```bash
xattr -dr com.apple.quarantine /Applications/ScheutieOS.app
```

用 `.pkg` 安装的话一般不会遇到第 3、4 步。

打开后用你自己的 DeepSeek 账号登录即可，**软件不含任何账号或密钥**，聊天记录存在你的账号里，换机器登录就能看到。

## 校验值

| 文件 | SHA-256 |
| --- | --- |
| `ScheutieOS-8.4.2.pkg` | `714e0000713056309079f14bbf927e6d628208733074ef8647d6f8e8c09d2177` |
| `ScheutieOS-8.4.2.dmg` | `ec648d95b0d5ba124a5b1ac1853fe58075927b622966fb51c7f3b0a891b232c9` |
| `ScheutieOS-8.4.2.zip` | `bb9d46132d8c984813c04f998ee57f0556d911ed9033c28281eab844f40fa15b` |

对比方式：`shasum -a 256 文件名`。

## 已知局限

- **依赖上游页面结构**。导出和统计都是解析 `chat.deepseek.com` 的 DOM，DeepSeek 改版就可能失效
- **不是官方客户端**。本项目与 DeepSeek 无关，只是把公开网页装进窗口
- **导出长度受渲染限制**。极长对话若网页本身虚拟滚动，没渲染到的部分取不到

## 关于源代码

源代码在 [ScheutieOS](https://github.com/LynneScheutie/ScheutieOS) 仓库公开，采用 MIT 许可证。

## 问题反馈

在 [Issues](../../issues) 里提交，请说明系统版本、软件版本，以及具体在做什么操作时出的问题。
