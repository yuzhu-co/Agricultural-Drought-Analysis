# Agricultural-Drought-Analysis
agri-drought-ML/
│
├── README.md                        ← 项目介绍（你的论文摘要 + 结果）
├── data/                            ← 数据或样例文件
│   ├── drought_indices.csv
│   └── yield_data.csv
│
├── src/                             ← 代码脚本（Python 或 R）
│   ├── model_training.ipynb         ← Colab Notebook
│   ├── feature_importance.py
│   └── evaluation_metrics.py
│
├── output/                          ← 模型结果图片与图表
│   ├── feature_importance.png
│   ├── NDI_validation.png
│   ├── model_comparison.png
│   └── yield_anomaly_map.png
│
└── requirements.txt                 ← 环境依赖（可选）


# Morocco Drought Monitoring using Machine Learning

This repository presents the Master Thesis Project focusing on the application of machine learning and deep learning models for agricultural drought monitoring in Morocco. The study integrates multi-source remote sensing datasets and statistical learning models to construct a New Drought Index (NDI) that captures the spatiotemporal dynamics of drought.

## Abstract

Drought is one of the most costly and complex natural disasters worldwide. This study develops a machine learning-based drought monitoring framework for Morocco's agricultural zones. The framework leverages multiple remote sensing indices—VCI, TCI, SMCI, and GPPCI—as proxies for crop responses to drought.

Four machine learning models (Random Forest, XGBoost, ANN, LSTM) and a linear regression baseline are compared. The models successfully predict drought at least three months in advance, revealing that temperature-related indices dominate early-season prediction, while vegetation indices become more influential later in the growing season.

**Keywords**: Drought prediction, Remote sensing, Machine Learning, Morocco, New Drought Index (NDI)

## Research Objectives

- Optimize multi-source data selection for agricultural drought monitoring.
- Develop a machine learning framework for constructing a New Drought Index (NDI).
- Monitor drought propagation and assess model effectiveness across Morocco's agricultural zones.

## Study Scope

The project integrates remote sensing data (temperature, precipitation, soil moisture, vegetation indices) and machine learning models (RF, XGBoost, ANN, LSTM) to monitor and predict agricultural drought. It focuses on winter wheat regions across Morocco and does not include yield forecasting beyond drought impact analysis.

## Methodology

### 1. Data Preparation

- **Data sources**: Landsat, MODIS, Sentinel, ERA5, GPM
- **Variables**: NDVI, LST, Soil Moisture, GPP, Precipitation, Temperature
- **Temporal span**: 2000–2023 (monthly data)

### 2. Machine Learning Models

- **Linear Regression** (baseline)
- **Random Forest (RF)** — ensemble tree model for nonlinear patterns
- **XGBoost** — gradient-boosted decision trees with regularization
- **Artificial Neural Network (ANN)** — non-linear regression for drought-yield mapping
- **LSTM** — time-series deep learning for drought propagation

### 3. Evaluation Metrics

- R² (Coefficient of determination)
- RMSE (Root Mean Square Error)
- SMAPE (Symmetric Mean Absolute Percentage Error)
- Feature importance and SHAP interpretation

## Model Outputs

| Figure | Description |
|--------|-------------|
| `feature_importance.png` | Feature importance of drought indices |
| `NDI_validation.png` | Validation of New Drought Index vs SPI |
| `model_comparison.png` | Performance comparison of ML/DL models |
| `yield_anomaly_map.png` | Spatial variation of yield anomalies |

## Results and Findings among Different ML/DL Models
4.3.1 Performance Evaluation of the Proposed NDI
Figure 6 compares performances among different models: Linear Regression, Random Forest, XGBoost, ANN, and LSTM. XGBoost and Random Forest reach the top two performance levels, with an R² of 0.68 and 0.64, RMSE of 0.31 and 0.32, and SMAPE of 91.4 and 95.2 on the validation set, respectively. The performance of models like ANN and LSTM is better than the Linear Regression baseline, with R² values of 0.66 and 0.65. The figure also demonstrates that the prediction performance in March is already close to the actual performance in June, suggesting that the model can predict drought three months in advance.

4.3.2 Model Interpretation
Table 7. Zone-wise Comparison of Key Variables Across Models

### Zone-wise Comparison of Model Interpretation

| Zone | RF + SHAP | ANN Sensitivity (+5%) | LSTM Sensitivity (+5%) | Key Insight |
|------|-------------|------------------------|--------------------------|--------------|
| **1** | Nov–Feb: TCI<br>Mar: GPP + VCI | Mar: VCI + GPP<br>Nov–Feb: TCI | Nov–Feb: TCI<br>Mar: GPP | Similar pattern to whole region; transitional geographic characteristics |
| **2** | Jan–Feb: SMCI<br>Mar–Apr: GPP | Feb: TCI<br>Mar: GPP | Nov–Mar: TCI<br>Apr: GPP | SMCI critical in mountainous areas; delayed sowing pattern |
| **3** | Nov–Feb: TCI<br>Feb–Mar: GPP<br>Apr–Jun: VCI | Feb–Apr: GPP<br>May: VCI | Nov–Jan: GPP<br>Apr: Peak sensitivity | Early crop development; peak sensitivity in April |
| **4** | Nov–Feb: TCI<br>Mar–May: GPP | Feb: TCI<br>Mar: GPP<br>Apr: VCI | Nov–Jun: VCI<br>Mar: GPP | GPP in March consistently important despite variable performance |
| **5** | Mar: GPP<br>Mar: VCI | Feb–May: GPP | Feb–Jun: TCI<br>Mar: GPP | GPP in March strongest indicator; aligns with linear regression |

**Key Findings from Model Interpretation:**

- **Temporal Patterns:**  
  - TCI dominates the early season (Nov–Feb).  
  - GPP becomes the most influential factor in **March**.  
  - VCI gains importance during the late season (Apr–Jun).  
- **Spatial Variability:**  
  - Zone 2 shows strong dependence on **SMCI** due to mountainous terrain.  
  - Zone 3 exhibits the **earliest peak in sensitivity**, aligning with early crop development.  
  - Zone 5 demonstrates the highest model consistency, with GPP as the leading drought indicator.  

Spatial Variations:

Zone 1: Follows regional patterns

Zone 2: SMCI critical in mountainous regions

Zone 3: Early sensitivity peak in April

Zone 5: Strong GPP influence in March

4.3.3 Validation using SPI against NDI
The correlation analysis shows strong consistency between predicted NDI values and SPI values, particularly with SPI-3:

Zone 3 (March): XGBoost NDI vs SPI-3: R = 0.787 (p < 0.0001)

Zone 5 (January): LSTM NDI vs SPI-1: R = 0.665, vs SPI-3: R = 0.539 (p < 0.0001)
