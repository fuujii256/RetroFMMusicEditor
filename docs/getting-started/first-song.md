# はじめての曲

RetroFM-Music Editor で、音を 1 つ鳴らすところから、FM・リズム・複数音源の同時再生まで進めてみましょう。
各コマンドの詳しい書式は [コマンドリファレンス](../reference/index.md) を参照してください。

## 準備

1. 好きなフォルダに、新しい `.mml` ファイルを作ります (ファイルペインの「＋」ボタンが便利です)。
2. エディタに、下の MML を貼り付けます。
3. ファイルを保存 (`Ctrl + S`) して、Resources で開いているファイル名をダブルクリックすると再生されます。

途中から聴くには、MML Editor 内の音符や休符をダブルクリックします。未保存の編集内容も、その位置から再生できます。

## 1. 音を鳴らす

```text
; chip=opna
; tempo=75

CH3: @0 v13 o4 L8 c d e f g a b o> c
```

- `;` で始まる行はコメントです。ただし `; chip=opna` のように、曲全体の設定として読まれるものもあります ([曲ヘッダディレクティブ](../reference/headers.md))。
- `CH3:` は FM 音源の 1 番目のチャンネルです。その行の内容がこのチャンネルの演奏になります。
- `@0` は音色、`v13` は音量 (0〜15)、`o4` はオクターブです。
- `L8` は「これから書く音符は 8 分音符」という意味です。`c d e f g a b` はドレミファソラシ、`o>` はオクターブを 1 つ上げます。

!!! warning "音符の後ろに音長は書けません"
    `c4` や `d8.` のような書き方はできません。音長は、前に書いた `L` が効きます。詳しくは [音符・休符・オクターブ・音長](../reference/commands/notes.md) を参照してください。

## 2. 音色・ループ・リズムを足す

次の曲は、FM 2 パートにドラム (バスドラム + スネア・ハイハット) を足したものです。

```text
; chip=opna
; tempo=75
; opna_patch_01: 4 5 | 31 5 0 7 4 22 0 1 3 | 31 5 0 7 4 30 0 1 0 | 31 5 0 7 4 18 0 2 3 | 31 8 3 7 4 0 0 1 0

; role=FM_0
CH3: @1 v13 o4 L4 [LOOP 2] c e g e [LEND] L2 c

; role=FM_1
CH4: @1 v11 o3 L2 [LOOP 2] c g [LEND] c

; role=RHYTHM_BD
CH9: v15 L4 [RV b15] [LOOP 2] [RK b] o2 c r [RK b] o2 c r [LEND] [RK b] o2 c L4 r

; role=RHYTHM_SD
CH10: v15 L4 [RV s14 h12] [LOOP 2] r [RK s] o4 c r [RK sh] o4 c [LEND] L2 r
```

- `; opna_patch_01: ...` で、OPNA の 4 オペレータ音色を自分で定義しています。`@1` で呼び出します ([音量・音色・パン](../reference/commands/voice.md))。
- `; role=FM_0` のように書くと、直後の `CH` 行の役割を指定できます ([音源とチャンネル](../reference/chips.md))。
- `[LOOP 2] ... [LEND]` は、間の部分を 2 回繰り返します ([ループ・テンポ](../reference/commands/flow.md))。
- リズムは、`[RK b]` (どの楽器を鳴らすか) で楽器を選んでから、**音符を置いて** 鳴らします。休符では鳴りません ([リズム](../reference/commands/rhythm.md))。
- 4 つのパートは、すべて同じ長さ (480 tick) で終わるようにそろえています。パートごとの長さがずれると、ループや終了のタイミングがずれます。

## 3. 複数の音源を同時に使う

`; chip=all` を書くと、OPM・OPLL・OPNA を 1 つの曲で同時に使えます。`; role=` と `hw=` で、チャンネルごとに音源を選びます。

```text
; chip=all
; opll_default_vol=100
; opna_default_vol=80
; opm_default_vol=100

; opm_patch_01: 4 5 | 31 5 0 7 4 22 0 1 0 0 0 | 31 5 0 7 4 30 0 1 0 0 0 | 31 5 0 7 4 18 0 2 0 0 0 | 31 8 3 7 4 0 0 1 0 0 0

; role=OPM_0 hw=OPM
CH3: @1 p3 v13 o5 L8 [LOOP 0] c e g o> c o< g e [LEND]

; role=FM_0 hw=OPLL
CH4: @1 v12 o3 L4 [LOOP 0] c g a f [LEND]
```

プレイヤーペインでは、OPM のチャンネルが緑、OPLL のチャンネルが橙で表示されます。`[LOOP 0]` は無限ループです。

## 次のステップ

- [コマンドリファレンス](../reference/index.md) で、使えるコマンドの全体を見る
- [曲ヘッダディレクティブ](../reference/headers.md) で、曲ごとの音量や互換オプションを調べる
- [間違えやすい書き方](../reference/pitfalls.md) で、うまく鳴らないときの原因を調べる
