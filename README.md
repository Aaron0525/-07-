# -07-
String与Stringbuilder设计到的效率问题
分别用String和Stringbuilder创建一个字符串，并往这个歌字符串里面加字符"a"，测试加10000、20000、30000.......100000,分别所用的时间，并将得到数据在excel中做成散点图，观察加相同次数下，String与Stringbuilder所用的时间。

通过散点图可以看出，加相同次数下，Stringbuilder所用的时间比String要少，几乎少三个数量级。那么这是为什么呢？

第一点，利用Stringbuilder中的append方法给定义的变量temp加字符"a"时,只是将字符a直接加到temp的value中。而String+=“a”，这种方法去加字符串，String每加一次就会创建一个对象，哪怕只是更改一点也会创建新的对象，而Stringbuilder没有这个过程。

第二点，创建的对象多了，垃圾回收就多了，垃圾回收的过程也占据了一部分时间。
