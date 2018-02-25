# 開発メモ
* [OSXのパス通し](#OSXのパス通し)
* [Homebrewのインストール](#Homebrewのインストール)
* [gitのインストール](#gitのインストール)
* [railsのインストール](#railsのインストール)
* [postgreSQLのインストール](#postgreSQLのインストール)
* [Pythonのインストール](#Pythonのインストール)
* [PhantomJSのインストール](#PhantomJSのインストール)
* [herokuCLIのインストール](#herokuCLIのインストール)

<a id="OSXのパス通し"></a>
# OSXのパス通し

* ***パスの記述ファイル：*** `sudo nano ~/.bash_profile`

* ***環境変数のリロード：*** `source ~/.bash_profile`

* ***環境変数の確認：*** `echo $PATH`

<a id="Homebrewのインストール"></a>
# Homebrewのインストール ##
  `/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`
  * 参）https://brew.sh/index_ja.html

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
