# 音源とチャンネル

## チャンネルの既定の役割

チャンネル番号 (`CH<N>`) には、それぞれ既定の役割 (ロール) が割り当てられています。

| CH | 既定のロール | 出力 |
|---:|---|---|
| 0〜2 | `PSG_A` / `PSG_B` / `PSG_C` | PSG (SSG) の A / B / C |
| 3〜8 | `FM_0`〜`FM_5` | FM 音源の 0〜5 番 |
| 9 | `RHYTHM_BD` | リズム: バスドラム |
| 10 | `RHYTHM_SD` | リズム: スネア + ハイハット |
| 11 | `RHYTHM_TC` | リズム: シンバル + タム |
| 12〜19 | PCM 0〜7 | PCM (`CHP1:`〜`CHP8:` で自動的に割り当て) |

PCM を使わない曲は 12 チャンネル (CH0〜CH11) です。

## ロールの上書き `role=`

`; role=<名前>` というコメントで、チャンネルのロールを変えられます。書き方は 2 通りです。

```text
; role=OPM_1 hw=OPM          ← 次に来る CH の行に適用
CH4: ...

; CH3: role=FM_2 hw=OPLL     ← コメントの先頭に CH 番号を書く形
```

ロール名は、大文字小文字を区別せず、`_` はあってもなくても構いません (`FM_0` と `FM0`)。

| 種別 | 書き方 |
|---|---|
| PSG | `PSG_A` `PSG_B` `PSG_C` |
| FM (OPLL / OPNA) | `FM_0`〜`FM_5` |
| OPM | `OPM_0`〜`OPM_7` |
| リズム | BD: `RHYTHM_BD` `RHY_BD` `BD` / SD+HH: `RHYTHM_SD` `RHY_SD_HH` `SD` / TOM+CYM: `RHYTHM_TC` `RHY_TOM_CYM` `TC` |

!!! note "PCM のロールは `role=` で指定できません"
    PCM は、`CHP1:`〜`CHP8:` と書いたときだけ割り当てられます ([PCM](commands/pcm.md))。

## チップモード `; chip=`

曲全体の音源の構成を、`; chip=` で選びます。

| 指定 | 構成 |
|---|---|
| `; chip=opna` | すべてのロールを OPNA (YM2608) で鳴らす |
| `; chip=opm` | OPM ロールは OPM (YM2151)、それ以外は OPLL |
| `; chip=dual` | PSG ロールは OPNA の SSG、FM とリズムは OPLL (YM2413) |
| `; chip=all` | **OPM・OPLL・OPNA を同時に使う** |
| (指定なし) | エディタの既定。RetroFM-Music Editor では OPNA |

### `; chip=all` の割り当て

`chip=all` では、既定の割り当てが次のようになります。`hw=` を書くと、チャンネルごとに上書きできます。

| ロール | 既定の音源 |
|---|---|
| `OPM_0`〜`OPM_7` | OPM |
| `PSG_A`〜`PSG_C` | OPNA (SSG) |
| `FM_0`〜`FM_5`・リズム | OPLL |

## チャンネルごとの音源指定 `hw=`

`role=` と同じコメントに `hw=OPLL` / `hw=OPNA` / `hw=OPM` と書くと、そのチャンネルの音源を選べます。**`; chip=all` のときだけ** 有効です。それ以外のチップモードでは、書いても使われません。

同じ `FM_n` でも、`hw=OPLL` と `hw=OPNA` は別のチャンネルとして同時に鳴らせます。

```text
; chip=all

; role=FM_0 hw=OPLL
CH4: @1 v12 o3 L4 c g a f

; role=FM_1 hw=OPNA
CH5: @1 v11 o4 L4 e d c d
```

OPM と OPNA の音色は、別々のバンクとして管理されます。そのため、`opm_patch_01` と `opna_patch_01` のように、同じ番号を別の音色として同時に持てます ([音量・音色・パン](commands/voice.md))。

## 音源ごとの違い

| 項目 | OPLL | OPNA | OPM |
|---|---|---|---|
| FM の音数 | 6 | 6 | 8 |
| `@N` の意味 | 0〜15 は内蔵音色。16〜31 はユーザー音色 | 音色番号 (0〜255) | 音色番号 (0〜255) |
| パン `p0`〜`p3` | 受け付けるが音像は変わらない | 受け付けるが音像は変わらない | **ステレオ出力に反映** |
| リズム | 内蔵リズム (BD / SD / HH / TOM / CYM) | 内蔵リズム (+ RIM) | なし |
