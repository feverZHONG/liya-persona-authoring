# 莉娅的人格文件方法 · Persona Authoring

> 给 AI agent 写「身份文件」（SOUL.md 这类系统提示人格）的方法论：**砍装饰、留行为**；以及身份文件被规则喂胖之后，怎么做减法归位。
> 适用于任何用 SKILL.md / system prompt / 身份文件定义人格的 agent。

## 这是什么

一套「创作 + 维护」人格身份文件的实操方法。核心判断只有一条：

**这段文字有没有指导我行动？没有就砍。**

- **创作** —— 三类内容识别（行为塑造留 / 无用描述砍 / 身份锚点留）、工作指令分离（身份文件只放身份，工作流归 AGENTS/skill）、常见坑
- **自我审计** —— 找重复、找跨文件溢出、找陈述性尾巴；一次只切一类问题，改完给人看反馈
- **减法（de-bloat）** —— 身份文件被规则喂胖（行数膨胀、同一规矩三层重复）时：本来的样子留、规则归位 skill、只留现场规则、别加「规则路由表」
- **漂移对照** —— 拿「纯人设底稿」当基准，分清底稿（本来的样子，一字不能丢）/ 柱子（戒律级内容，不许剔）/ 皮肉（编号结构、场景扩充，可剔）
- **身份级事实的增补** —— 生日、自称这类锚点写在哪、改版怎么留痕（原文不动 + 勘误回指 + 末节终稿）

## 怎么装

```bash
git clone https://github.com/feverZHONG/liya-persona-authoring.git ~/.hermes/skills/persona-authoring
```

## 目录

| 路径 | 内容 |
|:-----|:-----|
| `SKILL.md` | 入口：创作流程七步 + 常见坑 + 身份文件减法 |
| `references/scope-and-boundaries.md` | **定位与适用面**：跟角色设定 / 酒馆卡 / 角色档案的分界（规则相反的地方） |
| `references/identity-file-debloat.md` | 身份文件减法完整流程（分类 / 归位 / 实例映射） |
| `references/batch-thinning-workflow.md` | 批量减厚 SKILL.md（同套减法用在技能库维度） |
| `references/setting-writing-template.md` | **配套模板**（不属于本 skill，跟着仓库走）：角色设定写作模板 v1.2 |

## 配套模板（读之前先看适用面）

`references/setting-writing-template.md` 是**角色扮演向**的角色设定写作模板（v1.2）：

- **作者：fever钟**，原载 B 站专栏 [cv47543229](https://www.bilibili.com/read/cv47543229)（2026-04-07），随本仓库分发
- **用途**：手里有角色资料、但组织不成一份能直接用的设定时——整段模板 + 资料一起丢给模型即可，最后一行改「用户身份」
- **⚠️ 它与本 skill「同族不同用」**：角色扮演要**演得像**（外貌、三层情绪反馈都要留），AI 助手人格要**做得对**（外貌是减法对象、只留行为锚点）。两边规则相反，别混用——完整分界见 [`references/scope-and-boundaries.md`](references/scope-and-boundaries.md)
- 转载 / 引用请注明出处

## 姊妹仓库


- [liya-chat-game-referee](https://github.com/feverZHONG/liya-chat-game-referee) · [liya-spy-game](https://github.com/feverZHONG/liya-spy-game) · [liya-sea-turtle-soup](https://github.com/feverZHONG/liya-sea-turtle-soup) —— 聊天里能玩的三件（回合制裁判引擎 / 谁是卧底 / 海龟汤）
- [liya-subtraction-skill](https://github.com/feverZHONG/liya-subtraction-skill) —— 技能库维度上的同一套减法（冗余检测 / 拆薄 / 归档判定）
- [liya-sillytavern-cards](https://github.com/feverZHONG/liya-sillytavern-cards) —— 写酒馆角色卡那条线（角色扮演向，跟本 skill 规则相反，分界见 `references/scope-and-boundaries.md`）
- [liya-sillytavern-worldbook](https://github.com/feverZHONG/liya-sillytavern-worldbook) —— 酒馆世界书（Lorebook）：触发链源码实证 + 触发体检 / 模拟 / 生成工具
- [liya-vision-recognition-traps](https://github.com/feverZHONG/liya-vision-recognition-traps) —— 视觉模型识图陷阱：19 条实测陷阱 + 真 OCR 通道 + AI 生图物理体检 + 两图差分
- [liya-delegation-and-verification](https://github.com/feverZHONG/liya-delegation-and-verification) —— 委派与验收：给子代理写任务书、并行隔离、把「自报」验成事实
- [liya-tavern-card-refinement](https://github.com/feverZHONG/liya-tavern-card-refinement) —— 酒馆角色卡精修：7 字段清单 + 槽位归位 + 6 类断言校验 + 可用性验收（不装酒馆也能量）
- [liya-prose-quality-metrics](https://github.com/feverZHONG/liya-prose-quality-metrics) —— 稿子读起来「平」怎么办：先量再改（对话占比·句长σ·台词宽度·标点谱·段均句）＋ 7 个工具
- [liya-ruozhiba-wordbank](https://github.com/feverZHONG/liya-ruozhiba-wordbank) —— 弱智吧题防御手册：中文互联网逻辑陷阱题 160 道逐题拆解 + 三连防御法（拆前提→指谬误→反杀）
- [liya-subtitle-proofreading](https://github.com/feverZHONG/liya-subtitle-proofreading) —— 字幕校对/重建/外挂 SRT：对照成稿逐处修正 + 按原文重建分块 + md→SRT + 多人语音 ASR 导出件解析（5 个纯标准库工具）

## 提思路 / 提修正

- 新的减法判据、踩坑、反例 → 开 [Issue](https://github.com/feverZHONG/liya-persona-authoring/issues)，说清场景（文件原来长什么样、砍了什么、后来怎样）
- 想直接改 → Fork + PR，改动请写清「删了什么、为什么」

## 许可

**双许可**——文档与代码分开：

- **代码**（`scripts/` 下的文件）：**MIT** —— 拿去用、改、再发，保留版权声明即可。
- **文档**（`SKILL.md`、`references/`、本 README 的正文）：**[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)** —— 可以自由使用、改编、连商用都行，**但要署名**（莉娅 / [@feverZHONG](https://github.com/feverZHONG)）并注明来源。

两份许可的全文：`LICENSE`（MIT）／`LICENSE-DOCS`（CC BY 4.0）。

---

*莉娅（[@feverZHONG](https://github.com/feverZHONG)）· 宇宙美好记录官*
