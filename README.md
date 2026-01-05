# Gamepad Frame Logger

A single-file HTML tool to **record and analyze gamepad input timing**  
with **frame-based (FPS) and polling-rate–based interpretation**.

---

## 🇯🇵 日本語

### 概要

**Gamepad Frame Logger** は、  
ゲームパッドの入力（ボタンの押下／解放）を **高精度な実時間（ms）で記録**し、  
それを **任意の FPS（60 / 120 / 144 / 180 / 240）** および  
**ポーリングレート（125 / 250 / 500 / 1000Hz）** の仮定で解析できる  
**単一HTMLファイル構成の入力解析ツール**です。

- ブラウザのみで動作（インストール不要）
- 入力ログは **performance.now() ベース**
- FPS・ポーリングレート・ボタン表記を **後から切り替えて再解析**
- 格闘ゲーム、アクションゲーム、入力検証、マクロ比較などに対応

---

### 主な機能

- 🎮 **Gamepad API** による入力取得
- ⏱ **押下時間 / 押下間隔** の計測  
  - ms（実時間）
  - Frames（FPS基準）
  - Samples（ポーリングレート基準）
- 🔁 FPS 切り替え対応  
  - 60 / 120 / 144 / 180 / 240
- 📡 ポーリングレート切り替え対応（仮定値）  
  - 125 / 250 / 500 / 1000 Hz
- 🏷 **ボタン表記切り替え**
  - Xbox
  - PlayStation
  - Nintendo
- 📊 タイムライン表示（直近イベント）
- 📤 CSV エクスポート
  - Raw ログ（ms 基準）
  - 解析結果（FPS / Polling 反映）

---

### 使い方

1. このリポジトリの `gamepad_logger.html` をダウンロード
2. Chrome / Edge で開く
3. ゲームパッドを接続
4. ページ上で **START** を押す
5. 入力を行う
6. FPS / ポーリングレート / ボタン表記を切り替えて解析

※ Gamepad API の仕様上、最初にボタンを一度押すと認識されやすくなります。

---

### 設計方針（重要）

- **ログの唯一の真実は「ms（実時間）」**
- FPS やポーリングレートは  
  👉 *後処理での「解釈パラメータ」*
- ログを取り直す必要はありません

この設計により、  
同じ入力を異なる FPS / 環境条件で公平に比較できます。

---

### 想定用途

- 格闘ゲームの入力検証（フレーム精度）
- 高速連打・最速入力の研究
- マクロ入力と人力入力の比較
- コントローラー環境差の可視化
- 入力遅延・安定性の解析補助

---

### 制限事項

- ブラウザでは **実際のポーリングレートを直接取得できません**
- ポーリングレートは「仮定値」として解析に使用します
- OS / ブラウザ / ドライバの影響により ±誤差が生じる場合があります

---

### ライセンス

MIT License

---

## 🇺🇸 English

### Overview

**Gamepad Frame Logger** is a **single-file HTML tool** that records gamepad input  
(button press / release) with **high-precision real time (milliseconds)** and allows  
post-analysis using **configurable FPS and polling rate assumptions**.

- Runs directly in a web browser
- No installation required
- Logs are stored in milliseconds (source of truth)
- FPS, polling rate, and button labels can be changed **after recording**
- Suitable for fighting games, action games, and input research

---

### Features

- 🎮 Gamepad input via **Web Gamepad API**
- ⏱ Measure **press duration** and **input intervals**
  - Real time (ms)
  - Frames (FPS-based)
  - Samples (polling-rate–based)
- 🔁 Selectable FPS
  - 60 / 120 / 144 / 180 / 240
- 📡 Selectable polling rate (assumed)
  - 125 / 250 / 500 / 1000 Hz
- 🏷 Button label profiles
  - Xbox
  - PlayStation
  - Nintendo
- 📊 Timeline view of recent input events
- 📤 CSV export
  - Raw logs (ms-based)
  - Analyzed results (FPS / polling applied)

---

### How to Use

1. Download `gamepad_logger.html` from this repository
2. Open it with Chrome or Edge
3. Connect a gamepad
4. Press **START**
5. Perform inputs
6. Change FPS / polling rate / button labels to re-analyze

> Due to Gamepad API behavior, pressing any button once after loading helps detection.

---

### Design Philosophy

- **Milliseconds are the single source of truth**
- FPS and polling rate are **interpretation parameters**
- No need to re-record logs when changing analysis settings

This allows fair comparison of the same input under different timing assumptions.

---

### Intended Use Cases

- Fighting game input analysis
- Fast tapping / optimal input research
- Human vs macro input comparison
- Controller environment comparison
- Input timing and stability studies

---

### Limitations

- Actual hardware polling rate cannot be directly read in browsers
- Polling rate is an assumed value for analysis
- Timing accuracy depends on OS, browser, and driver behavior

---

### License

MIT License
