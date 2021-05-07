### 基础搭建 画布组件 vue 2.6

### 安装
```
npm i -S pd-drag-base

yarn add -S pd-drag-base

```


### 引入

```javascript
//main.js
import pdDragBase from 'pd-drag-base'
import 'pd-drag-base/dist/pdDragBase.css'
Vue.use(pdDragBase)
//自动注入全局组件


```

### 开发
```xml
<pdDragBase ref="sketch">
<!--自定义画布插槽-->
</pdDragBase>
```
### 容器组件
内置容器组件 组件名 `dragdropbox` ,只有这个组件才能 编组，和打散

### 数据格式
```javascript
var itemtemplate = {
              "left": 148,//相对父级坐标
              "top": 63,//相对坐标
              "rotate": 0,//旋转角度
              "width": 31,//宽
              "height": 38,//高
              "active": false,//是否激活
              "childActiveAble": false,//子集能否激活，用于 内置组件dragdropbox
              "type": "dtext",//全局用户组件
              "children": [],//子集
              "id": "",//全局唯一id
              "parentId": ""//父级id 顶部根节点为null
}
```


### attrs

|  key   | 解释  | 默认值|
|  ----  | ----  | ---- |
| beforeCopy  | event 拷贝前置函数|空|
| beforeDelete  | event 删除确定函数 |空|
| ruleConfig  | props 规则配置 | {scale: 1, /*px 2 cm*/ frameSelectType:'pointer',/*框选规则*/ hotKey:false, /*是否开启快捷键*/ stackLength:10 /*压栈长度*/}|

#### ruleConfig
|  key   | 解释  | 默认值| 可选值|
|  ----  | ----  | ---- | ---- |
| scale  | px转自定义单位比例| 1||
| frameSelectType  | 框选规则 |'fit' |'touch' 'fit'|
| hotKey  | 是否开启快捷键 |false | Boolean|
| stackLength  | 压栈长度(建议在20栈内) |10 | Number|


#### $refs.sketch提供以下api

|  key   | 解释  | 默认值| 可选参数|
|  ----  | ----  | ---- |----|
| select  |选中指定id组件| {id}|{}|
| move  |移动选中组件| {direction} |'up','right','down','left'|
| copy  |复制选中组件| -- |--|
| paste  |粘贴中组件| -- |--|
| undo  |撤销| -- |--|
| group  |选中组件编组| -- |--|
| breakGroup  |打散编组(只打散内置组件`dragdropbox`)| -- |--|
| deleteSelect  |删除选中项| -- |--|
| zIndex  |指定id组件z轴调整| ｛type,id｝ |type可选参数：'bringForward','sendBackward','bringToFront','sendToBack'|
| cleanSelect  |清空选择| |
| initTree  |初始化画布,根节点name值只会是sketchup| --|{data, snapShot = true}|
| updateItem  |更新指定item| {id, data, snapShot = true}|
| addToSketch  |添加到画布| {parent = null, item = [], snapShot = true}|

#### $refs.sketch 数据
|  key   | 解释  | 
|  ----  | ----  |
| sketchupData  | 获取画布内数组数据|
| selected  |画布选中项| 

#### $refs.sketch.$bind 方法
|  key   | 解释  | 参数|
|  ----  | ----  | ---- |
| selected  |画布选中项| []|
| addend  |每次添加后返回添加id合集| [ids]|
