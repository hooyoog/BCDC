# 查询、解析、排版


#### 1 函数实现    
必须使用箭头函数，如果使用function的在react中无效
```javascript
vote_For_Announcer= (ID,num) => {
    const contractAddress = 'Contract9m7S1Y66YL2XqXvh1VxrL7X8cdh19MKkMknGKXWPFZhk'
    //const { announcer_ID } = this.state

    
      IWalletJS.enable().then((account) => {
        if(account){
          const iost = IWalletJS.newIOST(IOST)
          
          const tx = iost.callABI(contractAddress, "vote_For_Announcer", [ID,num]);
          tx.addApprove('pet', "10");
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
  }
```
