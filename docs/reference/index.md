# コマンドリファレンス

RetroFM-Music Editor 0.13.10 の MML コマンドの一覧です。書き方の基本は [MML ファイルの基本構文](syntax.md)、音源の使い分けは [音源とチャンネル](chips.md) を参照してください。

このリファレンスは、標準の **RetroFMEditor独自方言** を説明しています。MXDRV (X68000) 方言と `#dual` 方言は [MXDRV 方言と #dual](mxdrv.md) を参照してください。

## 早見表

### 音符・音長

| コマンド | 意味 | 詳細 |
|---|---|---|
| `c d e f g a b` | 音符 (`+` / `#` で半音上げ、`~N` でデチューンの variant) | [音符・休符・オクターブ・音長](commands/notes.md) |
| `r` | 休符 | 同上 |
| `o<N>` `o>` `o<` | オクターブ | 同上 |
| `L<分母>` `L<分母>.` | 音長 (全音符 = 192 tick。大文字の `L`) | 同上 |
| `l(<n>)` | 音長 (tick で指定) | 同上 |
| `[F2]`〜`[F9]` | FM のゲートファクタ | 同上 |
| `[TRANS n]` | 移調 | 同上 |

### 音量・音色

| コマンド | 意味 | 詳細 |
|---|---|---|
| `v<N>` `v+` `v-` | 音量 (0〜15) | [音量・音色・パン](commands/voice.md) |
| `@<N>` | 音色 | 同上 |
| `p<N>` | パン (0〜3。OPM で有効) | 同上 |
| `; opna_patch_NN: ...` | OPNA の音色の定義 | 同上 |
| `; opm_patch_NN: ...` | OPM の音色の定義 | 同上 |
| `; custom_patch_NN: ...` | OPLL のユーザー音色の定義 | 同上 |

### 表現

| コマンド | 意味 | 詳細 |
|---|---|---|
| `E0`〜`E15` | エンベロープ | [表現](commands/expression.md) |
| `M0`〜`M15` | ビブラート・ピッチスライド | 同上 |
| `D<N>` `[MXD n]` | デチューン | 同上 |
| `[FE 00]`〜`[FE 0A]` | ピッチ・音量エフェクト | 同上 |
| `&` `[SLUROFF]` | スラー・タイ | 同上 |
| `[PORT n]` | ポルタメント | 同上 |

### ループ・テンポ

| コマンド | 意味 | 詳細 |
|---|---|---|
| `[LOOP n]` `[LEND]` | ループ (`n = 0` は無限) | [ループ・テンポ](commands/flow.md) |
| `[LB]` | ループからの脱出 | 同上 |
| `[TB n]` `[BPM n]` | 曲の途中のテンポ変更 | 同上 |
| `; tempo=<N>` | 曲全体のテンポ | 同上 |

### リズム・PSG・PCM

| コマンド | 意味 | 詳細 |
|---|---|---|
| `[RK <文字>]` | リズムの楽器を選ぶ (音符で鳴らす) | [リズム](commands/rhythm.md) |
| `[RV <楽器><0-15>]` | リズムの楽器ごとの音量 | 同上 |
| `[EV n]` `[EV -]` | PSG のエンベロープの割り当て | [PSG](commands/psg.md) |
| `[FC xx]` | PSG のノイズ | 同上 |
| `CHP1:`〜`CHP8:` | PCM のチャンネル | [PCM](commands/pcm.md) |
| `n<番号>` `F0`〜`F4` `@v<N>` | PCM のサンプル・レート・音量 | 同上 |
| `#pcmfile "..."` | PDX の宣言 | 同上 |

### 曲全体の設定

| 書き方 | 意味 | 詳細 |
|---|---|---|
| `; chip=dual\|opna\|opm\|all` | 音源の構成 | [音源とチャンネル](chips.md) |
| `; role=<名前> hw=<音源>` | チャンネルの役割と音源 | 同上 |
| `; *_default_vol=<%>` | 音源ごとの音量 | [曲ヘッダディレクティブ](headers.md) |
| `; song_loop=forever` | 曲全体を無限ループ | 同上 |

## ページ一覧

- [MML ファイルの基本構文](syntax.md)
- [音源とチャンネル](chips.md)
- [音符・休符・オクターブ・音長](commands/notes.md)
- [音量・音色・パン](commands/voice.md)
- [表現 (エンベロープ・ビブラート・スラー ほか)](commands/expression.md)
- [ループ・テンポ](commands/flow.md)
- [リズム](commands/rhythm.md)
- [PSG (エンベロープ・ノイズ)](commands/psg.md)
- [PCM (ADPCM / PDX)](commands/pcm.md)
- [生レジスタ書き込み](commands/register.md)
- [曲ヘッダディレクティブ](headers.md)
- [MXDRV 方言と #dual](mxdrv.md)
- [間違えやすい書き方](pitfalls.md)
