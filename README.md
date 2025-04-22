# 114-2 演算法期中量子退火專題

## 檔案結構
```
├── dataset/  
│   ├── keller4.mis          # Keller4 資料集  
│   ├── keller5.mis          # Keller5 資料集  
│   ├── keller6.mis          # Keller6 資料集  
│   ├── p_hat300-1.mis       # p_hat300‑1 資料集  
│   ├── p_hat700-1.mis       # p_hat700‑1 資料集  
│   └── p_hat1500-1.mis      # p_hat1500‑1 資料集  
│  
├── notebooks/               # Jupyter Notebook 存放目錄  
│   ├── main.ipynb           # 解所有資料集的code
│   └── experiments.ipynb    # 進行實驗&結果分析與可視化的code
│  
├── docs/                    # 文件與報告存放目錄  
|   ├── readme_image.png     # 此readme 用到的圖片文件，可不予理會
│   └── 114-2演算法期中報告.pdf  # 期中報告書  
│ 
├── README.md                # 專案說明（此檔案）  
└── requirements.txt         # Python 套件依賴清單  
```

## 如何執行
1. 在 terminal 執行
```
pip install -r requirements.txt
```
2. 在 `notebooks/main.ipynb` 檔案中可以找到對所有資料集的實作以及結果
3. 在 `notebooks/experiments.ipynb` 檔案中可以找到我所有報告中出現實驗的 implement code
* 執行時請注意 dataset 檔案路徑
## Results Overview

以下為各資料集的最小頂點覆蓋結果（MVC），與已知最佳解比較：

| Dataset          | \|V\| | \|E\|   | Known Best MVC | My Result (MVC) | Reads | Sweeps | λ (computed) | Valid | Time (s) |
|------------------|------|--------|----------------|------------------|--------|--------|----------------|--------|----------|
| keller4.mis      | 171  | 5100   | 160            | 160              | 2000   | 1000   | 149.12         | ✅     | 0.6      |
| keller5.mis      | 776  | 22599  | 749            | 749              | 2000   | 2000   | 481.38         | ✅     | 5.4      |
| keller6.mis      | 3361 | 153729 | 3302           | 3306             | 5000   | 5000   | 1527.2         | ✅     | 178.6    |
| p_hat300-1.mis   | 300  | 10933  | 292            | 292              | 1000   | 2500   | 565.28         | ✅     | 1.3      |
| p_hat700-1.mis   | 700  | 48644  | 689            | 689              | 1000   | 4000   | 1311.79        | ✅     | 6.3      |
| p_hat1500-1.mis  | 1500 | 568960 | 1488           | 1488             | 1000   | 6000   | 2797.76        | ✅     | 44.9     |

- ✅ 表示所求解皆為合法解（覆蓋所有邊）
- 唯一未達到最佳解者為 `keller6`，與最小值僅相差 4 點，屬於高品質近似解

此外也進行了參數調整與可視化分析實驗，包括：
- 不同 reads 對結果穩定性與品質的影響
- sweeps 深度對收斂速度的效益分析
- beta_range 與 beta_schedule 的比較實驗
- λ 懲罰權重的調整策略與經驗公式 $\lambda = \frac{|E|}{|V|} \cdot c$
- 解答分布圖，觀察解空間的穩定性與變異性
![alt text](/docs/readme_image.png)

詳細數據、圖表與分析內容請參考 `notebooks/experiments.ipynb` 與 `docs/114-2演算法期中報告.pdf`