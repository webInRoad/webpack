## entry(入口)
### 语法
* 单个入口(简写)语法 

  用法：`entry: string|Array<string>`
  * 字符串
  ```
  const config = {
    entry: './path/to/my/entry/file.js'
  };
  ```
  * 数组
  ```
  const config = {
    entry: ['./path/to/my/entry/file.js','./path/to/my/entry/file2.js']
  };
  ```
 
 > 向 entry 属性传入「文件路径(file path)数组」将创建“多个主入口(multi-main entry)”。在你想要多个依赖文件一起注入，并且将它们的依赖导向(graph)到一个“chunk”时，传入数组的方式就很有用。
 
 这种方式当用于单页面应用时较有用，因为只有一个出口文件，但同时有失灵活性，因为没有KEY(用于与output相对应)
 
 * 对象语法
 
  用法:`entry: {[entryChunkName: string]: string|Array<string>}`
  
  ```
  const config = {
    entry: {
      pageOne: './src/pageOne/index.js',
      pageTwo: './src/pageTwo/index.js',
      pageThree: './src/pageThree/index.js'
    }
  };
  ```
  这种方式用于多页面应用，比较灵活
