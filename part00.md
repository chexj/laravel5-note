1.安装laravel5.2 
  composer create-project laravel/laravel learnlaravel5 5.2.31    //cmd 命令下操作
2.激活自带的auth
  php artisan make:auth   //cmd命令下操作
3.修改数据库配置
  在.env文件中修改，若不存在，可复制.env.example,修改以下字段：
  DB_HOST=127.0.0.1
  DB_PORT=3306
  DB_DATABASE=laravel5
  DB_USERNAME=root
  DB_PASSWORD=password
4.新建一个model类
  php artisan make:model Article  //cmd命令下操作
  执行之后 app 目录下将增加一个 Article.php 文件
5.生成一个model类的 Migration 文件(可以理解为数据库创建文件)
  php artisan make:migration create_article_table
  php artisan make:migration create_article_table
  执行之后 database/migrations 目录下将增加一个 create_article_table 文件
6.执行 Migration 文件，生成数据库对应的表
  php artisan migrate
7.生成某个数据表的 seeder 类文件
  php artisan make:seeder ArticleSeeder
  php artisan make:seeder ArticleSeeder
  执行之后, database/seeds 目录下多了 ArticleSeeder.php
8.执行 seeder 文件，向数据库中导入数据
  8.1 修改 seeder 文件的 run 方法：
        public function run()
      {
          DB::table('articles')->delete();

          for ($i=0; $i < 10; $i++) {
              \App\Article::create([
                  'title'   => 'Title '.$i,
                  'body'    => 'Body '.$i,
                  'user_id' => 1,
              ]);
          }
      }
  8.2 将 ArticleSeeder 注册到系统中：
    修改 database/seeds 目录下的 DatabaseSeeder.php 的 run 方法
    public function run(){
      $this->call(ArticleSeeder::class);
    }
  8.3 将 ArticleSeeder 注册为自动加载：
    composer dump-autoload
  8.4 执行 seeder 写入
    php artisan db:seed
