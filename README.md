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

browserslist

- `npx browserslist` 查看代码覆盖率

- `package.json key browserslist` or `.browserslistrc`config

```
  "browserslist": "> 1%, last 3 versions"
```


babel reference
* [babel docs](https://www.babeljs.cn/docs/, "文档参照")
* [polyfill & runtime](https://juejin.im/post/5d553706e51d4561e84fcc13, "两种兼容模式对比")
* [webpack babel-loader](https://webpack.js.org/loaders/babel-loader/, "求积若渴就点吧")
* [browserslist](https://github.com/browserslist/browserslist)
* [A page to display compatible browsers from a browserslist string.](https://browserl.ist/)
* [Autoprefixer + Browserslist 浏览器兼容配置](https://zhuanlan.zhihu.com/p/81286302)

## ESLint
install
```
npm install eslint --save-dev

# or

yarn add eslint --dev
```
genarator lint configuration file
```
npx eslint --init
```

eslint-loader
```
{
    test: /\.jsx?$/,
    // exclude: /node_modules/,
    include: /src/,
    use: ['babel-loader', 'eslint-loader']
}
```

configuration
```
module.exports = {
  env: {
    browser: true,
    es6: true,
  },
  extends: [
    'plugin:vue/essential',
    'airbnb-base',
  ],
  globals: {
    Atomics: 'readonly',
    SharedArrayBuffer: 'readonly',
  },
  parserOptions: {
    ecmaVersion: 2018,
    sourceType: 'module',
  },
  plugins: [
    'vue',
  ],
  rules: {
    'no-console': 'off'
  },
}
```

## autoprefixer & postcss
[![npm](https://img.shields.io/npm/v/autoprefixer-stylus.svg?style=flat)](http://badge.fury.io/js/autoprefixer-stylus)
[![tests](https://img.shields.io/travis/jescalan/autoprefixer-stylus/master.svg?style=flat)](https://travis-ci.org/jescalan/autoprefixer-stylus)
[![coverage](https://img.shields.io/coveralls/jescalan/autoprefixer-stylus/master.svg?style=flat)](https://coveralls.io/r/jescalan/autoprefixer-stylus)
[![dependencies](https://img.shields.io/david/jescalan/autoprefixer-stylus.svg?style=flat)](https://david-dm.org/jescalan/autoprefixer-stylus)

install
```
npm install postcss-loader autoprefixer --save-dev
```

configurable
```
// postcss.config.js
module.exports = {
  parser: 'sugarss',
  plugins: {
    'postcss-import': {},
    'postcss-preset-env': {},
    'cssnano': {}
  }
}

// 
```

## template
[meta references](https://www.jianshu.com/p/b5dcc3fc1aed)
[vue-loader references](https://vue-loader.vuejs.org/zh/)
