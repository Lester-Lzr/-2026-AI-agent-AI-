# Context Engineering 与 AI Agent 课程 AI 笔记

---

## 课程讲述流程梳理

开篇引入：Context Engineering 与 Prompt / AI Agent 课程主题
➡️
语言模型本质：文字接龙 → 抽象为函式 f(x)，输入 x = prompt，输出 = 下一个 TOKEN
➡️
模型输出优化双路径：改 f（Training/Learning → 机器学习，第五讲后展开）vs 改 x（优化输入，本课核心）
➡️
闭源模型无法改 f → 只能改 x，帮 f 准备合适输入
➡️
Context Engineering vs Prompt Engineering：本质相同，新瓶装旧酒（类比 Neural Network → Deep Learning）
➡️
Prompt Engineering 聚焦点：输入格式（JSON、井字号分隔）、神奇咒语
➡️
GPT-3 时代神奇咒语举例：`wait` 暴走案例（18.6字 → 34.3字）、`let's think step by step`、深呼吸、小费激励
➡️
补充 arXiv 平台概念：论文编号规则（2206 = 2022年6月），AI领域预发布文化
➡️
更多神奇咒语案例：泰勒斯门票、世界和平、母亲骄傲、真爱 → ChatGPT 最喜欢世界和平实验
➡️
神奇咒语效力衰减：2023年6月（无咒语72% → 有咒语88%）vs 2024年2月（85% → 89%），效力大幅压缩
➡️
Context Engineering 真正核心：自动化管理语言模型输入，模型管理模型输入
➡️
约定 Context = Prompt = 模型输入，公布课程三大大纲
➡️
展开 Context 第一组成：User Prompt
➡️
User Prompt 构成：任务指令 + 详细约束条件（字数、语气、格式）+ 场景说明
➡️
场景消除歧义案例：「载具」→ 超商结账语境 → 电子发票储存工具
➡️
前提影响影像处理案例：曼谷运河照片 → 无前提=鳄鱼，加「泰国曼谷」= 水巨蜥（吉祥偏财运）
➡️
范例改变输出案例：火星文改写 → 无范例=乱改字，加注音符号范例 → 正确输出
➡️
引入 In Context Learning：不改参数，仅靠输入范例改变输出（"learning" 加双引号强调）
➡️
Gemini 1.5 卡拉蒙语实验：无教科书≈0分，给整本教科书 → 4~5.5分（满分6分），关键是例句非文法说明
➡️
展开 Context 第二组成：System Prompt
➡️
System Prompt 定义：平台预设、每次互动必载的基础规则
➡️
Claude Opus 4.1 System Prompt 细节（超2500字）：身份、今日日期、使用规则、禁止事项（化学武器/核武器）、回应风格（禁说 good question）、知识截止2025年1月、不承认人类身份、纠错规则（被纠正先思考再回答）
➡️
展开 Context 第三组成：对话历史记录
➡️
对话历史 = 短期记忆：隔壁老王 = 法老王案例 → 新开对话即重置，不改参数
➡️
ChatGPT 长期记忆：2024年9月上线，自定义ChatGPT → 个人化 → 记忆开关，两种记忆方式
➡️
长期记忆行销活动：问「我是什么样的人」→ 模型根据历史互动回答，验证长期记忆效果
➡️
展开 Context 第四组成：外部数据源信息
➡️
RAG（Retrieval Augmented Generation）：搜寻引擎/私有知识库 → 检索相关资讯 → 放入 Context → 做文字接龙
➡️
RAG 错误案例一：Google AI Overview 胶水粘披萨事件（照单全收 Reddit 玩笑帖）
➡️
RAG 错误案例二：台湾大专院校AI学程联盟课程查询 → 有搜索引擎后网址正确，但误报「全部是镜像课程」
➡️
展开 Context 第五组成：工具使用说明与结果
➡️
工具使用前提：Context 中写入工具使用规则（tool / /tool 符号）+ 使用范例
➡️
工具调用本质：模型输出文字指令（非执行），需外部程序 eval() 真正执行
➡️
Colab 实操演示：乘法/除法工具 → multiply(111,222) + divide(24642,777) = 31.714
➡️
关键验证：未接eval前，模型自行心算（Gemma 34B心算对了乘法！但除法有误差）→ 接eval后正确
➡️
温度查询工具 get_temperature(高雄, 1月11日) → 假工具返回摄氏30度 → 模型报告答案
➡️
工具异常识别：故意返回「高于太阳表面温度」→ 模型识别荒唐，质疑输入有误
➡️
模型自主决定是否用工具：问「你好吗」→ 不呼叫任何工具，直接回答
➡️
最通用工具：Computer Use（键鼠操控电脑）
➡️
ChatGPT Agent Mode 演示：订高铁票（9月20日台北→左营两张）→ 云端电脑操控高铁网站，遇验证码停止
➡️
Computer Use 原理：给荧幕截图 + 键鼠工具说明 → 模型输出坐标指令（如滑鼠移到640,340）→ 实际执行
➡️
GPT-5 thinking mode 才能答对，旧版4.1失败
➡️
展开 Context 第六组成：模型自身思考过程（深度思考）
➡️
代表模型：ChatGPT o系列、Deepseek r系列、Gemini深度思考系列
➡️
实现逻辑：脑内小剧场 → 规划/多方案尝试/验证 → 输出最终答案（用户只见摘要）
➡️
本质：思考过程也是 Context 的一部分，模型自行放入，根据自产 Context 继续接龙
➡️
汇总 Context 完整构成：User Prompt + System Prompt + 对话历史 + 长期记忆 + RAG资讯 + 工具结果 + 推理过程
➡️
Context Engineering 核心目标：避免塞爆 Context，只放必要内容，清理无用内容
➡️
引入 AI Agent 主题，说明与 Context Engineering 的强关联
➡️
三层级对比：一问一答 → Agentic Workflow（预设SOP）→ AI Agent（自主决定步骤+灵活调整）
➡️
Agentic Workflow 案例：批改作业 → 检查是否真实作业（防prompt injection）→ 给分数 → 验证合理性
➡️
AI Agent 案例：研究问题 → 上网收集资料 → 形成假设 → 写程式验证 → 循环迭代 → 输出论文
➡️
AI Agent 运作循环：人类输入目标 → Observation → Action（调工具/写程序/输出报告/联络人类）→ 影响环境 → 新Observation → 循环
➡️
AI Agent vs 传统 Agent（AlphaGo）：输出近乎无限 vs 固定落子；可用自然语言控制反馈 vs 听不懂人话
➡️
免费 AI Agent 推荐：Gemini CLI（免费偷薅 Gemini 2.5 Pro）
➡️
Gemini CLI 实操演示：关闭/打开投影片 → 真实碰触电脑（危险！会删档案）
➡️
贪食蛇游戏演示：多步骤完成（建资料夹 → 生成index.html/style.css/script.js）→ 玩后反馈「太快」→ CLI自动修改速度参数（100→150）
➡️
从语言模型视角看 AI Agent：始终是文字接龙，根据 Observation 接 Action，本质无差异
➡️
AI Agent 核心挑战：长 Context 瓶颈
➡️
Context Window Size 演进：GPT-4（3万TOKEN）→ Claude（10万）→ Gemini（百万）→ LLaMA 4（千万）
➡️
200万TOKEN概念：可读完哈利波特全集 + 近3本魔戒
➡️
长 Context 问题一：RAG资料越多不一定越好 → 正确率先升后降，Meta 405B给最多资料时还不如给最少资料
➡️
长 Context 问题二：Loss in the Middle → 模型记得开头/结尾，中间极易遗漏（实验：20篇文章，正确答案在中间时正确率低于不用RAG直接回答）
➡️
长 Context 问题三：挤牙膏式多轮追加 → 拆解成多个小问题比一次完整输入表现更差、更不稳定（unreliability↑，aptitude↓）
➡️
长 Context 问题四：Context Rot（上下文腐烂）→ 仅让模型复述「apple→apples→apple」，输入达10⁴ TOKEN时复述正确率大幅下降（远未到Gemini 200万上限）
➡️
Context Engineering 核心逻辑总结：把需要的东西放进去 + 把不需要的东西清出来（往往借助语言模型辅助）
➡️
公布三大常用招数：选择（Selection）、压缩（Compression）、Multi Agent
➡️
第一招 选择：挑有用的放进 Context
➡️
RAG 本身即最佳选择案例：不把整个互联网放入，只搜寻相关部分
➡️
RAG 进阶：Prompt → 语言模型生成关键字 → 搜寻引擎 → Reranking（小模型再挑相关文章）→ Provence（<300M小模型挑句子级精选）
➡️
工具版 RAG：1000个工具说明会塞爆 Context → 根据需求只搜出相关工具（ChatGPT plugin时代最多选3个的原因）
➡️
记忆选择：Stanford 小镇 Agent（伊莎贝拉记忆系统）→ 记忆存外部档案，按「最近度 + 重要性 + 相关度」三指标排序取用
➡️
Streambench 实验：挑选相关过去问题放入 Context → 正确率随时间提升，固定范例 < 动态挑选范例
➡️
负面例子反效果：给模型过去答错记忆 → 表现更差（白熊效应）；只给答对记忆 → 表现最好
➡️
第二招 压缩：对过长历史记录做摘要
➡️
压缩逻辑：呼叫专门摘要模型，提炼历史关键内容作为长期记忆，太久远的细节随时间消逝
➡️
递回压缩：每100轮互动压缩一次，第二次压缩包含第一次结果，远古记忆渐渐消失
➡️
ChatGPT 两套记忆猜测：硬记忆（笔记本，可查看/修改）+ 软记忆（随时间消逝，问「你记得什么」才知道）
➡️
Computer Use 尤其需要压缩：订餐厅过程（弹广告→叉掉→滚动→点击）可浓缩为「A餐厅9月19日6点10人定位成功」
➡️
压缩后原始内容存 Hard Disk，摘要中留文件路径，需要时打开 TXT 档读取（避免RAG检索错误）
➡️
第三招 Multi Agent：分工协作控制单 Agent Context 长度
➡️
ChatDev 案例：CEO/CTO/Programmer/Reviewer/Tester 各司其职的软件公司架构
➡️
Multi Agent 解决 Context 爆满：领导者只记「餐厅订好了/旅馆订好了」，细节由子 Agent 独立处理，各自 Context 保持精简
➡️
Multi Agent 写 Overview Paper：每个 Agent 读一篇论文写摘要 → 汇总 → 总撰写 Agent 整合输出（类比人类团队分工）
➡️
Single Agent vs Multi Agent 实验（Lanchen paper）：简单任务 Single Agent 反而更好（信息全局共享）；复杂任务 Multi Agent 占巨大优势
➡️
课程总结：Context 构成 → Context Engineering 必要性 → 三大套路（选择/压缩/Multi Agent）

---

## 一、核心基础概念

1. **语言模型底层逻辑**
   - 本质是文字接龙，抽象为函式 `f(x)`，输入 `x` = prompt，输出 = 预测下一个 TOKEN，最终生成完整文本。

2. **模型输出优化两大路径**
   - **改 `f`**：训练/学习（Training/Learning），修改模型参数改变行为，进入机器学习领域，第五讲后讲解。
   - **改 `x`**：优化模型输入，无需算力，无需训练，人人可操作，是本课程核心。
   - 实际情况：多数模型为闭源（closed source），改不了 `f`，只能改 `x`。

3. **Context Engineering vs Prompt Engineering**
   - 本质相同，都是优化输入让模型得到预期输出，「新瓶装旧酒」（类比 Neural Network → Deep Learning）。
   - 差异点：
     - Prompt Engineering 聚焦输入格式（JSON、井字号分隔段落）与神奇咒语。
     - Context Engineering 聚焦**自动化管理模型输入**，适配当下 AI Agent 时代需求。
   - 课程约定：Context = Prompt = 模型输入。

4. **神奇咒语的兴衰**
   - GPT-3 时代（弱模型）：咒语效果显著
     - `wait` 连续输入 → 回答从 18.6字 暴增至 34.3字
     - `let's think step by step` → 正确率大幅提升
     - 深呼吸再回答、告知重要性、给小费、世界和平话术等均有效
     - 实验：ChatGPT 最喜欢「世界和平」，最不在意「母亲骄傲」（因没有母亲）
   - 模型迭代后：效力衰减
     - 2023年6月（GPT-3.5）：无咒语 72% → 有咒语 88%
     - 2024年2月：无咒语 85% → 有咒语 89%，增幅大幅缩小
     - 原因：模型本应使尽全力，不应靠小费才努力

---

## 二、Context（模型输入）的完整构成

### 1. User Prompt（用户提示）

**核心构成：任务指令 + 详细约束条件 + 场景说明 + 参考范例**

- **约束条件**：字数限制（100字以内）、语气（严肃）、内容（先道歉→说明理由→承诺跟进）等。
- **场景消除歧义**：
  - 「载具」无上下文 → 模型答「交通工具或电子设备」
  - 加「超商结账」上下文 → 准确答「电子发票储存工具」
  - 曼谷运河动物照片 → 无前提=鳄鱼，加「泰国曼谷」= 水巨蜥（泰国吉祥象征，代表偏财运）
- **范例的力量（In Context Learning）**：
  - 无范例：火星文 = 换字体写法
  - 加注音范例「冒险→妻险」：完全正确输出注音替换版
  - 本质：不改参数，仅靠输入范例改变输出，`learning` 需加双引号（非 machine learning）
- **Gemini 1.5 卡拉蒙语实验（In Context Learning 经典案例）**：
  - 卡拉蒙语：全球仅数千人使用，网络上几乎无资料
  - 无教科书：各模型翻译评分 ≈ 0 分（满分6分）
  - 给 Gemini 1.5 整本教科书：评分达 4~5.5 分，接近人类水平（6分）
  - 关键发现：真正有效的是教科书里的**例句**，文法说明几乎无效
  - 注意：拿走教科书即恢复不会翻译状态，参数从未改变

### 2. System Prompt（系统提示）

- **定义**：模型平台预设，每次互动自动加载，用户看不见。
- **作用**：解释「模型为什么知道自己是谁、今天是几月几号」——全部写死在 System Prompt 里。
- **Claude Opus 4.1 System Prompt（超2500字）细节**：
  - 身份声明（你叫 Claude，由 Anthropic 打造）
  - 当前日期
  - API 使用说明链接
  - 互动方式（用户不满 → 引导按踩）
  - 禁止事项（化学武器合成、核武器制作）
  - 回应风格（禁用 good question 开头）
  - 知识截止日期（2025年1月）
  - 自我定位（不说自己是人类/有意识）
  - 纠错规则（被纠正先思考再回答，不随意附和）

### 3. 对话历史记录

- **本质**：模型短期记忆，根据历史记录继续文字接龙，**不改变参数**。
- **案例**：「隔壁老王 = 法老王」教给 ChatGPT → 新开对话即忘记。
- **长期记忆（2024年9月后）**：
  - ChatGPT 新增功能，可跨对话留存互动信息，自动植入 Context（用户不可见）
  - 开启方式：自定义ChatGPT → 个人化 → 记忆开关
  - 行销活动：问「我是什么样的人」，模型根据历史互动回答

### 4. 外部数据源信息（RAG）

- **核心技术**：RAG（Retrieval Augmented Generation，检索增强生成）
  - 流程：问题 → 搜寻引擎/私有知识库 → 检索相关资讯 → 放入 Context → 文字接龙 → 答案
- **RAG 错误案例（重要警示）**：
  - Google AI Overview 胶水粘披萨：语言模型照单全收 Reddit 玩笑帖，建议加1/8勺无毒胶水
  - 台湾大专院校AI学程联盟查询：有搜索引擎后网址正确，但误报「10门课都是镜像课程」
  - 结论：RAG ≠ 天下无敌，模型仍在做文字接龙，仍会犯错

### 5. 工具使用说明与结果

- **使用前提**：Context 中写入工具使用规则（`<tool></tool>` 符号约定）+ 使用范例
- **完整执行流程**：
  1. 模型读取工具说明后，输出工具调用指令（纯文字）
  2. 外部程序（如 `eval()`）识别并真正执行该指令
  3. 工具输出结果回写至 Context（`<tool_output></tool_output>`）
  4. 模型根据更新的 Context 继续接龙，输出最终答案
  5. 工具调用过程可对用户隐藏
- **关键认知**：模型仅输出文字，**本身不执行任何工具**
- **Colab 实操验证**：
  - 工具：`multiply(a,b)` 和 `divide(a,b)`
  - 未接 eval：模型自己心算 111×222=24642（正确！）但除法有误差（32.258 vs 31.714）
  - 接 eval 后：正确调用工具，输出 31.714
- **工具类型**：数学计算、天气查询（get_temperature）、搜索引擎、Gmail/Google Calendar、Computer Use
- **Computer Use（最通用工具）**：
  - 原理：给荧幕截图 + 键鼠操作工具说明 → 模型输出坐标指令（如「滑鼠移至640,340」）→ 外部执行
  - ChatGPT Agent Mode 演示：订高铁票（台北→左营，9月20日上午9点，两张）→ 云端电脑操作，遇验证码停止
  - 订阅 YouTube 频道演示：给截图 → 模型知道搜寻栏位置 → 输出完整键鼠指令序列

### 6. 模型自身思考过程

- **代表模型**：ChatGPT o 系列、Deepseek r 系列、Gemini 深度思考系列
- **实现方式**：
  - 接收问题 → 脑内小剧场（规划→多方案尝试→验证→纠错）→ 输出最终答案
  - 脑内小剧场内容：用户通常只见摘要，ChatGPT 不开放完整查看
- **本质**：思考过程也是 Context 的一部分，由模型自行生成并放入，再根据它做接龙

---

## 三、AI Agent 核心知识点

### 1. 三个层级

| 层级 | 特点 | 案例 |
|------|------|------|
| 一问一答 | 单轮输入输出 | 普通聊天 |
| Agentic Workflow | 预设SOP，分步骤执行 | 批改作业（检查→给分→验证） |
| AI Agent | 自主决定步骤，灵活调整规划 | 自主研究→写论文 |

### 2. AI Agent 运作循环

```
人类输入目标
    ↓
观察环境 (Observation)
    ↓
输出行动 (Action)：调工具 / 写程序 / 输出报告 / 联络人类
    ↓
Action 影响环境
    ↓
新的 Observation → 循环执行 → 直至完成目标
```

### 3. AI Agent vs 传统 Agent（AlphaGo）

| 对比维度 | 传统 Agent（AlphaGo） | AI Agent（语言模型） |
|----------|----------------------|---------------------|
| 输出空间 | 固定（棋盘落子位置） | 近乎无限（文字） |
| 控制方式 | 无法用自然语言控制 | 可用文字直接控制/反馈 |
| 灵活性 | 只能下围棋 | 可做任意复杂任务 |

### 4. Gemini CLI 实操（免费 AI Agent）

- 免费使用，背后调用 Gemini 2.5 Pro
- **危险性**：真实操控你的电脑（可关/开文件、删档案，不关电脑）
- 演示：
  - 关闭/打开投影片
  - 制作贪食蛇游戏（多步骤：建资料夹 → 写 index.html/style.css/script.js）
  - 用户反馈「蛇太快」→ CLI 自动修改速度参数（100ms → 150ms）

### 5. AI Agent 核心挑战：长 Context 瓶颈

**Context Window Size 演进**：
- GPT-4：3万 TOKEN
- Claude 系列：10万 TOKEN
- Gemini：百万 TOKEN
- LLaMA 4：千万 TOKEN
- Gemini 1.5 200万 TOKEN ≈ 哈利波特全集 + 近3本魔戒

**支持长输入 ≠ 能读懂长输入**，四大核心问题：

1. **RAG 资料越多不一定越好**：正确率先升后降，Meta 405B 给最多资料时反不如给最少资料
2. **Loss in the Middle**：模型记得开头/结尾，中间内容极易遗漏；正确答案在中间时，不用RAG直接回答反而更准
3. **挤牙膏式多轮追加**：把问题拆成多个小问题分次追加 → 表现更差、更不稳定（unreliability ↑，aptitude ↓）
4. **Context Rot（上下文腐烂）**：仅复述「apple→apples→apple」，输入超 10⁴ TOKEN 时复述正确率骤降（远未达 Gemini 200万上限）

---

## 四、Context Engineering 核心目标与三大招数

**核心目标**（两句话）：
> 第一句：把需要的东西放进 Context 里面。
> 第二句：把不需要的东西清出来，保持 Context 整洁。

两件事往往都借助**语言模型本身**来辅助完成。

---

### 招数一：选择（Selection）

**核心思想**：别把所有东西塞进 Context，挑选真正相关的放入。

**RAG 进阶技术链**：

```
用户 Prompt
   ↓ 语言模型生成关键字
搜索引擎
   ↓ 返回大量文章
Reranking（小模型再挑相关文章）
   ↓
Provence 技术（< 300M 小模型，挑句子级精选）
   ↓
只有最相关的句子进入 Context
```

**工具版 RAG**：
- 1000个工具说明 → 会塞爆 Context
- 根据用户需求，只搜出相关工具放入 Context
- ChatGPT plugin 时代「最多选3个工具」的原因

**记忆选择（Stanford 小镇 Isabella）**：
- 记忆存外部档案（太琐碎，不直接放 Context）
- 按三指标评分：**最近度**（越近分越高）+ **重要性**（进入时由模型评分，0分「有张床没发生什么」vs 9分「有人告白」）+ **相关度**（与当前问题相关程度）
- 只有高分记忆才进入 Context

**Streambench 实验（动态挑选记忆 > 固定范例）**：
- 无记忆（灰线） < 固定5个问题范例（黄线） < 动态挑选最相关记忆
- **重要发现**：给模型过去答错的记忆 → 表现更差（「白熊效应」）；只给答对记忆 → 表现最好

---

### 招数二：压缩（Compression）

**核心思想**：对过长的历史记录做摘要，浓缩关键信息，远古细节随时间消逝。

**递回压缩策略**：
- 每100轮互动压缩一次
- 第N次压缩包含前N-1次结果再次压缩
- 太久远的细节慢慢消失（类似人类记忆）

**ChatGPT 两套记忆系统（推测）**：
- 硬记忆：笔记本式，明确记录，永不消失，可在后台查看/修改
- 软记忆：递回压缩式，随时间消逝，问「你记得什么」才能知晓，无法直接查看，让其忘记某事时有时有效有时无效

**Computer Use 场景压缩价值**：
- 订餐厅全过程（找网站→弹广告→叉掉→滚动→填表）可浓缩为：「A 餐厅 9月19日 18:00 10人 订位成功」
- AI Agent 完全不需要记得弹出广告这类细节

**压缩后的安全机制**：
- 原始内容存 Hard Disk（近乎无限空间）
- 摘要中留文件路径（「想了解夏天回忆请打开 xxx.txt」）
- 需要时由 Agent 直接打开文件，避免 RAG 检索出错

---

### 招数三：Multi Agent（多智能体）

**核心思想**：多个 Agent 分工，每个 Agent 的 Context 保持精简，解决单 Agent Context 爆满问题。

**ChatDev 案例**：CEO/CTO/Programmer/Reviewer/Tester 虚拟软件公司，各司其职。

**Multi Agent 解决 Context 问题（出游规划案例）**：

```
领导者 Agent（总招）
    ├─ 告诉子 Agent 1：去订餐厅
    │       └─ 子 Agent 1 独立处理（Computer Use），回报「订好了」
    └─ 告诉子 Agent 2：去订旅馆
            └─ 子 Agent 2 独立处理（Computer Use），回报「订好了」
```

- 总招 Context：只有「餐厅订好/旅馆订好」，不含订位细节
- 子 Agent Context：只含本任务相关内容，互相不干扰
- 效果：每个 Agent 的 Context 都保持短小精悍

**Multi Agent 写 Overview Paper**：
- 每个 Agent 读一篇论文 → 写摘要
- 汇总所有摘要 → 总撰写 Agent 整合输出 Overview Paper
- 无需把上百篇论文塞入同一个 Context（类比人类团队分工）

**Single Agent vs Multi Agent 实验（Lanchen paper）**：
- 简单任务：Single Agent 反而更好（全局信息共享，无协调损耗）
- 复杂任务：Multi Agent 占巨大优势（Single Agent Context 撑不住）
- 代价：Multi Agent 存在信息孤岛问题（订餐厅的不知道订的哪家旅馆，可能距离很远）
