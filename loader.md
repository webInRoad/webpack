## loader(加载器)
> loader 用于对模块的源代码进行转换。loader 可以使你在 import 或"加载"模块时预处理文件。因此，loader 类似于其他构建工具中“任务(task)”，并提供了处理前端构建步骤的强大方法。loader 可以将文件从不同的语言（如 TypeScript）转换为 JavaScript，或将内联图像转换为 data URL。loader 甚至允许你直接在 JavaScript 模块中 import CSS文件！
### 语法
  ```
    module.exports = {
      module: {
        rules: [{
          test: /\.css$/,
          exclude: /node_modules|bootstrap/,
          // loader: 'style!css?minimize&-autoprefixer!postcss',//使用 ! 将资源中的 loader 分开,选项可以传递查询参数,通过?
          use: [
            {
              loader: 'style-loader'
            },
            {
              loader: 'css-loader'
              // options: {
              //   minimize: true,
              //   '-autoprefixer': true,
              // },
            },
            // {
            //   loader: 'postcss-loader',
            // },
          ],
        }
        ]
      }
    };
  ```
