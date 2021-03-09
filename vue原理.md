1.获取data，创建依赖实例，通过Object.defineProperty劫持getters，setter

2.触发get时，添加观察者Dep.target(wather实例）到依赖数组deps中

3.触发set时，触发依赖实例的notify方法，更新dom

4.创建文档片段，遍历dom节点，正则匹配，匹配到时，如果是v-model，监听事件，在输入完后更新对应的data，实现数据从dom=>data的更新。
然后创建观察者watcher，触发update方法，替换内容。并且watcher赋值给Dep.target,存入依赖容器数组deps。

5.由于get就把观察者都存入依赖数组了，所以实现data=>dom的更新

5.再返回文档中