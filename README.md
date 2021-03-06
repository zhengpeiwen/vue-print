# vue页面打印
## 概述
    在vue框架中实现打印功能，记录一下方便以后使用。
## 基本使用方法

```javascript
import Print from  './print.js' ;  // 引入插件  
Vue.use(Print); // 注册
```


```html
<button @click="print">打印</button>
<div ref="print">
        打印区域 
</div>
  
```

```javascript
print(){
   this.$print(this.$refs.print);
}
```

## 设置不打印区域

![alt 属性文本](./image/6.png)

```html
<div class="no-print">
        不打印区域
</div>
```

如果你想要打印的区域中有部分内容是不需要打印的，那么直接在class加上一个no-print就行了，
no-print这个类名是可以自定义的。
如果想把类名改为no-print-me

```html
<div class="no-print-me">
        不打印区域
</div>
```

那么在调用打印页时就需要多传一个对象

```javascript
  this.$print(this.$refs.print,{'no-print':'no-print-me'});

```

## 打印前后调用方法
在这里我讲打印前和打印后的对象也当参数传入
中间的空对象{}是自定不打印区域的对象，如果不需要自定义直接空对象

```javascript
berforeFun(){
   alert("打印前")
},
afterFun(){
   alert("打印后")
},
print(){
   this.$print(this.$refs.print,{},this.berforeFun,this.afterFun);
}
```

## 分页打印
#### 添加一个样式打印表格行不分裂

```css
tr{
page-break-inside:avoid;
}
```

![alt 属性文本](./image/1.png)

![alt 属性文本](./image/4.png)

#### 添加一个样式打印表格不分页，数据如果超过一页的就只能分页了

```css
table{
page-break-inside:avoid;
}
```
![alt 属性文本](./image/2.png)

![alt 属性文本](./image/3.png)


### page-break-inside


属性用于设置是否在指定元素中插入分页符。
| 值 | 描述 |
|------ | ------|
auto | 默认。如果必要则在元素内部插入分页符。 |
avoid | 避免在元素内部插入分页符。 |
inherit | 规定应该从父元素继承 page-break-inside 属性的设置。 |

#### 添加样式打印表格分页

```css
style=“page-break-before:always”
```

```css
style=“page-break-after:always”
```

![alt 属性文本](./image/5.png)

### page-break-before


属性用于设置是否在指定元素前插入分页符。
| 值 | 描述 |
|------ | ------|
auto | 默认。如果必要则在元素前插入分页符。 |
always |在元素前插入分页符。 |
avoid | 避免在元素前插入分页符。 |
left |在元素之前足够的分页符， 直到指定的组件出现在一个左边的空白页上。 |
right | 在元素之前足够的分页符，直到指定的组件出现在一个右边的空白页上。 |
inherit | 规定应该从父元素继承 page-break-before 属性的设置。 |


### page-break-after


属性用于设置是否在指定元素后插入分页符。
| 值 | 描述 |
|------ | ------|
auto | 默认。如果必要则在元素后插入分页符。 |
always |在元素后插入分页符。 |
avoid | 避免在元素后插入分页符。 |
left | 在元素之后足够的分页符，直到指定的组件出现在一个左边的空白页上。 |
right | 在元素之后足够的分页符，直到指定的组件出现在一个右边的空白页上。 |
inherit | 规定应该从父元素继承 page-break-after 属性的设置。 |





