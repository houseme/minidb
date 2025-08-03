# MiniDB Test Framework

基于第一性原理、奥卡姆剃刀法则、KISS法则和软件工程最佳实践设计的数据库测试框架。

## 设计原则

### 🎯 第一性原理
- **测试目的**: 验证功能正确性、发现问题、辅助调试
- **核心需求**: 快速定位问题、全面覆盖功能、简化维护

### 🔪 奥卡姆剃刀法则
- **简单有效**: 选择最直接的测试方法
- **避免过度设计**: 只实现必要的测试功能

### 💡 KISS法则
- **保持简单**: 测试脚本易读易懂
- **统一接口**: 一个命令运行所有测试
- **清晰输出**: 直观的测试结果展示

## 框架结构

```
test/framework/
├── README.md                 # 框架说明文档
├── run_tests.sh             # 统一测试入口
├── config/                  # 测试配置
│   ├── test_config.sh       # 全局配置
│   └── test_data.sh         # 测试数据定义
├── unit/                    # 单元测试
│   ├── basic_operations/    # 基础操作测试
│   ├── query_engine/        # 查询引擎测试
│   └── storage_engine/      # 存储引擎测试
├── integration/             # 集成测试
│   ├── sql_features/        # SQL功能测试
│   ├── performance/         # 性能测试
│   └── compatibility/       # 兼容性测试
├── regression/              # 回归测试
│   └── bug_fixes/           # 已修复问题测试
├── utils/                   # 测试工具
│   ├── test_runner.sh       # 测试执行器
│   ├── report_generator.sh  # 报告生成器
│   ├── db_helper.sh         # 数据库辅助函数
│   └── assertion.sh         # 断言库
└── reports/                 # 测试报告输出目录
```

## 使用方法

### 运行所有测试
```bash
cd test/framework
./run_tests.sh
```

### 运行特定类型测试
```bash
./run_tests.sh unit           # 仅运行单元测试
./run_tests.sh integration    # 仅运行集成测试
./run_tests.sh regression     # 仅运行回归测试
```

### 运行特定模块测试
```bash
./run_tests.sh unit/basic_operations     # 基础操作测试
./run_tests.sh integration/sql_features  # SQL功能测试
```

### 调试模式
```bash
./run_tests.sh --debug       # 详细调试信息
./run_tests.sh --verbose     # 详细输出
./run_tests.sh --stop-on-fail # 遇到失败立即停止
```

## 测试报告

测试完成后会生成以下报告：
- `reports/summary.html`: 测试总结报告
- `reports/detailed.log`: 详细测试日志
- `reports/coverage.txt`: 功能覆盖报告
- `reports/performance.json`: 性能测试数据

## 添加新测试

1. 确定测试类型（unit/integration/regression）
2. 在相应目录下创建测试脚本
3. 遵循命名规范：`test_[module]_[feature].sh`
4. 使用统一的断言库和工具函数