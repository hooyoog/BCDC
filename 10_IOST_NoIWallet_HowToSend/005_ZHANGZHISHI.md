# 涨姿势 -0=（o ~ o）=0-


#### 1 如果运行着react start ，不小心按了Ctrl+z，可以用：   fg 命令进入，然后再Ctrl+c来关闭本次启动    

#### 2 cnpm install fetch-jsonp --save 可以读取加密的json   

#### 3 想利用js修改div宽度，js必须在div下方   
```HTML
    <style>
        #root{
            width: 100%;
               
        }
    </style>

    <title>iControll - damin</title>
   
    
    <div id="root" class="root"></div>
    <script>
      let x = window.outerHeight;
      let y = window.outerWidth;
      
      if(x<y){
        console.log(x+"-"+y)
        var div1=document.getElementById('root');
        div1.style.setProperty('width','50%');
      }
    </script>
```

#### 4 箭头函数里调用的函数，必须是用箭头声明的函数，不能是function声明的   

#### 5 对于mysql中存储url的字段，至少128个
```SQL
ALTER TABLE `table_name` CHANGE `url` `url` VARCHAR(128) CHARACTER SET utf8 COLLATE utf8_unicode_ci NOT NULL;
```

#### 6 关于智能合约的一些计算符号
```javascript
//除法最好前面加上（），除完.toFixed(2)一下，省得太大，写入数据库要.toString()
level.plus((amount_All2*0.01)/level).toFixed(2)).toString()

//加法不用“+”号，用.plus()
level.plus(123)
```

#### 7 安装react干脆把源设为淘宝   
```
npm config set disturl https://npm.taobao.org/dist   
npm config set registry https://registry.npm.taobao.org   
```   

#### 8 linux备份数据库  
```shell
 mysqldump -u root -p dzjj_app > /home/download/dzjj_app_20_11_12.sql

 ```   

 #### 9 git 新建分支
 ```
 首先上传当前分支
 git add .
 git commit -m '将整直播工程备份，包括mysql和javaweb，在beifen文件夹里'
 git push origin three_iwallet_lesson_0.0.2

 然后新建分支
 （查看当前*）git branch
 （新建并切换）git checkout -b three_iwallet_lesson_0.0.3 
 （上传）git push origin three_iwallet_lesson_0.0.3

 ```
