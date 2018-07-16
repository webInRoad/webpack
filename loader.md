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
 ### 类型
  * 在js中采用import方式引入css文件，需要用css-loader、style-loader加载器解析
  * 对于sass文件，需要安装node-sass sass-loader
  ```
    {
    test: /\.(sass|scss)$/,
    //loader: 'style-loader!css-loader!sass-loader'',
    use: [
      {
        loader: 'style-loader',
      },
      {
        loader: 'css-loader',
        // options: {
        //   minimize: true,
        //   '-autoprefixer': true,
        // },
      },
      // {
      //   loader: 'postcss-loader',
      // },
      {
        loader: 'sass-loader',
      },
    ]
  }
  ```
  *　对于less文件，需要安装less less-loader
  *  对于下一代js(比如es6、TypeScript)则需要babel加载器
    安装 `npm install --save-dev babel-core babel-loader babel-preset-env babel-preset-react`
    {
      test: /\.(js|jsx)$/,
      include:dirVars.staticRootDir+'/js/modules',
      loader: 'babel-loader',
      options:{
        presets:[
          "env"
        ]
      }
    }
    当然也可以创建个.babel文件
  * 对于background中引用图片，或者html中img嵌入图片，则需要用到url-loader
  ```
    {
      // 图片加载器，雷同file-loader，更适合图片，可以将较小的图片转成base64，减少http请求
      // 如下配置，将小于10kb的图片转成base64码
      test: /\.(png|jpg|gif)$/,
      // include: dirVars.srcRootDir,
      use: [{
            //加载url-loader 同时安装 file-loader;
            loader: 'url-loader',
             // include:  __dirname+'/js/modules',
            options: {
              //小于10240K的图片文件转base64到css里,当然css文件体积更大;
              limit: 10240,
              //设置最终img路径;
              name: 'cssAndImg/img/[name]-[hash:8].[ext]',
              publicPath:"../../../"
            }
          },
          {
            //压缩图片(另一个压缩图片：image-webpack-loader);
            loader: 'img-loader?minimize&optimizationLevel=5&progressive=true'
          },
    ]}
  ```
  * 图标加载需要用file-loader
  ```
     {
      // 专供iconfont方案使用的，后面会带一串时间戳，需要特别匹配到
      test: /\.(woff|woff2|svg|eot|ttf)\??.*$/,
      // exclude: /glyphicons/,
      // loader: 'file-loader?name=static/fonts/[name].[ext]',
      loader: 'file-loader',
      options: {
        name: './fonts/[name].[hash].[ext]',
      },
    }
  ```
