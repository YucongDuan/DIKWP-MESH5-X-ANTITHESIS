# DIKWP-MESH5 ΦX / ANTITHESIS

## 自证伪因果宪法与科研生态编译系统

**ANTITHESIS 不是又一个概念仓库。它是位于全部仓库之上的“证据—证伪—冲突—晋级”总控层。**

它把公开仓库、README、测试回执、复现记录、失败记录和跨系统依赖，编译为：

- 逐主张的 E0—E7 证据状态；
- 强制失败阈值、停止条件、反例与回滚的证伪合同；
- `supports / contradicts / duplicates / depends_on` 主张图；
- 在固定预算内最大化信息增益的“最小决定性实验集”；
- `PROMOTE / PILOT / REVIEW / HOLD / RETIRE` 五态、可撤回、自动到期的发布宪法；
- 防篡改哈希链、Merkle 根与可选 HMAC 封印；
- 完全离线、无外部脚本依赖的交互式仪表盘。

系统的第一条规则是：**仓库通过自测，不等于仓库内所有主张成立。**

![ANTITHESIS offline dashboard](dashboard/preview.png)

---

## 为什么是这个系统

对 YucongDuan 公共 GitHub 生态的研究显示，现有仓库已经覆盖：

1. DIKWP/MESH 理论、25 类转换、无定义语义与 Φ0 无语义因果等价；
2. Runtime Commons、TRUSTFABRIC、Inquiry Kernel 等运行时与互操作层；
3. ProofLedger、CREDENCE²、MANDATE² 等证据与授权层；
4. P-Space、ACRS 等行动门控与封闭世界安全评测；
5. ARK 等高影响垂直应用；
6. EIR-Mesh 的主航道、Repo Atlas、Flagship Funnel 与 Release Gate。

真正缺少的不是第 N+1 个垂直仓库，而是一个能够对**所有仓库和自身**执行以下动作的系统：

- 把每条宏大主张变成可被杀死的实验合同；
- 把同一团队的多次成功与独立复现严格区分；
- 发现重复、依赖和跨仓库理论冲突；
- 拒绝“README 完整”“代码开源”“10/10 自测通过”被包装成普遍有效；
- 用最小实验预算决定该合并、试点、暂停、退役还是晋级。

ANTITHESIS 对自己应用同一套规则。本版本内部测试通过后，仍只能获得 **PILOT**，不能获得 PROMOTE。

---

## 当前演示的关键发现

内置演示使用 10 个代表性公开仓库、ANTITHESIS 自身，以及用户提供的 DIKWP-MESH5 Φ0 回执：

- 12 个仓库；
- 14 条核心主张；
- 19 条证据记录；
- 4 个 `HOLD`；
- 7 个 `REVIEW`；
- 1 个 `PILOT`；
- 0 个 `PROMOTE`。

当前第一优先级不是继续增加仓库，而是执行一个联合证伪实验：

> **Φ0 无永久语义核心 ↔ MESH Runtime Commons 语义资源运行时**

实验比较三条路径：

- A：纯 Φ0 因果等价迁移；
- B：纯 Runtime Commons 语义合同迁移；
- C：`Φ0 核心 → 有损 DIKWP 审计影子 → Runtime 合同` 的分层架构。

关键测量包括：跨开放权重模型的留出迁移准确率、cycle error、投影损失、语义泄漏、残差保留、25 转换一致性、回滚误差和跨团队复现。若语义见证层改变 Φ0 因果等价类、残差被吞没，或分层架构显著劣于任一单独路径，则拒绝统一架构并保持两套系统分离。

---

## 六条不可修改的系统宪法

1. **No claim without a kill test.** 没有失败阈值的主张不能进入发布流程。
2. **No release without rollback.** 没有可执行回滚的系统只能 HOLD。
3. **No flagship promotion without independent replication.** 同一团队的成功最多支撑 PILOT。
4. **Evidence is per claim, never per repository.** 禁止仓库级证据洗白。
5. **Failures, contradictions and residuals are first-class.** 失败、冲突与残差不得被静默删除。
6. **Promotion is reversible, scoped and time-bounded.** 晋级自动到期，必须用新证据续期。

---

## 快速启动

要求 Python 3.10 或更高版本。运行时不依赖第三方库。

```bash
python -m venv .venv
source .venv/bin/activate          # Windows: .venv\Scripts\activate
pip install -e .

dikwp-antithesis conformance

dikwp-antithesis demo \
  --out outputs/demo \
  --phi0 /path/to/phi0/outputs \
  --budget 60
```

打开：

```text
outputs/demo/dashboard.html
```

验证账本：

```bash
dikwp-antithesis verify-ledger --input outputs/demo/ledger.jsonl
```

运行测试：

```bash
python -m pytest -q
```

本交付包验证结果：**27/27 单元测试通过，12/12 宪法一致性检查通过。**

---

## 命令行接口

### 1. 编译现有 Portfolio JSON

```bash
dikwp-antithesis compile \
  --input examples/portfolio_minimal.json \
  --out outputs/custom \
  --policy config/default_constitution.json
```

### 2. 导入 Φ0 回执

```bash
dikwp-antithesis phi0 \
  --input /path/to/phi0/outputs \
  --out outputs/phi0_review
```

Φ0 适配器明确执行以下降格规则：

- 合成世界测试：最多 E3；
- 同一作者组的 conformance：仍是 E3；
- 残差记录：保留为未决义务，不计为支持；
- 没有独立复现：绝不生成 E5。

### 3. 只读扫描 GitHub 公开账号

```bash
export GITHUB_TOKEN=...            # 可选，仅用于提高 GitHub API 限额

dikwp-antithesis github \
  --owner YucongDuan \
  --readme-limit 30 \
  --out outputs/github_review
```

安全与证据边界：

- 只使用 GitHub 公开只读 API；
- 不执行任何仓库代码；
- README 中的主张只生成 E1“可追溯断言”；
- 不因 stars、forks、提交数量或开源许可证提高证据等级。

### 4. 离线扫描本地仓库

```bash
dikwp-antithesis scan /repos/project-a /repos/project-b --out outputs/local_review
```

---

## 输出结构

```text
outputs/demo/
├── input_portfolio.json
├── portfolio_report.json
├── decisions.json
├── experiment_queue.json
├── minimum_decisive_set.json
├── claim_graph.json
├── ledger.jsonl
├── ledger_verification.json
├── EXECUTIVE_BRIEF_CN.md
└── dashboard.html
```

`portfolio_report.json` 是完整机器可读交付物；`dashboard.html` 是单文件离线驾驶舱；`ledger.jsonl` 是逐事件哈希链。

---

## E0—E7 证据状态

| 层级 | 含义 | 不能被误称为 |
|---|---|---|
| E0 | 裸断言 | 证据 |
| E1 | 可追溯来源 | 可运行、正确 |
| E2 | 可执行程序或回执 | 稳定复现 |
| E3 | 作者侧/内部重复验证 | 独立复现 |
| E4 | 对抗、红队或反事实挑战 | 外部独立性 |
| E5 | 独立团队复现 | 跨情境普遍有效 |
| E6 | 跨模型、跨机构或跨情境验证 | 长期有效 |
| E7 | 持续现实审计与漂移监测 | 永久真理 |

证据状态属于单条主张，不能覆盖整个仓库。

---

## 设计边界

ANTITHESIS：

- 不证明意识；
- 不证明通用语义；
- 不替代科学同行评审、法律授权、伦理审查或受影响群体同意；
- 不执行任意 shell 命令；
- 不自动运行第三方仓库；
- 不把词法相似度称为语义真理；
- 不因系统生成了漂亮仪表盘而提高证据等级。

自动冲突与重复检测只是透明、可替换的词法基线。涉及重大决策时，应换接领域模型、因果干预或人工审查，并保留原始推断与修订记录。

---

## English synopsis

**DIKWP-MESH5 ΦX / ANTITHESIS** is a self-falsifying causal constitution and research-portfolio compiler. It sits above a repository ecosystem and turns prose claims into kill tests, evidence states, contradiction graphs, minimum decisive experiments, reversible release decisions, and tamper-evident receipts.

Its central rule is simple: a repository passing its own tests does not validate every claim inside it. Evidence is assessed per claim; same-producer successes are discounted; independent replication is mandatory for promotion; failures and residuals remain first-class records.

See `QUICKSTART_EN.md` and `docs/ARCHITECTURE_EN.md` for the English operational path.

---

## License

Apache License 2.0. See `LICENSE`.
