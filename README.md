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