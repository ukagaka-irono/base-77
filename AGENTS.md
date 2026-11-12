# AGENTS.md

伺か（ukagaka）のゴースト「base 77」のフォルダです。SHIORI は YAYA。

- **作業を始める前に、ルートの `GHOST.md` を読むこと。** ゴーストの名前、キャラクターと
  使えるサーフェス、ライセンス、辞書の構成、トークの書き方の決まりはそちらにある。
- 辞書の本体は `ghost/master/dic/normal/*.dic`。UTF-8（BOM なし）、改行 LF。
- 文字コードや改行を変えると YAYA が辞書を読めなくなる。エディタの設定を変えないこと。
- `ghost/master/dic/system/` と `ghost/master/yaya.dll` は外部の配布物。編集しない。
- 動作確認は Windows の SSP で行う。この環境では動かせないので、辞書を変えたら
  「SSP で確かめる」ことを作者に伝える。
- シェル（`shell/master/`）は仮。画像を差し替えるときは `surfaces.txt` の当たり判定も
  合わせる。
- 原作者のクレジット（紺野ややめ）と、`readme-yaya.txt` は消さない。
