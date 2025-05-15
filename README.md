# EEG Hands-On

このリポジトリでは、公開EEGデータセット（Kara One, ZuCo 2.0, BCI Competition IV, Imagined Speech EEG）を対象に、  
MNE-Python を使った前処理・可視化・機械学習パイプラインのハンズオンを行います。

## 目次

1. 環境構築  
2. データ配置  
3. Jupyterノートブック実行例  
4. ディレクトリ構成  

## 環境構築

```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
# EEG Hands-On

このリポジトリでは、公開EEGデータセット（Kara One, ZuCo 2.0 (TSR), BCI Competition IV, Imagined Speech EEG）を対象に、  
MNE-Python を用いた前処理・可視化・機械学習パイプラインのハンズオンを行います。

## 目次

1. [環境構築](#環境構築)  
2. [データ配置](#データ配置)  
3. [Jupyterノートブック実行例](#jupyterノートブック実行例)  
4. [ディレクトリ構成](#ディレクトリ構成)  

---

## 環境構築

1. リポジトリをクローンまたはダウンロードしてプロジェクトルートに移動  
   ```bash
   git clone <リポジトリURL> eeg-hands-on
   cd eeg-hands-on
   ```
2. Python仮想環境を作成＆有効化  
   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```
3. 必要パッケージをインストール  
   ```bash
   pip install --upgrade pip
   pip install -r requirements.txt
   ```
4. JupyterLab を起動  
   ```bash
   jupyter lab
   ```

---

## データ配置

1. `data/raw/zuco2/` フォルダを作成  
   ```bash
   mkdir -p data/raw/zuco2
   ```
2. OSF から ZuCo 2.0 TSR の MATLAB ファイルをダウンロードし、  
   `data/raw/zuco2/` に配置  
3. 他のデータセット（Kara One, BCI IV, Imagined Speech）も同様に `data/raw/` 配下に保存  
4. ファイル配置を確認  
   ```bash
   ls -lh data/raw/zuco2/
   ```

---

## Jupyterノートブック実行例

1. `notebooks/zuco2_load_demo.ipynb` を開く  
2. 以下のセルを実行してデータ構造と信号を確認  
   ```python
   import h5py
   import numpy as np
   import matplotlib.pyplot as plt

   # ファイルパスを指定
   file_path = "data/raw/zuco2/TSR_01.mat"
   with h5py.File(file_path, "r") as f:
       print("Top-level keys:", list(f.keys()))
       eeg = np.array(f['eeg'])
       print("EEG shape:", eeg.shape)

       # 最初のチャネルをプロット
       plt.plot(eeg[0, :1000])
       plt.title("EEG Channel 1")
       plt.show()
   ```
3. 他のファイルやタスクでも同様に試してみる

---

## ディレクトリ構成

```
eeg-hands-on/
├── data/
│   ├── raw/         # 元データ（.mat, .cnt, .edf など）
│   └── processed/   # 前処理後データ
├── notebooks/       # Jupyter notebooks
│   └── zuco2_load_demo.ipynb
├── scripts/         # 分析用スクリプト
├── venv/            # Python仮想環境（.gitignoreで除外）
├── requirements.txt # 必要パッケージ
├── README.md        # 本ファイル
├── .gitignore       # 除外設定
└── LICENSE          # ライセンス情報
```