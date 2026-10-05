# RetroFM-Music Editor

RetroFM-Music Editor は、レトロ FM 音源 (YM2413 OPLL / YM2608 OPNA / YM2151 OPM / MSM6258 ADPCM) の曲を MML で書き、編集しながらその場で再生できる Windows 用のエディタです。
RetroFMEditor独自方言の MML に加えて、MXDRV (X68000) 方言の MML も読み込んで鳴らせます。OPLL・OPM・OPNA は 1 曲の中で同時に使えます。

- **ドキュメント・コマンドリファレンス**: <https://fuujii256.github.io/RetroFMMusicEditor/>
- **ダウンロード**: [最新版 (0.13.11)](https://github.com/fuujii256/RetroFMMusicEditor/releases/tag/v0.13.11)
- **お問い合わせ・不具合報告**: [しるふぁ工房 お問い合わせページ](https://fuujii256.github.io/sylfa-studio/contact.html)

## 主な機能

- MML のテキスト編集と、編集内容の即時反映 (再生位置を保ったまま差し替え)
- OPLL / OPNA / OPM / PCM (PDX) のチャンネルごとの発音表示、レベルメーター、Solo / Mute
- 音源ごとの色分け表示 (OPLL 橙・OPM 緑・OPNA 青・PCM 桃)。チャンネルをクリックすると、演奏中の MML 位置へ移動します
- 再生位置のシーク、演奏中の MML のハイライト
- 曲ごとの音源コア音量の指定
- ウィンドウのサイズ変更・最大化 (サイズは次回起動時に復元)
- 新しい版の通知と、ボタン 1 つでの更新 (署名と SHA-256 を検証してから適用します)

## 動作環境

- Windows 10 / 11 (64 ビット)
- 音声の出力デバイス

.NET は同梱しているので、別途インストールする必要はありません。

## ダウンロードしたら (SmartScreen について)

実行ファイルにはコード署名をしていないため、初めて起動するときに Windows の警告が表示されることがあります。
**zip を展開する前に、zip のプロパティで「許可する」にチェックを入れてください。**
詳しい手順は [SmartScreen の警告が出たとき](https://fuujii256.github.io/RetroFMMusicEditor/getting-started/smartscreen/) を参照してください。

## 更新の確認について

起動時に、このリポジトリの更新情報 (`manifest/v1/stable.json`) を取得して、新しい版があるかを確認します。送信するのは、通常の HTTPS の取得に伴う情報だけで、MML ファイルや個人情報は送りません。画面右上の「更新確認」のチェックを外すと、起動時の確認をしなくなります。

## 利用規約

[EULA.md](EULA.md) を参照してください。RetroFM-Music Editor で作った曲は、商用・非商用を問わず無料で公開・配布・販売できます。クレジット表記は任意です。

## 第三者のソフトウェア

同梱している OSS とそのライセンスは [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md) に記載しています。

## このリポジトリについて

このリポジトリは、RetroFM-Music Editor の配布物 (Releases)、ドキュメント、更新情報を置く場所です。ソースコードは公開していません。
お問い合わせは GitHub ではなく、上記のお問い合わせページからお願いします。
