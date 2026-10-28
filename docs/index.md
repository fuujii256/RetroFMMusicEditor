# RetroFM-Music Editor ドキュメント

RetroFM-Music Editor は、レトロ FM 音源の曲を MML で書き、編集しながらその場で再生できる Windows 用のエディタです。

| 音源 | チップ | 用途 |
|---|---|---|
| OPLL | YM2413 | FM 6 音 + リズム 5 音 |
| OPNA | YM2608 | FM 6 音 + SSG 3 音 + リズム |
| OPM | YM2151 | FM 8 音 (X68000 の音源) |
| PCM | MSM6258 | ADPCM 8 音 (PDX サンプルバンク) |
| SCC | SCC / SCC+ | 波形メモリ 5 音 |

1 つの曲の中で OPLL・OPM・OPNA を同時に使えます (`; chip=all`)。

## まずはここから

- [インストール](getting-started/install.md)
- [SmartScreen の警告が出たとき](getting-started/smartscreen.md)
- [画面と操作](getting-started/screen.md)
- [はじめての曲](getting-started/first-song.md)
- [音源パック RetroFM Drums v1](getting-started/sound-kit.md)

## リファレンス

- [コマンドリファレンス](reference/index.md) — すべてのコマンドの書式と例
- [曲ヘッダディレクティブ](reference/headers.md) — `; chip=` など、曲全体の設定
- [MXDRV 方言と #dual](reference/mxdrv.md) — X68000 の MDX 由来の MML を読み込むとき
- [間違えやすい書き方](reference/pitfalls.md) — 動いているように見えて、実は何もしない書き方

## お問い合わせ

不具合報告やご質問は、[しるふぁ工房のお問い合わせページ](https://fuujii256.github.io/sylfa-studio/contact.html) からお願いします。詳しくは [お問い合わせ](support.md) を参照してください。
