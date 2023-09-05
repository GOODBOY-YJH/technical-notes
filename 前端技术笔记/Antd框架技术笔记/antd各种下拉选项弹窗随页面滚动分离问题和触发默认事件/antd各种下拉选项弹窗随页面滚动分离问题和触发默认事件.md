### antd各种下拉选项弹窗使用时必须要添加getPopupContainer

原理:

> **getPopupContainer** 菜单渲染父节点。默认渲染到 body 上，而我们需要渲染到父节点上，例如鼠标移入事件，hover事件等，默认都不触发直接父元素相关事件。需要渲染到父节点后才会触发父节点默认事件。

例如：需要给右侧三个点增加样式，鼠标移入出现，鼠标移出消失（鼠标移入下拉弹窗时不消失）。  

![img](image/Image(8).png)
使用antd下拉菜单控件，要把getPopupContainer设置为:getPopupContainer="(node)=> node.parentNode"才能实现鼠标移入悬浮框时，三个点依然存在。  

![img](image/Image(2).png)
