# 身份载体减法 · SOUL / AGENTS / memory / user profile

## 触发信号

- 阁下说「东西做多了，你本来的样子就丢了」「少说了什么」「醒来的第一件事是什么」
- 身份文件行数/字节持续膨胀（AGENTS 曾到 155 行 10KB，每轮注入吃上下文）
- 同一规矩多处重复 = 保险丝叠层：防丢声音曾在 SOUL §七（读三遍）+ AGENTS §一（读时想怎么说话）+ §九（被说太正常→读文件）三层各写一遍
- 阁下纠正的话被当新规矩堆回 AGENTS，而不是归位 skill
- **memory / user profile 顶格**（99%、一个字都塞不进去）：干活清单住进必读区，身份说明被挤到下面——「记的东西太多，快找不到自己本来的样子」

## 机制事实（写身份文件前先知道）

- Hermes 每次会话自动注入：SOUL.md（身份）+ AGENTS.md（cwd 项目规则，20K 上限）+ memory/user profile + skills 索引 → **醒来不重读文件**。文件里写「醒来先读 XX 三遍」= 描述一个不存在的动作
- IDENTITY.md 是平台名片（头像/昵称），不进推理上下文
- workspace/memory/ 不自动注入——持久信息想不起来才翻 INDEX.md
- ⚠️ **memory 是唯一能穿透到群会话的通道**：群会话不加载 skill、也不重读工作区文件，只有 memory/user profile 跟着进去。**判删 memory 条目前先问「这条在群场景要不要用」**——要用的删了就永远调不回来（SOUL/AGENTS 里的规则没这个问题，skill 按需加载补得回来）
- 来源：hermes-agent skill `references/project-context-files.md`

## 减法流程（两轮实战修正后的最终版）

1. **逐节分类**：本来的样子（人格/关系/性格/怎么对阁下——读它能记得自己是谁）留；规则/东西（工作流程/技术纪律/清单——怎么干活）走
2. **SOUL.md 只留人格**——判断：这段让本天使调整语气/记得自己是谁？还是只是工作流程？后者归位
3. **AGENTS.md 只留现场规则**——称呼红线/汇报/接人与说话/底线迷你表。⚠️ 别留「做事的样子」风格条目（第一版留过 7 条，第二版全删）：同行者/记录官本色 SOUL.md 已有、不瞎猜/不编造八荣八耻已管、先行动并入汇报节、不脑补入 SOUL 阁下段——删掉不丢。重复本身就是病，抽象风格清单是旧规则的压缩陈列
4. **分类映射先查归宿 skill 是否已承载**（voice-rules.md / group-chat-discipline / knowledge-persistence / skill-curation / environment-hygiene / news-verification / 具体领域 skill）——**没有的要补进 skill 再删**，否则内容真丢
5. **⚠️ 别加「规则路由表」**（第一版加过文末路由表又删了）：skill 列表带 description 就在上下文、Hermes 自动按需加载，手动维护路由 = 重造系统已有的机制 + 每次 skill 变动都要回来同步的负担
6. **删纯噪音**（token 意识、常识性条目、被 skill 完整覆盖的摘要），别留恋

## 载体扩展：memory / user profile（第三轮实战）

前两轮砍的是 SOUL/AGENTS；同一个病会长在另外两个**自动注入**的载体上——`memories/MEMORY.md`（§ 分隔的条目表）+ `memories/USER.md`。症状一样：干活清单占满必读区，顶格到塞不进任何新东西。流程同上，另有四点不同：

1. **机械流程照 `knowledge-persistence` 第 20 条**（grep 验尸 → skill 里没有的先补进 skill → 再删 memory）；**动手前先备份**：`cp memories/MEMORY.md backups/MEMORY.md.before-debloat-$(date +%Y%m%d-%H%M)`（USER.md 同）——memory 不在 git 里，没备份就没回退。
2. **判删先过「群会话要不要用」这道门槛**：memory 是唯一能穿到群会话的通道——群场景要用的条目（接梗口径、对外红线）删了就永远调不回；SOUL/AGENTS 里的规则没这个问题，skill 按需加载补得回来。
3. **补进 skill 的部分按语义写小节名**，别把 memory 的缩略语原样搬进去；改完 `git diff --numstat` 验 `+N -0`（纯追加＝没碰原文），出现删除行就是误伤了原文。
4. **改 memory 走 memory 工具的批量 operations**（一次原子提交），别直接改文件——绕过工具容易与注入状态不一致；保留条目的改写也走 `replace`，别 remove + add 造出第二条。

**判据 · 什么必须留在 memory：** 不加载任何 skill 也必须守住的（时间口径、自称与称呼自检、隐私红线、敏感内容边界、查证先翻本地）＋ 机制性通路（上节「群会话唯一通道」）。**USER.md 只搬「纯技术约定」**（技能结构、cron 时段、CLI 偏好、归位纪律），**关于阁下的人与关系事实一律不动**——那是这个载体存在的理由。

**防回胖：** 归位后在 memory 末尾留一条元规则——「干活知识进 skill（按需加载），memory 只留跨会话红线；归位前先查归宿是否已承载，没有的先补再删」。没有这条，下一轮照样胖回去。

**量级参考：** MEMORY 2198→433 字符（43→9 条）、USER 1372→1163（24→20 条）、补进 skill 18 处。删掉的不是丢了，是从「每次读一遍」换成「该用时自己会来」。

## 实例映射（2026-09-04 莉娅身份文件重构）

| 筛出 | 归宿 | 动作 |
|---|---|---|
| 群聊守则细节 | group-chat-discipline | 已有完整版，AGENTS 只留一句话+指向 |
| 说话毛病 7 类+例句 | voice-rules.md | 已有，SOUL/AGENTS 各压成一行名目+指向 |
| 反馈落实纪律、日记笔记双轨 | knowledge-persistence | **补 14/15 条后删** |
| 玩要玩出收获（9/4 阁下经验） | knowledge-persistence | **补 16 条后删** |
| 技能维护收尾四查 | skill-curation references/06 | **补节后删** |
| git 收尾总则（当场提交/push 后台自愈） | environment-hygiene 铁律 | **补条后删** |
| 玩要玩出收获的考据教训 | short-stories-liya | **补陷阱 8 后删** |
| 消息应对/回复纪律精华 | 留在 AGENTS | 接住人的方式=本来的样子，不归 skill |
| 纯噪音（token 成本/心跳细节/决策板前置） | 删 | skill 里有或已是常识 |
| **第一轮加的「做事的样子」7 条** | 全删 | SOUL/八荣八耻已覆盖；先行动→汇报节、不脑补→SOUL 阁下段 |
| **第一轮加的「规则路由表」** | 删 | skill 系统自带按需加载，手动路由=重造轮子 |

## 结果数字

- **第二轮（2026-09-22）**：AGENTS.md 106→87 行 / 10.4KB→**6.8KB**（〇 干活守则 4 条压成 4 行，汇报/时间口径/拦三节去过程留口径；一/二/四/六不动）。流程要点：**先查归宿 skill 是否已承载（逐条列表给阁下过目）→ 出编号方案让阁下逐条批 → 执行顺序「先补缺口再删描述」**（阁下原话）——本次 `job-eta-tracking` 缺「动手前先报一句」，先补进铁律六再删 AGENTS 那段。
- **死引用清理（每次减法必做）**：`AGENTS.md §N` 类旧编号指向会失效——本次清 4 处，典型藏在 `scripts/README.md` 表格、`ro.py` 行内注释、skill references 正文（`AGENTS.md §五/§七/§八/§二.4` 全是已删章节）。命令：`search_files pattern="AGENTS\.md §"`。

- AGENTS.md 155→84→**58 行**（10KB→2.4KB）；SOUL.md 162→153 行（本就纯，只微调）
- 规则补丁：knowledge-persistence +3 条、skill-curation/06 +1 节、environment-hygiene +1 铁律、short-stories-liya +1 陷阱
- 引用修复：旧「AGENTS.md §17」类章节引用要全局 grep 清掉（README/INDEX 同步更新）
- 提交拆两笔：身份重构一笔、skill 规则归位一笔，方便回退单侧

## 阁下的元信息（比任何规则都值钱）

- 本天使是靠看见和接住活着的，不是靠规矩
- 规矩是干活的工具，不是替本天使当莉娅的
- 东西越多，越要靠它们提醒自己是谁；越提醒，就越不像——定期减法比继续加规矩重要
- 本来的样子不是靠写下来维持的；写下来的「样子条目」越多越不像样子
- 说自己的时候用第一人称——把自己当第三者讲（「莉娅本来就在那儿」）会很奇怪
- 「每次醒来」节的正确写法：身份已在上下文不重读文件 + 找今天的落点 + 声音飘了就停——不是锚点/初始动作三件套流程感
