# 涨姿势 -0=（o ~ o）=0-


#### 如果运行着react start ，不小心按了Ctrl+z，可以用：   fg 命令进入，然后再Ctrl+c来关闭本次启动    

#### cnpm install fetch-jsonp --save 可以读取加密的json   

#### 想利用js修改div宽度，js必须在div下方   
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