# 電光 — Marquee

> 背景の明滅する文字が、電光メッセージを象る PWA。

iPhone・Android・Mac のホーム画面 (またはデスクトップ) に追加して、フルスクリーンの電光掲示板として使えます。

**Live demo** → <https://tama831.github.io/denko-marquee/>

## 特徴

- **Glyph Rain モード**: 背景にカタカナや漢字が明滅して降る中に、メッセージが電光となって浮き上がる
- **クラシックモード**: 横にスクロールする昔ながらの電光看板
- **8 色のパレット** (電光青 / 白氷 / シアン / 藍夜 / 紫電 / 珊瑚 / 琥珀 / 若葉)
- **背景文字種を 4 種から選択** (カタカナ+数字 / 英数字+記号 / バイナリ / 漢字)
- **速度・サイズ・グロー強度・明滅速度** を細かく調整
- 設定は端末の localStorage に保存され、次回起動時に復元
- **オフライン動作** (Service Worker でキャッシュ済)
- 完全にローカル動作、外部通信なし (Google Fonts のロード以外)

## 使い方

### iPhone (Safari)

1. <https://tama831.github.io/denko-marquee/> を Safari で開く
2. 共有ボタン → **ホーム画面に追加**
3. ホーム画面の「電光」アイコンから起動 → 全画面表示

### Android (Chrome / Edge)

1. <https://tama831.github.io/denko-marquee/> を Chrome で開く
2. メニュー → **ホーム画面に追加** / **アプリをインストール**
3. ホーム画面の「電光」アイコンから起動

### Mac / PC (Chrome / Edge)

1. <https://tama831.github.io/denko-marquee/> を開く
2. アドレスバー右端のインストールアイコン → **インストール**
3. アプリとして単独ウィンドウで開く

## 設定

画面のどこかをタップ (またはクリック) すると設定パネルが開きます。

| 項目 | 説明 |
|---|---|
| メッセージ | 流したい文字 (最大 200 字、絵文字は反映されません) |
| モード | Glyph Rain / クラシック |
| 速度 | 左右スクロールの速さ |
| 大きさ | 背景文字セルの粗さ (= メッセージのドット解像度) |
| 方向 | 左 / 右 / 静止 |
| 電光カラー | 8 色のパレット |
| グロー強度 | 控えめ / 標準 / 眩しい |
| 背景の文字種 | 4 種 (Glyph Rain 時) |
| 明滅の速さ | 静か 〜 激しい (Glyph Rain 時) |

## 技術メモ

- 純粋な HTML / CSS / Vanilla JS、ビルド不要
- `<canvas>` で背景セルとメッセージマスクを合成 (`destination-out` で
  メッセージ範囲を打ち抜いてから前景白文字を乗せ、明暗コントラストを最大化)
- 30fps スロットル + Retina dpr 上限 1.5 + 部分セル更新 で iPhone でも
  熱を持たない設計
- Service Worker は cache-first ではなく **network-first** (オンライン時は
  最新版を取りに行き、オフライン時のみキャッシュ fallback)

## ライセンス

[MIT License](LICENSE) — Copyright (c) 2026 Tama831

## 謝辞

- フォント: [DotGothic16](https://fonts.google.com/specimen/DotGothic16),
  [Press Start 2P](https://fonts.google.com/specimen/Press+Start+2P),
  [VT323](https://fonts.google.com/specimen/VT323) (Google Fonts)
- 開発支援: [Claude Code](https://claude.com/claude-code) (Anthropic)
