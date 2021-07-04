###### 从网上搜索到需要在项目的根目录创建一个`jsconfig.json`的配置文件
```
{
    "compilerOptions": {
      "baseUrl": ".",
      "paths": {
        "@/*": ["src/*"]
      },
      "target": "ES6",
      "module": "commonjs",
      "allowSyntheticDefaultImports": true
    },
    "include": ["src/**/*"],
    "exclude": ["node_modules"]
  }
```

#### 我的项目是vite创建的vue3+ts项目, 发现根目录本身存在一个`tsconfig.json`的配置文件
```
{
  "compilerOptions": {
    "target": "esnext",
    "module": "esnext",
    "moduleResolution": "node",
    "strict": true,
    "jsx": "preserve",
    "sourceMap": true,
    "resolveJsonModule": true,
    "esModuleInterop": true,
    "lib": ["esnext", "dom"]
  },
  "include": ["src/**/*.ts", "src/**/*.d.ts", "src/**/*.tsx", "src/**/*.vue"]
}

```
#### vscode里面使用的新一代Volar插件, 对比二个配置文件,是缺少某些配置项导致@不提示, 于是把jsconfig.json的一些配置搬运过去
```
"baseUrl": ".",
"paths": {
    "@/*": ["src/*"]
},
```
### 添加完毕后重启VScode, @提示路径开始生效了, 以下是tsconfig.json完整的配置文件路径
```
{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@/*": ["src/*"]
    },
    "target": "esnext",
    "module": "esnext",
    "moduleResolution": "node",
    "strict": true,
    "jsx": "preserve",
    "sourceMap": true,
    "resolveJsonModule": true,
    "esModuleInterop": true,
    "lib": ["esnext", "dom"]
  },
  "include": ["src/**/*.ts", "src/**/*.d.ts", "src/**/*.tsx", "src/**/*.vue"]
}
```