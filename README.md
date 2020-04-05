# vue页面打印
## 概述
使用vue实现打印功能也是开发中经常使用的，根据我在github中看到的插件自己修改整理了一下，本人才疏学浅，如有错误之处，还请见谅。
## 使用方法
### 引入注册插件

```
import Print from  './print.js' ;  
Vue.use(Print);
```

### 指定打印区域

```
      <button @click="print">打印</button>
<div ref="print">
        打印区域 
  </div>
  
```

### 调用打印方法

```
 print(){
          this.$print(this.$refs.print);
        }
```

## 设置不打印区域

![alt 属性文本]('../image/6.png')

```
      <div class="no-print">
        不打印区域
      </div>
```

如果你想要打印的区域中有部分内容是不需要打印的，那么直接在class加上一个no-print就行了，
no-print这个类名是可以自定义的。
我如果想把类名改为no-print-me

```
      <div class="no-print-me">
        不打印区域
      </div>
```

那么在调用打印页面时就需要传一个对象告诉程序我把no-print类名改了

```
          this.$print(this.$refs.print,{'no-print':'no-print-me'});

```

## 打印前和打印后调用方法
中间的空对象{}是自定不打印区域的对象

```
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

## 表格打印分页

![alt 属性文本]('../image/1.png')

```
tr{
page-break-inside:avoid;
}
```

![alt 属性文本]('../image/4.png')

![alt 属性文本]('../image/2.png')

```
table{
page-break-inside:avoid;
}
```

![alt 属性文本]('../image/3.png')

```
page-break-inside
```

属性用于设置是否在指定元素中插入分页符。
| 值 | 描述 |
|------ | ------|
auto | 默认。如果必要则在元素内部插入分页符。 |
avoid | 避免在元素内部插入分页符。 |
inherit | 规定应该从父元素继承 page-break-inside 属性的设置。 |

![alt 属性文本]('../image/5.png')

```
style=“page-break-before:always”
```

```
style=“page-break-after:always”
```

```
page-break-before
```

属性用于设置是否在指定元素前插入分页符。
| 值 | 描述 |
|------ | ------|
auto | 默认。如果必要则在元素前插入分页符。 |
always |在元素前插入分页符。 |
avoid | 避免在元素前插入分页符。 |
left |在元素之前足够的分页符， 直到指定的组件出现在一个左边的空白页上。 |
right | 在元素之前足够的分页符，直到指定的组件出现在一个右边的空白页上。 |
inherit | 规定应该从父元素继承 page-break-before 属性的设置。 |

```
page-break-after
```

属性用于设置是否在指定元素后插入分页符。
| 值 | 描述 |
|------ | ------|
auto | 默认。如果必要则在元素后插入分页符。 |
always |在元素后插入分页符。 |
avoid | 避免在元素后插入分页符。 |
left | 在元素之后足够的分页符，直到指定的组件出现在一个左边的空白页上。 |
right | 在元素之后足够的分页符，直到指定的组件出现在一个右边的空白页上。 |
inherit | 规定应该从父元素继承 page-break-after 属性的设置。 |





