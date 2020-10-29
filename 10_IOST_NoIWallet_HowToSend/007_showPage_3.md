# 在REACT中排版

数据参考：
```javascript
{\"announcer_ID\":\"ZLrbXAeUteQG1601161084500113200\",\"pet_name\":\"加密酱\",\"announcer_name\":\"甜蜜直播\",\"vote\":1,\"url\":\"/chat/list/player.jsp?name=jiamijiang\",\"content\":\"魔兽、DOTA2、LOL！\",\"icon\":\"/images/new_room/new_room_003.png\"}
```
react排版   
```html

<div className="juzhong4 kuan90p ">
  <div className="kuan50p floatLeft gao155PP  beijing_14_lock" onClick={this.announcer_Register}>
    <div className="zhibozhong3" >点击申请</div>
  </div>
  {//this.inputPile
    
  this.state.new_rom_All.map( (item)=> {
  return (
      <div key={item.icon.substring(27,29)} className={"kuan50p floatLeft gao155PP  beijing_14_"+item.icon.substring(28,29)}>
        
        <div className="zhibozhong3">票 : {item.vote}</div>
      <div className="zhibozhong3"><a href={item.url}>{item.announcer_name}</a></div>
      
        <div className=" paddingTop10">
          {item.vote<=10?<div className="toupiao3" onClick={(id,num)=>this.vote_For_Announcer(item.announcer_ID,item.icon.substring(27,29),id,num)}></div>:
          <a href={item.url}><div className="kaitong" ></div></a>
          }
        
          </div>
        <div className="kuan90 zhibozhong3 juzhong4"> {item.content}</div>
      </div>
  )
  })
}

</div>



```

#### 其中此语句   
```
this.state.new_rom_All.map( (item)=> {
  return ()
```
#### ()中的内容，会根据数组个数，循环排版