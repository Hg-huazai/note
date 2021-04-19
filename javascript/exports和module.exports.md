### exports 和 module.exports 的区别

- 每个模块中都有一个module 对象
- module 对象总有一个expore 对象
- 我们可以把需要导出的成员都挂载到module.exports 接口对象中
- 也就是： ‘module.exports.xxx = xxx’  的方式
- 但是每次都‘module.exports.xxx = xxx’ 很麻烦，点有点太多了
- 所以 Node 为了方便，同时在每一个模块中都提供了一个成员叫：‘exports’ （var exports = module.exports）
- exports === module.exports   结果为true
- 所以对于： ’module.exports.xxx = xxx‘ 的方式  完全可以：'exports.xxx = xxx'
- 当一个模块需要导出单个成员的时候,这个时候必须使用:'module.exports = xxx'的方式
  - 这会断开exports以module.exports的引用
- 不要使用'exports = xxx' 不管用
  - 这会断开exports以module.exports的引用
- 因为每个模块最终向外 'return' 的是 'module.exports'
- 而 ‘exports’ 只是 ‘module.exports’ 的一个引用
- 所以即便你为‘exportst = xxx’ 重新赋值，也不会影响‘module.exports’
- 但是有一种赋值比较特殊： ‘exports = module.exporst’ 这个用来重新建立引用关系的
- node是一个比肩 java、php的一个平台