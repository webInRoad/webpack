## 插件
### 类型
  * html-webpack-plugin(生成html)
    参数
    * template 模板文件的绝对路径
    * filename 生成html文件名称
    * hash 为true时在加载资源时会加上hash值
    * showErrors 是否显示错误
    * minify 压缩配置
      ```
        minify:{
          removeComments: true,//去掉注释
          collapseWhitespace: true//去掉空格，换成一行
        },
      ```
     * chunks 为数组，配置要加载的相应js名称
