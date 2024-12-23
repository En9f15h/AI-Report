YOLOv5 在 Colab 平台上的使用與基本功能測試報告
一、背景與目的
YOLOv5（You Only Look Once）是一種廣泛應用於目標檢測的深度學習模型。本報告記錄了在 Google Colab 平台上完整運行 YOLOv5 主要功能（包括推理、驗證及訓練）的過程，旨在熟悉 YOLOv5 的基本工作流程及其主要功能實現。

二、實驗步驟
1. 環境準備
克隆代碼庫：使用 git clone 命令將 YOLOv5 的代碼庫克隆到本地環境。
安裝依賴：執行 pip install 命令安裝 requirements.txt 中列出的所需依賴。Colab 預先安裝了一些必要的依賴，因此會顯示 already satisfied 提示。
初始化測試：導入 PyTorch 和 YOLOv5 的工具模組，驗證 Notebook 初始化是否成功。
2. 推理（Inference）
使用 YOLOv5 預訓練模型 yolov5s.pt 進行目標檢測，執行 detect.py 腳本。
檢測結果存儲於 runs/detect/exp 目錄下，可直接顯示或通過 Notebook 輸出進行查看。
3. 驗證（Validation）
下載 COCO128 測試數據集並解壓至指定目錄。
運行 val.py 腳本對模型進行驗證，驗證結果顯示模型在不同指標上的表現（如 mAP）。
4. 訓練（Training）
使用 COCO128 數據集訓練模型，執行 train.py 腳本，並設置以下參數：
批量大小（Batch size）：64
訓練輪數（Epochs）：5
優化器：Adam
訓練結果存儲於 runs/train 目錄，包含模型權重和訓練過程的性能指標。
5. 使用自訓練模型進行推理
將訓練所得的最佳模型權重 best.pt 移至 YOLOv5 主目錄。
運行 detect.py 指定權重為 best.pt，生成新推理結果，並存儲於 runs/detect/exp3 目錄下。
三、結果與分析
預訓練模型在推理階段的檢測效果顯著，能準確識別圖像中的目標。
在僅訓練 5 個 Epoch 的情況下，自訓練模型的檢測精度較低，這是由於訓練次數不足導致模型未能充分學習數據特徵。增加 Epoch 數量或使用更大的數據集將有效提升檢測效果。
四、結論與建議
本次實驗成功實現了 YOLOv5 的主要功能（推理、驗證、訓練）的運行，並驗證了其流程的可操作性。
建議在未來實驗中：
增加訓練數據和 Epoch 次數以提升模型性能。
調整其他參數（如學習率、數據增強策略）以進一步優化模型效果。
