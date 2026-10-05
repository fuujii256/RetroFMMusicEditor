# 曲ヘッダディレクティブ

曲全体の設定は、`;` のコメントとして書きます。ファイルのどこに書いても (チャンネルの本文と同じ行でも) 読み取られますが、見やすいように **ファイルの先頭にまとめる** のがおすすめです。

## 基本

| ディレクティブ | 内容 |
|---|---|
| `; chip=dual\|opna\|opm\|all` | 音源の構成 ([音源とチャンネル](chips.md)) |
| `; tempo=<N>` | 曲のテンポ。1 フレームに `N/75` tick 進む ([ループ・テンポ](commands/flow.md)) |
| `; song_loop=forever\|loop\|1` | すべてのチャンネルを無限ループにする |
| `; loop_start_tick=<N> loop_period_tick=<M>` | 直後の `CH` の行だけに効く、暗黙のループの位置 |
| `; initial_frame_delay=<N>` | 曲の頭の無音のフレーム数 |
| `; channel_start_frame=<ch>:<frame>,...` | チャンネルごとの、発音開始の遅れ |

## 音色・音量

| ディレクティブ | 内容 |
|---|---|
| `; custom_patch_<NN>: ...` | OPLL のユーザー音色 (16 進 8 バイト) |
| `; opna_patch_<NN>: ...` | OPNA の 4 オペレータ音色 (10 進 38 個) |
| `; opm_patch_<NN>: ...` | OPM の 4 オペレータ音色 (10 進 46 個) |
| `; psg_env_<NN>=...` | PSG のソフトウェア音量エンベロープ ([PSG](commands/psg.md)) |
| `; opll_default_vol=<%>` | OPLL の音量 |
| `; opna_default_vol=<%>` | OPNA の音量 (`opn_default_vol=` でも書けます) |
| `; opm_default_vol=<%>` | OPM の音量 |
| `; pdx_default_vol=<%>` | PCM (PDX) の音量 |

音色の書式は [音量・音色・パン](commands/voice.md) を参照してください。

### 音源ごとの音量 `*_default_vol`

その曲を再生している間だけ、音源ごとの音量を変えられます。

| 値 | 意味 |
|---:|---|
| `100` | 標準の音量 (指定しなかったときも、これと同じ) |
| `50` | 半分 |
| `0` | その音源だけを無音にする |
| `400` | 最大 |

```text
; opll_default_vol=100
; opna_default_vol=80
; opm_default_vol=70
; pdx_default_vol=50
```

この音量は、再生される音と、プレイヤーのレベルメーターの両方に反映されます。

!!! note "綴りについて"
    `dafult` のような綴り間違いの書き方も、互換のために読み取られます。新しく書くときは `default` を使ってください。

## 互換・再現のためのオプション

曲ごとに、実機に近い動作を選ぶための設定です。ふつうの作曲では、指定する必要はありません。

| ディレクティブ | 内容 |
|---|---|
| `; ssg_pitch_table=mako\|opna\|ay` | SSG の音程テーブルの選択 |
| `; mxdrv_slur=oneshot\|1\|true` | `&` を、MXDRV と同じ「直後の 1 音だけをつなぐ」動作にする |
| `; pitch_mod=faithful` | 実機に準拠したピッチ変調にする |
| `; vibrato_oneshot=1` | `M` を「次の 1 音だけ」に効かせる |
| `; vibrato_bound_channels=<ch,...>` | 累積ビブラートの幅を抑える |
| `; effect_freerun=1` | `[FE]` を休符の間も進める |
| `; effect_freerun_exclude=<ch,...>` | `effect_freerun` から除外するチャンネル |
| `; effect_keep_level_channels=<ch,...>` | 音を鳴らし始めるときに、エフェクトのレベルを引き継ぐチャンネル |
| `; volume_latch_at_note=1` | `v` の反映を、次の音符を読み込むまで遅らせる |
| `; full_gate_channels=<ch,...>` | 常に音符の全長を鳴らすチャンネル |
| `; immediate_pitch_mod_tick=1` / `; initial_pitch_mod_ticks=` | ピッチ変調の最初の tick |
| `; keyon_zero_volume_channels=<ch,...>` | 音量 0 でも発音を保つチャンネル |
| `; psg_envelope_loop=<ch,...>` | 休符の間も PSG のエンベロープを続ける |
| `; psg_noise_timed_channels=<ch,...>` | `@N` をノイズ周期の指定として扱うチャンネル |
| `; psg_rest_hold_volume_channels=<ch,...>` | 休符でも PSG の音量を保つチャンネル |
| `; suppress_resident_voice_install=1` | 曲の頭の、標準音色の書き込みを止める |
| `; suppress_rhythm_pitch_channels=<ch,...>` | リズムの音程の書き込みを止めるチャンネル |
| `; rhythm_pair_order=runtime` | リズムの書き込み順 |
| `; rhythm_playback=register\|shadow` | リズムをレジスタの列で再生する |
| `; rhythm_mode_latch=onset` | リズムモードのビットを反映するタイミング |
| `; rhythm_sd_hh_key_bits=` / `; rhythm_tom_cym_key_bits=` | リズムのキービットの上書き |

## レジスタ列の直接再生

実機の曲を再現するための設定です。

| ディレクティブ | 内容 |
|---|---|
| `; opll_seed=` | 曲の頭の OPLL レジスタの初期値 |
| `; opll_init=` | フレーム 0 (曲の頭より前) の OPLL レジスタの初期値 |
| `; opll_register_events=` | 予定した OPLL レジスタの書き込み |
| `; opll_register_events_loop_start=` / `; opll_register_events_loop_period=` | 上記のループの範囲 |
| `; ay_register_events=` | 予定した AY (PSG) レジスタの書き込み |
