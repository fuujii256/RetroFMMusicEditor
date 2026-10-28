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

All three packages use the MIT License. The full license texts are included as
`CommunityToolkit.Mvvm-LICENSE.md`, `AvalonEdit-LICENSE.txt` and `NAudio-LICENSE.txt`
under `THIRD-PARTY-NOTICES`. NAudio's notice also covers its bundled 2.2.1 component packages.
The toolkit's upstream third-party notices are included as `CommunityToolkit-THIRD-PARTY-NOTICES.txt`.

AvalonEdit source revision: `862415d51eddc9eac93f462dbc522ffbf929cd52`.
Official license: https://github.com/icsharpcode/AvalonEdit/blob/862415d51eddc9eac93f462dbc522ffbf929cd52/LICENSE

## .NET runtime and Windows Desktop runtime

The Windows x64 self-contained build includes .NET 9.0.12 and the Windows Desktop
runtime 9.0.12. Their MIT license texts are included as `dotnet-runtime-LICENSE.txt`
and `WindowsDesktop-LICENSE.txt`; the runtime's upstream third-party notices are
included as `dotnet-runtime-THIRD-PARTY-NOTICES.txt`.

NAudio also brings Microsoft.Win32.Registry, System.Security.AccessControl and
System.Security.Principal.Windows 4.7.0. Their shared Microsoft MIT license and
upstream notices are included as `Microsoft-System-LICENSE.txt` and
`Microsoft-System-THIRD-PARTY-NOTICES.txt`.

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

## Optional music assets / 任意の音源パック

RetroFM Drums v1 は、録音素材を使わずに合成した12音のPDXと、数式で作成したSCC波形、
オリジナルの付属MMLからなる音源パックです。アプリ本体とは別に CC0 1.0 Universal を適用します。
商用利用、改変、ゲームへの同梱、素材そのものの再配布が可能で、クレジット表記は不要です。

音源パックは任意配布です。音源のみの版にはサンプルMMLを含めません。
配布時の `MML/RetroFM-Drums-v1/LICENSE.md`、`PCM_PROVENANCE.md`、`kit.json` に
利用条件、生成方法、音番号、再生レートとハッシュを記載しています。

CC0: https://creativecommons.org/publicdomain/zero/1.0/

第三者から入手した外部PDXや楽曲には、その素材自身の利用条件が適用されます。
