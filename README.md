# Student Feedback Skill｜学生课堂反馈 Skill

[![Codex Skill](https://img.shields.io/badge/Codex-Skill-111827)](https://learn.chatgpt.com/docs/build-skills)
![Version](https://img.shields.io/badge/version-1.1-2563eb)
![Language](https://img.shields.io/badge/language-%E4%B8%AD%E6%96%87-e11d48)

把老师的课堂速记，整理成**真实、自然、可直接通过微信发送给家长**的中文课堂反馈。

适用于少儿编程、教培课堂和一对一教学，支持普通课堂、小讲师、综合反馈、已有反馈重写，以及多名学生批量生成。

## 为什么做这个 Skill

老师写课堂反馈时，常见的难点不是“没内容”，而是：

- 课堂记录零散，整理起来耗时；
- 容易把局部表现扩大成整体能力；
- 负面情况太直接，或被过度美化；
- 每条反馈都像同一个模板；
- 一大段文字不方便家长快速阅读。

这个 Skill 会先提取明确事实，再选择有证据的评价维度，用自然的微信语气组织为 2～3 个短段落。

## 核心能力

- **忠于课堂事实**：不编造行为、正确率、专注度、进步或知识掌握情况。
- **控制评价边界**：某个知识点表现好，不自动扩大为“基础非常扎实”。
- **保留真实程度**：不会把“反复出现”弱化为“偶尔出现”，也不会把“有时候”写成绝对结论。
- **描述行为，不贴标签**：把“粗心、不认真、依赖老师”等判断转换成可观察的课堂表现。
- **区分会做、会讲与真理解**：小讲师表达流畅，不等于知识一定正确。
- **自然分段**：信息充分时按“整体情况—具体表现—提升方向”组织成 2～3 个短段落。
- **支持多人输入**：每位学生独立生成，避免姓名、知识点和课堂表现串线。

## 效果示例

### 老师原始记录

```text
王俊皓：上次课他讲解了全局变量和局部变量的题目，能够清晰分辨出，
题目中每一个变量是全局变量还是局部变量，能说出来，局部变量的改变
不会影响全局变量，对于全局变量和局部变量的知识点掌握还是非常不错的！

在这几次课中，整体的专注力和课堂纪律的表现，觉得相比于之前是有进步的。
```

### 生成结果

> 俊皓爸爸妈妈好，俊皓上次课讲解了全局变量和局部变量相关题目，能够清楚判断题目里的每个变量属于全局变量还是局部变量，也能说出局部变量的改变不会影响全局变量，说明这部分知识掌握得比较清楚👍
>
> 这几次课里，俊皓整体的专注力和课堂纪律相比之前也有进步，希望继续保持现在的课堂状态💪

## 安装

### 方法一：使用 Codex 的 Skill Installer

在 Codex 中输入：

```text
$skill-installer 请从 https://github.com/code-stzzz/student-feedback-skill 安装这个 Skill
```

### 方法二：手动安装到个人 Skill 目录

Windows PowerShell：

```powershell
git clone https://github.com/code-stzzz/student-feedback-skill "$HOME\.agents\skills\student-feedback-skill"
```

macOS / Linux：

```bash
git clone https://github.com/code-stzzz/student-feedback-skill "$HOME/.agents/skills/student-feedback-skill"
```

Codex 通常会自动识别新增或更新的 Skill；如果没有出现，请重启 Codex。安装和目录规则可参考 [OpenAI 官方 Build skills 文档](https://learn.chatgpt.com/docs/build-skills)。

## 使用

在 Codex 中明确调用：

```text
$student-feedback-skill

崔梓懿：这几次课主要学习了自定义函数、全局变量和局部变量。
他能够独立完成“用自定义函数判断一个数是否为质数”的编程题。
```

也可以直接粘贴一名或多名学生的课堂记录，让 Codex 根据 Skill 的描述自动匹配。

## 支持的反馈类型

| 类型 | 典型输入 | 重点处理 |
| --- | --- | --- |
| 普通课堂 | 专注、做题、编程、互动、知识点 | 选择有事实支撑的评价维度 |
| 小讲师 | 上台讲题、复述概念、回答追问 | 区分知识正确性、表达和理解深度 |
| 综合反馈 | 普通课堂与小讲师信息同时出现 | 融合成一条可直接发送的反馈 |
| 已有反馈重写 | 老师已经写出一版长反馈 | 提取事实、去重并重新组织重点 |
| 多学生批量 | 一次提供多名学生记录 | 独立生成，避免信息串线 |

## 评价原则

规则冲突时，按以下顺序判断：

```text
真实性
→ 证据范围
→ 严重程度与不确定性
→ 反馈类型
→ 重要变化
→ 具体行为
→ 最小充分表达
→ 自然微信感
→ 分段可读性
```

最终原则：**不编、不拔高、不贴标签、不洗白。**

详细规则：

- [普通课堂评价与事实保真规则](references/evaluation-rules.md)
- [小讲师与综合反馈规则](references/small-teacher-rules.md)
- [语言、长度、分段与 Emoji 风格](references/style-guide.md)

## 项目结构

```text
student-feedback-skill/
├── SKILL.md
├── references/
│   ├── evaluation-rules.md
│   ├── small-teacher-rules.md
│   └── style-guide.md
└── tests/
    ├── normal-cases.md
    ├── edge-cases.md
    └── gold-cases.md
```

## 测试与质量门槛

项目包含普通案例、边界案例和黄金回归案例，覆盖：

- 知识错误与表达流畅同时出现；
- 正面和负面课堂表现并存；
- 主观标签与老师情绪的转换；
- 信息不足、严重程度和不确定性；
- 多学生批量输入与信息隔离；
- 信息充分时的自然分段。

较大规则修改后，应优先运行 [黄金回归案例](tests/gold-cases.md)。任一案例触发硬失败时，不应发布新版本。

## 适合谁

- 少儿编程老师与助教；
- 教培机构和课程顾问；
- 需要稳定输出课堂反馈的教学团队；
- 希望把家校沟通规范沉淀为可复用流程的人。

如果你有新的课堂场景或边界案例，欢迎提交 Issue。
