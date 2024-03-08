---
title: CSS Position
date: 2024-02-16 16:25:08
tags: [css, position]
---

## Position property
- `static` (default)
- `relative`
- `fixed`
- `absolute`
- `sticky`

## 1. 静态定位 <a href="https://www.w3schools.com/css/css_positioning.asp">`position: static`</a>
HTML elements are positioned static by default.
Static positioned elements are not affected by the `top`, `bottom`, `left`, and `right` properties.
An element with `position: static`; is not positioned in any special way; it is always positioned according to the normal flow of the page.

## 2. 相对定位 <a href="https://www.bilibili.com/video/BV1p84y1P7Z5?p=139">`position: relative`</a>
- 可以使用`left`, `right`, `top`, `bottom`四个属性调整位置。
    - 距离`left`, `right`, `top`, `bottom`有多远。
    - e.x.
        1. `left: 100px`：距离左边`100px`
        1. `right: 100px`：距离右边`100px`
        1. `top: 100px`：距离上边`100px`
        1. `bottom: 100px`：距离下边`100px`
- 参考点：相对自己**原来的位置**
- 特点
    1. 不脱离文档流
    2. 定位元素的显示**层级**比普通元素高，无论什么定位，显示层级都是一样的。
        默认规则是：
        - 定位的元素会覆盖在普通元素之上。
        - 都发生定位的两个元素，后写的元素会盖在先写的元素之上
    3. `left`不能和`right`一起设置，`top`不能和`bottom`一起设置.
    4. 相对定位的元素，也能继续浮动，但不推荐这样做。
    5. 相对行为的元素，也能通过`margin`调整位置，但不推荐这么做
    > 绝大多数情况下，相对定位，会与绝对定位配合使用。
- E.X.
    ```
    .box2 {
        ...
        position: relative; // 开启相对定位
        left: 100px;        // 距离左边100像素
        ...
    }
    ```

## 3. 绝对定位 <a href="https://www.bilibili.com/video/BV1p84y1P7Z5?p=140">`position: absolute`</a>
- 可以使用`left`, `right`, `top`, `bottom`四个属性调整位置。
- 参考点：相对自己**包含块**
    > 包含块：
    > 1. 没有脱离文档流的元素，包含块就是父元素。
    > 2. 脱离文档流的元素，包含块是第一个开启定位的祖先元素。
- 特点
    1. **脱离文档流**
    2. 定位元素的显示**层级**比普通元素高，无论什么定位，显示层级都是一样的。
        默认规则是：
        - 定位的元素会覆盖在普通元素之上。
        - 都发生定位的两个元素，后写的元素会盖在先写的元素之上
    3. `left`不能和`right`一起设置，`top`不能和`bottom`一起设置.
    4. 绝对定位和浮动不能同时设置，如果同时设置，浮动失效，以定位为主。
    5. 绝对行为的元素，也能通过`margin`调整位置，但不推荐这么做。
    > 定位元素：
    > 默认宽高被内容所撑开，且能自由设置宽高。
- E.X.
    ```
    .box2 {
        ...
        position: absolute; // 开启相对定位
        left: 100px;        // 距离左边100像素
        ...
    }
    ```

## 4. 固定定位 <a href="https://www.bilibili.com/video/BV1p84y1P7Z5?p=141">`position: fixed`</a>
- 可以使用`left`, `right`, `top`, `bottom`四个属性调整位置。
- 参考点：相对当前**视口**
    > 视口：
    > 1. 对于PC浏览器来说，视口就是我们看网页的那扇“窗户”。
- 特点
    1. **脱离文档流**
    3. `left`不能和`right`一起设置，`top`不能和`bottom`一起设置.
    4. 固定定位和浮动不能同时设置，如果同时设置，浮动失效，以定位为主。
    5. 固定行为的元素，也能通过`margin`调整位置，但不推荐这么做。
    5. 无论是什么元素（行内、行内块、块级）设置为固定定位之后，都变成了定位元素。
    > 定位元素：
    > - 默认宽高被内容所撑开，且能自由设置宽高。
- E.X.
    ```
    .box2 {
        ...
        position: fixed;
        right: 0;
        bottom: 0;
        ...
    }
    ```

## 5. 粘性定位 <a href="https://www.bilibili.com/video/BV1p84y1P7Z5?p=142">`position: sticky`</a>
- 可以使用`left`, `right`, `top`, `bottom`四个属性调整位置，不过最常使用的是`top`值。
- 参考点：离它最近的一个拥有“滚动定位”的祖先元素，即使这个祖先不是最近的真实可滚动祖先。
    > 视口：
    > 1. 对于PC浏览器来说，视口就是我们看网页的那扇“窗户”。
- 特点
    1. 不脱离文档流，专门用于窗口滚动时的新的定位方式。
    3. 最常用的值是`top`值。
    4. 粘性定位和浮动可以同时设置，但不推荐这样做。
    5. 粘性定位的元素，也可以通过`margin`调整位置，但不推荐这样做。
    > 粘性定位和相对定位特点基本一致，不同的是：粘性定位可以在元素到达某个位置（`top`值）时将其固定。
- E.X.
    ```
    .box2 {
        ...
        position: sticky;
        top: 0;
        ...
    }
    ```