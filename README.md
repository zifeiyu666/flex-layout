# flex-layout
About the apply of flex

#### 容器的属性
1. flex-direction
    - row(默认)
    - row-reverse
    - column
    - column-reverse
2. flex-wrap
    - wrap
    - nowrap(默认)
    - wrap-reverse
3. flex-flow
    - 前两个属性的简写形式
    - row nowrap(默认值)
4. justify-content
    - flex-start
    - flex-end
    - center
    - space-between
    - space-around
5. align-items
    - flex-start
    - flex-end
    - center
    - baseline
    - stretch
6. align-content
    - flex-start
    - flex-end
    - center
    - stretch
    - space-between
    - space-around

#### 项目的属性
1. order
    - 0(默认)/1/2...
2. flex-grow
    - 0(默认)/1/2....
3. flex-shrink
    - 1(默认)
    - 0
4. flex-basis
    - auto(m默认)
    - 300px
> 关于flex-basis与width的区别，权重不同，min/max-widht > flex-basis > width
5. flex
    - 前三个属性的简写
    - 0 1 auto(默认)
    - auto (1 1 auto)
    - none (0 0 auto)
6. align-self
    - auto
    - flex-start
    - flex-end
    - center
    - baseline
    - stretch

#### 难以理解的地方
1. flex-basis

之类flex-basis规定了子元素的基准值，如果为auto，则浏览器会按照空间最大利用率来布局：
```
<div class="Grid">
    <div class="Grid-cell">
      文字内容文字内容文字内容文字内容文字内容文字内容
      文字内容文字内容文字内容文字内容文字内容文字内容
      文字内容文字内容文字内容文字内容文字内容文字内容
      文字内容文字内容文字内容文字内容文字内容文字内容
      文字内容文字内容文字内容文字内容文字内容文字内容
    </div>
    <!-- <div class="Grid-cell">
      asdfasd
    </div> -->
    <div class="Grid-cell">
       文字内容文字内容文字内容文字内容文字内容文字内容

    </div>
  </div>
```
```
.Grid {
  display: flex;
}
.Grid-cell {
  flex-grow: 1;
  flex-basis: auto; 
  padding: 10px;
  margin: 10px;
  background-color: #ddd;
}
```

例如上面的例子中，两个Grid-cell并不是等宽的，而是在等高的基础上互相压缩，就像中间加了可以滑动的隔板的一个容器，隔板两边的水不一样多，这时候用力向上挤压，让容器的高度变小，直到不能改变，也就是隔板两边空间都充满了，没有空隙。

```
.Grid {
  display: flex;
}
.Grid-cell {
  flex-grow: 1;
  flex-basis: 0%; 
  padding: 10px;
  margin: 10px;
  background-color: #ddd;
}
```

如果是百分比或者具体的数值，那么Grid-cell都会是等分的，即使某一边在高度上还有空隙，就相当于隔板被固定在中间，不能移动。

---

2. flex各种简写形式
    - flex: auto (flex: 1 1 auto)
    - flex: none (flex: 0 0 auto)
    - flex: 1 (flex: 1 1 0%)
        - 当 flex 取值为一个非负数字，则该数字为 flex-grow 值，flex-shrink 取 1，flex-basis 取 0%
    - flex: 0%/24px (flex: 1 1 0%/24px)
        - 当 flex 取值为一个长度或百分比，则视为 flex-basis 值，flex-grow 取 1，flex-shrink 取 1
    - flex: 2 3 (flex: 2 3 0%)
        - 当 flex 取值为两个非负数字，则分别视为 flex-grow 和 flex-shrink 的值，flex-basis 取 0%
    - flex 2 24px/0% (flex: 2 1 24px/0%) 
        - 当 flex 取值为一个非负数字和一个长度或百分比，则分别视为 flex-grow 和 flex-basis 的值，flex-shrink 取 1


