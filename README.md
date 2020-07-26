# ansible-ubuntu-xenial
ローカル開発環境構築用の Ansible Playbook．

## 環境
- macOS Catalina 10.15.6

## インストール
- [Homebrew](https://github.com/Homebrew/brew) 2.4.8
- [mutagen](https://github.com/mutagen-io/mutagen) 0.11.5
- [Vagrant](https://www.vagrantup.com/) 2.2.9
- [VirtualBox](https://www.virtualbox.org/) 6.1.12r139181
- 下記の Vagrant のプラグインをインストールする
```bash
❯ vagrant plugin install vagrant-disksize vagrant-hostsupdater vagrant-mutagen vagrant-docker-compose
```

# 使い方
普段、開発しているコードのプロジェクトディレクトリ直下で `git clone` する．  
`vagrant up`を実行すると「ansible_local」という Vagrant のプロビジョナが実行され、開発に必要なツールがインストールされる．  
構築が終了すると Mutagen により、ホスト(PC)側とゲスト(ローカル開発環境)でファイルが同期された状態になる．  
あとは`vagrant ssh`し、普段通りに開発する．  

```bash
❯ pwd
/Users/ユーザ名/projects
❯ git clone git@github.com:bake0937/ansible-ubuntu-xenial.git
❯ vagrant up
❯ vagrant ssh
```

## ローカル開発環境にインストールされるツール
- Docker
  - vagrant-docker-compose プラグインによりインストール
- Docker Compose
  - vagrant-docker-compose プラグインによりインストール
- Ansible
  - Vagrant の ansible_local プロビジョナによりインストール
- git
- zsh
- peco
- zinit
