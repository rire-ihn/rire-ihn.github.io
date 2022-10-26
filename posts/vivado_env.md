[TOP](/index) - [投稿](/posts) - [fpga環境構築](/posts/vivado_env)

# FPGAの環境構築（Arty S7 + Xilinx Vivado）

秋月で[Arty S7](https://akizukidenshi.com/catalog/g/gM-12558/)を買いました。環境構築のメモです。

- [Xilinxのダウンロードページ](https://japan.xilinx.com/support/download.html)からVivadoをダウンロードし、インストールします。

    - 注意:例えば2022.1の場合100GB以上の空き容量が必要になります。

- Newプロジェクトからプロジェクトをつくります。デバイスはXC7S50CSGA324-1を選びましょう。

- Add SourcesのAdd or crate constaraintsから[ここ](https://github.com/Digilent/digilent-xdc)にあるxdcファイルを読み込みます。使うピンのコメントアウトを外しましょう。

- Add SourcesのAdd or crate design sourcesからVerilogファイルをインポートするなり作って書いたりします。

- Generate BitstreamしてPrograma deviceすれば書き込めます。

ところで、Vivadoをインストールした時の初期設定では、エディタ起動時にフリーズするバグが発生しました。Xilinxのサポートのページに同じ症状で悩んでいる人がいて、その解答の通りにやったら解決しました。

- [Xilinxのサポートのページ](https://support.xilinx.com/s/question/0D52E00006hpSMzSAM/vivado-freeze?language=ja)

- [Tools] → [Settings] → [Tool Settings] → [Text Editor] → [Syntax Checking]に移動し、 [Syntax Checking ]設定を Sigasiから Vivadoに変更