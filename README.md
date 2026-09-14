# 基于Spark的中国新冠疫情统计分析与回归预测

## 项目简介

基于Spark对新冠疫情数据进行统计分析与回归预测，对比决策树与线性回归模型效果，通过Matplotlib实现可视化。

## 技术栈

- **数据处理**：PySpark + Spark SQL
- **机器学习**：Spark MLlib（决策树回归、线性回归）
- **可视化**：Matplotlib
- **语言**：Python 3.8+

## 项目架构

```
原始Excel数据 → Pandas数据预处理(ETL) → Spark SQL多维度统计分析 → Matplotlib可视化
                                                          ↓
                                              Spark MLlib回归预测建模
                                              (决策树回归 vs 线性回归对比)
```

## 目录结构

```
covid-19-spark-analysis/
├── README.md                    # 项目说明
├── requirements.txt             # 依赖包
├── config/
│   └── config.py                # 配置文件
├── data/
│   └── README.md                # 数据说明
├── src/
│   ├── 01_data_preprocessing.py # 数据预处理
│   ├── 02_spark_sql_analysis.py # Spark SQL多维度分析
│   ├── 03_regression_prediction.py # 回归预测建模（决策树vs线性回归）
│   └── 04_visualization.py      # Matplotlib可视化
├── output/                       # 输出结果
└── docs/
    └── architecture.md           # 详细架构说明
```

## 数据说明

- 数据来源：新冠疫情公开数据（覆盖全国31个省份）
- 数据量：10万+条时序数据
- 字段：日期、省份、城市、确诊人数、死亡人数、治愈人数等
- 数据清洗准确率：98%+

## 运行步骤

### 1. 环境准备
```bash
pip install -r requirements.txt
```

### 2. 数据预处理
```bash
python src/01_data_preprocessing.py
```
- 读取Excel疫情数据（覆盖全国31个省份、10万+条时序数据）
- 检查缺失值与重复值
- 完成格式转换（Excel转CSV）
- 数据清洗准确率达98%+

### 3. Spark SQL多维度分析
```bash
python src/02_spark_sql_analysis.py
```
- TopN查询（确诊前五省份、湖北前五城市）
- 窗口函数排名
- 武汉月度确诊趋势分析
- 疫情拐点识别
- 复杂查询响应时间<3秒

### 4. 回归预测建模
```bash
python src/03_regression_prediction.py
```
- 训练决策树回归模型
- 训练线性回归模型
- 对比模型评估结果（决策树R²约0.46，线性回归R²约0.0）
- 分析线性回归失效原因（疫情数据呈非线性特征）
- 得出决策树回归更适合疫情预测的结论

### 5. 数据可视化
```bash
python src/04_visualization.py
```
- 湖北前五城市确诊柱状图
- 武汉每日确诊折线图
- 疫情趋势与拐点展示

## 项目成果

1. 完成疫情数据从预处理、Spark SQL多维度分析到回归预测建模的完整数据分析流程
2. 识别武汉疫情拐点（2月12日确诊人数最多）
3. 通过模型对比验证决策树回归在疫情预测中的适用性

## 量化指标

| 指标 | 数值 |
|------|------|
| 覆盖省份 | 31个 |
| 数据量 | 10万+条时序数据 |
| 数据清洗准确率 | 98%+ |
| 复杂查询响应时间 | <3秒 |
| 决策树回归R² | 约0.46 |
| 线性回归R² | 约0.0 |
| 疫情拐点识别 | 2月12日（确诊人数最多） |
