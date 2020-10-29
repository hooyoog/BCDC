# 关于gitbook的使用   
有了良好的文档，可以帮助大家提高学习与开发的效率   

### 安装开发文档工具，让自己开发的项目有完整的API文档和学习建议   
**1. npm install gitbook-cli -g**  
**2. gitbook -V**  
**3. 把npm的各层级模块文件夹从.gitignore中忽略掉**
```
//例如
node_modules/
*node_modules/
**node_modules/
dist/
*dist/
**dist/
```  
**4. 新建项目文件夹，例如/10_IOST_NoIWallet_HowToSend**  
**5. cd 10_IOST_NoIWallet_HowToSend**  
**6. 初始化文档 gitbook init**  
**7. gitbook serve 后就能在浏览器里看到文档了**  
**8. gitbook build 构建文档，就输出了html文档文件**  
**9. SUMMARY.md是目录文件，其他内容页面用.md文件关联好，就可以写开发文档和API文档了**   
![baidu](http://www.baidu.com/img/bdlogo.gif "百度logo")   