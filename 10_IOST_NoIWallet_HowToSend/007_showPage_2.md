# 解析

获得区块链上的数据，通常是JSON序列化后的字符串，最要命的是会有"\\\"   
把"\\\"去掉   
```javascript
let tempData = JSON.parse(xhrRes).data
                for(var i=0;i<tempData.length;i++){
                  tempData=tempData.replace("\\","")
}
```
变成没有斜杠的字符串存入this.state.new_rom_All，使用时转为JSON

```javascript
let temp_New_Room_All = this.state.new_rom_All

this.setState({temp_room:tempData})


let tempObj = JSON.parse(this.state.temp_room)
temp_New_Room_All.push(tempObj)
this.setState({new_rom_All:temp_New_Room_All})
```