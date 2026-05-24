## Agents's rule
这里做了中英对照：[English](kinfai_agent_note/rules/Agents_Rule_EN) | [简体中文](Agents_Rule_CN.md)
这里参考了 Andrej 的行为准则，可以直接在 [Github](https://github.com/multica-ai/andrej-karpathy-skills) 上通过插件的方式进行安装到自己的 Agnet 工作空间中。
另外还增加了一些自己在使用过程中发现的一些问题，并针对**中文版本**使用了更加绝对严肃的语气来规范 Agent 的行为。
**注意：** 编写必须简明，禁止废话。


## Cpp Code Style
尝试规范 Agent 的代码输入准则，一般来说 Agent 会通过阅读代码知道你的代码规范。但是难保 Agent 会一些诸如幻觉之类的原因，会弄乱代码的格式。
[cpp_stysle_example.md](cpp_stysle_example.md) 是我根据规范文档，使用 deepseek-v4-pro 输出的，基本正确。
目前的方案是：
1. 将 [cpp_stysle.md](cpp_stysle.md) 拷贝到 `.claude/` 或者是 `.codex/` 中的 rules 文件夹下（没有就自己创建一个）。
2. 在 Rule 中注明：“编写 C/C++ 代码时必须遵循 @rules/cpp_stysle_doc.md 中的声明”。
 - **！！！ 注意 ！！！** ：这部分还在进行验证！