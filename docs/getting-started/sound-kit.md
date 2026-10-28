# 音源パック RetroFM Drums v1

RetroFM Drums v1 は、録音素材を使わずに合成した12音のドラム用 PDX です。
アプリ本体とは別の zip で配布します。採用版は v1 です。

## ダウンロード

| 配布物 | 内容 |
|---|---|
| [音源のみ](https://github.com/fuujii256/RetroFMMusicEditor/releases/download/v0.13.17/RetroFM_Drums_v1_Kit.zip) | 12音の PDX、利用条件、出典、音番号の説明 |
| [試奏曲付き](https://github.com/fuujii256/RetroFMMusicEditor/releases/download/v0.13.17/RetroFM_Drums_v1_WithExamples.zip) | 音源のみの内容と、2つの MML |

## 導入と試奏

1. 上の zip をダウンロードし、[SmartScreen の手順](smartscreen.md)に従って展開前にブロックを解除します。
2. zip 内の `MML` フォルダーを、エディタと同じフォルダーなど好きな場所へ展開します。
3. エディタの Resources にあるフォルダーボタンから `MML/RetroFM-Drums-v1` を開きます。
4. 試奏曲付きの版では、`Drum_Audition_v1.mml` または `Shadow_Reactor_Public_v1.mml` を選び、再生ボタンを押します。

`Drum_Audition_v1.mml` は12音の試奏です。
`Shadow_Reactor_Public_v1.mml` は、SCC 5パートと PCM 3パートによる BPM 150、25.6秒ループの曲です。
MML と `retrofm_drums_v1.pdx` は同じフォルダーに置いてください。
音源のみの版に MML は含まれません。

## 自分の曲で使う

```text
; chip=all
; pdx_default_vol=100
#pcmfile "retrofm_drums_v1.pdx"
CHP1: [BPM 120] F4 p3 v12 L4 n0 r n2 r
```

全音を **F4 (15.625 kHz)** で再生してください。別のレートでは音程と長さが変わります。
音番号とコマンドは [PCM リファレンス](../reference/commands/pcm.md) を参照してください。

## 利用条件と更新

パック内の PDX、SCC 波形、付属 MML は CC0 1.0 Universal です。
商用利用、加工、ゲームへの同梱、素材そのものの再配布ができ、クレジット表記は不要です。
詳しくはパック内の `LICENSE.md`、`PCM_PROVENANCE.md`、`kit.json` を参照してください。
アプリ本体には別途 [利用規約](https://github.com/fuujii256/RetroFMMusicEditor/blob/main/EULA.md) が適用されます。

アプリの自動更新は音源パックを追加せず、既存の MML フォルダーのファイルも上書きしません。
音が変わる改訂は新しいバンク名・フォルダー名で提供します。