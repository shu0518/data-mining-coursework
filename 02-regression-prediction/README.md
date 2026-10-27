# Data Mining Project 2: Regression Prediction

本專案的目標是解決連續數值的預測問題。在 Adult 資料集上以 KNN、SVR、Random Forest、XGBoost 預測每週工時（hours_per_week），比較四種演算法的表現；並在 Boston Housing 資料集上以 XGBoost 搭配 5-Fold 交叉驗證預測房價，評估模型的穩定性與特徵篩選的效果。

## 📂 專案結構

本專案包含以下核心程式碼與資料集：

### 核心模型
- **`KNN_regressor.ipynb`**:
  - 使用 **K-Nearest Neighbors** 進行迴歸預測。
  - 包含資料標準化（Standardization）以優化距離計算。
  
- **`SVR.ipynb`**:
  - 使用 **Support Vector Regression**。
  - 探討不同核函數（Kernel functions）對預測的影響。

- **`RandomForest.ipynb`**:
  - 使用 **Random Forest**（Bagging 集成學習）。
  - 分析特徵重要性（Feature Importance），找出影響房價的關鍵因素。

- **`XGBoost.ipynb`**:
  - 使用 **XGBoost**（Gradient Boosting）。
  - 比較其與傳統機器學習模型的效能差異。

### 進階實驗
- **`XGBoost_kfold.ipynb`**:
  - 使用 **K-Fold Cross-Validation** 進行模型驗證。
  - 透過多折驗證確保模型沒有 Overfitting，並取得更客觀的平均誤差值。

### 資料集
- **`housing.csv`**:
  - 經典的波士頓房價資料集。
  - **目標變數 (Target)**: `MEDV` (自有住宅房價中位數)。
  - **特徵 (Features)**: 包含犯罪率 (`CRIM`)、房間數 (`RM`)、屋齡 (`AGE`) 等 13 個特徵。

## 🚀 實驗結果 (Results)

透過比較 RMSE (均方根誤差)、MAPE (平均絕對百分比誤差) 與 R² Score 評估各模型表現。

### 1. Adult 資料集：預測每週工時 (`hours_per_week`)

在相同的訓練／測試切分下比較四種演算法，**XGBoost** 的整體表現最佳，且訓練時間遠低於 SVR 與 Random Forest。

| Model | RMSE | MAPE (%) | R² Score | Note |
|-------|------|----------|----------|------|
| **XGBoost** | **10.86** | 30.68 | **0.243** | Best Accuracy, Fastest Training |
| **SVR (RBF)** | 10.92 | **30.16** | 0.234 | |
| **Random Forest** | 11.15 | 31.14 | 0.202 | Feature Importance Analysis |
| **KNN** | 11.30 | 32.15 | 0.181 | Baseline |

> 註：四個模型的 R² 皆低於 0.25，代表 Adult 資料集的人口統計特徵僅能解釋每週工時的一小部分變異。

### 2. Boston Housing：XGBoost 5-Fold 交叉驗證（預測房價 `MEDV`）

以 5-Fold 交叉驗證評估模型穩定性，並比較依特徵重要性篩選特徵的效果。以累積重要性 95.4% 篩選特徵時表現最佳。

| Feature Setting | RMSE | MAPE (%) | R² Score | Note |
|-----------------|------|----------|----------|------|
| Baseline (13 Features) | 3.08 | 10.80 | 0.886 | |
| Strategy 1: Top-5 Features | 3.38 | 12.01 | 0.861 | |
| Strategy 2: Threshold (1%) | 3.00 | 10.84 | 0.892 | |
| **Strategy 3: Cumulative Importance (95.4%)** | **2.97** | **10.77** | **0.894** | Best |

> 註：表中數值為 5-Fold 的平均結果，詳細數值請參考各 Notebook 的輸出結果。

## 🛠️ 技術細節

- **資料前處理 (Preprocessing)**:
  - 缺失值檢查。
  - 特徵縮放 (Feature Scaling)：針對 KNN 與 SVR 使用 `StandardScaler`。
- **評估指標 (Metrics)**:
  - **RMSE**: 衡量預測值與真實值的平均誤差程度。
  - **MAPE**: 衡量誤差的百分比，較易於商業解釋。
  - **R²**: 解釋模型對變異數的解釋能力。
