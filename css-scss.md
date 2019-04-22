# 1 注释规范



# 2 缩进/空格/换行规范

- 每个缩进使用4个空格，不允许使用 2 个空格 或 tab

  ```
  //正确
  .sample {
      display: flex;
  }
  //错误
  .sample {
    display: flex;
  }
  ```

- 选择器 与 花括号 之间必须包含空格

  ```
  //正确
  .sample {
      display: flex;
  }
  //错误
  .sample{
      display: flex;
  }
  ```

- 每条规则之间必须包含空行

  ```
  //正确
  .sample {
      display: flex;
  }
  
  .sample1 {
      display: block;
  }
  //错误
  .sample {
      display: flex;
  }
  .sample1 {
      display: block;
  }
  ```

- 属性名与冒号之间不允许包含空格， 冒号与属性值之间必须包含空格

  ```
  //正确
  display: flex;
  //错误
  display:flex
  display : flex
  display :flex
  ```

- 逗号前不允许有空格，逗号后必须跟一个空格

  ```
  //正确
  font-family: Helvetica, Arial
  //错误
  font-family: Helvetica , Arial
  font-family: Helvetica ,Arial
  font-family: Helvetica, Arial
  ```

- SCSS mixin的方法参数括号与 { 之间必须包含一个空格, 各参数间必须有一个空格

  ```
  //正确
  @mixin color-box($bg-color: $grey-light, $border-color: $grey) {
      background-color: $bg-color;
      border: 1px solid $border-olor;
  }
  //错误
  @mixin color-box($bg-color:$grey-light,$border-color:$grey) {
      background-color: $bg-color;
      border: 1px solid $border-olor;
  }
  ```

- '+' '~' '>'选择器前后必须跟一个空格

  ```
  //正确
  .radio-label + .radio-box {
  
  }
  //错误
  .radio-label+.radio-box {
  
  }
  ```

- 引用mixin和多层嵌套必须有一个空行

  ```
  //正确
  .sample {
      @include color-box;
  
      margin: 15px;
  
      &:hover {
        display: block;
      }
  }
  //错误
  .sample {
      @include color-box;
      margin: 15px;
      &:hover {
        display: block;
      }
  }
  ```

- 一组变量的定义，尽量以冒号对齐

  ```
  //推荐
  $link-hover-color        : #29e;
  $hover-color-gray        : #ebebeb;
  $icon-hover-color        : #4d4d4d;
  $btn-hover-color         : #f0f0f0;
  $btn-hover-color-form    : #f9f9f9;
  $btn-hover-color-cancel  : #f63737;
  //不推荐
  $link-hover-color : #29e;
  $hover-color-gray : #ebebeb;
  $icon-hover-color : #4d4d4d;
  $btn-hover-color : #f0f0f0;
  $btn-hover-color-form : #f9f9f9;
  $btn-hover-color-cancel : #f63737;
  ```

- 多个并行选择器使用同一规则，必须换行

  ```
  //正确
  .a,
  .b,
  .c {
      box-sizing: border-box;
  }
  //错误
  .a, .b, .c {
      box-sizing: border-box;
  }
  ```

# 3 选择器

- 禁止使用ID应用于样式，应该使用class

  ```
  //正确
  .content {
      display: flex;
  }
  //错误
  #content {
      display: flex;
  }
  ```

- CSS选择器中避免标签名
  选择器应该是准确和有语义的class(类)名，不推荐使用标签选择器。这样会更容易维护, 只需要修改你的标签名，而不是你的class
  从分离的角度考虑,在表现层中不应该分配html标记/语义。

  ```
  //推荐
  .content {
      display: flex;
  
      > .nav {
          flex: 1;
      }
  }
  //不推荐
  .content {
      display: flex;
  
      > nav {
          flex: 1
      }
  }
  ```

- 尽量精准的选择

  ```
  //推荐
  .content {
      display: flex;
  
      > .nav {
          flex: 1;
      }
  }
  //不推荐
  .content {
      display: flex;
  
      .nav {
          flex: 1
      }
  }
  ```

- 选择器嵌套
  正常的情况下，我们不推荐使用嵌套，如果需要使用嵌套，我们不推荐嵌套超过三层, 如果嵌套超过三层，应该考虑是不是哪里可以使用更精准更语义化的class。不推荐直接使用css的嵌套，而是使用SCSS的嵌套。

  ```
  //推荐
  .content {
      display: flex;
  
      > .nav {
          flex: 1;
  
          > .item {
              text-align: center;
          }
      }
  }
  //不推荐
  .content .nav .item a {
      text-align: center;
  }
  ```

- 在CSS预处理器如LESS 和 SASS 里 media query 推荐直接在选择器的嵌套中使用，有助于保持媒体查询属于的上下文

  ```
  //推荐
  .content {
      font-size: 1.2rem;
  
      @media screen and (min-width: 767px) {
          font-size: 1rem;
      }
  }
  //不推荐
  .content {
      font-size: 1.2rem;
  }
  @media screen and (min-width: 767px) {
      .content {
          font-size: 1rem;
      }
  }
  ```

- 属性选择器必须使用双引号

  ```
  //正确
  [class="icon-"] {
      font-size: 1rem;
  }
  //错误
  [class='icon-'] {
      font-size: 1rem;
  }
  ```

# 4 属性规范

- 属性定义必须另起一行

  ```
  // 正确
  .selector {
      margin: 0;
      padding: 0;
  }
  
  // 错误
  .selector { margin: 0; padding: 0; }
  ```

- 属性必须以分号结尾

  ```
  // 正确
  .selector {
      margin: 0;
      padding: 0;
  }
  // 错误
  .selector {
      margin: 0;
      padding: 0
  }
  ```

- 属性值为0时，省略单位

  ```
  // 正确
  .box {
      padding: 0;
  }
  // 错误
  .box {
      padding: 0px;
  }
  ```

- 使用16进制表示颜色，颜色值采用小写，#rrggbb的情况简写为#rgb，有透明度的情况使用rgba表示

  ```
  // 正确
  .box {
      background: rgba(0, 0, 255, .5);
      color: #3ec;
  }
  // 错误
  .box {
      background: white;
      opacity: 0.5;
      color: #33eecc;
  }
  ```

- 同一组属性尽量按照功能顺序书写，以 Formatting Model（布局方式、位置） > Box Model（尺寸） > Typographic（文本相关） > Visual（视觉效果） 的顺序书写，以提高代码的可读性

  - Formatting Model 相关属性包括：display / position / top / right / bottom / left / float /  overflow 等
  - Box Model 相关属性包括：margin / border / padding / width / height 等
  - Typographic 相关属性包括：font / line-height / text-align / word-wrap 等
  - Visual 相关属性包括：background / color / transition / list-style 等

  ```
  // 推荐
  .sidebar {
      // formatting model
      position: absolute;
      top: 50px;
      left: 0;
      overflow-x: hidden;
      // box model
      width: 200px;
      padding: 5px;
      border: 1px solid #ddd;
      // typographic
      font-size: 14px;
      line-height: 20px;
      // visual
      background: #f5f5f5;
      color: #333;
      transition: color 1s;
  }
  ```

- font-family 属性

  - font-family 属性中的字体族名称应使用字体的英文 Family Name，其中如有空格，须放置在引号中。

    ```
    // 示例
    h1 {
        font-family: "Microsoft YaHei";
    }
    ```

  - font-family 不区分大小写，但在同一个项目中，同样的 Family Name 大小写必须统一。

    ```
    // 正确
    body {
        font-family: Arial, sans-serif;
    }
    
    h1 {
        font-family: Arial, "Microsoft YaHei", sans-serif;
    }
    
    // 错误
    body {
        font-family: arial, sans-serif;
    }
    
    h1 {
        font-family: Arial, "Microsoft YaHei", sans-serif;
    }
    ```

  - font-family 按「西文字体在前、中文字体在后」、「效果佳 (质量高/更能满足需求) 的字体在前、效果一般的字体在后」的顺序编写，最后必须指定一个通用字体族( serif / sans-serif )

    ```
    // 示例
    body {
        font-family: "Helvetica Neue", Helvetica, Arial, PingFangSC-Regular, "Microsoft Yahei", Verdana, sans-serif;
    }
    
    ```

  - 不推荐在业务中重写font-family

- url()中的路径不添加引号

  ```
  // 推荐
  .box {
      background-image: url(../imgs/banner.jpg);
  }
  // 不推荐
  .box {
      background-image: url('../imgs/banner.jpg');
  }
  ```

- 推荐并适当缩写值
  “适当”是因为缩写总是会包含一系列的值，而有时候我们并不希望设置某一值，反而造成了麻烦，那么这时候你可以不缩写，而是分开写。

  ```
  // 有时我们只想设置一个容器水平居中，那么设置left，right就好，而top和bottom不是这个样式要关心的（如果设置了反倒会影响其他样式在这个容器上的使用）
  
  // 示例
  <div class="box center"></div>
  
  .box {
      margin-top: 10px;
  }
  // 这种简写将会覆盖.box里的设置
  .center {
      margin: 0 auto;
  }
  
  // 比如下面这个模块的样式设置，我们确实需要设置padding的所有项，于是我们就可以采用缩写
  .footer {
      padding: 12px 3px;
  }
  ```

- 对于属性值或颜色参数，省略小于 1 的小数前面的 0 （例如，.5 代替 0.5；-.5px 代替 -0.5px）

- 无边框设置

  ```
  // 正确
  .box {
      border: none;
  }
  // 错误
  .box {
      border: 0; // 浏览器会进行多余的渲染，性能不佳
  }
  ```

- 层级(z-index)禁止随意设置，页面弹窗、气泡为最高级（最高级为999）；普通区块为10-90内10的倍数；同层的多个元素，在该层级内使用相同的 z-index 或递增。

- 禁止使用 !important (特殊情况除外，如覆盖第三方插件中的样式等)

- 禁止使用 filter

- 多个class里有一个或多个公共属性，应该将属性抽取到一个单独的class中或者使用泛选择器([attribute~=value], [attribute^=value],[attribute$=value],[attribute*=value])，泛选择器应确保不会有全局污染，避免多次书写重复代码

  ```
  // 正确
  <div>
      <span class="icon-book"></span>
      <span class="icon-pen"></span>
  </div>
  
  [class^="icon-"] {
      background-image: url(../imgs/sprite.png) no-repeat;
  }
  
  .icon-book {
      background-positon: 0 -16px;
  }
  
  .icon-pen {
      background-positon: -16px -16px;
  }
  // 错误
  <div>
      <span class="icon-book"></span>
      <span class="icon-pen"></span>
  </div>
  
  .icon-book {
      background-image: url(../imgs/sprite.png) no-repeat;
      background-positon: 0 -16px;
  }
  
  .icon-pen {
      background-image: url(../imgs/sprite.png) no-repeat;
      background-positon: -16px -16px;
  }
  ```

# 5 Hack规范

  通常我们禁止在CSS的一个选择器中使用hack混编，如果你确实需要写hack, 我们应该有一个class： xxx-fix, 最好把所有的hack放在一个独立的文件, 通过JS特性检测或者直接添加到dom中。

```
  // 错误
  .selector {
      key: value;
      key: fix-value\0; //ie 9-11
  }
  // 正确
  .selector {
      key: value;
  }

  .selecor-ie-fix {
      key: fix-value\0; //ie 9-11
  }
```

# 6 命名规范

- 文件夹命名

  - css文件夹命名应参照项目文件夹命名规则，命名总是以字母开头而不是数字，且字母一律小写，以中划线连接多个单词且不带其他标点符号。
    如：input-number
    有复数结构时，采取复数命名法。
    如： style styles
    |- components
    |- input-number
            |- inputNumber.html
        |- inputNumber.js
        |- styles
            |- input_number.scss
            |- images
        |- menu

- 文件命名

  - 全站架构：(以下文件放在跟路径下的styles目录中)

  ```
  基本共用 base.scss
  布局、版面 layout.scss
  主题 themes.scss
  专栏 columns.scss
  文字 font.scss
  主要的 main.scss
  表单 forms.scss
  补丁 mend.scss
  打印 print.scss
  变量 variables.scss
  功能函数 mixins.scss
  色值 colors.scss
  动画 animations.scss
  字体 iconfont.scss
  ```

  - 组件级 / 应用级：（放在组件/应用目录中）

  ```
  css模块文件，其文件名必须与模块名一致。
  css页面文件，其文件名必须与HTML文件名一致。
  目的是让开发人员快速找到该页面或组件对应的css文件。
  文件命名总是以字母开头而不是数字，且字母一律小写，以下划线连接且不带其他标点符号。
  radio.scss
  main-list.scss
  main-detail.scss
  ```

- 变量命名

  - 命名变量的最佳方式就是使用抽象名词，尽量取消名字和值之间的直接关系。
  - 使用'$'开头+ 语义化的变量名。
  - 避免使用无意义的词，如: $calendar-component -> $calendar
  - 推荐变量的意义在前面，功能在后面

  ```
  // 不推荐
  $red: #F50707;
  $yellow: #B3F724;
  
  // 推荐
  $brand-color: #F50707;
  $accent-color: #B3F724;
  
  // 你可能会使用名称加-color的后缀来命名颜色的变量:
  // Base colors
  $base-color: #333;
  $brand-color: #F50707;
  $brand-80-color: rgba($color-brand, 0.8);
  $accent-color: #B3F724;
  
  // 或者使用header-或者footer-来命名一些特殊的区域：
  // Header
  $header-height: 100px;
  $header-background-color: $color-brand;
  // Footer
  $footer-height: 200px;
  $footer-background-color: #aaa;
  
  // 不推荐
  $z-index-modal
  $padding-body
  // 推荐
  $modal-z-index
  $body-padding
  ```

- 选择器命名

  ```
    推荐采用BEM方式命名
    // BE模式 block__element：块里的元素，如：nav（block）里的 a 标签(element)
    <nav class="g-nav">
        <a href="#" class="g-nav__item">工作动态</a>
    </nav>
    .g-nav__item {
  
    }
  
    // BM模式 block--modifier: 块元素加修饰符
    // g-nav表示导航的通用样式，g-nav-top表示该导航特有的样式，g-nav--active表示激活的nav
    <nav class="g-nav g-nav-top g-nav--active">
    </nav>
    .g-nav--active {
  
    }
  
    // BEM模式 block__element--modifier nav块里的a元素加上active状态
    <nav class="g-nav">
        <a href="#" class="g-nav__item g-nav__item--active">当前状态</a>
    </nav>
    .g-nav__item--active {
  
    }
  
    BEM只允许出现B__E--M,不允许出现B__B__B__E--M   B__E__E__E--M   B__E--M--M--M
    如果层级过多，可以使用以下方式：
    B__E--M > B__E--M > B__E--M(最多3层B__E--M嵌套)
  
    // 推荐
    <div class="c-card"><!-- B -->
        <div class="c-card__header"><!-- B__E -->
            <h2 class="c-card-title"><!-- B__E > B -->
                <i class="c-card-title__icon--small"></i><!-- B__E > B__E--M -->
                <i class="c-card-title__icon--big"></i><!-- B__E > B__E--M -->
                <span class="c-card-title__text-wrap">Title text here</span><!-- B__E > B__E -->
            </h2>
        </div>
    </div>
    // 推荐
    .c-card {                      // B
  
        &__header {                // B__E
  
            > .c-card-title {      // B__E > B
  
                &__icon--small {   // B__E > B__E--M
  
                }
  
                &__icon--big {     // B__E > B__E--M
  
                }
  
                &__text-wrap {     // B__E > B__E
  
                }
            }
        }
  
    }
  
    // 不推荐
    <div class="c-card">
        <div class="c-card__header">
            <h2 class="c-card__header__title">
                <i class="c-card__header__title__icon"></i>
                <span class="c-card__header__title__text">Title text here</span>
            </h2>
        </div>
    </div>
  
    // 不推荐
    .c-card {
  
        &__header{
  
            &__title {
  
                &__icon {
  
                }
  
                &__text {
  
                }
            }
        }
    }
  
    - 注意到以上示例中使用了c- 前缀。这个c代表'component'，给组件加上命名空间，它提高了代码的可读性。
    类型 | 前缀 | 例子 | 描述
    布局 | (g-) | g-header | (global)例如头部，尾部，主体，侧栏等
    组件 | (c-) | c-card | (component)较大整体，如登录注册，搜索等
    元件 | (u-) | u-btn | 不可再分个体，例如按钮，input框等
    功能 | (f-) | f-clear | (function)使用频率较高样式，例如清除浮动
    皮肤 | (s-) | s-nav | (skin) 只包含皮肤的样式
    主线 | (ig-) | ig-header | (igoal)主线模块中组件Block的前缀
    审批 | (ap-) | ap-header | (approve)审批模块中组件Block的前缀
    ...
  ```

```
命名时需要注意的点：
- 规则命名中，一律采用小写加中划线的方式，不允许使用大写字母或_
- 命名避免使用中文拼音，应该采用更简明有语义的英文单词进行组合
- 命名注意缩写，但是不能盲目缩写
- 不允许通过1、2、3等序号进行命名
- 避免class与id重名
- class用于标识某一个类型的对象，命名必须言简意赅
- 尽可能提高代码模块的复用，样式尽量用组合的方式
- 公共样式名不得包含业务名称
```

- mixins命名

  - 见名知义
  - 小写加中划线，不允许出现大小字母或_

  ```
  // 不推荐
  @mixin button($background: green) {
  
  }
  // 不推荐
  @mixin buttonBg($background: green) {
  
  }
  // 不推荐
  @mixin button_bg($background: green) {
  
  }
  // 推荐
  @mixin button-bg($background: green) {
  
  }
  
  ```

  多个参数之间用逗号分隔，给参数设置默认值

# 7 重写规范

  我们不允许直接使用公共库的选择器进行重写，如果要进行重写，必须自己重新加一个新的选择器，并且，这个选择器不能对公共库有影响。