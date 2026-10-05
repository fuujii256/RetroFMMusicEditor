# リズム

CH9〜CH11 は、リズム音源のチャンネルです。

| CH | ロール | 鳴らせる楽器 |
|---:|---|---|
| 9 | `RHYTHM_BD` | バスドラム |
| 10 | `RHYTHM_SD` | スネア・ハイハット |
| 11 | `RHYTHM_TC` | タム・シンバル |

## 楽器の指定

| 文字 | 楽器 |
|---|---|
| `b` | バスドラム (BD) |
| `s` | スネア (SD) |
| `t` または `m` | タム (TOM) |
| `c` | シンバル (CYM) |
| `h` | ハイハット (HH) |
| `i` | リムショット (RIM。OPNA のリズムのみ) |

## コマンド

| コマンド | 意味 |
|---|---|
| `[RK <文字>]` | 次の音符で鳴らす楽器を選びます。複数を同時に選べます (`[RK h]` `[RK sh]`) |
| `[RV <楽器><0-15> ...]` | 楽器ごとの音量。15 が最大です (`[RV h14]` `[RV s12 h10]`) |

!!! important "リズムは音符で鳴らします"
    `[RK b]` は、鳴らす楽器を選ぶだけです。**音符 (`c` など) を置いたところで、選んだ楽器が鳴ります。** 休符 (`r`) では鳴りません。音符の高さは関係ないので、どの音程でも構いません。

```text
; role=RHYTHM_BD
CH9: v15 L4 [RV b15] [LOOP 2] [RK b] o2 c r [RK b] o2 c r [LEND]

; role=RHYTHM_SD
CH10: v15 L4 [RV s14 h12] [LOOP 2] r [RK s] o4 c r [RK sh] o4 c [LEND]
```

上の例では、CH9 が 1・3 拍目でバスドラムを鳴らし、CH10 が 2 拍目でスネア、4 拍目でスネアとハイハットを鳴らします。

!!! warning "楽器の文字や音量を間違えると、エラーになります"
    `[RK]` と `[RV]` は、不正な文字や、範囲外の音量を書くと、曲が読み込めなくなります。「書いたのに何も起きない」状態を避けるための動作です。

## 関連する曲ヘッダ

リズムの細かな再現のための設定です ([曲ヘッダディレクティブ](../headers.md))。

- `; rhythm_pair_order=runtime`
- `; rhythm_playback=register` / `shadow`
- `; rhythm_mode_latch=onset`
- `; rhythm_sd_hh_key_bits=` / `; rhythm_tom_cym_key_bits=`
- `; suppress_rhythm_pitch_channels=<ch,...>`
