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
| ruleConfig  | props 规则配置 | {scale: 1, /*px 2 cm*/ frameSelectType:'pointer'/*框选规则*/}|

#### ruleConfig
|  key   | 解释  | 默认值| 可选值|
|  ----  | ----  | ---- | ---- |
| scale  | px转自定义单位比例| 1||
| frameSelectType  | 框选规则 |'fit' |'touch' 'fit'|


#### $refs.sketch提供以下api

|  key   | 解释  | 默认值|
|  ----  | ----  | ---- |
| sketchupData  | 获取画布内数组数据|{}|
| selected  |画布选中项| []||{}|
| selected  |画布选中项| []||{}|

####  $refs.sketch.$fire 方法

|  key   | 解释  | 参数|
|  ----  | ----  | ---- |
| addToSketch  |添加数据到画布| {parent = {}, item, index = -1}|
| cleanSelect  |清空选择| |
| updateSelected  |更新当前选择节点数据 目前只支持更新单个，选中多个无法更新| {...editKey}|
| removeSelected  |移除画布选中项，默认走快捷键|
| initTree  |初始化画布,根节点name值只会是sketchup| 默认值{type:'sketchup',width:300,height:300,children:[]}|
| updateItem  |更新指定item| {id,{...editKey}}|
| select  |选中指定id组件| {event: {ctrlKey: false/*请强制设置为false*/}, id}|
| bringForward  |上移一层| {id}|
| sendBackward  |下移一层| {id}|
| bringToFront  |移动到顶部| {id}|
| sendToBack  |移动到底部| {id}|

#### $refs.sketch.$bind 方法
|  key   | 解释  | 参数|
|  ----  | ----  | ---- |
| selected  |画布选中项| []|
| addend  |每次添加后返回添加id合集| [ids]|


#### 快捷键操作

#### 移动
上下左右方向键移动，最小单位为1 

##### windows
ctrl+c 复制

ctrl+v 粘贴

ctrl+g 编组 默认添加内置组件节点

ctrl+shift+g 取消编组 ，只能打散 内置组件

delete 删除选中

##### macos
command+c 复制

command+v 粘贴

command+g 编组 默认添加内置组件节点

command+shift+g 取消编组 ，只能打散 内置组件

### 支持框选


#### undo redo

```text
1.undo 目前支持 10栈压栈
```




#### todo 
[ ] undo redo
[-] 框选规则交给用户
[ ] Zindex 问题
[-] 拖拽对齐线 
[-] 选中逻辑 压栈问题