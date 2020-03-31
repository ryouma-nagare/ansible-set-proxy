# ansible-set-proxy


## 概要
Linuxのプロキシを設定／解除するためのplaybookです。

## 対象OS
- CentOS
- RHEL/Fedora
- Ubuntu
- Debian


## 設定対象

- 環境変数
- gem
- apt/yum/dnf
- curl/git/wget/subversion
    - パッケージのインストールも行う

※ついでにselinuxをオフにしています

## 環境依存の設定

#### パラメータ設定
- `group_vars/allserver`
    - `is_set_proxy` ：プロキシを設定する場合は`true`、それ以外の場合はプロキシの解除
    - `proxy_host` ：プロキシのIP
    - `proxy_host` ：プロキシのポート

#### ssh設定
- `inventory/hosts`
    - `ansible_host` ：サーバのIP
    - `ansible_ssh_user` ：ログインするユーザ名
	- `ansible_ssh_pass` ：ログインするユーザのパスワード
	- `ansible_su_pass` ：rootのパスワード

※インストール直後の Ubuntu には sudo が導入されていないため、"become_method: su"に変更

## 実行方法

```
ansible-playbook -i ./inventory/hosts setproxy.yml
```
