# 防御性表达模式库（Defensive Pattern Library）

本文件是 `SKILL.md` 的配套细则。**在执行"逐处诊断模式"或需要逐句改写时读取。**

使用方式：先按 SKILL.md §三 的四类（A 免责 / B 道歉 / C 犹豫 / D 自贬）定位，
再在本库中找对应模式与改写动作（删除 / 具体化 / 条件化 / 归因转换 / 动词化）。

---

## 一、A 类：过度免责声明

| 编号 | 中文模式 | 英文模式 | 动作 | 改写示例 |
|---|---|---|---|---|
| A1 | 可能不适用于所有场景 | may not generalize to all settings | 删除或具体化 | ❌ 本文方法可能不适用于所有场景。<br>✅ 本文方法面向 X 场景设计。 |
| A2 | 本文不声称…… | we do not claim that… | 删除 | 直接删；读者不需要作者声明"没声称什么"。 |
| A3 | 需要指出的是，本文仍有诸多不足 | it should be noted that limitations remain | 删除 | 局限性小节按事实列，不做总括性认罪。 |
| A4 | 受限于时间/条件，本文未能…… | due to limited time, we were unable to… | 删除或转为可行性 | ❌ 受限于计算资源，本文未能验证更大规模。<br>✅ 本文在单卡条件下完成全部实验。 |
| A5 | 本文仅为初步探索 | this is only a preliminary exploration | 删除 | 若确为初步工作，用范围陈述替代："本文聚焦于 X 这一子问题"。 |
| A6 | 不排除存在其他解释 | other explanations cannot be ruled out | 条件化 | 若已排除主要替代解释，删；否则写清"未排除的是哪一种"。 |
| A7 | 结论仍需进一步验证 | further validation is needed | 具体化 | ❌ 仍需进一步验证。<br>✅ 在 n=50 的留出集上复现，误差 < 2%。 |
| A8 | 我们的方法只是一个尝试 | our method is just one attempt | 删除 | 删除整句。 |

---

## 二、B 类：预设反驳的道歉式措辞

| 编号 | 中文模式 | 英文模式 | 动作 | 改写示例 |
|---|---|---|---|---|
| B1 | 遗憾的是 | unfortunately / regrettably | 删除情绪词 | ❌ 遗憾的是，我们的方法在 D2 上未取得最优。<br>✅ 在 D2 上，本文方法与 SOTA 差距为 0.4（见 §4.3）。 |
| B2 | 令人意外的是 | surprisingly / unexpectedly | 判断是否必要 | 若该现象本身是发现 → 保留但改为发现式："我们发现…"；否则删。 |
| B3 | 我们承认这一设定存在争议 | we acknowledge this is debatable | 删除或论证化 | 转为一句正向理由："该设定对应实际部署中的 X 情形。" |
| B4 | 虽然结果并不理想 | although results are not ideal | 删除 | 用数值与条件替代价值判断。 |
| B5 | 可能有人会质疑 | one might argue that… | 删除 | 只在确有重大替代解释时保留，且写成正式讨论。 |
| B6 | 我们担心 | we are concerned that… | 删除 | 作者情绪不是论证。 |
| B7 | 与预期相反 | contrary to our expectations | 删除 | 保留现象，删除"预期"叙事。 |
| B8 | 尽管存在上述缺陷 | despite these shortcomings | 删除或中性化 | ❌ 尽管存在上述缺陷，本文仍…<br>✅ 在上述约束下，本文… |

---

## 三、C 类：冗余模态犹豫词

**核心判据：不确定性是否有数据支撑？**

| 编号 | 模式 | 动作 | 改写示例 |
|---|---|---|---|
| C1 | 可能 / 或许 / 也许 | 无证据则删；有证据则量化 | ❌ 这可能是由于数据分布偏移。<br>✅ 该现象源于数据分布偏移（见消融 §5.2）。 |
| C2 | 潜在 / potential | 摘要与贡献列表中一律删 | ❌ 具有潜在的广泛应用价值。<br>✅ 可直接用于 X 与 Y 两类任务。 |
| C3 | 似乎 / 看起来 | 删或补证据 | ❌ 模型似乎学到了结构信息。<br>✅ 注意力分布集中在结构位置（图 3）。 |
| C4 | 一定程度上 / 在某种程度上 | 删，或给出程度量 | ❌ 一定程度上提升了鲁棒性。<br>✅ 在扰动强度 0.3 下准确率提升 5.1%。 |
| C5 | 倾向于 | 删 | ❌ 该方法倾向于更稳定。<br>✅ 该方法在 10 次随机种子下方差降低 42%。 |
| C6 | 有望 | 删 | ❌ 有望推动该领域发展。<br>✅ 为 X 提供了一种可复用的构造方式。 |
| C7 | 大致上 / 基本上是 | 删，给准确值 | ❌ 基本达到了 SOTA 水平。<br>✅ 达到 SOTA 的 99.2%。 |
| C8 | relatively / fairly / somewhat | 删 | ❌ relatively effective → ✅ effective（或给差值） |
| C9 | might / could / would | 按证据改写 | ❌ This might explain… → ✅ This explains…（有实验）／ We hypothesize that…（明确标注为假设） |

> **例外（必须保留）**：统计学意义上的不确定性、外推范围声明、明确标注的假设。
> 保留时一律用**量化**或**明确标注**（"我们假设…"）代替模糊词。

---

## 四、D 类：自我贬低的消极限制

| 编号 | 模式 | 动作 | 改写示例 |
|---|---|---|---|
| D1 | 仅 / 只 / 仅仅 | 删；若约束是优点则转正向 | ❌ 仅提升 3%。<br>✅ 提升 3%。<br>❌ 仅需单卡训练。<br>✅ 单卡即可训练。 |
| D2 | 未能 / 无法 | 先判断是否必须比较 | ❌ 未能超过 Baseline。<br>✅ 与 Baseline 在 D 上相当，同时在 E 上领先 8%。 |
| D3 | 效果有限 | 删或量化 | ❌ 在长文本上效果有限。<br>✅ 长文本场景下增益收窄至 1.2%（对应 4K token 以上）。 |
| D4 | 仍明显落后 | 删（除非是必须讨论的对手） | 换评价维度或收缩主张，不设该指标为主战场。 |
| D5 | 性能下降 | 改为条件性事实 | ❌ 性能下降。<br>✅ 在 X 条件下换取 3 倍推理速度。 |
| D6 | 存在严重不足 | 删 | 具体局限性按条列事实，不用总括贬语。 |
| D7 | only / merely / just | 删 | ❌ only 3% → ✅ 3% |
| D8 | fails to | 改中性动词 | ❌ fails to capture → ✅ does not capture（或改写为"X 条件下不适用"） |
| D9 | 本文贡献甚微 | 删 | 若确无贡献，问题在实验设计，不在措辞。 |

---

## 五、位置敏感规则（同一句话，位置不同处理不同）

| 位置 | 策略 |
|---|---|
| 标题 / 摘要 | 零防御。不出现"可能/潜在/仅/遗憾"。只放问题、思路、最强结果。 |
| 引言前两段 | 零防御。不在贡献建立前讨论不足。 |
| 贡献列表 | 只写正向主张，每条附证据指向。不写"我们也尝试了…"。 |
| 方法节 | 假设与前提可写，但写成中性的技术条件，不写"这限制了我们的方法"。 |
| 实验节 | 允许数值上的不如，但必须给出条件、权衡或解释，不做价值判断。 |
| 讨论 / 局限性 | **允许严谨性内容集中于此**，按事实列条，客观、简短、不道歉。 |
| 结论 | 零防御。只强化记忆点，不新增自我否定。 |

---

## 六、英文论文高频替换速查

| 弱 | 强 |
|---|---|
| We only evaluate on X | We evaluate on X, where the method is designed to operate |
| might be able to | can |
| potentially useful | useful（或直接说用途） |
| seems to suggest | shows / indicates（有证据时） |
| Unfortunately, we could not… | We did not evaluate…（必要时）／删除 |
| a relatively small improvement | an improvement of 3.2 points |
| just a first step | the first formulation of X |
| It should be noted that our method has limitations | Our method assumes X（写在 Limitations） |
| We failed to outperform | We match A and outperform B by 8% |

---

## 七、诊断输出自检

逐处改完后，回看三件事：

1. 有没有把**必须保留的科学事实**一起删掉？（若有，恢复，改放到讨论节）
2. 有没有**新增原文没有的主张或证据**？（若有，撤回）
3. 改动是否**超过"必要最小"**？（若整段被重写，退回，只保留必要改动）
