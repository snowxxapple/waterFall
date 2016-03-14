# waterFall
**利用jQuery来实现的瀑布流布局**<br/>
1. **瀑布流布局思想**：根据浏览器可视区宽度，要显示的图片（等宽）的宽度，计算出一行可以放的图片数；设置所有图片为向左浮动；遍历所有的图片，把第一行的图片存放到数组colHeight中，将第二行要放的图片，放到colHeight中最小值图片对应位置的下方，设置定位为绝对定位，高度为上一行最小值，横坐标为对应的上一行图片的横坐标，之后更新colHeight的值，将最小值加上刚放置图片的高度，继续寻找最小值，以此类推。<br/>
如果鼠标的滚动距离$(window).scrollTop()加上可视区的高度$(window).height()大于最后一个盒子的offsettop+图片自身,距离的一半，则自动加载图片。<br/>
2. 将要加载图片的名字写在了.json文件中，利用ajax模拟从后台读取数据，加载文件的过程。<br/>
3. jQuery的width()<innerWidth()<outerWidth()<outerWidth(true) <br/>
4. apply(obj,arguments)<br/>
```javascript
Math.min.apply(null,colHeight);//找到数组colHeight中的最小值
```
Math.min(para)中参数列表只能是(para1,para2,para3,....)，而apply可以把数组转化成参数列表
5. **apply详解**
* apply:能够劫持另外一个对象的方法，继承另外一个对象的属性<br>/
function.apply(obj,args)<br/>
obj:代替function 里面的this对象<br/>
args:数组形式的参数列表，将数组转化为参数列表后传递给function  [para1,para2,para3,.....]-->(para1,para2,para3,....)<br/>
call: 和apply意思一样，只是参数列表不一样call(obj,args),args只能是普通的参数列表<br/>
6. **apply妙用**
* 可以将数组转化成参数列表<br/>
```javascript
Math.max.apply(null,arr)//找到数组中的最大值
Math.min.apply(null,arr)//找到数组中的最小值
```
* 合并两个数组.push()
arr.push(para1,para2...)只接受参数列表,没有提供push一个数组。eg:
```javascript
var arr1=new Array('1','2','3');
var arr2=new Array('4','5','6');
arr1.push.apply(arr1,arr2);//arr1-->[1,2,3,4,5,,6]
```
arr1调用apply方法，将arr2数组转化成参数列表，之后arr1调用push方法，将已经转化成参数列表的arr2,push到arr1的尾部
