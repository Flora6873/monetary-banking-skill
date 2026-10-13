# monetary-banking — 货币银行学学习助手

一个用于《货币银行学》/《货币金融学》课程学习的 GitHub Skill，覆盖知识整理、习题生成、概念讲解、论文写作四类任务，并内置一个经过校验的货币金融计算器。

## 安装

把本目录放到 CodeBuddy 的 skills 目录即可：

```bash
cp -r monetary-banking ~/.codebuddy/skills/
```

## 目录结构

```
monetary-banking/
├── SKILL.md                        # 主文件：任务路由与工作流
├── README.md                       # 本文件
├── scripts/
│   └── calc.py                     # 货币金融计算器（7 个子命令）
├── references/
│   ├── knowledge-map.md            # 核心知识地图（八大主题）
│   ├── formulas.md                 # 公式速查（含适用条件）
│   ├── exercise-templates.md       # 六种题型的模板与示例
│   └── paper-guide.md              # 论文写作规范与选题
└── assets/                         # 预留资源目录
```

## 四类任务

| 任务 | 触发示例 | 产出 |
|---|---|---|
| 知识整理 | "把这章笔记整理一下" | 结构化 Markdown 笔记 |
| 习题生成 | "出几道货币乘数计算题" | 题目 + 详解 + 易错点 |
| 概念讲解 | "什么是流动性陷阱" | 三层递进式讲解 |
| 论文写作 | "写篇数字人民币的论文" | 提纲 → 正文 → 参考文献 |

## 计算器用法

```bash
python3 scripts/calc.py --help

# 货币乘数
python3 scripts/calc.py money_multiplier --rr 0.1 --c 0.05 --e 0.02 --t 0.3 --rt 0.05

# 存款派生
python3 scripts/calc.py deposit_expansion --reserve 0.2 --base 1000

# 费雪方程
python3 scripts/calc.py fisher --nominal 0.06 --inflation 0.02

# 债券久期
python3 scripts/calc.py duration --face 1000 --coupon 0.05 --ytm 0.06 --years 3

# 现值 / 复利终值
python3 scripts/calc.py present_value --fv 1000 --rate 0.05 --years 3
python3 scripts/calc.py compound --pv 1000 --rate 0.05 --years 3 --freq 12

# 外汇掉期
python3 scripts/calc.py exchange_swap --buy 6.45 --sell 6.50 --amount 1000000
```

支持子命令：`money_multiplier`、`deposit_expansion`、`present_value`、`compound`、`fisher`、`duration`、`exchange_swap`。

所有结果同时输出**计算过程**与**结果**，可直接写入习题解析。

## 使用示例

```
"帮我整理第三章利率理论的笔记"       → 生成结构化笔记
"出 5 道关于货币乘数的题，带计算题"   → 生成题目与详解
"解释一下基础货币和货币供应量的区别"  → 三层递进讲解
"写一篇关于 LPR 改革的课程论文"       → 提纲 → 正文 → 参考文献
```

## 设计原则

- **计算必校验**：所有数值经 `calc.py` 计算，杜绝心算错误。
- **公式带条件**：每个公式标注适用条件（考试的分水岭）。
- **诚实边界**：不编造数据与文献，不确定处明确说明。
