## 1 代码风格

### 1.1 缩进与换行

#### [强制] 使用 `4` 个空格做为一个缩进层级，不允许使用 `2` 个空格 或 `tab` 字符。

解释： 对于非 HTML 标签之间的缩进，比如 script 或 style 标签内容缩进，与 script 或 style 标签的缩进同级。

示例：

```
<style>
/* 样式内容的第一级缩进与所属的 style 标签对齐 */
ul {
    padding: 0;
}
</style>
<ul>
    <li>first</li>
    <li>second</li>
</ul>
<script>
// 脚本代码的第一级缩进与所属的 script 标签对齐
require(['app'], function (app) {
    app.init();
});
</script>
```

### 1.2 命名

#### [强制] `class` 必须单词全字母小写，单词间以 `-` 分隔。

#### [强制] `class` 必须代表相应模块或部件的内容或功能，不得以样式信息进行命名。

示例：

```
<!-- good -->
<div class="sidebar"></div>

<!-- bad -->
<div class="left"></div>
```

#### [强制] 元素 `id` 必须保证页面唯一。

解释：

同一个页面中，不同的元素包含相同的 `id`，不符合 `id` 的属性含义。并且使用 `document.getElementById` 时可能导致难以追查的问题。

#### [建议] `id` 建议单词全字母小写，单词间以 `-` 分隔。同项目必须保持风格一致。

#### [建议] `id`、`class` 命名，在避免冲突并描述清楚的前提下尽可能短。

示例：

```
<!-- good -->
<div id="nav"></div>
<!-- bad -->
<div id="navigation"></div>

<!-- good -->
<p class="comment"></p>
<!-- bad -->
<p class="com"></p>

<!-- good -->
<span class="author"></span>
<!-- bad -->
<span class="red"></span>
```

#### [强制] 同一页面，应避免使用相同的 `name` 与 `id`。

解释：

IE 浏览器会混淆元素的 `id` 和 `name` 属性， `document.getElementById` 可能获得不期望的元素。所以在对元素的 `id` 与 `name` 属性的命名需要非常小心。

一个比较好的实践是，为 `id` 和 `name` 使用不同的命名法。

示例：

```
<input name="foo">
<div id="foo"></div>
<script>
// IE6 将显示 INPUT
alert(document.getElementById('foo').tagName);
</script>
```

### 1.3 标签

#### [强制] 标签名必须使用小写字母。

示例：

```
<!-- good -->
<p>Hello StyleGuide!</p>

<!-- bad -->
<P>Hello StyleGuide!</P>
```

#### [强制] 对于无需自闭合的标签，不允许自闭合。

解释：

常见无需自闭合标签有 `input`、`br`、`img`、`hr` 等。

示例：

```
<!-- good -->
<input type="text" name="title">

<!-- bad -->
<input type="text" name="title" />
```

#### [强制] 对 `HTML5` 中规定允许省略的闭合标签，不允许省略闭合标签。

解释：

对代码体积要求非常严苛的场景，可以例外。比如：第三方页面使用的投放系统。

示例：

```
<!-- good -->
<ul>
    <li>first</li>
    <li>second</li>
</ul>

<!-- bad -->
<ul>
    <li>first
    <li>second
</ul>
```

#### [强制] 标签使用必须符合标签嵌套规则。

解释：

比如 `div` 不得置于 `p` 中，`tbody` 必须置于 `table` 中。

#### [建议] 标签的使用应尽量简洁，减少不必要的标签。

示例：

```
<!-- good -->
<img class="avatar" src="image.png">

<!-- bad -->
<span class="avatar">
    <img src="image.png">
</span>
```

### 1.4 属性

#### [强制] 属性名必须使用小写字母。

示例：

```
<!-- good -->
<table cellspacing="0">...</table>

<!-- bad -->
<table cellSpacing="0">...</table>
```

#### [强制] 属性值必须用双引号包围。

解释：

不允许使用单引号，不允许不使用引号。

示例：

```
<!-- good -->
<script src="esl.js"></script>

<!-- bad -->
<script src='esl.js'></script>
<script src=esl.js></script>
```

#### [建议] 布尔类型的属性，建议不添加属性值。

示例：

```
<input type="text" disabled>
<input type="checkbox" value="1" checked>
```

#### [建议] 自定义属性建议以 `xxx-` 为前缀，推荐使用 `data-`。

解释：

使用前缀有助于区分自定义属性和标准定义的属性。

示例：

```
<ol data-ui-type="Select"></ol>
```

## 1通用

### 1.1 DOCTYPE

#### [强制] 使用 `HTML5` 的 `doctype` 来启用标准模式，建议使用大写的 `DOCTYPE`。

示例：

```
<!DOCTYPE html>
```

#### [建议] 在 `html` 标签上设置正确的 `lang` 属性。

解释：

有助于提高页面的可访问性，如：让语音合成工具确定其所应该采用的发音，令翻译工具确定其翻译语言等。

示例：

```
<html lang="zh-CN">
```

### 1.2 编码

#### [强制] 页面必须使用精简形式，明确指定字符编码。指定字符编码的 `meta` 必须是 `head` 的第一个直接子元素

示例：

```
<html>
    <head>
        <meta charset="UTF-8">
        ......
    </head>
    <body>
        ......
    </body>
</html>
```

#### [建议] `HTML` 文件使用无 `BOM` 的 `UTF-8` 编码。

解释：

`UTF-8` 编码具有更广泛的适应性。`BOM` 在使用程序或工具处理文件时可能造成不必要的干扰。

### 1.3 CSS 和 JavaScript 引入

#### [强制] 引入 `CSS` 时必须指明 `rel="stylesheet"`。

示例：

```
<link rel="stylesheet" href="page.css">
```

#### [建议] 展现定义放置于外部 `CSS` 中，行为定义放置于外部 `JavaScript` 中。

解释：

结构-样式-行为的代码分离，对于提高代码的可阅读性和维护性都有好处。

#### [建议] 在 `head` 中引入页面需要的所有 `CSS` 资源。

解释：

在页面渲染的过程中，新的CSS可能导致元素的样式重新计算和绘制，页面闪烁。

#### [建议] `JavaScript` 应当放在页面末尾，或采用异步加载。

解释：

将 `script` 放在页面中间将阻断页面的渲染。出于性能方面的考虑，如非必要，请遵守此条建议。

示例：

```
<body>
    <!-- a lot of elements -->
    <script src="init-behavior.js"></script>
</body>
```

## 3 head

### 3.1 title

#### [强制] 页面必须包含 `title` 标签声明标题。

#### [强制] `title` 必须作为 `head` 的直接子元素，并紧随 `charset` 声明之后。

解释：

`title` 中如果包含 ASCII 之外的字符，浏览器需要知道字符编码类型才能进行解码，否则可能导致乱码。

示例：

```
<head>
    <meta charset="UTF-8">
    <title>页面标题</title>
</head>
```

### 3.2 favicon

#### [强制] 保证 `favicon` 可访问。

解释：

在未指定 favicon 时，大多数浏览器会请求 Web Server 根目录下的 `favicon.ico` 。为了保证 favicon 可访问，避免 404，必须遵循以下两种方法之一：

1. 在 Web Server 根目录放置 `favicon.ico` 文件。
2. 使用 `link` 指定 favicon。

示例：

```
<link rel="shortcut icon" href="path/to/favicon.ico">
```

## 4 图片

#### [强制] 禁止 `img` 的 `src` 取值为空。延迟加载的图片也要增加默认的 `src`。

#### [建议] 避免为 `img` 添加不必要的 `title` 属性。

解释：

多余的 `title` 影响看图体验，并且增加了页面尺寸。

#### [建议] 为重要图片添加 `alt` 属性。

解释：

可以提高图片加载失败时的用户体验。

#### [建议] 添加 `width` 和 `height` 属性，以避免页面抖动。

#### [建议] 有下载需求的图片采用 `img` 标签实现，无下载需求的图片采用 CSS 背景图实现。

解释：

1. 产品 logo、用户头像、用户产生的图片等有潜在下载需求的图片，以 `img` 形式实现，能方便用户下载。
2. 无下载需求的图片，比如：icon、背景、代码使用的图片等，尽可能采用 CSS 背景图实现。

## 5 表单

### 5.1 控件标题

#### [强制] 有文本标题的控件必须使用 `label` 标签将其与其标题相关联。

解释：

有两种方式：

1. 将控件置于 `label` 内。
2. `label` 的 `for` 属性指向控件的 `id`。

推荐使用第一种，减少不必要的 `id`。如果 DOM 结构不允许直接嵌套，则应使用第二种。

示例：

```
<label><input type="checkbox" name="confirm" value="on"> 我已确认上述条款</label>

<label for="username">用户名：</label> <input type="textbox" name="username" id="username">
```

### 5.2 按钮

#### [强制] 使用 `button` 元素时必须指明 `type` 属性值。

解释：

`button` 元素的默认 `type` 为 `submit`，如果被置于 `form` 元素中，点击后将导致表单提交。为显示区分其作用方便理解，必须给出 `type` 属性。

示例：

```
<button type="submit">提交</button>
<button type="button">取消</button>
```

#### [建议] 尽量不要使用按钮类元素的 `name` 属性。

解释：

由于浏览器兼容性问题，使用按钮的 `name` 属性会带来许多难以发现的问题。具体情况可参考[此文](http://w3help.org/zh-cn/causes/CM2001)。

### 5.3 可访问性 

#### [建议] 负责主要功能的按钮在 DOM 中的顺序应靠前。

解释：

负责主要功能的按钮应相对靠前，以提高可访问性。如果在 CSS 中指定了 `float: right` 则可能导致视觉上主按钮在前，而 DOM 中主按钮靠后的情况。

示例：

```
<!-- good -->
<style>
.buttons .button-group {
    float: right;
}
</style>

<div class="buttons">
    <div class="button-group">
        <button type="submit">提交</button>
        <button type="button">取消</button>
    </div>
</div>

<!-- bad -->
<style>
.buttons button {
    float: right;
}
</style>

<div class="buttons">
    <button type="button">取消</button>
    <button type="submit">提交</button>
</div>
```

## 6 多媒体

#### [建议] 当在现代浏览器中使用 `audio` 以及 `video` 标签来播放音频、视频时，应当注意格式。

解释：

音频应尽可能覆盖到如下格式：

- MP3
- WAV
- Ogg

视频应尽可能覆盖到如下格式：

- MP4
- WebM
- Ogg

#### [建议] 在支持 `HTML5` 的浏览器中优先使用 `audio` 和 `video` 标签来定义音视频元素。

#### [建议] 只在必要的时候开启音视频的自动播放。