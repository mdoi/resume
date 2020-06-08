# レジュメ
## 求職条件
- 勤務地: 福岡のお仕事を探しています。
- できれば副業可がよいです。

## 概要

ITエンジニアとして13年の実務経験があります。

前半3年はフィーチャーフォン向けのソフトウェアエンジニアを、中盤5年は大規模ウェブ/ソーシャルゲームサービスのインフラエンジニアとして、サーバ・ネットワークエンジニア等の下回りから、SREに近い部分を担当、後半5年はWebサービスをメインに様々なITシステムのアーキテクトをしています。直近は、AWSを用いたサービス基盤の設計やコンサルティングを多く行っています。

## スキル

- Linuxベースのインフラ構築・運用
    - 10年の実務経験があります。
    - オンプレ・パブリッククラウド(とりわけAWS)の経験があり、高トラフィック環境でのパフォーマンスチューニングも対応できます。
    - 得意とする要素技術
        - パブリッククラウド
            - AWS 全般
        - 構成管理
            - Terraform, Chef, Ansible
        - モニタリング環境整備
            - Datadog プラグイン開発
        - CI/CD プロセス整備
            - CircleCI
- Webのバックエンド開発
    - 3年の実務経験があります。Ruby (と Rails)が最も得意です。

### その他
Kaggle の SIIM-ACR Pneumothorax Segmentation コンペで、1475人中256位でした。
専門は SRE ですが、アルゴリズムエンジニアの機械学習タスクを理解した基盤の構築ができます。
- https://www.kaggle.com/masdoi

JAWS DAYS 2015 で Github と IaC を連携したインフラ運用のセッションを持ちました。
AWS に関しては一定の専門性を有しています。
- https://speakerdeck.com/mdoi/kai-fa-suruyouniyun-yong-suruinhura-jaws-days-2015

大規模な基盤向けのモニタリングを OSS で行っていましたが限界があり、自社の規模向けのモニタリングシステムを設計・開発しました。
- https://labs.gree.jp/blog/2011/01/2390/

同システムの基盤となるメッセージング手法について、特許を取得しました。
- https://patents.google.com/patent/JP5869018B2/ja

## 主な担当プロジェクト

### 深層学習の研究開発基盤の設計・運用

#### チーム構成
- インフラエンジニア x 1
- 機械学習エンジニア x 2

#### 役割
- インフラ

#### 担当業務
プロジェクトに関わる全てを担当した。
- GPUサーバを収容するためのデータセンター手配
- ネットワーク構築
- GPUサーバ・ストレージ・ネットワーク機器等ハードウェアの選定
- 柔軟な環境を構築可能な基盤の設計
- 監視の整備
- 運用

#### 発揮したバリュー
研究開発用のデータには適切なセキュリティの確保と権限管理が必要なので、コンテナ環境を実現しつつ従来のユーザの権限も維持できるように Singularity を用いたコンテナ環境を構築した。
また、様々なフレームワーク、バージョン、言語を用意できるように、研究開発に必要となる環境を GNU modules で用意し、利用者が自身でセットアップをしなくても選択してすぐ利用できるような環境を用意した。
監視については、GPU 特有の監視項目を監視できるように、Datadog のプラグインを独自に作成して必要な監視を実現した。

### ヘルスケア系Webサービスの基盤設計・開発・運用

#### チーム構成

- プロダクトオーナー1名
- フロントエンドエンジニア1名
- サーバサイドエンジニア3名
- サーバサイド & インフラエンジニア1名

#### 役割

- サーバサイド
- インフラ

#### 担当業務

主にインフラ設計やアプリケーションのアーキテクチャ設計作業を担当し、ECS + Terraform によるAWSのインフラ構築と管理、CircleCIによるCI/CD環境の構築、APIサーバのWebフレームワークの選定、各種実装作業等を担当。

言語はRuby。WebフレームワークはRuby on Rails。データベースはPostgres(オンプレミス及びAWS RDS/Aurora)、ログ収集には CloudWatch Logs、モニタリングには Datadog を使用。

バックエンドの開発も実施。

#### 発揮したバリュー

基盤に積極的に AWS の機能を取り入れることで、少人数で安定した運用が可能な基盤を構築した。

例えば、EC2上で直接アプリケーションを動作させる基盤から、インフラを宣言的に定義できる ECS を用いた構成に移行することで、障害時やスケールアップ時の運用コストを省力化し、安定したスケーラブルな基盤を実装した。

また、AWSとオンプレミスとの連携が必要なアーキテクチャだったが、オンプレ側に AWS SSM を活用して、極力 AWS の API を介したコントロールができるようにすることで、連携コストの省力化を行った。

開発プロセスについても Github と CircleCI を連携させつつ環境ごとのブランチ利用方法、連携部のデプロイ処理を実装し、統一的で追跡可能なデプロイプロセスの整備を行った。

また、Terraform による構成管理は初体験であったが短期間で学習しキャッチアップし取り入れることで、レビュー可能な構成管理を実現した。

### 広告バナーのログ集計システムの設計・構築・運用

#### チーム構成

- サーバサイドエンジニア1名
- サーバサイド & インフラエンジニア1名

#### 役割

- サーバサイド
- インフラ

#### 担当業務

主にインフラ設計やログ集計基盤の設計作業を担当した。

基盤は AWS で作成、ログの収集は Fluentd、集計は Fluentd プラグインや Norikra、BigQuery を活用、データ保存は DynamoDB を利用した。

#### 発揮したバリュー

発生したログを Fluentd で収集し、高速に処理すべきデータは Fluentd プラグインやNorikraで処理した後、DynamoDB に投入、バッチとして処理すべきデータは BigQuery に保存することで、スケーラブルかつ安価に SaaS を活用したラムダアーキテクチャを組むことができた。

また、必要になった Fluentd プラグインは開発を行い、Github にオープンな状態で公開し、広く使えるようにした。

ログ受信のフロントのサーバは負荷に応じて簡易に自動・手動で拡張できるように ECS で構成した。

### 大規模インフラの監視システムの設計・開発・運用

#### チーム構成

- エンジニア2名

#### 担当業務

プロジェクトに関わる全てを担当した。

ActiveMQ を核とし、大量のサーバから出力されるログを監視し必要に応じてアラートを上げるシステムを Ruby を用いて開発した。

#### 発揮したバリュー

監視システムとして主要な OSS である Nagios では間に合わなくなってしまったインフラの監視が行えるよう、拡張性、可用性を考慮したアーキテクチャを考えることができた。

拡張性に関してはメッセージキューをうまく活用し、処理の増大に対しても単純にサーバを増やすだけで継続して監視が行なえるよう柔軟なシステムにすることができた。

可用性に関してはネットワークの技術である VRRP を参考にしたアルゴリズムを実装し、障害に強いシステムにすることができた。

設計概要については会社のブログに公開することで、一般に広く知見を公開した。

## 登壇・ブログ等

https://lapras.com/public/9DULZYZ

を参照
