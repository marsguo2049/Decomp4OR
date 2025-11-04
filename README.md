# Decomp4OR

运筹优化模型分解对比框架 | Operations Research Decomposition Benchmarking Framework

标准化拆分集成模型为子问题流水线，公平对比求解性能 | Standardized pipeline for splitting integrated OR models into subproblems with fair performance comparison

---

## 描述 | Overview

运筹优化模型分解对比框架：标准化拆分集成模型为子问题流水线，公平对比求解性能。

Operations Research decomposition benchmarking framework: standardized pipeline for splitting integrated OR models into subproblems with fair performance comparison.

---

## 核心功能 | Features

- **模块化拆分 | Modular Decomposition**：按决策域/时间/空间/资源维度拆解模型 | Split by decision domain/time/space/resource
- **标准流水线 | Standard Pipelines**：集成基线、顺序求解、迭代修复、主从分解 | Integrated baseline, sequential, iterative, master-sub
- **公平对比 | Fair Comparison**：统一实例、预算、随机种子 | Unified instances, budgets, random seeds
- **可复现 | Reproducible**：结构化输出与配置管理 | Structured outputs and configuration management

---

## 快速开始 | Quick Start

### 1. 分析模型 | Analyze Model
识别决策变量、耦合约束、目标组成 | Identify decision variables, coupling constraints, objective components

### 2. 选择流水线 | Select Pipelines
- 必选 | Required：集成基线 | Integrated baseline
- 可选 | Optional：顺序/迭代/主从分解（选 1-3 条）| Sequential/iterative/master-sub (choose 1-3)

### 3. 执行对比 | Run Benchmark
```bash
# 配置流水线 | Configure pipelines
pipelines:
  - Integrated_Baseline
  - Sequential_A_B
  
# 运行 | Execute
python run_benchmark.py --config config.yaml

# 输出 | Outputs
results/{instance}/{pipeline}/summary.json
```

### 4. 查看结果 | View Results
```bash
python aggregate_results.py --output report.csv
```

---

## 输出格式 | Output Format

```json
{
  "instance": "case01",
  "pipeline": "Sequential_A_B",
  "solver": {"status": "optimal", "wall": 120.5, "gap": 0.005},
  "objective": {"total": 1050.2, "components": {...}},
  "coupling": {...}
}
```

---

## 目录结构 | Directory Structure

```
Decomp4OR/
├── config.yaml          # 流水线配置 | Pipeline configuration
├── models/              # 模型实现 | Model implementations
│   ├── integrated.py
│   └── decomposed.py
├── pipelines/           # 流水线定义 | Pipeline definitions
├── instances/           # 实例数据 | Instance data
├── results/             # 求解结果 | Solving results
└── scripts/             # 执行脚本 | Execution scripts
```

---

## 文档 | Documentation

详见 `SPEC.md` 完整规范 | See `SPEC.md` for full specification

---

## 许可 | License

MIT
