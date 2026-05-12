# 项目知识

记录项目的技术栈、架构和开发规范。

## 项目概述

- 项目名称：Stock
- 项目路径：d:\TRAE_Project\Stock

## 技术栈

- Python 3.14
- finshare（金融数据获取库）
- akshare（备用，数据源有时不通）
- 新浪财经API（直接请求，无需安装）

## A股数据获取

### finshare（主力方案）

```python
from finshare import get_data_manager

m = get_data_manager()
# 单只股票
s = m.get_snapshot_data('600519')
# 批量股票
r = m.get_batch_snapshots(['600519','000858','300750'])
```

特点：
- 多数据源自动切换（东方财富、腾讯、新浪、通达信、BaoStock）
- 内置缓存和熔断器
- 批量查询高效
- 完全免费，无需API Key

安装：`python -m pip install finshare`

### 新浪财经API（备用方案）

```python
import requests
r = requests.get('https://hq.sinajs.cn/list=sh600519',
    headers={'Referer': 'https://finance.sina.com.cn'})
```

特点：
- 无需安装
- 稳定可靠
- 支持上海(sh)、深圳(sz)股票和指数

### akshare（当前不通）

东方财富数据源被拒绝连接，暂不可用。

## 目录结构

```
Stock\
├── .trae\
│   ├── rules\       # 规则文件
│   ├── skills\       # 技能文件
│   ├── memory\       # 记忆层
│   ├── docs\         # 文档
│   └── 状态快照.json
└── docs\             # 项目文档
```

## 开发规范

- 使用Trae IDE内置工具
- 修改前先读取文件
- 复杂任务使用TodoWrite跟踪
