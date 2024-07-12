1.css 样式优先级？

- !important > 行内样式>ID 选择器 > 类选择器 > 标签 > 通配符 > 继承 > 浏览器默认属性.

##### 2.css隐藏元素的方式？

在CSS中，隐藏元素可以通过多种方式实现，以下是一些常用的方法：

使用 `display: none;`：元素会被完全移除，不再占据空间，也不可交互。

```css
.hidden-element {  display: none;}
```

使用 `visibility: hidden;`：元素不可见，但仍然占据原来的空间，不可交互。

```css
.invisible-element {  visibility: hidden;}
```

使用 `opacity: 0;`：元素不可见，但仍然占据空间，视情况可能可交互。

```css
.transparent-element {  opacity: 0;}
```

使用 `position: absolute;` 配合负的 `left` 或 `top` 属性：元素会被移出视口，不可见，不占据空间，不可交互。

```css
.offscreen-element {  position: absolute;  left: -9999px;}
```

使用 `width: 0; height: 0; overflow: hidden;`：将元素大小设置为0，使其不可见，但仍然占据空间，不可交互。

```css
.hidden-element {  width: 0;  height: 0;  overflow: hidden;}
```

使用 `pointer-events: none;`：使元素不可点击，但仍然可见。

```css
.unclickable-element {  pointer-events: none;}
```

选择哪种方式取决于你的具体需求，比如是否需要保留布局空间、是否需要保留交互性等。
