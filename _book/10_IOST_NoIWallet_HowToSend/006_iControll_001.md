# POST传参获得json返回值-打印

查询功能（这些都是在REACT里的）   
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
------
增删改查    
```html
<script>
state={storage_iGet:"",
        storage_Name:"",
        storage_Feild:"",
        storage_value:"",
    }

//输入就会更新state
handleChange = (e) => {
this.setState({
    [e.target.name]: e.target.value,
})
}

//合约地址
contractAddress_1='Contract9m7S1Y66YL2XqXvh1VxrL7X8cdh19MKkMknGKXWPFZhk'

  comm_callABI=(contract2,action2,sympol2,to2,howmuch2,memo2,array2)=>{

    const contractAddress = contract2
    const { storage_iGet,storage_Name,storage_Feild,storage_value } = this.state

    IWalletJS.enable().then((account) => {
      if(account){
        const iost = IWalletJS.newIOST(IOST)
        
        const tx = iost.callABI(contractAddress, "iControll", [storage_iGet,storage_Name,storage_Feild,storage_value]);
        iost.signAndSend(tx)
        .on('pending', (pending) => {
          console.log(pending, 'pending')
          this.setState({
            isLoading: true,
            txHash: pending,
            result: ''
          })
        })
        .on('success', (result) => {
          console.log(result,'result')
          this.setState({
            isLoading: false,
            result: result.returns[0],
            jiaoyihao:result.returns[0]
          })
        })
        .on('failed', (failed) => {
          console.log(failed, 'failed')
          this.setState({
            isLoading: false,
            jiaoyihao:failed.status_code
          })
        })
      }else{
        console.log('not login')
      }
  })
  setTimeout(() => {
    alert("每个账户可以注册领取一次空投，感谢支持！\n填写昵称可以保护账户隐私，如果未填写，可以返回填写。")
  }, 100);

  }

  iControll_Storage_1=()=>{
    this.comm_callABI(this.contractAddress_1,"IControll","iost","name","10","memo",["不用填写，因为comm_callABI自动识别state"])
  }


</script>
<div className="juzhong4 wenzi16 kuan90 ">
                           
     
    iGet:<input
                className="input1 juzhong3"
                name="storage_iGet"
                onChange={this.handleChange}
                />
    mapName:<input
                className="input1 juzhong3"
                name="storage_Name"
                onChange={this.handleChange}
                />
    map_feild:<input
                className="input1 juzhong3"
                name="storage_Feild"
                onChange={this.handleChange}
                />
    
    map_value:<input
                className="input1 juzhong3"
                name="storage_value"
                onChange={this.handleChange}
                />
    <div className="anniu juzhong3"  onClick={this.iControll_Storage_1}>iDoit</div>



    </div>
```

智能合约   
```javascript
iControll(iTools, tableName, tableField, Value) {
    this._is_Admin();
    if (iTools === "iSetOne") {
        storage.mapPut(tableName, tableField, Value);
        return "iSetOne | " + tableName + "|" + tableField + "|" + Value + "|"
    } else if (iTools === "iGetOne") {
        return storage.mapGet(tableName, tableField)
    } else if (iTools === "iGetLen") {
        return storage.mapLen(tableName)
    } else if (iTools === "iGetAll") {
        return storage.mapKeys(tableName)
    } else if (iTools === "iGetHas") {
        return storage.mapHas(tableName, tableField)
    } else if (iTools === "iDelOne") {
        storage.mapDel(tableName, tableField)
        return "iDelOne | " + tableName + "|" + tableField + "|"
    } else {
        throw "iTools wrong !"
    }
}
```