# . 一个网页从开始请求到显示的过程

- （1）在浏览器中输入网址，浏览器解析 URL，浏览器检查缓存；
- （2）发送至 DNS 服务器并获得域名对应的 WEB 服务器 IP 地址，将这 IP 地址缓存以便下次快速查询；
- （3）与 WEB 服务器建立 TCP 连接，进行三次握手；
- （4）浏览器向 WEB 服务器的 IP 地址发送相应的 HTTP 请求；
- （5）WEB 服务器响应请求并返回指定 URL 的数据，
- （6）浏览器下载数据后解析 HTML,css,js 源文件，浏览器解析 HTML 代码，按照其结构（标签嵌套关系）在内存中构建一个  DOM  树
- (7)在解析 HTML 的过程中，如果遇到  `<link>`标签引用外部 CSS 文件或  `<style>`  标签包含内联 CSS：获取这些 CSS 文件，浏览器会解析 CSS 代码，构建一个  **CSSOM (CSS Object Model)**   树。
- (8)浏览器将 DOM 树和 CSSOM 树结合起来，创建一个  **渲染树 (Render Tree)**

- (9)布局：  浏览器根据渲染树和视口（Viewport）的大小，计算每个节点在屏幕上的精确位置和尺寸

- (10)绘制 ：  浏览器遍历渲染树，调用图形库（如 Skia）将每个节点绘制成屏幕上的实际像素。这个过程可能发生在多个图层上

- (11)合成 ：  浏览器将绘制好的各个图层按照正确的顺序（考虑  z-index  等）合并到一起，最终显示在屏幕上。


### 1 什么是重排（回流 / Reflow / Layout）？它在浏览器渲染过程中扮演什么角色？

1. 是什么
   重排（或回流、Layout）是指浏览器为了重新计算文档中元素的位置和大小，并重新构建渲染树（Render Tree）的过程。重排是**所有渲染操作中开销最大的**

2. 为什么
   当 DOM 结构、元素尺寸或位置发生变化时，浏览器需要重新计算所有受影响的元素在屏幕上的确切位置和大小。

3. 怎样触发
   改变 DOM 元素的几何属性（`width`, `height`, `padding`, `margin`, `border`, `font-size`, `top`, `left` 等）。
   添加、删除或移动 DOM 节点。
   改变浏览器窗口大小（Resize）。
   激活伪类（如 `:hover`）。
   改变 CSS 属性的 `display` 为 `none` 或 `block` 等。

---

### 2：什么是重绘（Repaint）？它和重排有什么区别？

1. 是什么
   重绘是指当元素的外观属性发生变化，但其几何属性（位置、大小）没有改变时，，而无需重新计算布局的过程。重排开销远大于重绘

2. 为什么

3. 怎样触发
   元素的颜色 (`color`)、
   背景 (`background-color`, `background-image`)、
   阴影 (`box-shadow`)、
   可见性 (`visibility: hidden` 但 `display: block` 或 `opacity`) 等样式属性时，会触发重绘。

### 3：为什么我们要关注重排和重绘？它们对前端性能有什么影响？

1. 为什么
   重排和重绘是浏览器渲染过程中最耗费性能的环节，特别是重排。频繁或大量的重排和重绘会导致：

2. 对性能的影响
   **页面卡顿：** 浏览器需要花费大量时间重新计算和绘制，从而阻塞了用户界面的响应，导致页面出现卡顿、不流畅的。
   **帧率下降：** 影响页面的帧率，降低用户体验，尤其是在动画和滚动场景中更为明显。
   **耗电量增加：** 对于移动设备，频繁的渲染操作还会增加设备的耗电量。

### 4：如何减少和优化重排和重绘？请列举一些常见的方法。

1.  **批量修改 DOM：**

2.  **避免频繁访问导致强制同步布局的属性：**

3.  **使用 CSS 动画替代 JavaScript 动画：**

4.  **避免使用表格布局（尤其是复杂表格）：**

5.  **合理使用 CSS 属性：**