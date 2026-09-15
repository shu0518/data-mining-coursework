# 資料探勘課堂練習

大學資料探勘課程的四份練習，各自獨立成一個資料夾，處理不同的資料探勘任務。每個子資料夾都有自己的 README 說明實作細節，這份是總覽。

## 四個練習

| 資料夾 | 主題 | 資料集 | 演算法 |
|---|---|---|---|
| [`01-decision-tree-classification`](01-decision-tree-classification) | 決策樹分類 | Adult 收入預測 | ID3、C4.5、CART、C5.0，比較四種切割準則 |
| [`02-regression-prediction`](02-regression-prediction) | 迴歸預測 | Boston Housing 房價 | KNN、SVR、Random Forest、XGBoost，含 K-Fold 交叉驗證 |
| [`03-clustering-analysis`](03-clustering-analysis) | 分群分析 | Banana / Sizes3（2D 非凸資料） | K-Means、DBSCAN、Hierarchical Clustering |
| [`04-association-rule-mining`](04-association-rule-mining) | 關聯規則探勘 | 模擬電商交易資料 | Apriori / FP-Growth 購物籃分析 |

## 執行方式

全部都是 Jupyter Notebook（`.ipynb`），沒有額外的 Python 依賴檔——用 Jupyter 或 Colab 直接開啟對應資料夾裡的 `.ipynb` 即可執行，資料集（csv/xlsx）都已放在同一資料夾內，不需要額外下載。

```bash
git clone https://github.com/shu0518/data-mining-coursework.git
cd data-mining-coursework/01-decision-tree-classification
jupyter notebook ID3.ipynb
```

## 說明

這是課堂練習，重點是比較同一類任務下不同演算法的行為差異（例如決策樹切割準則、分群演算法對非凸資料的表現），不是要做成一個可重複使用的框架或套件。
