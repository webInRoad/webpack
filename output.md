## output
  配置 output 选项可以控制 webpack 如何向硬盘写入编译文件。注意，即使可以存在多个入口起点，但只指定一个输出配置
### 语法
  output属性设置为一个对象，包括以下两点
  * filename 用于输出文件的文件名。
  * path 出口文件的绝对定位
  * publicPath 文件中访问静态资源的路径,像script中的src的前缀
 
 ```
 {
  entry: {
    app: './src/app.js',
    search: './src/search.js'
  },
  output: {
    filename: '[name].js',//[name]表示entry每一项中的key，用以批量指定生成后文件的名称
    path: __dirname + '/dist',//绝对路径
    publicPath:'../../',
  }
}

 ```
    
  
