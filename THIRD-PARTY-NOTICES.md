# Third-party notices (第三者のソフトウェア)

RetroFM-Music Editor が同梱している第三者のソフトウェアと、そのライセンスの一覧です。ライセンス本文は、配布する zip の `THIRD-PARTY-NOTICES` フォルダと、このリポジトリの [THIRD-PARTY-NOTICES](THIRD-PARTY-NOTICES) フォルダにあります。

## 演奏エンジン

演奏エンジンは、作者が開発した RetroFMEditor独自のものです。その一部として、次の OSS を使っています。

- emu2413 (YM2413 / OPLL エミュレータ) — MIT License
- emu2149 (YM2149 / PSG エミュレータ) — MIT License

ライセンス本文は `THIRD-PARTY-NOTICES/emu2413_LICENSE.md` と `THIRD-PARTY-NOTICES/emu2149_LICENSE.md` にあります。

## NuGet packages

- CommunityToolkit.Mvvm 8.4.0 — Microsoft
- AvalonEdit 6.3.1.120 — ICSharpCode / AvalonEdit contributors
- NAudio 2.2.1 — Mark Heath and contributors

Package license metadata is available from each package's NuGet page. Review
the applicable license terms before redistributing a modified binary.

## ymfm

The Windows x64 OPNA FM and OPM/YM2151 backends use Aaron Giles' ymfm Yamaha FM sound cores,
vendored from revision `17decfae857b92ab55fbb30ade2287ace095a381` under the
BSD 3-Clause License. The license text is included in published builds as
`THIRD-PARTY-NOTICES/ymfm_LICENSE.txt`.

Official source: https://github.com/aaronsgiles/ymfm

## OKI MSM6258 decoder

MXDRV PDX playback uses a managed OKI MSM6258 ADPCM decoder adapted from
MAME's `okim6258.cpp` at revision
`55d4cd5fd1d7c63682d70281ddca29457c4e621b`, under the BSD 3-Clause License.
The license text is included in published builds as
`THIRD-PARTY-NOTICES/msm6258_LICENSE.md`.

Official source: https://github.com/mamedev/mame/blob/master/src/devices/sound/okim6258.cpp

## DotGothic16

The application embeds DotGothic16 Regular, Copyright 2020 The DotGothic16
Project Authors. DotGothic16 is based on a 16x16-dot Japanese Gothic bitmap
font and is distributed under the SIL Open Font License 1.1. The license text
is included as `THIRD-PARTY-NOTICES/DotGothic16-OFL.txt` in published builds.

Official source: https://github.com/fontworks-fonts/DotGothic16

Embedded TTF SHA-256: `155DA8F318553C11D9DFFC2AFFBC7C2114C6A46F9740BCF639ED5568AF92BE71`
