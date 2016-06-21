Array.prototype.slice()
slice() 是一个非常重要的方法,很多地方都会用到。
顾名思义,slice函数返回一个array被切割的一部分, 但是很重要的一点是slice函数不会去修改原array, 它会返回一个新的array。
slice除了用于最基本的'切割'功能,还有其他重要的应用场合,接下来就一一展开:

1: 切割array
arr.slice(indexBegin, indexEnd)
 indexBegin:
    B1: 以0为基础, 切割开始的地方,最终的结果包含此indexBegin的元素
    B2: 如果indexBegin是一个负数(slice(-3)),那就从array的末尾开始切割3个元素
    B3: 如果indexBegin是undefined, 那么indexBegin = 0
 indexEnd:
    E1: 以0为基础,切割结束的坐标,但是不包括这个坐标的元素本身。
    E2: 如果indexEnd是一个负数(slice(0, -2)), 就是舍弃掉原array的倒数两个元素
    E3: 如果省略indexEnd(slice(1)), 最终结果就是从下标为1的元素到原array的最后

 接下来对以上总共六点进行代码验证
  B1: [0, 1, 2, 3, 4].slice(0)         //[0, 1, 2, 3, 4]
  B2: [0, 1, 2, 3, 4].slice(-3)        //[2, 3, 4]
  B3: [0, 1, 2, 3, 4].slice(undefined) //[0, 1, 2, 3, 4]

  E1: [0, 1, 2, 3, 4].slice(0, 2)     //[0, 1]
  E2: [0, 1, 2, 3, 4].slice(0, -2)    //[0, 1, 2]
  E3: [0, 1, 2, 3, 4].slice(1)        //[1, 2, 3, 4]

2: 对于 object reference 为数组成员来说,slice 复制的是object的reference, 所以一旦原object修改了,那原数组和新数组都会跟着修改。
  var apple = {color: 'red'};
  var fruitBasket = [apple, {}, {}];
  var newFruitBasket = fruitBasket.slice(0, 2);

  console.log(fruitBasket[0].color); //'red'
  console.log(newFruitBasket[0].color); //'red'

  apple.color = 'green';
  console.log(fruitBasket[0].color); //'green'
  console.log(newFruitBasket[0].color); //'green'



