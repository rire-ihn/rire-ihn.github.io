[TOP](/) - [投稿](/posts) - [FPGAの環境構築](/posts/vivado_env)

# FPGAの環境構築（Arty S7 + Xilinx Vivado）

2022.11.06

秋月で[Arty S7](https://akizukidenshi.com/catalog/g/gM-12558/)を買いました。環境構築のメモです。

1. [Xilinxのダウンロードページ](https://japan.xilinx.com/support/download.html)からVivadoをダウンロードし、インストールします。

    - 注意:例えば2022.1の場合100GB以上の空き容量が必要になります。

1. Newプロジェクトからプロジェクトをつくります。デバイスはXC7S50CSGA324-1を選びましょう。

1. Add SourcesのAdd or crate constaraintsから[ここ](https://github.com/Digilent/digilent-xdc)にあるxdcファイルを読み込みます。使うピンのコメントアウトを外しましょう。

1. Add SourcesのAdd or crate design sourcesからVerilogファイルをインポートするなり作って書いたりします。

1. 左側のFlow Navigatorの中にあるProgram And Debug → Generate Bitstreamを実行します。SYNTHESISとIMPLEMENTATIONをするか聞かれるので、OKをしてそれらも実行してもらいます。実行中は右上がぐるぐるします。

1. Generate Bitstreamが終わったらHardware Managerを開きます。上の緑の帯(もしくは左のFlow Navigator)のOpen Target → Auto Connectを選びます。

1. 上の緑の帯(もしくは左のFlow Navigator)のProgram deviceを押してProgramボタンを押せば書き込めます。

ところで、Vivadoをインストールした時の初期設定では、エディタ起動時にフリーズするバグが発生しました。Xilinxのサポートのページに同じ症状で悩んでいる人がいて、その回答の通りにやったら解決しました。

- [Xilinxのサポートのページ](https://support.xilinx.com/s/question/0D52E00006hpSMzSAM/vivado-freeze?language=ja)

- [Tools] → [Settings] → [Tool Settings] → [Text Editor] → [Syntax Checking]に移動し、 [Syntax Checking ]設定を Sigasiから Vivadoに変更