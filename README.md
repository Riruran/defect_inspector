🔸 モデルやテスト画像、実行ファイルなど、容量が大きいためGitHubには直接載せていません。  
必要なファイルは以下のギガファイル便にまとめてあります：

  [ギガファイル便でダウンロード](https://xgf.nu/BM5Rb）

※ 本プロジェクトに含まれるREADMEにも同様の内容を記載しています（オフラインでの利用時などにご活用ください）。


🧠 欠陥検出AI × ONNX × C++/Python
このプロジェクトは、画像から製品の欠陥を検出する機械学習モデルを活用し、
PyTorch × ONNX × C++/Python による高速かつ柔軟な推論環境を構築したものです。
GUIアプリからの操作や、C++での軽量推論まで、実運用を意識した設計になっています。

🖼 アプリ概要
画像分類モデルを学習し、欠陥の有無を判定

モデルは PyTorch で学習し、ONNX に変換して再利用

Python GUI（Tkinter）で簡単に推論実行

C++ + ONNX Runtime による高速な実行環境も用意

モデルファイル（.pth, .onnx）やサンプル画像を同梱

📌 主な機能

機能	内容
✅ 学習スクリプト	train.py により PyTorch で画像分類モデルを学習
✅ モデル変換	convert_to_onnx.py により ONNX 形式に変換可能
✅ Python推論	GUIアプリ（app.py）でONNXモデルを読み込み推論を実施
✅ C++推論	main.cpp をビルドして高速推論（ONNX Runtime使用）
✅ テスト画像同梱	data/test にある画像で簡単に動作確認が可能
🛠 技術スタック

技術	役割
Python / PyTorch	モデル学習、推論アプリ（app.py）
ONNX	モデル共有・C++と連携
ONNX Runtime	ONNXモデルの実行エンジン（Python/C++）
C++ / CMake	高速なエッジ推論環境の構築
OpenCV	画像処理
VSCode	開発環境


🚀 実行手順

# 仮想環境の作成
python -m venv venv

# 仮想環境の有効化
# Windows:
venv\Scripts\activate

# macOS/Linux:
source venv/bin/activate

# モデルのONNX変換
python convert_to_onnx.py

# C++での高速推論
cd onnx_infer_cpp
cmake -S . -B build
cmake --build build
cd build\Debug
.\onnx_infer_cpp.exe

# テスト方法（制度確認）
学習用画像は data\train\ にクラスごとに分類して保存されています
onnx_infer_cpp\image の中にテスト画像を配置してください（test.jpg ← この名前で画像を保存）

上記の onnx_infer_cpp.exe を実行することで、画像が欠陥品かどうかが分類表示されます
