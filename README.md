# 開発メモ
* [OSXのパス通し](#OSXのパス通し)
* [Homebrewのインストール](#Homebrewのインストール)
* [gitのインストール](#gitのインストール)
* [railsのインストール](#railsのインストール)
* [postgreSQLのインストール](#postgreSQLのインストール)
* [Pythonのインストール](#Pythonのインストール)
* [PhantomJSのインストール](#PhantomJSのインストール)
* [herokuCLIのインストール](#herokuCLIのインストール)
* [Composerのインストール](#Composerのインストール)
* [VirtualBoxでraspbianのセットアップ](#VirtualBoxでraspbianのセットアップ)
* [raspbian(Debian)でComposerのインストール](#raspbianでComposerのインストール)
* [raspbian(Debian)でapache + phpのセッティング](#raspbianでapache+phpのセッティング)
* [raspbian(Debian)でcakephpの詰まる所](#raspbianでcakephpの詰まる所)
* [npmでモジュールの最新バージョン確認を簡易化する](#npmでモジュールの最新バージョン確認を簡易化する)

<a id="OSXのパス通し"></a>
# OSXのパス通し

* ***パスの記述ファイル：*** `sudo nano ~/.bash_profile`

* ***環境変数のリロード：*** `source ~/.bash_profile`

* ***環境変数の確認：*** `echo $PATH`

<a id="Homebrewのインストール"></a>
# Homebrewのインストール ##
  * `/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`
  参）https://brew.sh/index_ja.html

<a id="gitのインストール"></a>
# gitのインストール
  * `brew install git`

<a id="railsのインストール"></a>
# railsのインストール

## rbenvのインストール
  * `brew install rbenv`
  * `brew install ruby-build`
  * `rbenv -v`でバージョン確認

## ~/.bash_profileに記述
  * `echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bash_profile`
  * `echo 'if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi' >> ~/.bash_profile`
  * `source ~/.bash_profile`

## rubyのインストール
  * `rbenv install 2.2.3`
  * `ruby -v`で成功しているか確認

## rbenvのバージョン切り替え
  * `rbenv global 2.2.3`
  * `rbenv rehash`
  * `ruby -v`でバージョン確認
  * `gem -v`でインストールされているか確認

## bundlerのインストール
  * `gem install bundler`
  * `bundle -v`で成功しているか確認

## mysqlのインストール
  * `brew install mysql`
  * `mysql.server.start`で起動できるか確認

## railsのインストール
  * 適当なワークスペースに移動
  * `bundle init`
  * Gemfileの編集
    * `- #gem rails`
    * `+ gem rails`
  * `bundle install`

## 環境変数に適用
  * `source ~/.bash_profile`

<a id="postgreSQLのインストール"></a>
# postgreSQLのインストール
  * `brew install postgresql`
  * `initdb /usr/local/var/postgres -E utf8`
  * `postgres --version`
  * `postgres -D /usr/local/var/postgres`

<a id="Pythonのインストール"></a>
# Pythonのインストール

## pyenvのインストール
  * `brew install pyenv`

## パス設定
  * `echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bash_profile`
  * `echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bash_profile`
  * `echo 'eval "$(pyenv init -)"' >> ~/.bash_profile`
  * `source ~/.bash_profile`

## バージョン選択
  * `pyenv install -l`で選択できるバージョン確認
  * `pyenv install` バージョン

## バージョン確認
  * `pyenv versions`
  * `python -V`

<a id="PhantomJSのインストール"></a>
# PhantomJSのインストール

## npmのインストール
  * `brew install npm`

## PhantomJSのインストール
  * `npm install phantom phantomjs -g`

<a id="herokuCLIのインストール"></a>
# herokuCLIのインストール

  * `brew install heroku/brew/heroku`

<a id="Composerのインストール"></a>
# Composerのインストール
  * `curl -sS https://getcomposer.org/installer | php`
  * `mv composer.phar /usr/local/bin/composer`
  * `compose -V`でバージョン確認
  参）https://qiita.com/m_snow/items/f9397760fb20733c9e5b

<a id=""></a>
# cakephpプロジェクトの作成
  * `composer create-project --prefer-dist cakephp/app {プロジェクト名}`
### 注）intl関連でエラーが出た時
  解決）php7.2に乗り換えるとうまくいく
  * `brew install homebrew/php/php72-intl`
  * .bash_profileに`export PATH="$(brew --prefix homebrew/php/php72)/bin:$PATH"`を追記
  * `php -v`でバージョン確認

<a id="VirtualBoxでraspbianのセットアップ"></a>
# VirtualBoxでraspbianのセットアップ
  * isoのダウンロード
  url）https://www.raspberrypi.org/downloads/raspberry-pi-desktop/
  * VirtualBoxで仮想イメージの作成
  <br>
  ***必須設定***
  <br>
  <br>
  ***タイプ：*** Other
  <br>
  ***バージョン：*** Other Unknown(64bit)
  <br>
  ***容量：*** 8GB以上が必要
  <br>
  <br>
  * 作成したイメージを起動
  * OSイメージを要求されるのでOSイメージ（ex. .iso）ファイルを選択
  * メニューが出たらInstal系項目から選んでインストーラの起動
  * OSのインストーラに従う

<a id="raspbianでapache+phpのセッティング"></a>
# raspbian(Debian)でapache + phpのセッティング
  * `sudo apt-get install php7.0`
  * `sudo apt-get install apache2`
  * ドキュメントルート(初期は`/var/www/html`)にindex.phpを作成して`<?php phpinfo(); ?>`を追記
  * `sudo service apache2 start`でサーバーを起動
  * http://localhost/index.php でphp情報が表示されれば成功

<a id="raspbianでComposerのインストール"></a>
# raspbian(Debian)でComposerのインストール
  * 適当なディレクトリに移動
  * 適当な名前でフォルダ作成して移動
  * 必要なものを落とす：`curl -sS https://getcomposer.org/installer | php`
  * エイリアスで'composer'コマンドを登録：`alias composer='{ディレクトリ}/composer.phar'`
  * 移行'composer'コマンドで利用できる

<a id="raspbianでcakephpの詰まる所"></a>
# raspbian(Debian)でcakephpの詰まる所
  ## php-intlを'php.ini'で有効化
  * php.iniを編集

    php.iniの場所：`/etc/php/{バージョン}/cli/php.ini`又は`/etc/php/{バージョン}/apache2/php.ini`

    php.ini：
    ```
      + extension=php_intl.so
      #もし'mbstingがない言われたらapt-getでインストールして'
      + extension=php_mbstring.so

      #もしWindowsなら
      + extension=php_intl.dll
      + extension=php_mbstring.dll
    ```

  ## プロジェクト作成時に'ext-simplexml'がないと言われる
  参）https://saka24.blue/index.php/2017/07/10/simplexml/

  * まずphp-xmlのインストール：`sudo apt-get install php-xml`
  * ext-simplexmlは存在しないので、'halilim/xml-iterator'をインストールする

    `composer require halilim/xml-iterator`

# [非推奨]raspbian(Debian{Stretch})でphp7.1のインストール（ビルド）(Apacheとの連携不可)
  参）http://aonasuzutsuki.hatenablog.jp/entry/2017/07/24/005028
  * 適当なディレクトリを作成して移動
  * ダウンロード：`wget http://jp2.php.net/get/php-7.1.7.tar.gz/from/this/mirror -O php-7.1.7.tar.gz`
  * 解凍：`tar -xf {ディレクトリ}/{圧縮ファイル名}`
  * 解凍したフォルダに移動
  * `./buildconf`を実行して、必要がないと言われれば次へ


<a id="npmでモジュールの最新バージョン確認を簡易化する"></a>
# npmでモジュールの最新バージョン確認を簡易化する
  * 'npm-check-updates'をインストール
  ```
    npm install -g npm-check-updates
  ```
  * 最新版を確かめる
  ```
    ncu
  ```
  * 最新ばんにpackage.jsonを書き換える
  ```
    ncu -u
  ```
  * インストールする
  ```
    npm install
  ```
