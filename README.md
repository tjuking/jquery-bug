jquery-bug
==========

jQuery问题研究

- `.get(num)`的返回内容为`num < 0 ? this[ this.length + num ] : this[ num ]`，但num为负值且其绝对值大于当前元素集的个数时，就会有问题。可以改成这种返回值，`num < 0 ? this[ this.length + num % this.length ] : this[ num ]`
