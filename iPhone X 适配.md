# iPhone X 适配

## Safe Area

- Safe Area 是 iOS 11 中推出的布局概念
- 用来取代 iOS 7 之后出现的 topLayoutGuide/bottomLayoutGuide 概念
- 其目的就是圈定一块区域，用来放置界面中的核心交互或展示组件，防止被各种 bar 还有刘海、圆角遮住

## 新的 viewport 属性和新的 CSS 变量

- 新的 viewport 属性：viewport-fit，可选 auto，contain 或 cover 三个值
- 新的 CSS 变量： constant(safe-area-inset-${direction})，标明了 Safe Area 与屏幕四周的距离

## 如何适配

- 依靠能力嗅探，只为开启了 Safe Area 布局的 webview 提供适配
  - 宿主 APP 不开启 Safe Area
    - 对于 iPhone X，webview 会形成矩形屏效果，上方和下方补黑色
    - 对于非 iPhone x，和原来没区别
  - 宿主 APP 开启 Safe Area
    - 在 HTML 的 viewport 中设置 viewport-fit=cover 属性
    - 在 CSS 中使用新的 constant(safe-area-inset-${direction}) 将会被支持


[具体参见](https://www.npmjs.com/package/enable-safe-area)
