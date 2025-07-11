# 什么是 CSS 的继承性，那些属性可继承，哪些不可以？

CSS 的继承性是指某些样式属性可以从父元素传递到其子元素，使得子元素继承父元素的样式属性。这意味着，如果父元素上设置了特定的样式，子元素可能会自动继承这些样式，而无需显式地在子元素上设置相同的样式。  
**可继承的属性**

1.  `文字相关属性`： font-family、font-size、font-weight、font-style 等。
1.  `颜色属性`： color、background-color。
1.  `文本相关属性`： line-height、text-align、text-transform 等。
1.  `链接相关属性`： text-decoration、link、visited、hover、active 等。
1.  `列表属性`： list-style-type、list-style-image 等。
1.  `表格属性`： border-collapse、border-spacing 等。
1.  `元素显示属性`： display、visibility。
1.  `百分比属性`： 某些属性（如 padding、margin）中的百分比值可以继承。

**不可继承的属性**

1.  `盒模型属性`： width、height、margin、padding、border 等。
1.  `定位和布局属性`： position、top、right、bottom、left、float、clear 等。
1.  `背景属性`： background-image、background-position、background-repeat 等。
1.  `定位属性`： z-index。
1.  `轮廓属性`： outline、outline-width、outline-style、outline-color。
1.  `文字选择属性`： user-select、cursor。
1.  `表格属性`： table-layout、border-collapse、border-spacing。
1.  `元素显示属性`： display、visibility

# 什么是媒体查询，有什么作用？

媒体查询（Media Queries）是一种在 CSS 中用于针对不同设备和屏幕尺寸**应用不同样式**的技术。

1.  `响应式设计`： 媒体查询使得网页能够根据不同设备的特性和屏幕尺寸自动调整布局和样式，以适应不同的屏幕大小和分辨率。
1.  `移动优先设计`： 使用媒体查询，开发人员可以首先为移动设备设计样式，然后在更大的屏幕上逐渐增加适当的样式，实现移动优先的设计理念。
1.  `适配不同设备`： 媒体查询允许开发人员针对不同设备类型和特性（如手机、平板、电脑、打印机等）创建专门的样式，从而提供更好的用户体验。
1.  `减少加载时间`： 通过在适用设备上应用特定样式，可以减少不必要的样式和资源的加载，提高网页加载性能。
1.  `单一代码库`： 使用媒体查询，可以在一个 CSS 文件中管理不同设备的样式，从而避免维护多个样式文件。

# z-index 属性在什么情况下会失效？

z-index 属性用于控制元素在**堆叠上下文**中的显示顺序，即元素的层叠顺序。然而，有一些情况下 z-index 属性可能会失效或产生意外的结果：

1.  `未创建层叠上下文`： z-index 只在层叠上下文中有效。如果某个元素未创建层叠上下文（例如，通过设置 position、opacity、transform 等属性），那么 z-index 可能不会按预期工作。
1.  `父元素没有设置定位`： 如果父元素未设置定位属性（例如，position: relative; 或 position: absolute;），子元素的 z-index 可能无法正确生效。
1.  `相对定位的元素`： 如果一个元素使用相对定位（position: relative;），而且没有设置 z-index，那么该元素的层叠顺序可能会被其他具有 z-index 值的元素覆盖。
1.  `父子关系`： 如果父元素和子元素都设置了 z-index，则子元素的 z-index 不会影响父元素之间的层叠关系。子元素的层叠顺序仅影响同一父元素下的其他子元素。
1.  `Flexbox 布局`： 在某些情况下，Flexbox 容器的 z-index 行为可能会比预期复杂。使用 z-index 来影响 Flexbox 内部的元素堆叠顺序时要特别注意。
1.  `浮动元素`： 浮动元素可能会与定位元素的 z-index 发生冲突，导致层叠关系出现问题。

为避免 z-index 失效的问题，您可以考虑以下几点

确保定位元素的父元素设置了定位属性，以创建正确的层叠上下文。
避免过度使用 z-index，尽量采用更简单的布局方案。
使用开发者工具检查元素的层叠顺序，以确定是否达到了预期效果。
将元素的 z-index 值设置为大于或小于其他元素的值，而不是随意的值，以确保正确的层叠顺序。

# 说说设备像素，css 像素，设备独立像素，dpr，ppi 之间的区别？

设备像素（Device Pixel）：设备像素是**物理屏幕上的一个点**，是显示器或移动设备**屏幕的最小单位**。设备像素的数量决定了屏幕的分辨率。

CSS 像素（CSS Pixel）：CSS 像素是 Web 开发中使用的**抽象单位**，它与设备像素之间存在一定的关系，但并不直接映射到具体的物理像素上。浏览器会根据设备像素比（简称 DPR）将 CSS 像素转换为实际的设备像素。

设备独立像素（也称为密度无关像素）：设备独立像素是一个抽象的单位，用来在不同设备上保持一致的显示效果。在 CSS 中，1 个设备独立像素通常等于 1 个 CSS 像素。设备独立像素的概念有助于实现**响应式设计和跨设备兼容性**。

设备像素比（DPR）：物理像素 (Physical Pixels) 和 CSS 像素 (CSS Pixels / Logical Pixels) 之间的比率。如果一个设备的 DPR 为 2，那么 1 个 CSS 像素将对应 4 个设备像素（2x2）。


# link 和 @import 的区别

两者都是外部引用 css 的方式，区别如下：

- link 是 xhtml 标签，除了引入 css 外，还可以加载库，框架，工具等；@import 属于 css 范畴，只能加载 css
- link 引用 css 的时候，在页面载入时同时加载。 @import 需要页面完全加载完成后加载
- link 是 xhtml 标签，无兼容问题，@import 是 css2 提出来的，低版本的浏览器不支持

# 以下是常见的隐藏元素的方法：

### 1. `display: none;`

这是最常用、最彻底的隐藏元素的方法。

- **实现方式：**

  ```css
  .hidden-element {
    display: none;
  }
  ```

- **优点：**

  - **完全从文档流中移除：** 元素不占用任何空间，也不会触发任何布局或渲染。它就像完全不存在一样。
  - **不影响其他元素布局：** 由于元素被移除，周围的元素会像它不存在一样重新排列。
  - **无法交互：** 元素及其所有子元素都不会接收点击、触摸等事件。

- **缺点：**

  - **无法进行过渡动画：** `display` 属性的变化是即时的，无法通过 CSS `transition` 或 `animation` 实现平滑的显示/隐藏动画效果。
  - **DOM 重排（Reflow/Layout）：** 隐藏和显示都会导致文档重排，因为它会改变页面布局。

- **适用场景：** 需要完全隐藏一个元素，并且不占用空间，也不需要动画效果的场景，例如模态框的初始状态、根据条件动态加载/卸载部分内容等。

### 2. `visibility: hidden;`

这种方法会隐藏元素，但元素仍然会占用其原始空间。

- **实现方式：**

  ```css
  .hidden-element {
    visibility: hidden;
  }
  ```

- **优点：**

  - **保留文档流空间：** 元素依然占据它应有的布局空间，不会影响周围元素的排列。
  - **可以进行过渡动画：** `visibility` 属性的变化可以配合 `transition` 实现淡入淡出等动画（虽然 `hidden` 到 `visible` 之间可能需要一些技巧，但通常与 `opacity` 结合使用）。
  - **DOM 重绘（Repaint）** ：隐藏和显示通常只触发重绘，因为它不改变元素的几何属性（除非与布局相关的属性同时改变）。

- **缺点：**

  - **仍占用空间：** 即使元素不可见，但它在页面上依然占据一块空白区域。
  - **无法交互：** 元素及其所有子元素不会接收点击、触摸等事件。

- **适用场景：** 需要在隐藏元素的同时保留其布局空间，例如图片预加载、鼠标悬停时显示/隐藏工具提示，或者用于某些需要保留占位符的动画效果。

### 3. `opacity: 0;`

通过将元素的透明度设置为 0 来隐藏元素。

- **实现方式：**

  ```css
  .hidden-element {
    opacity: 0;
    /* 可选：为了防止元素仍然可以点击，可以加上 pointer-events: none; */
    /* pointer-events: none; */
  }
  ```

- **优点：**

  - **保留文档流空间：** 元素依然占据它应有的布局空间。
  - **最适合动画：** `opacity` 属性的变化可以完美地与 `transition` 或 `animation` 结合，实现平滑的淡入淡出效果。
  - **性能较好：** 通常只触发**合成 (Compositing)** ，因为透明度变化可以直接由 GPU 处理，不会引起重排或重绘，性能开销最小。

- **缺点：**

  - **仍占用空间：** 即使元素不可见，但它在页面上依然占据一块空白区域。
  - **默认可交互：** 默认情况下，即使 `opacity` 为 0，元素仍然可以接收点击、触摸等事件。如果你不希望它被点击，需要额外添加 `pointer-events: none;`。

- **适用场景：** 制作平滑的淡入淡出动画、需要隐藏但不影响布局且对性能要求较高的场景。

### 4. `position: absolute;` / `fixed;` + 移出可视区域

将元素从正常文档流中移除，然后将其定位到屏幕外部，使其不可见。

- **实现方式：**

  ```css
  .hidden-element {
    position: absolute; /* 或 fixed */
    left: -9999px; /* 移到屏幕左边很远的地方 */
    /* top: -9999px; */
  }
  ```

- **优点：**

  - **完全从文档流中移除：** 元素不占用任何空间，不会影响其他元素的布局（因为它脱离了文档流）。
  - **可以进行动画：** 可以对 `left`/`top` 等属性进行动画，实现滑入滑出效果。

- **缺点：**

  - **代码略复杂：** 需要精确的定位，并且如果需要精确地回到原位，管理起来可能比 `display` 或 `visibility` 复杂。
  - **元素仍在 DOM 树中：** 即使移出可视区，它仍然存在于 DOM 树中并占用少量内存。

- **适用场景：** 模态框、侧边抽屉、提示框等需要从屏幕边缘滑入滑出的组件。

### 5. `height: 0;` 或 `width: 0;` （配合 `overflow: hidden;`）

通过将元素的尺寸设置为 0 并隐藏溢出内容来隐藏元素。

- **实现方式：**

  ```css
  .hidden-element {
    height: 0;
    overflow: hidden;
    /* 可选：配合 transition 实现折叠动画 */
    /* transition: height 0.3s ease; */
  }
  ```

- **优点：**

  - **完全不占用空间：** 元素折叠起来，不占用任何布局空间。
  - **适合折叠动画：** 可以对 `height` 或 `width` 进行 `transition` 动画，实现平滑的展开/折叠效果，例如手风琴菜单。

- **缺点：**

  - **可能触发重排：** 改变 `height` 或 `width` 会导致重排。
  - **需要注意子元素：** 如果子元素有固定大小或边距，可能需要额外的处理来确保完全隐藏。
  - **内容可能被裁剪：** `overflow: hidden` 会裁剪掉超出部分，如果动画效果不是折叠，可能不适用。

- **适用场景：** 手风琴菜单、可展开/折叠的内容区域等需要有折叠动画的场景。

### 6. 通过 `z-index` 将元素置于其他元素之下（相对不常见）

将元素的 `z-index` 设置为一个非常小的值，并确保有其他元素覆盖在它上方。

- **实现方式：**

  ```css
  .hidden-element {
    position: relative; /* 或 absolute/fixed */
    z-index: -1;
  }
  .covering-element {
    position: relative;
    z-index: 1; /* 确保在隐藏元素之上 */
  }
  ```

- **优点：** 可以在视觉上隐藏，但不改变布局。

- **缺点：**

  - **不是真正的隐藏：** 元素还在可视区域，只是被覆盖了。
  - **可能仍然可交互：** 除非被完全不透明的元素覆盖，否则仍然可能被点击。
  - **依赖其他元素：** 必须有另一个元素来覆盖它。

- **适用场景：** 很少直接用于“隐藏”，更多用于层级控制。

### 总结：

| **方法**              | **是否占用空间** | **是否触发重排/重绘** | **是否可动画化** | **是否可交互** | **常用场景**             |
| :-------------------- | :--------------- | :-------------------- | :--------------- | :------------- | :----------------------- |
| `display: none;`      | 否               | 重排/重绘             | 否               | 否             | 彻底隐藏，不占空间       |
| `visibility: hidden;` | 是               | 重绘                  | 是 (间接)        | 否             | 隐藏但保留空间           |
| `opacity: 0;`         | 是               | 合成                  | 是               | 是 (默认)      | 淡入淡出动画，高性能     |
| `position: absolute;` | 否               | 重排/重绘             | 是               | 是             | 滑入滑出动画，脱离文档流 |
| `height: 0;`          | 否               | 重排/重绘             | 是               | 否             | 折叠/展开动画            |

# transition transform animation

### transition 和 animation 有何区别？

- transition: 用于做过渡效果，没有帧概念，只有开始和结束状态，性能开销小
- animate：用于做动画，有帧的概念，可以重复触发且有中间状态，性能开销比较大，

### 可以怎么优化 CSS 动画性能?

1. 开启 gpu 加速
2. 利用 translate 进行元素移动。translateZ 函数或 translate3d 函数来开启 GPU 加速

# 布局

### flex 的基本使用

```js
.parent {
  flex-direction //属性决定主轴的方向
  flex-wrap//如果一条轴线排不下，能否换行
  flex-flow// flex-direction flex-wrap的简写
  justify-content//项目在主轴上的对齐方式。
  align-items//定义项目在交叉轴上如何对齐
  align-content//定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。
}

.children {
  order//数值越小，排列越靠前，默认为0。
  flex-grow//定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大
  flex-shrink//定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小。
  flex-basis//定义了在分配多余空间之前，项目占据的主轴空间
  flex//flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto
}
```

### flex 的子元素可以浮动吗？

不可以，冲突了，还是 flex 状态

### flex:1 的作用

首先 flex:1;等同于 flex:11auto;
flex:1 实际上是三个属性的缩写：`flex-grow：1; flex-shrink:1 flex-basis:auto;`

### flex 布局可以设置 item 子元素的顺序吗？

可以使用 CSS 的 order 属性来控制 flex 容器中项目的顺序。默认情况下，项目的 order 值为 0，你
可以为项目设置一个正数或负数的 order 值来改变它们的顺序。具有较小 order 值的项目会排在前面。

# div

### 1 让元素消失

1. 直接更改盒子模型 width height

2. display:none

3. visibility: hidden

4. opacity: 0

5. clip-path: 截取范围 100% 就没有了

6. transform： 缩放 旋转 变形

7. 移动元素 1 margin-top:-9999px

8. 移动元素 2 position:absolute

### 2 BFC

#### 1. **是什么 (Definition):**

BFC 是一个独立的渲染区域，规定了内部块级盒子（Block-level boxes）如何布局。

#### 2. 在 html 中的块级元素是不是都在 bfc 中，即使父 div 没有开启 bfc？

是的，！**在 HTML 中，所有的块级元素（Block-level elements）最终都存在于某个块格式化上下文 (BFC) 之中。**

原因如下：

1.  **根元素    自动创建 BFC:**   页面上所有可见元素都嵌套在    元素内。根据 CSS 规范，  元素本身就会自动创建整个文档的**根 BFC (Root BFC)** 。
1.  **默认归属:**   如果一个块级元素（比如你的  div) 的父元素**没有**通过特定 CSS 属性（如  overflow: hidden, display: flow-root, float: left, position: absolute  等）来创建**新的、嵌套的 BFC**，那么这个块级元素就**默认属于其父元素所在的那个 BFC**。
1.  **传递性:**   这个归属关系会一直向上追溯，直到找到一个创建了 BFC 的祖先元素。由于    总是创建 BFC，所以任何元素最终都会归属于至少一个 BFC（最差也是根 BFC）。

**总结来说：**

- **所有块级元素都位于某个 BFC 内。**
- 如果一个元素的直接父元素没有明确创建新的 BFC，那么这个元素就和它的父元素（以及它的兄弟元素）一起，位于**同一个**更上层的 BFC 中（最终可以追溯到    创建的根 BFC）。
- **这正是为什么即使父  div  没有“开启 BFC”，其内部的相邻块级子元素（如  .box3  和  .box5）之间仍然会发生外边距塌陷** —— 因为它们处于同一个（通常是上层的）BFC 环境中，满足了塌陷的条件。

#### 3. **如何触发/创建 BFC (Triggers):**

一个元素要形成 BFC，需要满足以下**至少一个**条件：

- 根元素 () 本身就是一个 BFC。 - 浮动元素 (float 值不为 none)。
- 绝对定位元素 (position 值为 absolute 或 fixed)。
- 行内块元素 (display: inline-block)。
- 表格单元格 (display: table-cell，HTML 表格单元格默认属性)。
- 表格标题 (display: table-caption)。
- 匿名表格单元格元素（display: table、table-row、table-row-group、table-header-group、table-footer-group 的直接子元素，如果不是 table-cell，则会创建匿名单元格，该单元格是 BFC）。
- overflow 值不为 visible 或 clip 的块元素（即 overflow: hidden, auto, scroll)。**这是开发中最常用来手动创建 BFC 的方式之一。**
- display: flow-root。**这是专门为了创建无副作用 BFC 而设计的现代 CSS 属性。**
- 弹性元素（display: flex 或 inline-flex 的直接子元素）。
- 网格元素（display: grid 或 inline-grid 的直接子元素）。
- 多列容器（column-count 或 column-width 值不为 auto，包括 column-count: 1）。

#### 4. **BFC 的特性/布局规则 (Characteristics/Rules):**

- **内部垂直布局:** 在 BFC 内部，块级盒子在垂直方向上一个接一个地放置，从包含块的顶部开始。 - **盒子间垂直距离:** 同一个 BFC 内的两个相邻块级盒子的垂直外边距会发生**塌陷 (Margin Collapsing)** 。
- **外边距不塌陷:** **关键点！** BFC 区域**不会**与外部元素的垂直外边距发生塌陷。也就是说，属于不同 BFC 的相邻块级盒子的垂直外边距不会塌陷。
- **包含浮动元素:** **关键点！** BFC 可以包含其内部的浮动元素。计算 BFC 的高度时，其内部的浮动元素也会参与计算。这意味着 BFC 不会发生高度塌陷（即父元素高度为 0，即使内部有浮动元素）。
- **隔离性:** BFC 的区域**不会**与外部的浮动元素重叠。它就像一道屏障，阻止外部浮动元素侵入其内部，也阻止其内部布局影响外部。

#### 5. **BFC 的应用/解决了什么问题 (Applications):**

基于 BFC 的特性，它可以用来解决很多常见的 CSS 布局问题：

- **防止外边距塌陷 (Prevent Margin Collapsing):** 当两个相邻元素（兄弟或父子）的垂直外边距相遇时可能发生塌陷。将其中一个元素包裹在一个 BFC 容器中，可以阻止它与外部元素的边距塌陷。例如，给父元素创建 BFC 可以阻止子元素 margin-top 传递给父元素（父子边距塌陷的一种情况）。
- **清除浮动/包含浮动 (Clear/Contain Floats):** 当一个容器内的所有子元素都浮动时，父容器的高度会塌陷为 0。给父容器创建 BFC（如设置 overflow: hidden 或 display: flow-root）可以强制它包裹住内部的浮动元素，从而正确计算高度。这是最常见的 BFC 应用之一，常被称为“自清除”浮动。
- **阻止元素被浮动元素覆盖 (Prevent Text Wrapping Around Floats):** 创建一个多列布局，例如左侧栏浮动，右侧主内容区自适应。如果不做处理，右侧内容区的文字可能会环绕左侧浮动元素。将右侧主内容区设置为 BFC，可以使其形成一个独立的布局区域，不会与左侧的浮动元素发生重叠，内容也不会环绕。

#### 6. **现代方法 (display: flow-root):**

过去常用 overflow: hidden/auto/scroll 来创建 BFC 以清除浮动或解决其他布局问题，但这可能会带来不必要的副作用（如内容被裁剪、出现滚动条）。display: flow-root 是 CSS Display Module Level 3 中引入的新值，它的唯一目的就是创建一个无副作用的 BFC，是现代 CSS 中解决上述问题的**首选方案**。

#### 7. 没有 BFC 会发生什么

| 问题描述               | 原因                                   |
| ---------------------- | -------------------------------------- |
| 父元素高度塌陷         | 子元素浮动，没有被包含                 |
| 相邻元素 margin 合并   | 没有 BFC，margin 发生合并              |
| 后续元素被浮动元素影响 | 没有触发 BFC，浮动没有被隔离           |
| 布局混乱、难以控制     | 缺乏独立格式化上下文，元素之间相互干扰 |

### 3 div 水平居中

### 4 div 垂直居中

2. `align-items: center;` /_ 使子项在交叉轴（垂直方向）上居中 _/

3. `place-items: center;` 同时在水平和垂直方向上居中内容 或者使用 `align-items: center;`

4. 这种方法通过绝对定位和 transform 属性来实现元素的精确居中，适用于任何元素类型

   ```css
   .container {
     position: relative; /* 父容器需要有定位上下文 */
     height: 150px; /* 父容器的高度 */
     background-color: #f0f0f0;
   }

   .text {
     position: absolute; /* 子元素绝对定位 */
     top: 50%; /* 顶部偏移50% */
     left: 50%; /* 左侧偏移50%（如果也需要水平居中） */
     transform: translate(-50%, -50%); /* 向上和向左各偏移自身宽/高的一半 */
     width: max-content; /* 让宽度自适应内容，避免多行文本换行问题 */
     /* 或者设置一个固定宽度和 text-align: center; */
   }
   ```

### 5 水平和垂直居中 4 种方法

1. 使用 flex

```css
/* 1 */
.parent {
  display: flex;
  justify-content: center;
  align-items: center;
}

/* 2 parent */
.parent {
  display: flex;
}
/* children */
.children {
  margin: auto;
}
```

2. 使用 position

```css
/* 3  */
.parent {
  position: relative;
}
.children {
  position: absolute;
  left: 50%;
  top: 50%;
  transform: tranlate(-50%, -50%);
}

/* 4 */
.parent {
  position: relative;
}
.children {
  position: absolute;
  left: 0;
  right: 0;
  left: 0;
  right: 0;
  margin: 0;
}
```

### 有一个高度自适应的 div，里面有两个 div，一个高度 100px，希望另一个填满剩下的高度，怎么实现？

```css
.children2 {
  height: calc(100% - 100px);
}
```

# 关于文本的

### 1 为什么浏览器默认最小字体是 12px？

1. 可读性： 12px 通常被认为是 PC 端屏幕上文字可读性的一个下限。小于 12px 的字体在大多数显示器上会变得难以辨认，影响用户体验。

2. 兼容性： 早期浏览器在处理小于 12px 的字体时，可能会出现渲染问题或显示效果不佳。为了统一和保证基本的可读性，大多数浏览器设定了最小字体大小。

3. 防止滥用： 限制最小字体大小可以防止开发者过度使用极小的字体，从而损害用户体验。

### 2 如何实现字体小于 12px?

1. 这是目前最常用也是效果最好的方法，因为它实际上是渲染了一个正常大小的字体，然后过 CSS 的 transform 属性对其进行视觉上的缩小，因此不会有字体渲染模糊的问题

2. 使用图片代替 (针对少量固定文本)

3. 使用 SVG

### 3 单行文本溢出

- **`white-space: nowrap;`** : 强制文本不换行。

- **`overflow: hidden;`** : 隐藏超出容器边界的内容。

- **`text-overflow: ellipsis;`** : 当文本溢出时，显示省略号。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>实现单行和多行文本溢出</title>
    <style>
      .box {
        width: 100px;
        white-space: nowrap; /*不转行*/
        overflow: hidden; /*超出则隐藏*/
        text-overflow: ellipsis; /*超出则打点*/
      }
    </style>
  </head>
  <body>
    <div class="box">ukdkasldaskajhas83182903812iewsa213sjansn</div>
  </body>
</html>
```

### 4 多行文本溢出

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>实现单行和多行文本溢出</title>
    <style>
      .box {
        width: 100px;
        display: -webkit-box; /*将对象作为弹性伸缩盒子模型显示 */
        -webkit-box-orient: vertical; /*转行方向排列*/
        -webkit-line-clamp: 3; /*转3行*/
        overflow: hidden; /*超出则隐藏*/
        word-break: break-all; /*强制转换*/
      }
    </style>
  </head>
  <body>
    <div class="box">
      ukdkasldaskajhas831829038238901237982199312iewsa213sjansn
    </div>
  </body>
</html>
```

### 5 css 文本水平居中（块级元素和行内块级元素）

1. text-align: center

### 6 css 文本垂直居中（块级元素和行内块级元素）

1. `line-height` （单行文本） 将行高 (line-height) 设置为与父容器高度相同。

### 7 line-height: 120% 和 line-height: 1.2 有什么区别?

当你使用百分比值时，子元素会继承计算后的行高值；而当你使用数值时，子元素会继承这个数值，并根据
自己的字体大小重新计算行高。

# 关于 基本选择器 伪类选择器 伪元素选择器

### div:nth-child(2n + 1) div:nth-of-type(2n + 1)

1. `div:nth-child(2n + 1)` 先满足奇数行即可，再满足是 div

2. `div:nth-of-type(2n + 1)` 先过滤所有的 div，再找奇数行的 div

# 关于图片

### webp

WebP 是一种现代的图片格式，有 Google 公司开发。用于在 web 上提供更好的有损和无损压缩图片。

### 什么是 精灵图(雪碧图)？作用和原理了解吗?

1. 把小图片利用工具合成一张，使用的时候通过 css 的 background 控制位置进行展示。

2. 优点
   - 减少网页的 http 请求，从而大大提高了页面的性能
   - 通常减少图片的字节
   - 提高缓存效率
3. 缺点
   - 开发和使用的时候比较麻烦的时候相对来说有点麻烦，
  - 维护的时候比较麻烦

# 其他

# 响应式设计是什么？原理？

1. 是什么
   是一个网站能够兼容多个终端，而不是为每一个终端做一个特定的版本

2. 为什么
   通过媒体查询检测不同设备屏幕尺寸做处理。

3. 怎么触发
   页面头部必须有 meta 声明 viewport

```html
<meta
  name="viewport"
  content="width=device-width, initial-scale=1.0, minimum-scale=1.0, maximum-scale=1.0, user-scalable=no"
/>
```
