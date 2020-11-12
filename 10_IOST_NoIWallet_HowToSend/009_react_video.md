# 为react中加入视频

#### 方案 

##### 1 使用bilibili开发的flv.js   

```
cnpm install --save flv.js   
```   

这是VideoPlayer
```javascript
bofang(){
    if (flvjs.isSupported()) {
      var videoElement = document.getElementById('videoElement');
      var flvPlayer = flvjs.createPlayer({
          enableStashBuffer:true,
          type: 'flv',
          isLive: true,//<====加个这个,
          url: 'http://honey.pet:8009/live/Undead.flv?sign=1668700800-31c549aed3ddafa27a9212b49f524146'
      });
      flvPlayer.attachMediaElement(videoElement);
      flvPlayer.load();
      flvPlayer.play();
    }
}

```   
```javascript
componentDidMount() {
   
    this.bofang()
}
```    
```javascript
<button
onClick={this.bofang}
>点击播放</button>
<video  id="videoElement"></video>
```

