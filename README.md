# 垃圾分類專案

## 1. 專案介紹
垃圾分類是一個重要的環保議題。本專案旨在開發一個機器學習模型，將垃圾分類為六大類別：**紙板 (Cardboard)、玻璃 (Glass)、金屬 (Metal)、紙張 (Paper)、塑膠 (Plastic)、一般垃圾 (Trash)**。目標是提高垃圾分類效率，促進環保永續發展。

## 2. 專案結構
```
Garbage-Classification/
├── Garbage-Classification-main/
│   ├── test/
│   ├── test_data_set/
│   │   ├── cardboard/
│   │   ├── glass/
│   │   ├── metal/
│   │   ├── paper/
│   │   ├── plastic/
│   │   └── trash/
│   ├── training_data_set/
│   │   ├── cardboard/
│   │   ├── glass/
│   │   ├── metal/
│   │   ├── paper/
│   │   ├── plastic/
│   │   └── trash/
│   ├── model/
│   ├── scripts/
│   │   ├── train.py   
│   │   ├── predict.py 
│   │   ├── preprocess.py 
│   ├── requirements.txt
│   ├── README.md
```

## 3. 環境設定
### 必要套件
使用以下指令安裝相依套件：
```sh
pip install -r requirements.txt
```

## 4. 資料集
本專案的資料集分為 **訓練集 (Training Set)** 和 **測試集 (Test Set)**：
- **訓練集**：共 1800 張圖片（每類 300 張）
- **測試集**：共 300 張圖片（每類 50 張）

圖片來源包含網路下載與自行拍攝，並經過統一預處理。

## 5. 資料前處理
- 統一將圖片調整為 **512x384** 大小。
- 進行 **資料增強**（翻轉、旋轉）。
- 轉換所有圖片為 **JPEG 格式**。
- 依類別存放圖片至對應資料夾。

## 6. 模型訓練
本專案使用了三種深度學習模型進行訓練：
- **CNN**
- **VGG16**
- **ResNet50V2**

### 訓練參數：
- 訓練回合數 (Epochs)：150
- 損失函數 (Loss Function)：Categorical Crossentropy
- 優化器 (Optimizer)：Adam
- 提早停止 (Early Stopping)：當驗證集損失 (Validation Loss) 連續 30 次未提升時，停止訓練。

## 7. 模型表現
| 模型         | 準確率 |
|-------------|--------|
| CNN         | 0.69   |
| VGG16       | 0.75   |
| ResNet50V2  | 0.84   |

ResNet50V2 的表現最佳，主要因為 **殘差網路 (Residual Block) 架構**，能有效學習深層特徵，提高準確率。

## 8. 部署與使用
執行垃圾分類預測：
```sh
python predict.py --image path/to/image.jpg
```

## 9. 未來改進方向
- 擴增資料集，提高多樣性。
- 微調模型參數，提升分類準確率。
- 開發 Web 應用，提供即時垃圾分類服務。



 
