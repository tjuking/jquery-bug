jquery-bug
==========

jQuery问题研究

- `.get(num)`的返回内容为`num < 0 ? this[ this.length + num ] : this[ num ]`，但num为负值且其绝对值大于当前元素集的个数时，就会有问题。可以改成这种返回值，`num < 0 ? this[ this.length + num % this.length ] : this[ num ]`
- `.isWindow(obj)`用于判断是否为window对象，返回内容为`obj != null && obj == obj.window`。如果传入参数为如下就会有问题，`var obj = {}; obj.window = obj;`（是否有更合适的方法？）
- 在IE8-浏览器中`.isFunction(obj)`无法判断DOM相关操作方法或类似于`alert()`这样的方法（由于这些浏览器将这些方法在应用`Object.prototype.toString(obj)`时返回值不为`[object Function]`）
