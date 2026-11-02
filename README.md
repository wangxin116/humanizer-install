# Humanizer

Humanizer 用于修改带有 AI 写作痕迹的文本，在保留原意和事实的同时，让表达更贴近作者的语气。本仓库提供 Humanizer 的技能副本和安装指南；上游项目为 [blader/humanizer](https://github.com/blader/humanizer)。

## 快速安装

在支持 Skills CLI 安装方式的环境中运行（需要 Node.js / npm）：

```bash
npx skills add blader/humanizer --global
```

仅为当前项目安装时，省略 `--global`。安装后重新加载或重启使用该技能的智能体。

以上命令安装的是上游 `blader/humanizer`。安装本仓库副本的方法，以及插件安装和排障说明，见 [安装指南](install.md)。

## 基本用法

在支持技能命令的环境中输入：

```text
/humanizer
请润色以下文本，保留原意和事实：
[粘贴文本]
```

也可以提供自己的写作样本，让技能参考句长、用词、标点和衔接方式。具体命令形式取决于所用平台。

## 文件模式

在支持文件编辑的平台中，可以指定需要修改的文件：

```text
/humanizer docs/launch-post.md
```

文件模式只将最终改写结果写回文件，修改正文，保留代码块、行内代码、命令、路径、YAML 元数据、数据和表格等内容。

直接粘贴文本时，默认返回初稿、仍需调整的模式简表和最终改写；被其他任务调用时，嵌入模式只返回最终文本。

## 文档与源码

- [SKILL.md](SKILL.md)：技能定义、编辑流程和写作规则。
- [install.md](install.md)：完整安装、用法和排障说明。
- 上游源码：[blader/humanizer](https://github.com/blader/humanizer)。
- 当前分发仓库：[wangxin116/humanizer-install](https://github.com/wangxin116/humanizer-install)。
- 许可证：MIT。

技能要求保留已有事实，不编造姓名、日期、数字或引用。
