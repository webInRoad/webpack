## webpack
### 简介
`webpack`就是一个模块化打包工具，相当于将之前用seajs、commonjs实现的模块化用webpack来进行实现，它是以js文件为入口，然后通过`require`或`import`去加载相应的静态资源(`css`、`png`),在加载过程中如果发现扩展语言(`sass`、`less`)或下一代`js`语言(`TypeScript`、`es6`)则用`loader`(加载器)将其转换和打包为合适的格式供浏览器使用,以及用`plugins`(插件)进行一些扩展功能，比如自动生成`html`(`html-webpack-plugin`)
