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
- 1 枚のキャンバスサイズは全サーフェスで共通で、400×600 の縦長（立ち絵）。
  サイズを変えるときは、`surfaces.txt` の `collision` 座標も描き直す。
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

まばたきと口パクは、表情サーフェスの上に重ねる専用画像（1000 番台）で動かします。
どれも 400×600 の透明なキャンバスに、変わる部分だけを描いています。

| 番号 | キャラクター | 用途 | ファイル |
|---|---|---|---|
| 1000 | 基 | まばたき（半目） | animation/surface1000.png |
| 1001 | 基 | まばたき（閉じ目） | animation/surface1001.png |
| 1002 | 七々 | まばたき（半目） | animation/surface1002.png |
| 1003 | 七々 | まばたき（閉じ目） | animation/surface1003.png |
| 1010 | 基 | 口パク（口を開ける） | animation/surface1010.png |
| 1011 | 七々 | 口パク（口を開ける） | animation/surface1011.png |

- 定義は `surfaces.txt` の `surface1000`〜`surface1011` と、末尾の `animation0`
  （まばたき）・`animation1`（口パク）ブロック。まばたきは目を開けている表情にだけ付けて
  いて、すでに閉じている 5・6（基）と 16・17（七々）には付けていない。
- 表情を描き直して目や口の位置が変わったら、この 6 枚も同じ位置に描き直す。
- 1000 番以降はアニメーション専用。通常の表情には使わない（`\s[1000]` などで直接呼ばない）。
