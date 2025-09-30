# Otomo-e Web Interface おとも絵

**Otomo-eフォトフレーム用WebBluetoothアプリケーション**

このリポジトリは、Otomo-eフォトフレームデバイスと通信するためのWebアプリケーションです。WebBluetooth APIを使用してスマートフォンやPCから直接写真を送信できます。

## 関連リポジトリ

- **メインファームウェア**: [otomo-e](https://github.com/manomono-23/e-otomo) - nRF52840用ファームウェア
- **Webアプリケーション**: [otomo-e-web](https://github.com/manomono-23/e-otomo-web) (このリポジトリ)

## ライブデモ

🌐 [art-frame.manomono.net](http://e-otomo.manomono.net/)

## 特徴

- **WebBluetooth対応**: スマートフォンブラウザから直接操作
- **自動プラットフォーム検出**: iOS/Android/PCに最適化
- **複数の描画モード**: Floyd-Steinberg、Atkinson、Ordered、Thresholdディザリング
- **自動圧縮**: RLE圧縮でデータ転送を最適化
- **iOS対応**: Bluefyアプリでの使用をサポート
- **レスポンシブデザイン**: モバイル・デスクトップ両対応

## 技術仕様

### 対応ブラウザ

- **Android**: Chrome, Edge, Opera
- **PC**: Chrome, Edge, Opera (Windows/Mac/Linux)
- **iOS**: Bluefy Web Browser（専用アプリ必要）

### WebBluetooth要件

- HTTPS接続が必須（localhost除く）
- Bluetooth Low Energy対応デバイス
- WebBluetooth API対応ブラウザ

## セットアップ

### 開発環境

```bash
# リポジトリをクローン
git clone https://github.com/manomono-23/otomo-e-web.git
cd otomo-e-web

# HTTPSサーバーで起動（WebBluetoothにはHTTPS必須）
# Python 3の場合
python -m http.server 8000 --bind 127.0.0.1

# Node.jsの場合
npx http-server -S -C cert.pem -K key.pem
```

### 本番環境

```bash
# Webサーバーにindex.htmlをデプロイ
# HTTPS必須（Let's Encryptなど）
```

## 使い方

### 基本操作

1. **デバイス準備**: Otomo-eデバイスの電源を入れ、ボタン長押しでQRコード表示
2. **Webアプリアクセス**: QRコードをスキャンまたは直接URLアクセス
3. **写真選択**: 送信したい写真を選択
4. **デバイス接続**: 「デバイスに接続」ボタンをクリック
5. **送信**: 写真が自動的にe-paperディスプレイに送信される

### iOSでの使用

1. App Storeから「Bluefy Web Browser」をダウンロード
2. Bluefyアプリで[art-frame.manomono.net](http://art-frame.manomono.net/)にアクセス
3. 通常のブラウザと同様に操作

## 機能詳細

### 画像処理

- **対応形式**: JPEG, PNG, GIF, WebP
- **自動リサイズ**: 200×200ピクセルに最適化
- **ディザリング**: 4種類のアルゴリズムから選択可能
- **カラーモード**: 2色/3色/4色モード

### データ転送

- **圧縮**: 自動RLE圧縮でデータサイズを最適化
- **進捗表示**: リアルタイム転送進捗バー
- **エラーハンドリング**: 接続エラー時の自動再試行

## 開発

### ファイル構成

```
web/
├── index.html          # メインアプリケーション
├── README.md          # このファイル
└── LICENSE           # MITライセンス
```

### 主要機能

- **WebBluetooth管理**: デバイス検出・接続・通信
- **画像処理**: Canvas APIでのディザリング処理
- **圧縮アルゴリズム**: RLE圧縮実装
- **UI/UX**: レスポンシブデザイン、プログレス表示

## ハードウェア要件

Otomo-eデバイスが必要です。詳細は[メインリポジトリ](https://github.com/manomono-23/otomo-e)を参照してください。

### 必要な部品

- Seeed Studio XIAO nRF52840
- Waveshare 1.54inch e-Paper Module (3色)
- CR2032電池 + 電池ホルダー
- プッシュボタン、プルダウン抵抗

## トラブルシューティング

### 接続できない場合

1. **HTTPS確認**: WebBluetoothはHTTPS必須
2. **ブラウザ対応**: Chrome/Edge/Operaを使用
3. **Bluetooth有効**: デバイスのBluetoothがONか確認
4. **デバイス状態**: Otomo-eが接続待機中か確認

### iOSで動作しない場合

1. **Bluefyアプリ**: 通常のSafariではなくBluefyアプリを使用
2. **アプリ更新**: Bluefyアプリが最新版か確認

## 貢献

プルリクエストや Issue の投稿を歓迎します！

### 開発方針

1. WebBluetooth標準準拠
2. クロスプラットフォーム対応
3. パフォーマンス最適化
4. ユーザビリティ重視

## ライセンス

このプロジェクトは MIT License の下でライセンスされています。

## 作者

- **manomono** - [GitHub](https://github.com/manomono-23)

## 謝辞

- WebBluetooth Community
- Canvas API Documentation
- Bluefy Web Browser

---

**Otomo-e Web Interface - いつでも、どこでも、あなたの写真を美しく。**