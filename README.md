# base 77

伺か（ukagaka）のゴースト「base 77」です。SHIORI は YAYA。

「紺野ややめ」（https://github.com/YAYA-shiori/konnoyayame 、Public Domain / Unlicense）の
テンプレートを土台に、ゴースト名・キャラクター・辞書を差し替えたものです。
シェルはまだ仮の絵で、見た目はこれから考えます。

## インストール

1. このフォルダを丸ごと `base77` という名前で、SSP の `ghost` フォルダ（既定では
   `%APPDATA%\SSP\ghost`）にコピーします。
   フォルダの中に `install.txt`、`ghost/`、`shell/` が並ぶ形にしてください。
2. SSP を起動し、ゴーストの一覧から「base 77」を選びます。
3. バルーンは SSP 付属のものをそのまま使えます（このゴーストには同梱していません）。

`install.txt` の `directory` は `base77` です。nar にして入れる場合も同じ場所に入ります。

## 中身

- `ghost/master/` … ゴースト本体。`descript.txt`、YAYA（`yaya.dll`）、辞書（`dic/normal/`）。
- `shell/master/` … シェル。画像は `shell/master/images/`（`motoi/`・`nanana/`・`animation/`）に置く。
  いまは仮のサーフェスだけ。配置のルールは `shell/master/images/README.md`。
- `GHOST.md` … キャラクター、サーフェス、辞書の構成、トークの書き方。
- `AGENTS.md` … AI エージェント向けの案内。

## 辞書を直す

トークは `ghost/master/dic/normal/*.dic` にあります（UTF-8、BOM なし）。

辞書にエラーがあると、ゴーストは緊急モードで起動してほとんど話さなくなります。
`dic/emerg/` に最低限の辞書を置いてあるので、そのときは「辞書でエラーが出てるみたい」と
言います。直したら SSP でゴーストを読み込み直してください。

## ライセンス

- 辞書・シェルなどこのゴーストの内容: Public Domain（Unlicense、`LICENSE`）。
- `ghost/master/yaya.dll`: YAYA（`readme-yaya.txt` を参照）。
- `ghost/master/dic/system/`: yaya-dic（`ghost/master/dic/system/LICENSE` を参照）。
- 元のテンプレート「紺野ややめ」のシェル画像は使っていません（CC BY-NC-ND のため）。
