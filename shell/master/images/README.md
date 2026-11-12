# シェル画像の置き場所

`shell/master/surfaces.txt` から相対パスで参照している、シェルアートの画像置き場です。

## ディレクトリ構成

```
shell/master/
├─ surfaces.txt            シェル定義（element のパス・当たり判定・アニメーション）
└─ images/
   ├─ motoi/               基（\0）のサーフェス 0〜9
   ├─ nanana/              七々（\1）のサーフェス 10〜18
   └─ animation/           まばたき・口パク用（1000 番以降）
```

## 画像のきまり

- ファイル名は `surfaceNNNN.png`（4桁）。番号はサーフェス番号と一致させる。
- 1 枚のキャンバスサイズは全サーフェスで共通。仮画像は 256×256。
  正式な絵でサイズを変えるときは、`surfaces.txt` の `collision` 座標も描き直す。
- 背景は透明。アルファ付き PNG で書き出す。
- フォルダを動かすときは、`surfaces.txt` の `element` のパスも合わせて直す。

## 表情と番号

| 番号 | キャラクター | 表情 | ファイル |
|---|---|---|---|
| 0 | 基 | 素 | motoi/surface0000.png |
| 1 | 基 | 照れ（喜） | motoi/surface0001.png |
| 2 | 基 | 驚き | motoi/surface0002.png |
| 3 | 基 | 不安（哀） | motoi/surface0003.png |
| 4 | 基 | 眠い | motoi/surface0004.png |
| 5 | 基 | 笑い（喜） | motoi/surface0005.png |
| 6 | 基 | 目閉じ | motoi/surface0006.png |
| 7 | 基 | 怒り（怒） | motoi/surface0007.png |
| 8 | 基 | 喜び（楽） | motoi/surface0008.png |
| 9 | 基 | 悲しみ（哀） | motoi/surface0009.png |
| 10 | 七々 | 素 | nanana/surface0010.png |
| 11 | 七々 | しかめ面（怒） | nanana/surface0011.png |
| 12 | 七々 | 照れ（喜） | nanana/surface0012.png |
| 13 | 七々 | 驚き | nanana/surface0013.png |
| 14 | 七々 | 不安（哀） | nanana/surface0014.png |
| 15 | 七々 | 眠い | nanana/surface0015.png |
| 16 | 七々 | 笑い（喜・楽） | nanana/surface0016.png |
| 17 | 七々 | 目閉じ | nanana/surface0017.png |
| 18 | 七々 | 悲しみ（哀） | nanana/surface0018.png |

## 差し替え手順

1. 同じファイル名・同じキャンバスサイズで上書きする（フォルダ構成は変えない）。
2. 絵に合わせて `surfaces.txt` の `collision`（基は Face / Head / Body、七々は Head）を直す。
3. Windows の SSP で起動し、`\s[0]`〜`\s[18]` の表示と当たり判定を確かめる。

## アニメーション（まばたき・口パク）

- `animation/` に次の画像を置く。
  - `surface1000.png` / `surface1001.png`: まばたきのコマ
  - `surface1010.png`: 口パクのコマ
- 置いたあと、`surfaces.txt` の `surface1000`〜`surface1010` の定義と、
  `animation0` / `animation1` ブロックのコメントを外す。
- 1000 番以降はアニメーション専用。通常の表情には使わない。
