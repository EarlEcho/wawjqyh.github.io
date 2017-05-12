# 概览

## 会改变自身的方法

下面的这些方法会改变调用它们的对象自身的值：

`copyWithin() *`<br>
在数组内部，将一段元素序列拷贝到另一段元素序列上，覆盖原有的值。

`fill() *`<br>
将数组中指定区间的所有元素的值，都替换成某个固定的值。

`pop()`<br>
删除数组的最后一个元素，并返回这个元素。

`push()`<br>
在数组的末尾增加一个或多个元素，并返回数组的新长度。

`reverse()`<br>
颠倒数组中元素的排列顺序，即原先的第一个变为最后一个，原先的最后一个变为第一个。

`shift()`<br>
删除数组的第一个元素，并返回这个元素。

`unshift()`<br>
在数组的开头增加一个或多个元素，并返回数组的新长度。

`sort()`<br>
对数组元素进行排序，并返回当前数组。

`splice()`<br>
在任意的位置给数组添加或删除任意个元素。





## 不会改变自身的方法
下面的这些方法绝对不会改变调用它们的对象的值，只会返回一个新的数组或者返回一个其它的期望值。

`concat()`<br>
返回一个由当前数组和其它若干个数组或者若干个非数组值组合而成的新数组。

`includes() *`<br>
判断当前数组是否包含某指定的值，如果是返回 true，否则返回 false。

`join()`<br>
连接所有数组元素组成一个字符串。

`slice()`<br>
抽取当前数组中的一段元素组合成一个新数组。

`toString()`<br>
返回一个由所有数组元素组合而成的字符串。遮蔽了原型链上的 Object.prototype.toString() 方法。

`toLocaleString()`<br>
返回一个由所有数组元素组合而成的本地化后的字符串。遮蔽了原型链上的 Object.prototype.toLocaleString() 方法。

`indexOf()`<br>
返回数组中第一个与指定值相等的元素的索引，如果找不到这样的元素，则返回 -1。

`lastIndexOf()`<br>
返回数组中最后一个（从右边数第一个）与指定值相等的元素的索引，如果找不到这样的元素，则返回 -1。





## 遍历方法
在下面的众多遍历方法中，有很多方法都需要指定一个回调函数作为参数。在回调函数执行之前，数组的长度会被缓存在某个地方，所以，
如果你在回调函数中为当前数组添加了新的元素，那么那些新添加的元素是不会被遍历到的。此外，如果在回调函数中对当前数组进行了其它修改，
比如改变某个元素的值或者删掉某个元素，那么随后的遍历操作可能会受到未预期的影响。总之，不要尝试在遍历过程中对原数组进行任何修改，
虽然规范对这样的操作进行了详细的定义，但为了可读性和可维护性，请不要这样做。

`Array.prototype.forEach()`<br>
为数组中的每个元素执行一次回调函数。

`Array.prototype.entries() *`<br>
返回一个数组迭代器对象，该迭代器会包含所有数组元素的键值对。

`Array.prototype.every()`<br>
如果数组中的每个元素都满足测试函数，则返回 true，否则返回 false。

`Array.prototype.some()`<br>
如果数组中至少有一个元素满足测试函数，则返回 true，否则返回 false。

`Array.prototype.filter()`<br>
将所有在过滤函数中返回 true 的数组元素放进一个新数组中并返回。

`Array.prototype.find() *`<br>
找到第一个满足测试函数的元素并返回那个元素的值，如果找不到，则返回 undefined。

`Array.prototype.findIndex() *`<br>
找到第一个满足测试函数的元素并返回那个元素的索引，如果找不到，则返回 -1。

`Array.prototype.keys() *`<br>
返回一个数组迭代器对象，该迭代器会包含所有数组元素的键。

`Array.prototype.map()`<br>
返回一个由回调函数的返回值组成的新数组。

`Array.prototype.reduce()`<br>
从左到右为每个数组元素执行一次回调函数，并把上次回调函数的返回值放在一个暂存器中传给下次回调函数，并返回最后一次回调函数的返回值。

`Array.prototype.reduceRight()`<br>
从右到左为每个数组元素执行一次回调函数，并把上次回调函数的返回值放在一个暂存器中传给下次回调函数，并返回最后一次回调函数的返回值。

`Array.prototype.values() *`<br>
返回一个数组迭代器对象，该迭代器会包含所有数组元素的值。

`Array.prototype[@@iterator]() *`<br>
和上面的 values() 方法是同一个函数。





## 通用方法
在 `JavaScript` 中，很多的数组方法被故意设计成是通用的。也就是说，那些看起来像是数组的对象（类数组对象），即拥有一个 `length` 属性，
以及对应的索引属性（也就是数字类型的属性，比如 `obj[5]`）的非数组对象也是可以调用那些数组方法的。其中一些数组方法，比如说 `join` 方法，
它们只会单纯的读取当前对象的 length 属性和索性属性的值，并不会尝试去改变这些属性的值。而另外一些数组方法，比如说 `reverse` 方法，
它们会尝试修改那些属性的值，因此，如果当前对象是个 `String` 对象，那么这些方法在执行时就会报错，因为字符串对象的 `length` 属性和索引属性都是只读的。