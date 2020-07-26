# ansible-ubuntu-xenial
ローカル開発環境用の Ansible の Playbook．

## 環境
- macOS Catalina 10.15.6

## インストール
- [Homebrew](https://github.com/Homebrew/brew) 2.4.8
- [mutagen](https://github.com/mutagen-io/mutagen) 0.11.5
- [Vagrant](https://www.vagrantup.com/) 2.2.9
- [VirtualBox](https://www.virtualbox.org/) 6.1.12r139181

# 使い方
普段、開発しているコードのプロジェクトディレクトリ直下で `git clone` する．  
`vagrant up`を実行すると「ansible_local」という Vagrant のプロビジョナが実行され、開発に必要なツールがインストールされる．  
構築が終了すると Mutagen により、ホスト(PC)側とゲスト(ローカル開発環境)でファイルが動悸される状態になる．  
あとは`vagrant ssh`し、普段通りに開発する．  

```bash
❯ pwd
/Users/ユーザ名/projects
❯ git clone git@github.com:bake0937/ansible-ubuntu-xenial.git
❯ vagrant up
❯ vagrant ssh
```
