# Vagrantを使用したUbuntu開発環境構築

## 出来ること

- VirtualBox上にUbuntu(GUI)環境を生成
- Visual Studio Codeを自動インストール
- Dockerを自動インストール

## 使用方法

### [VirtualBoxのインストール]

以下のリンクから自身のOS用インストーラーを取得し、インストール  
https://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html?ssSourceSiteId=otnjp

### [Vagrantのインストール]

以下のリンクから自身のOS用インストーラーを取得し、インストール  
https://www.vagrantup.com/downloads.html

### [実行]

本リポジトリをクローンし、コマンド実行

```bash
git clone https://github.com/MasanoriIwakura/ubuntu-dev.git
cd ubuntu-dev
# vagrantの実行　※初回はインストールに時間がかかります。
vagrant up
```

後からプロビジョニング内容を変更したい場合は`Vagrantfile`修正後、以下のコマンドを実行

```bash
vagrant provision
```

### [ログイン情報]

ユーザー: vagrant  
パスワード: vagrant

---

## Vagrantfileの解説

>config.vm.box = "ubuntu/xenial64"

→使用するOSの指定

>config.vm.network "forwarded_port", guest: 3000, host: 3000

→ホストOSのポートと紐付け

>config.vm.network "private_network", ip: "192.168.33.10"

→ゲストOSのIPアドレス設定

>config.vm.provider "virtualbox" do |vb| 付近

→仮装マシンスペックの設定

>config.vm.provision "shell", inline: <<-SHELL

→プロビジョニング設定。初期起動時に入れておきたいツール等を記載
