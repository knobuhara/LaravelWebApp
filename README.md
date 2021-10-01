## LaravelWebApp

#### 環境構築

- composerのインストール
  ~~~
  curl -sS https://getcomposer.org/installer | php
  ~~~
  - 環境設定
    - sudo mv composer.phar /usr/local/bin/composer
    - composer -V で確認完了

- laravelのインストールとプロジェクト作成
  - エラー発生するので、Macにあるphpを最新化、brew install php@7.4
    - Homebrewのインストールは
    ~~~
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
    ~~~

    - phpバージョンアップ後に環境変数設定
    ~~~
    $ echo 'export PATH="/usr/local/opt/php@7.4/bin:$PATH"' >> ~/.bash_profile
    $ echo 'export PATH="/usr/local/opt/php@7.4/sbin:$PATH"' >> ~/.bash_pro
     ~~~

  - Project作成:LaravelWebApp
  ~~~
  composer create-project --prefer-dist laravel/laravel LaravelWebApp
  ~~~
    - フォルダ権限設定
    ~~~
    chmod -R 777 storage
    chmod -R 777 bootstrap/cache
    ~~~
    - .envのDB設定、app.phpのアプリ名、タイムゾーン、言語設定
