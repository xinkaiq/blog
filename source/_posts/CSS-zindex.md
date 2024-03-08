---
title: CSS zindex
date: 2024-02-16 17:28:26
tags: [css, position, zindex]
---

## <a href="https://www.bilibili.com/video/BV1p84y1P7Z5?p=143">z-index</a>
1. 定位元素的显示层级比普通元素高，无论什么定位，显示层级都是一样的。
2. 如果位置发生重叠，默认情况是：后面的元素，会显示在前面元素之上。
3. 可以通过css属性`z-index`调整元素的显示层级。
4. `z-index`的属性值是数字，没有单位，值越大显示层级越高。
5. 只有定位的元素设置`z-index`才有效。
6. 如果`z-index`值大的元素，依然没有覆盖掉`z-index`值小的元素，那么请检查其包含块的层级。
