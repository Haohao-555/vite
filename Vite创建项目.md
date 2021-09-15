## 一、 Vite 创建 Vue3 项目   
* 打开 cmd 运行 **npm init @vitejs/app**  
![](https://img-blog.csdnimg.cn/img_convert/8a2b7e150f1414fb0a377523388cf018.png)
![](https://img-blog.csdnimg.cn/img_convert/8a2b7e150f1414fb0a377523388cf018.png)
* 项目目录文件及其分类
![](https://img-blog.csdnimg.cn/img_convert/6c67f616be21bed46aadbccf756a4cb1.png)
* package.json 文件内容
![](https://img-blog.csdnimg.cn/img_convert/16cef065b305afa8ebc523c190f66032.png)

> 在 Vite 中是不支持 eslink 语法校验的，需要自己配置。

* **npm run dev** 启动项目 此时就已经通过Vite2.0来曾经项目成功。


补充：项目中三个文件（index.html、main.js、App.vue）的关系
![](https://img-blog.csdnimg.cn/img_convert/4763e9cb04bfe13574f435eab76efcf8.png)

> 因此在 Vite2 搭建的项目中，index.html 是必须存在的，不能删除。

---
接下来，在 vue3 中是支持 Jsx 开发模式的，而在上面的配置中是不支持 Jsx 的开发模式
![](https://img-blog.csdnimg.cn/img_convert/05fed78f7d013d4621376894dec24101.png)
因此我们是需要自己手动去下载Vite 的插件及配置！！！！

> 这里补充一点：在下载 Vite 的插件时官方建议是使用 yarn 来下载不会造成不必要的麻烦。
> 如何安装 yarn 呢 ？？？
> 很简单，打开 cmd 输入命令全局安装 yarn：**npm i -g yarn**

一切准备完成后，进入到项目根目录，
* 下载插件 @vitejs/plugin-vue-jsx

> yarn add @vitejs/plugin-vue-jsx -D

   此时可能会报一个错误  
 ![](https://img-blog.csdnimg.cn/img_convert/45c016fbba40acaa779697bf3d7b7d85.png)
[ 解决方法](https://blog.csdn.net/qq_30376375/article/details/116139870) 亲测有效

* 配置 vite.config.js

```javascript
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'
import vueJsx from "@vitejs/plugin-vue-jsx"

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [vue(), vueJsx()]
})
```
*  修改项目目录及相关文件
删除 App.vue 文件，并且在App.vue 的目录下创建 App.jsx 文件，修改main.js 中的 App的引入路径，将 App.jsx 引入即可。
* 此时项目就已经配置完成

可以将下面的内容添加到 App.jsx 中，并且启动项目（npm run dev）

```javascript
import { defineComponent } from "vue";

export default defineComponent({
    setup() {
        return () => {
            return <div>Hello Vue3 Jsx</div>
        };
    },
});
```

## 二、 Vite 创建 Vue2 项目   

> 补充：Vite2 没有官方插件来直接支持 Vue2，而 Vue3 是有官方提供的插件来进行安装的如第一点。 我们需要自己手动配置

我们可以下载插件：vite-plugin-vue2 来使 Vue2 可以使用 Vite
[官方链接](https://vitejs.dev/guide/features.html#vue)

![](https://img-blog.csdnimg.cn/img_convert/0af54cc134ad5fa83052efae375e2a15.png)
* 创建项目  **npm init @vitejs/app** 

> 之前，我们创建Vue 项目时是使用 Vue-cli 脚手架来创建项目的，此时我们不能使用这种方式。


选择创建的项目类型时不能选择 Vue， 此时的 Vue 是版本3，并不是版本2
![](https://img-blog.csdnimg.cn/img_convert/d48363cc2e452ce8ed2c21d6df90f35b.png)
应该选择 vanilla （没有任何第三方框架）
![](https://img-blog.csdnimg.cn/img_convert/79dba73e1687f07373ea4054619dde3f.png)
* 下载 vue 插件

> yarn add vue -S

* 下载 vite-plugin-vue2 

> yarn add vite-plugin-vue2 -D

* 配置 vite.vonfig.js
```javascript
import { creatVuePlugin } from "vite-plugin-vue2"
export default {
    plugins: [creatVuePlugin()],
}
```
接下就修改项目目录，使其跟 Vue-cli 创建的项目目录一致

![](https://img-blog.csdnimg.cn/img_convert/5cc1a7a29e40cf3b9586b2fa8121c81b.png)
修改 index.html

```html
<script type="module" src="./src/main.js"></script>
```
添加 App.vue

```html
<template>
    <div>
        hello vue2
    </div>
</template>
```

修改 main.html

```javascript
import Vue from 'vue'
import App from './App.vue'

new Vue({
  el: "#app",
  render: (h) => h(App),
}).$mount();
```

##  三、 Vite 创建 React 项目
这个就简单多了，一句命令解决！！


> npm init @vitejs/app

npm run dev 启动项目，完成！！！！