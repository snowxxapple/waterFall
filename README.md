# waterFall
**利用jQuery来实现的瀑布流布局**<br/>
**瀑布流布局思想**：根据浏览器可视区宽度，要显示的图片（等宽）的宽度，计算出一行可以放的图片数；设置所有图片为向左浮动；遍历所有的图片，
把第一行的图片存放到数组colHeight中，将第二行要放的图片，放到colHeight中最小值图片对应位置的下方，设置定位为绝对定位，高度为上一行
最小值，横坐标为对应的上一行图片的横坐标，之后更新colHeight的值，将最小值加上刚放置图片的高度，继续寻找最小值，以此类推。<br/>
该文件同时利用了鼠标滚轮事件，如果鼠标的滚动距离$(window).scrollTop()加上可视区的高度$(window).height()大于最后一个盒子的offsettop+图片自身
距离的一半，则加载图片<br/>
将要加载图片的名字写在了.json文件中，利用ajax模拟从后台读取数据，加载文件的过程。<br/>
**jQuery的width()<innerWidth()<outerWidth()<outerWidth(true)**
