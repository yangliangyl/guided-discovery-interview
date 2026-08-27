# Guided Discovery Interview

一个用于“引导式发现访谈”的 Agent Skill：从具体经历出发，通过连续追问、判断、反证和视角切换，帮助用户发现尚未说清的认知、能力、机会与盲点。

它不是固定问题清单，也不是把用户的朴素表达包装成宏大概念。它更关注：

- 追问是否紧扣上一句话；
- 结论是否有具体事件和行为证据；
- Agent 是否敢于判断，同时允许用户纠正；
- 是否能识别认知变化，而不只是优化措辞；
- 是否能管理支线并返回主线；
- 是否在信息充分后及时停止下钻。

> 当前版本：`v0.1`。这是一个等待真实用户检验的公开实验版本，而不是完成品。

## 适用场景

- 复盘工作经历，发现习以为常的专业能力；
- 从项目、日记、对话或真实事件中萃取隐性认知；
- 澄清一个模糊判断，例如“我不擅长销售”；
- 深挖专业决策背后的线索、目标、选项和不确定性；
- 从客户视角识别被自己低估的价值；
- 在长对话中保留主线、认知变化和待追问题。

不适合：只想快速总结文本、寻求单次建议，或不希望被持续追问和挑战的场景。

## 设计结构

```text
guided-discovery-interview/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── probing-toolkit.md
    └── session-ledger.md
```

- `SKILL.md`：访谈立场、核心循环、判断标准、主线控制和行动边界。
- `references/probing-toolkit.md`：下一步怎么追，包括 DICE、连续追问、关键决策深挖和防引导原则。
- `references/session-ledger.md`：暂停或跨会话继续时，保存主线与认知变化，不把摘要当成原始证据。
- `agents/openai.yaml`：Codex 中的显示信息和默认调用方式。

设计说明详见 [SKILL.md](SKILL.md)。

## 安装

### Codex

```bash
git clone https://github.com/yangliangyl/guided-discovery-interview.git \
  ~/.codex/skills/guided-discovery-interview
```

### Claude Code

```bash
git clone https://github.com/yangliangyl/guided-discovery-interview.git \
  ~/.claude/skills/guided-discovery-interview
```

如果你同时使用多个 Agent 框架，建议只保留一份实体目录，再通过软链接接入不同框架，避免多份 Skill 分叉。

## 使用示例

直接调用：

```text
使用 $guided-discovery-interview 采访我。
从具体经历开始，一次只问一个主要问题；不要急着总结，要有判断，也允许我纠正你。
```

带主题调用：

```text
使用 $guided-discovery-interview，帮我挖掘自己在数据分析工作中已经形成、但没有意识到的方法和能力。
```

带材料调用：

```text
使用 $guided-discovery-interview，结合我授权你读取的项目文件和日记采访我。
把文件当作证据，不要只做内容总结。
```

## 建议的测试方式

请带着一个真实但尚未想清楚的问题，完成一次连续访谈。测试后，优先反馈具体片段：

- 哪一次追问让你说出了此前没有意识到的内容？
- 哪一段擅自解释了你，或者显得“伪深刻”？
- 哪里追得过深、重复或偏离主线？
- 哪个判断改变了你的认识，哪个判断只是换了漂亮说法？
- 访谈结束后，你是否获得了更准确的判断或可验证的下一步？

欢迎通过 GitHub Issues 提交真实案例。请删除隐私、公司数据和敏感信息；只保留理解问题所需的最小上下文。

## 迭代原则

- 优先根据真实失败案例做窄修正，不为假想边界累积规则；
- 专业访谈材料只补强追问能力，不取代主线控制、判断和反证；
- 不用点赞、好评或“聊得很舒服”替代认知变化证据；
- 保留不确定性，不把个人案例直接写成普遍规律。

## License

[MIT](LICENSE)
