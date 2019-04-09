### SKILのインストール、起動について

Skymindインテリジェンスレイヤ（SKIL)のコミュニティ版は無償です。

SKILはディープラーニングのプロジェクトで、プロトタイプを作成し商用
サービスへの実装まで支援する統合開発運用環境ツールです。
ディープラーニングのワークフローを簡便化するツールで、学習状況を追跡し
学習済みモデルをワンクリックで実装したり、モデルの性能をモニタリング
するような機能を有します。

以下で簡単に始められます。

  - コミュニティ版SKILのダウンロードとインストール
  - ノートブックを用いたサンプルコードの作成とモデルの学習
  - 学習済みモデルのモデル管理サーバ（SKIL model Server)への展開

HWの最小構成

  CPU: 4コアでAVX命令セットがサポートされたもの<br>
  メモリ： 16 GB （サンプルを動かすだけでしたら8GBでも大丈夫）<br>
  ネットワーク： 1Gps<br>
  空きディスク空間：  50GB以上（サンプルを動かすだけでしたら25GBくらいでも大丈夫）<br>

1. SKILインストール前の事前準備
  <a href="https://git-scm.com/book/en/v2/Getting-Started-Installing-Git#Installing-on-Linux">Git</a>と<a href="https://maven.apache.org/install.html">Appache Maven</a>のインストールが必要です。事前にご準備願います。

1. SKILの構成設定
  - SKILの構成を設定するために以下でYumレポジトリ設定を作成
    （nanoに限らずご自分でお使いのテキストエディタで作成してください）
、
```
sudo nano /etc/yum.repos.d/skymind.repo
```

  - skymind.repoに入力する内容

```
[Skymind]
name=Skymind Repository
baseurl=https://nexus-ci.skymind.io/repository/rpms/centos/7/latest/os/x86_64
gpgcheck=0
```

1. SKILのインストール
  コマンドラインから以下のコマンドを入力することでSKILがインストールされます。

```
sudo yum install -y skil-server-cpu-spark-1.6-hadoop-2.7.x86_64 skil-server-spark-1.6-hadoop-2.7.x86_64 skil-server-interpreter.x86_64 skil-server-static-miniconda-python-2.x86_64
```

インストールが完了するために5分から20分かかりますので、我慢してください。

1. SKILを開始する方法

  SKILを開始するのにコマンドラインから以下のコマンドを入力してください。

```
sudo systemctl daemon-reload
sudo systemctl enable skil
sudo systemctl start skil
```

SKILが立ち上がったら以下でブラウザを開いてください。

```
http://localhost:9008/
```

初回の立ち上げではさまざまな環境設定が行われるため、立ち上げに5分〜10分
かかるのに注意してください。（2回目以降はずっと早く立ち上がります。）

1. SKILを終了する方法
  コマンドラインから以下のコマンドを入力してください。

```
sudo systemctl stop skil
```

"admin"ユーザにパスワードを追加します。

これでインストールは完了です。

1. 次回以降のSKILの立ち上げ方法

・SKILを開始する方法   （sudo systemctl start skil）<br>
・SKIL用のブラウザ立ち上げ （http://localhost:9008/）<br>
・ブラウザ内で以下を入力<br>
   USERNAME： admin<br>
   PASSWORD： ご自身で設定したパスワード<br>
・SKILを終了する方法    (sudo systemcl stop skil)<br>

以上
