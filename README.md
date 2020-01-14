# vue-ci
that vue framework project, includes vuex router lodash so on, it's can be custom assemble

## babel
install babel tools
```
npm install --save-dev @babel/core @babel/cli @babel/preset-env
npm install --save @babel/polyfill
```
config babel


compare with babel config several kinds programme

| 方案 | 优点  | 缺点 |
| :------------ |:---------------:| -----:|
| @babel/runtime & @babel/plugin-transform-runtime | 按需引入, 打包体积小 | 不能兼容实例方法 |
| @babel/polyfill | 完整模拟 ES2015+ 环境 | 打包体积过大, 污染全局对象和内置的对象原型 |
| @babel/preset-env | 按需引入, 可配置性高 | -- |

