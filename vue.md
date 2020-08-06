## 1.请说一下响应式数据的理解？
    vue的响应式原理使用Object.defineProperty对data中的每个属性循环递归并重新定义get和set方法，当在定义get方法是通过给每个属性存放一个dep类进行依赖收集存放对应watcher，当去set跟新时从dep中依次取出对应收集的watcher并触发watcher的跟新方法重新执行render并跟新视图
    
## 2.Vue中如何检测数组变化？
    处于对数组中元素递归性能考虑，通过函数劫持重写了数组原有的push/pop/shift/unshift/reverse/sort/splice并继承原数组类，并在重写方法中为跟新的属性添加观测，使其也达到响应式效果