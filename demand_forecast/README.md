# 采购/库存需求预测 PoC

## 项目简介
对关键物料进行短期（周/月）需求预测，帮助采购与备货决策，减少缺货与过量库存。适合展示数据处理、特征工程、时间序列建模与模型评估能力。

## 目标
- 基于历史出入库与订单数据，构建可复现的预测流程
- 在单一物料上实现比基线（Naive）更好的 MAE/SMAPE 指标

## 技术栈
- Python, pandas, scikit-learn
- 时间序列库：Prophet / statsmodels / sktime
- 可视化：plotly / matplotlib
- 部署：Docker + FastAPI（可选）

## 最小可行代码结构
projects/demand_forecast/
├─ data/                  # 历史出入库/订单 CSV
├─ notebooks/
│  └─ demand_forecast_demo.ipynb
├─ src/
│  ├─ preprocess.py       # 数据清洗与特征工程
│  ├─ model.py            # 建模与预测接口
│  └─ evaluate.py         # 指标计算与可视化
├─ requirements.txt
└─ README.md

## 安装与运行（示意）
1. pip install -r requirements.txt
2. 在 `data/` 放入示例 CSV（示例包含日期、物料编码、出入库数量等）
3. 打开 notebook 运行端到端示例

## 量化指标（示例）
- 训练集：过去 24 个月的日/周频数据
- 指标：MAE、SMAPE（目标优于基线 Naive）

## 扩展建议
- 对多个物料/品类做并行训练并抽取可解释特征（如促销、交付周期）
- 实现自动化 retrain pipeline（按月/按周）并推送预测到 SAP/BI 系统
