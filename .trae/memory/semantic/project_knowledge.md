# 项目知识

记录项目的技术栈、架构和开发规范。

## 项目概述

- 项目名称：Stock（量化分析工具）
- 项目路径：d:\TRAE_Project\Stock
- GitHub仓库：待创建

## 技术栈

- **Python 3.14**
- **finshare**（金融数据获取库）
- **akshare**（备用，数据源有时不通）
- **新浪财经API**（直接请求，无需安装）
- **Pandas**（数据处理）
- **Backtrader** / **Backtesting.py**（回测框架）
- **Jupyter Notebook**（开发环境）
- **Anaconda**（环境管理）

## 目录结构

```
Stock\
├── .gitignore           # Git忽略文件配置
├── .trae\               # AI辅助目录
│   ├── rules\           # 规则文件
│   ├── skills\          # 技能文件
│   ├── memory\          # 记忆层
│   └── docs\            # Trae文档
├── docs\                # 项目文档
│   ├── plan\            # 规划文档
│   │   ├── 量化分析学习规划.md
│   │   ├── 任务清单.md
│   │   └── 状态快照.json
│   └── tutorials\       # 教程文档
│       └── phase1\      # 阶段一教程
│           ├── 1.1_什么是量化投资.md
│           └── 阶段一_认知建立.md
├── src\                 # 源代码（待创建）
├── data\                # 数据存储（待创建，已在.gitignore）
├── strategies\          # 策略库（待创建）
└── notebooks\           # Jupyter笔记（待创建）
```

## .gitignore 配置

已配置以下忽略规则：

```
# Python缓存
__pycache__/
*.py[cod]

# Jupyter
.ipynb_checkpoints/

# 数据文件
data/
*.csv
*.xlsx

# 虚拟环境
venv/
env/

# 日志
*.log

# 量化相关
*.pkl
.backtest/
logs/
```

## A股数据获取

### finshare（主力方案）

```python
from finshare import get_data_manager

m = get_data_manager()
s = m.get_snapshot_data('600519')
r = m.get_batch_snapshots(['600519','000858','300750'])
```

特点：多数据源自动切换、完全免费

### 新浪财经API（备用方案）

```python
import requests
r = requests.get('https://hq.sinajs.cn/list=sh600519',
    headers={'Referer': 'https://finance.sina.com.cn'})
```

## 开发规范

1. 使用Trae IDE内置工具
2. 修改前先读取文件
3. 复杂任务使用TodoWrite跟踪
4. 教程文档同步生成到 docs/tutorials/
5. 规划文档存放在 docs/plan/
6. 状态快照实时更新

## 学习进度

当前阶段：阶段一 - 认知建立（已完成）
- [x] 1.1 什么是量化投资（已完成，含2张配图+参考答案）
- [x] 1.2 金融市场基础（已完成，含2张配图+参考答案）
- [x] 1.3 常见技术指标原理（已完成，含6张配图+参考答案）
- [x] 1.4 量化策略基础思想（已完成，含4张配图+参考答案）

**下一步：阶段二 - Python入门**
