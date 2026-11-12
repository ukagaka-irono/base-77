# GHOST.md

「base 77」に固有の情報です。AI エージェントは、作業の前に読みます。

## このゴーストについて

- 伺か（ukagaka）のゴースト「base 77：基と七々」。`name` は `base 77：基と七々`、
  バージョンは `0.1.0`、インストール先は `base77`。
- SHIORI は **YAYA**（`ghost/master/yaya.dll`）。
- 「紺野ややめ」（https://github.com/YAYA-shiori/konnoyayame ）のテンプレートを土台にしている。
  辞書の構成とイベントの受け持ちはテンプレートのまま。
- キャラクター名は決定済み。`\0`（`\h`）が **基（もとい）**、`\1`（`\u`）が **七々（なな）**。
  ゴースト名は「base 77：基と七々」（ふたり合わせた名前）。呼びかけも「基」「七々」を使う。
- **口調とシェルの絵はまだ仮**。決まったら `ghost/master/descript.txt`、辞書の台詞、`shell/` を
  まとめて直す。

## ライセンス

- このゴーストの内容（辞書、仮シェル）: Public Domain（Unlicense）。
- `ghost/master/yaya.dll`: YAYA（`readme-yaya.txt`）。
- `ghost/master/dic/system/`: yaya-dic（同梱の `LICENSE`）。**編集しない**。
- 元テンプレートのシェル画像（SATO M 氏、CC BY-NC-ND）は**使っていない**。
  シェルを作るときは、権利のある絵を用意すること。

## キャラクターとサーフェス

| スコープ | キャラクター | 人物像 | 使えるサーフェス |
|---|---|---|---|
| `\0`（`\h`） | 基（もとい） | 一人称「ぼく」。落ち着いていて、好奇心がある。まだ決まっていないことを、決まっていないと言える | 0 素 / 1 照れ（喜） / 2 驚き / 3 不安（哀） / 4 眠い / 5 笑い（喜） / 6 目閉じ / 7 怒り（怒） / 8 喜び（楽） / 9 悲しみ（哀） |
| `\1`（`\u`） | 七々（なな） | 一人称「わたし」。短くて、少し辛口。基の相方 | 10 素 / 11 しかめ面（怒） / 12 照れ（喜） / 13 驚き / 14 不安（哀） / 15 眠い / 16 笑い（喜・楽） / 17 目閉じ / 18 悲しみ（哀） |

- 当たり判定（`shell/master/surfaces.txt` の `collision`）は、基が `Face`、`Head`、`Body`。
  七々は `Head` のみ。
- 画像は `shell/master/images/` にキャラクター別で置く。基は `images/motoi/surface0000〜0009.png`、
  七々は `images/nanana/surface0010〜0018.png`。ファイル名の番号はサーフェス番号と対応する。
  `\s[-1]` は表示しない（消す）指定。アニメ用は `images/animation/`（1000 番以降）。
- **シェルは仮**。`shell/master/images/` の画像を差し替えるときは、同じファイル名・同じ
  キャンバスサイズで上書きし、`surfaces.txt` の当たり判定も新しい絵に合わせる。
  ファイル名は `surface0000.png` の形を崩さない。詳しくは `shell/master/images/README.md`。
- `surfaces.txt` は、各サーフェスに `element0,base,images/...` で画像を明示し、共通の当たり判定を
  `surface.append0-9`（基）/ `surface.append10-18`（七々）にまとめている。仮画像は 256×256。
- 感情に合わせて `\s[...]` を選ぶ。番号の意味は次のとおり。
  - 基: 0 素 / 1 照れ / 2 驚き / 3 不安（哀） / 4 眠い / 5 笑い / 6 目閉じ / 7 怒り（怒） /
    8 喜び（楽） / 9 悲しみ（哀）
  - 七々: 10 素 / 11 しかめ面（怒） / 12 照れ / 13 驚き / 14 不安（哀） / 15 眠い /
    16 笑い（楽） / 17 目閉じ / 18 悲しみ（哀）
- ランダムトークは、結びの台詞の感情に合う表情番号で終える（表情はトーク終了後も残るため）。
  平坦な結びや眠気など、既存の番号が合う場合は無理に変えない。
- まばたき・口パクのアニメーション定義はコメントで置いてある。**1000 番以降はアニメーション用**に
  空けてあるので、`images/animation/` に専用画像を用意してからコメントを外す。

## 辞書の構成

- `ghost/master/yaya.txt` が `dic/normal` を読む。辞書エラーのときは `yaya_emerg.txt` が
  `dic/emerg` を読む（緊急モード）。
- `ghost/master/dic/system/` はシステム辞書（yaya-dic）。編集しない。
- `yaya_tmpl_util.dic` の `AYATEMPLATE.*` が、メニューやマウス反応の関数を名前で呼び出す。
- ネットワーク更新はしていない（`On_homeurl` は置いていない）。配布するなら
  `dic/normal/` と `dic/emerg/` に `yaya_homeurl.dic` を足す。

## イベントと辞書ファイルの対応

| ファイル（`ghost/master/dic/normal/`） | 主な中身 |
|---|---|
| `yaya_talk.dic` | ランダムトーク（`RandomTalk` / `RandomTalkEx`）。台詞を足すときはここ |
| `yaya_aitalk.dic` | キー入力 `OnKeyPress`、時報 `OnMinuteChange`、見切れ `OnSecondChange` |
| `yaya_bootend.dic` | 初回起動 `OnFirstBoot`、起動 `OnBoot`、終了 `OnClose`、時間帯の判定 `GetTimeSlot`、最小化からの復帰 |
| `yaya_mouse.dic` | なで・つつきへの反応。関数名は「種別＋スコープ番号＋当たり判定名」（例: `MouseMove0Head`、`MouseDoubleClick1`） |
| `yaya_menu.dic` | メニュー `OpenMenu` と、選択肢ごとの処理 `Menu_*` |
| `yaya_communicate.dic` | ユーザーとの会話、他のゴーストとの会話（`TalkTo*` / `ReplyTo*`） |
| `yaya_change.dic` | ゴーストの切り替え・呼び出しのときのトーク |
| `yaya_etc.dic` | シェル変更、インストール、消滅、ネットワーク更新、ヘッドライン、時計合わせなど |
| `yaya_string.dic` | ユーザー名の初期値、メニュー項目の文字列（`On_*`） |
| `yaya_word.dic` | トーク中に `%(ms)` のように埋め込む単語 |
| `yaya_tmpl_util.dic` | テンプレートの共通処理。必要なとき以外は触らない |

新しいイベントに反応させる関数は、内容の近い辞書ファイルに書く。`dic/normal/` に新しい
`.dic` ファイルを置くと、自動で読み込まれる。

## トークの書き方

- 話し始める側のスコープと表情を最初に指定する（`\0\s[5]...`）。
- 話し手を交代する前に `\w8` を入れる。同じ話し手の中の間は `\w5`〜`\w9`。
- 同じ話し手の中で改行するときは `\w9\n`。
- すでに話したスコープに戻って話すときは、`\n\n` で空行を入れてから続ける。
- ユーザーは `%(username)` で呼ぶ。
- 口調を混ぜない。基は「ぼく」で落ち着いた話し方、七々は「わたし」で短い話し方。
- キャラクターを指すときは「基」「七々」。`base 77` はゴースト名なので、そのまま残す。
- 季節・時間帯で出し分けるときは、`yaya_talk.dic` の `RandomTalkEx` の中で `if` を書く。
  YAYA は `if` の中身を出力候補にばらすので、条件が真のときだけ抽選に加わる。
  季節は `GetSeason`（月で判定）、時間帯は `GetTimeSlot`（`yaya_bootend.dic`）を使う。

例:

```
'\0\s[1]%(username)、きょうは何してたの？\w8\1\s[10]聞くなよ。\w8\0\n\n聞きたいんだもん。\e'
```

## 確認のしかた

- 実行できるのは Windows の SSP（と YAYA）。Linux やブラウザでは動かない。
- 辞書を直したら、SSP でゴーストを読み込み直す。エラーが出るときは `ghost/master/` に
  `ayame.log` を出す設定（`system_config.txt` の `log`）が使える。
- 括弧（`{` `}`）の対応、`\e` の付け忘れ、`surfaces.txt` にないサーフェス番号の使用に注意する。
