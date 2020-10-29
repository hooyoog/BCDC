# POST传参获得json返回值-打印


```html
<script>
//打印到浏览器的控制台
  httpPostAPI=()=> {
        var url = 'http://119.249.54.118:30001/getContractStorage';
        var xhr = new XMLHttpRequest();
        xhr.responseType = "text";
        xhr.open('POST', url);
        xhr.setRequestHeader("Content-Type", "application/x-www-form-urlencoded;");
     
        //发送 字符串
         xhr.send(JSON.stringify({
         "id":"Contract9m7S1Y66YL2XqXvh1VxrL7X8cdh19MKkMknGKXWPFZhk",
         "key":"miguan",
         "field":"announcer_name",
         "by_longest_chain":true
         
         }));
     
        xhr.onload = (e) =>{
            console.log('httpPostTest onload。e====>' + JSON.stringify(e));
        };
        xhr.onreadystatechange = (e) =>{
            console.log('httpPostTest onreadystatechange。e====>' + JSON.stringify(e));
            
            if(xhr.readyState == 4 && xhr.status == 200){
                var xhrRes = xhr.responseText;

                console.log('httpPostTest return message====>' + xhrRes);
                console.log('data====>' + JSON.parse(xhrRes).data);
                
            }
        };
    }

</script>

```