# 查询



```javascript


state={
    new_rom_All:[],
    temp_room:""
}

//react的初始化函数
componentDidMount() {
    setTimeout(() => {
        //由于区块链API不能获取所有map的value，所以根据field调用多次
      this.httpGetPostAPI("01")
      this.httpGetPostAPI("02")
      this.httpGetPostAPI("03")
      this.httpGetPostAPI("04")
      this.httpGetPostAPI("05")
      this.httpGetPostAPI("06")
      this.httpGetPostAPI("07")
      this.httpGetPostAPI("08")
      this.httpGetPostAPI("09")
      
    }, 2000);
}

httpGetPostAPI=(which)=> {
        var url = 'http://119.249.54.118:30001/getContractStorage';
        var xhr = new XMLHttpRequest();
        xhr.responseType = "text";
        xhr.open('POST', url);
        xhr.setRequestHeader("Content-Type", "application/x-www-form-urlencoded;");
     
        //3. 发送 字符串
         xhr.send(JSON.stringify({
         "id":"Contract9m7S1Y66YL2XqXvh1VxrL7X8cdh19MKkMknGKXWPFZhk",
         "key":"new_room_11",
         "field":which,
         
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
                let tempData = JSON.parse(xhrRes).data
                for(var i=0;i<tempData.length;i++){
                  tempData=tempData.replace("\\","")
                }
                let temp_New_Room_All = this.state.new_rom_All
                temp_New_Room_All.push(tempData)
                this.setState({new_rom_All:temp_New_Room_All})

                console.log('data====>' + JSON.parse(xhrRes).data);

                setTimeout(() => {
                    //实验
                  let temp = this.state.new_rom_All[0];
                  
                  console.log(JSON.parse(temp).announcer_ID)
                 
                }, 2000);

            }
        };
    }

```

