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

- マイグレーションファイルの作成　[migretionチュートリアル](https://readouble.com/laravel/6.x/ja/migrations.html)
  - mysqlのDBはutf8mb4_general_ciで指定(日本語絵文字対応)
  - 作ったDBに対し、テーブルを作成
    - Usersテーブルのmigrationはlaravel uiで自動生成されるため不要
    - tasksテーブル：php artisan make:migration create_tasks_table --create=taskss
    - tagsテーブル：php artisan make:migration create_memos_table --create=memos
    - databaseフォルダー直下にxxx_create_xxx_table.phpが生成される
      - phpファイルを仕様に従い、カラムの追加を行う
  - マイグレーションの実行 ※これでテーブルが一気にDBに作成される　！！便利
  ~~~
  php artisan migrate
  ~~~
  - 間違った場合、実行したマイグレーション操作を取り消すことができる
  ~~~
  php artisan migrate:rollback
  ~~~

- Laravel uiのインストール
  - インストール(最新版がインストールされる　3.3.0)
  ~~~
  composer require laravel/ui
  ~~~
  - サーバ起動
  ~~~
  php artisan serve
  ~~~
  - laravel uiの展開
  ~~~
  php artisan ui vue --auth
  ~~~
  - npmのインストール(npmは node.js) 
  ~~~
  npm install && npm run dev
  ~~~
