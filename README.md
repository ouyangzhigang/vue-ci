# vue-ci
that vue framework project, includes vuex router lodash so on, it's can be custom assemble

## babel
install babel tools
```
npm install --save-dev @babel/core @babel/cli @babel/preset-env
// npm install --save @babel/polyfill
npm install --save-dev @babel/plugin-transform-runtime
npm install --save @babel/runtime
```

config babel
```
const presets = [
    [
      '@babel/env',
      {
        targets: {
            chrome: '58',
            safari: '8',
            ie: '9'
        },
        useBuiltIns: 'usage',
      },
    ],
  ];

const plugins = [
    [
        '@babel/plugin-transform-runtime',
        {
            // polyfill: true, // 默认就是开启的, This option was removed in v7 by just making it the default.
            regenerator: true
        }
    ]
]
  
module.exports = { presets, plugins }
```


compare with babel config several kinds programme

| 方案 | 优点  | 缺点 |
| :------------ |:---------------:| :-----:|
| @babel/runtime & @babel/plugin-transform-runtime | 按需引入, 打包体积小 | 不能根据版本加载相关插件支持编译 |
| @babel/polyfill | 完整模拟 ES2015+ 环境 | 打包体积过大, 污染全局对象和内置的对象原型 |
| @babel/preset-env | 按需引入babel插件, 可配置性高 | 能根据不同版本按需求加载相关插件编译, 但无法兼容实例方法 |
| @babel/preset-env & @babel/runtime & @babel/plugin-transform-runtime | 设置useBuiltIn: 'usage'按需引入, 可配置性高, 代码重用率高 | -- |


babel reference

[polyfill 与 runtime](https://juejin.im/post/5d553706e51d4561e84fcc13, "求知若渴")

