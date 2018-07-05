# APP内添加新图标  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;在开发的过程中，如果有需求在项目中添加新的图标，需要严格执行以下步骤，否则会出现所有图标与原先不对应，或者显示不出的问题。  
#### 一、步骤：
##### 1.首先保证图标格式是SVG，目前只支持SVG格式。
##### 2.访问地址 https://icomoon.io/app/#/select  ，登录
##### 3.左上角菜单，New Empty Set ，然后会创建出一个 Untitled Set ，import to set 将本地图标拉进去。  
##### 4.全选，点击右下角 generate font，下载到本地。
##### 5. git clone 项目 【ux-cnpm / ux-m-upaas-ui】，安装依赖，不需要启动。
##### 6.将下载的图标中 fonts 文件夹中的四个文件替换到项目 src/styles/fonts 中
##### 7.在项目中 src/styles/base.less 中处理。  
##### 8.处理完成之后，执行 npm run build ，打tag之后提交，修改tita-app项目中的版本号，重新安装图标库的包。
#### 二、 base.less文件处理步骤：
##### 1. 旧图标的区域不能改动！
##### 2. 从新增图标的区域开始处理
##### 3.新增图标以 upass-icon- 命名  
##### 4.特殊处理菜单页日报，项目，计划，从后端传过来的名字：
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;注意：设计给倒的图标带颜色，暂时手动删除带白色的颜色！！！
.sys-icon-jihua,.sys-icon-ribao,.sys-icon-xiangmu
.sys-icon-shenpi, .sys-icon-chaosong, .sys-icon-shenqing
.upaas-icon-search 开头的也不带颜色
#### 三、命名规则
##### 1.统一放在base.less 最下面，覆盖原有的，新图标 font-family: icomoon。
##### 2.注意：需要修改名字的，要单独加font-family以替换，如：font-family: icomoon;
##### 3.新增加的图标，自己约定名字的，统一命名：upaas-icon- 型式。  
#### 四、常见问题
##### 1.图标中设置family后的互相影响：  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;由于设置了匹配 "-icon" 和 "  -icon" 导致匹配到 m-sys-icon中的icon导致不显示  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;解决：以upaas-icon-为命名空间。
##### 2.多层图标有记得用基础组件中的chaos-icon进行引入，因为多级path，需要多个span接收。  
##### 3.有before，但是图标不显示内容，可能是多path图标（可以加display：flex；进行修改）。
##### 4.没有before：可能是不兼容多path！（让设计给单path文件）。
##### 5.图标显示错误，但before和名字都对，font-family 不对。
##### 6.图标显示为空：可能为白色，倒出图标自带白色（让设计倒出不带颜色的图标）。
##### 7.图标显示小方块：fonts文件没有加载，可能是
```
@font-face {
  font-family: 'icomoon';}  不能加 !important，
  ```  
##### 8.
```
@font-face {
  font-family: 'icomoon';
  src:  url('fonts/icomoon.eot');
  src:  url('fonts/icomoon.eot') format('embedded-opentype'),
    url('fonts/icomoon.ttf') format('truetype'),
    url('fonts/icomoon.woff') format('woff'),
    url('fonts/icomoon.svg') format('svg');
  font-weight: normal;
  font-style: normal;
}
```
在h5中不能写两个src，
在h5中注释不能使用// 。




