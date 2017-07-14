# laravel excel 迁移到 lumen
## 1.使用 composer 安装依赖
在 lumen 项目的根目录下执行 composer
    composer require maatwebsite/excel ~2.1.0
## 2.复制 vendor/maatwebsite/excel/src/config/下的excel.php文件到lumen根目录config文件夹。
## 3.在lumen的bootstrap/app.php中加入
    $app->register(Maatwebsite\Excel\ExcelServiceProvider::class);
## 4.修改vendor/maatwebsite/excel/src/maatwebsite/excel中ExcelServiceProvider.php文件。
### 4.1 boot 方法的修改
    public function boot()
    {
        $this->publishes([ 
          __DIR__.'/../../config/excel.php' => config_path('excel.php), 
        ]); ---注释掉该部分
    }
### 4.2 bindWriter 方法的修改
    protected function bindWriter()
    {
        $this->app['excel.writer'] = $this->app->share(function ($app))
        {
            return new laravelExcelWriter(
                $app->make('Illuminate\Support\Facades\Response'), ---此处为修改过的
                $app['files'],
                $app['excel.identifier']
            );
        }
    }
## 5. laravel-excel 的使用
### 5.1 处理 Excel 文件
    $sheetData = Excel::load($filePath, function($reader){}, 'UTF-8')->noHeading()->toArray();
*若只有一张表，那么 $sheetData 的子元素为表中一列的值  
格式为:
    
    $sheetData = array(
        '0' = array(
            '0' => '第一行的第一个值',
            '1' => '第一行的第二个值',
        ),
        '1' = array(
            '0' => '第二行的第一个值',
            '1' => '第二行的第二个值',
        )
    );
*若是多张表，那么 sheetData 的子元素为每张表的值  
格式为：
    
    $sheetData = array(
        '0' = array(
            '0' => array(
                '0' => '第一张表的第一行的第一个值',
                '1' => '第一张表的第一行的第二个值',
            ),
            '1' => array(
                '0' => '第一张表的第二行的第一个值',
                '1' => '第一张表的第二行的第二个值',
            ),
        ),
        '1' = array(
            '0' => array(
                '0' => '第二张表的第一行的第一个值',
                '1' => '第二张表的第一行的第二个值',
            ),
            '1' => array(
                '0' => '第二张表的第二行的第一个值',
                '1' => '第二张表的第二行的第二个值',
            ),
        ),
    );
### 5.2 生成 Excel 文件
    $cellData = [
        ['学号', '姓名', '成绩'],
        ['10001','AAAAA','99'],
        ['10002','BBBBB','92'],
        ['10003','CCCCC','95'],
        ['10004','DDDDD','89'],
        ['10005','EEEEE','96'],
    ];
    Excel::create(iconv('UTF-8', 'GBK', '学生成绩'), function($excel) use($cellData){
        $excel->sheet('score', function($sheet) use($cellData){
            $sheet->rows($cellData);
        });
    })->store('xls')->export('xls');
PS:  
+ iconv('UTF-8', 'GBK', $fileName)  ---防止文件名乱码  
+ ->store('xls')        --- 将生成的文件存储在服务器端  
+ ->export('xls')       --- 将生成的文件返回给用户（浏览器打开的话会下载该文件）
