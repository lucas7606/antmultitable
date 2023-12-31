<!--
 * @Author: lucas 13811537606@163.com
 * @Date: 2019-01-09 20:10:11
 * @LastEditors: lucas 13811537606@163.com
 * @LastEditTime: 2023-12-08 15:49:37
 * @FilePath: /antmultitable/README.md
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->
# Vue preview plugin

> 一个Vue集成[PhotoSwipe](https://github.com/dimsemenov/PhotoSwipe)图片预览插件

> 此插件并没有提供新的功能, 只是在原vue-preview插件基础之上简化了操作, 无需使用`vue-preview`组件, 直接使用`img`标签绑定点击事件即可

![](https://img.shields.io/npm/dm/antmultitable.svg)
![](https://img.shields.io/npm/v/antmultitable.svg)

## Requirements

[PhotoSwipe](https://github.com/dimsemenov/PhotoSwipe)

## Based on

[vue-preview](https://github.com/LS1231/vue-preview)

## Installation

``` bash
npm i antmultitable -S
```

## Usage

使用须知：

* 插件目前仅支持vue2.0以上版本
* img标签上的class不能去掉

如果你是使用vue-cli生成的项目，可能需要你修改`webpack.base.conf.js`文件中的loaders，添加一个loader。
原因：插件编写中使用了es6的语法，需要进行代码编译
``` javascript
{
    test: /vue-preview.src.*?js$/,
    loader: 'babel'
}
```

### Install plugin

``` javascript
import AntMultiTable from 'antmultitable'
Vue.use(AntMultiTable)
```

### Examples

```
<template>
  <img class="preview-img" v-for="(item, index) in list" :src="item.src" height="100" @click="$preview.open(index, list)">
</template>

<script>
export default {
    data () {
      return {
        list: [{
          src: 'https://placekitten.com/600/400',
          w: 600,
          h: 400
        }, {
          src: 'https://placekitten.com/1200/900',
          w: 1200,
          h: 900
        }]
      }
    }
  }
</script>
```

### Mothods

插件提供以下两个方法,```vm```代表组件实例

#### vm.$preview.open(index, list, options)

参数说明：

| 参数  | 说明  |  类型  |  必需
| :--: | :--: | :--:  | :--:
| index     |当前图片的索引值|   Number |    是
| list      |图片列表       |   Array  |    是
| options   |预览插件的配置选项（[参考PhotoSwipe配置](http://photoswipe.com/documentation/options.html)）  |  Object  |    否

#### vm.$preview.close()


## License

![](https://img.shields.io/badge/license-MIT-blue.svg)
