# インストール

!!! info "最新版"
    最新版は [RetroFM-Music Editor 0.13.8](https://github.com/fuujii256/RetroFMMusicEditor/releases/tag/v0.13.8) です (ベータ版)。

## 動作環境

- Windows 10 / 11 (64 ビット)
- 音声の出力デバイス

## インストールの手順

1. [Releases](https://github.com/fuujii256/RetroFMMusicEditor/releases) から `RetroFMMusicEditor_<バージョン>.zip` をダウンロードします (例: `RetroFMMusicEditor_0.13.8.zip`)。
2. **展開する前に**、zip を右クリック →「プロパティ」→「セキュリティ: 許可する」にチェック →「OK」を押します。詳しくは [SmartScreen の警告が出たとき](smartscreen.md) を参照してください。
3. 好きな場所に展開します。
4. 展開したフォルダの `NEWFMEditor.App.exe` をダブルクリックすると、エディタが起動します。

zip には、エディタ本体 (`NEWFMEditor.App.exe`)、サンプル曲 (`MML` フォルダ)、第三者ソフトウェアのライセンス (`THIRD-PARTY-NOTICES` フォルダ) が入っています。.NET を同梱しているので、別途インストールする必要はありません。

!!! note "実行ファイルの名前について"
    実行ファイルの名前は `NEWFMEditor.App.exe` ですが、ウィンドウに表示される名前は「RetroFM-Music Editor」です。

## 更新

新しい版の zip を別のフォルダに展開してください。設定 (ウィンドウサイズ、表示、開いていたフォルダなど) は引き継がれます。

## アンインストール

展開したフォルダを削除してください。エディタの設定は `%LOCALAPPDATA%\NEWFMEditor` にあるので、不要であればこのフォルダも削除してください。
自分で作った MML ファイルは、削除されません。
