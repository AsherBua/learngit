**JavaScript**
indexOf() 方法可返回某个指定的字符串值在字符串中**首次**出现的位置。
通过字符串创建一个数组：var myArr = Array.from("RUNOOB");
js 脚本的运行环境有浏览器环境和 Node.js 两种，根据 Node.js 官方网站的介绍，Node.js is a JavaScript runtime built on Chrome's V8 JavaScript engine.调用了 Document 类型提供的方法 getElementById()，属于 DOM 的应用，但是对于 DOM 和 BOM 的操作只有在浏览器环境下才能进行，

字符串：var carname = **"Volvo XC60"**;
数组：var myCars=**["Saab","Volvo","BMW"]**
对象：var car = **{name:"Fiat", model:500, color:"white"}**;
1. ctrl+shift+i 打开chrome developer tool

2. 注释://, /*.......*/

3. 使用console.log()代替alert()的好处是可以避免弹出烦人的对话框。

4. 数据类型：
    NaN; // NaN表示Not a Number，当无法计算结果时用NaN表示
    Infinity; // 表示无限大，当数值超过了JavaScript的Number所能表示的最大值时，就表示为Infinity
    true,false, &&(and),||(or),!(非运算)
    **比较**：实际上，JavaScript允许对任意数据类型做比较：
    要特别注意相等运算符==。JavaScript在设计时，有两种比较运算符：
    第一种是==比较，它会自动转换数据类型再比较，很多时候，会得到非常诡异的结果；
    第二种是===比较，它不会自动转换数据类型，如果数据类型不一致，返回false，如果一致，再比较。
    **由于JavaScript这个设计缺陷，不要使用==比较，始终坚持使用===比较。**
    **另一个例外是NaN这个特殊的Number与所有其他值都不相等，包括它自己：**
    唯一能判断NaN的方法是通过isNaN()函数：isNaN(NaN); // true
    **注意浮点数的相等比较：**
    `1 / 3 === (1 - 2 / 3); // false`
    这不是JavaScript的设计缺陷。浮点数在运算过程中会产生误差，因为计算机无法精确表示无限循环小数。要比较两个浮点数是否相等，只能计算它们之差的绝对值，看是否小于某个阈值:
    `Math.abs(1 / 3 - (1 - 2 / 3)) < 0.0000001; // true`
    **null 和 undefined**
    null表示一个“空”的值，它和0以及空字符串''不同，0是一个数值，''表示长度为0的字符串，而null表示“空”。大多数情况下，我们都应该用null。undefined仅仅在判断函数参数是否传递的情况下有用。
    **数组**
    `a=[1,2,'hello',null,true];//出于代码的可读性考虑，强烈建议直接使用[]。
    new Array(1,2,3) // 创建了数组[1, 2, 3]
    a[0] // 返回索引为0的元素，即1`
    **对象**
    JavaScript的对象是一组由键-值组成的无序集合，例如：
    `var person = {
   name: 'Bob',
   age: 20,
   tags: ['js', 'web', 'mobile'],
   city: 'Beijing',
   hasCar: true,
   zipcode: null
    };`
    **JavaScript对象的键都是字符串类型**，值可以是任意数据类型。上述person对象一共定义了6个键值对，其中**每个键又称为对象的属性，例如，person的name属性为'Bob'，zipcode属性为null。**
    `person.name; // 'Bob'
    person.zipcode; // null`
    **变量**
    变量在JavaScript中就是用一个变量名表示，变量名是大小写英文、数字、$和_的组合，且不能用数字开头。变量名也不能是JavaScript的关键字，如if、while等。申明一个变量用var语句，比如：
    var s_007 = '007'
    在JavaScript中，使用等号=对变量进行赋值。可以把任意数据类型赋值给变量，同一个变量可以反复赋值，而且可以是不同类型的变量，但是要注意只能用var申明一次，例如：
    `var a = 123; // a的值是整数123
   a = 'ABC'; // a变为字符串`
    **这种变量本身类型不固定的语言称之为动态语言，与之对应的是静态语言。静态语言在定义变量时必须指定变量类型，如果赋值的时候类型不匹配，就会报错。**
    **use strict**
    在strict模式下运行的JavaScript代码，强制通过var申明变量，未使用var申明变量就使用的，将导致运行错误。`'use strict';`

5. **字符串**
    JavaScript的字符串就是用''或""括起来的字符表示。
    如果'本身也是一个字符，那就可以用""括起来。如果字符串内部既包含'又包含"怎么办？可以用转义字符\来标识，比如：
    `'I\'m \"OK\"!';`
    转义字符\可以转义很多字符，比如\n表示换行，\t表示制表符，字符\本身也要转义，所以\\表示的字符就是\。
    ASCII字符可以以\x##形式的十六进制表示，例如：`'\x41'; // 完全等同于 'A'`
    还可以用\u####表示一个Unicode字符：`'\u4e2d\u6587'; // 完全等同于 '中文'`
    由于多行字符串用\n写起来比较费事，所以最新的ES6标准新增了一种多行字符串的表示方法，用反引号表示(typora里code用的那个)
    **模板字符串**
    要把多个字符串连接起来，可以用+号连接：`var message = '你好, ' + name + ', 你今年' + age + '岁了!';`
    如果有很多变量需要连接，用+号就比较麻烦。ES6新增了一种模板字符串：`var message = `你好, ${name}, 你今年${age}岁了!`;`
    **操作字符串**
    `var s = 'Hello, world!';//字符串
    s.length;`
    要获取字符串某个指定位置的字符，使用类似Array的下标操作，索引号从0开始：`s[0];`
    **需要特别注意的是，字符串是不可变的，如果对字符串的某个索引赋值，不会有任何错误，但是，也没有任何效果。**JavaScript为字符串提供了一些常用方法，注意，调用这些方法本身不会改变原有字符串的内容，而是返回一个新字符串：
    `s.toUpperCase()
    s.indexOf('world') //会搜索指定字符串出现的位置,没有找到指定的子串，返回-1
    var s = 'hello, world'
    s.substring(0, 5); // 返回指定索引区间的子串，从索引0开始到5（不包括5），返回'hello'`
    **数组（Array)**
    `var arr = [1, 2, 3.14, 'Hello', null, true];
    `arr.length; // 6`

6. 直接给Array的length赋一个新的值会导致Array大小的变化:
    var arr = [1, 2, 3];
    arr.length; // 3
    arr.length = 6;
    arr; // arr变为[1, 2, 3, undefined, undefined, undefined]
    arr.length = 2;
    arr; // arr变为[1, 2]`

7. Array可以通过索引把对应的元素修改为新的值：
    `var arr = ['A', 'B', 'C'];
    arr[1] = 99;
    arr; // arr现在变为['A', 99, 'C']`
    **请注意，如果通过索引赋值时，索引超过了范围，同样会引起Array大小的变化：**
    `var arr = [1, 2, 3];
    arr[5] = 'x';
    arr; // arr变为[1, 2, 3, undefined, undefined, 'x']`

8. **indexOf**: 与String类似，Array也可以通过indexOf()来搜索一个指定的元素的位置：
    `var arr = [10, 20, '30', 'xyz'];
    arr.indexOf(10); // 元素10的索引为0`

9. **slice()**就是对应String的substring()版本，它截取Array的部分元素，然后返回一个新的Array：
    `var arr = ['A', 'B', 'C', 'D', 'E', 'F', 'G'];
    arr.slice(0, 3); // 从索引0开始，到索引3结束，但不包括索引3: ['A', 'B', 'C']
    arr.slice(3); // 从索引3开始到结束: ['D', 'E', 'F', 'G']`
    **如果不给slice()传递任何参数，它就会从头到尾截取所有元素。利用这一点，我们可以很容易地复制一个Array：**
    `var arr = ['A', 'B', 'C', 'D', 'E', 'F', 'G'];
    var aCopy = arr.slice();
    aCopy; // ['A', 'B', 'C', 'D', 'E', 'F', 'G']
    aCopy === arr; // false`

10. **push和pop**:push()向Array的末尾添加若干元素，pop()则把Array的最后一个元素删除掉：
    `var arr = [1, 2];
    arr.push('A', 'B'); // 返回Array新的长度: 4
    arr; // [1, 2, 'A', 'B']
    arr.pop(); // pop()返回'B'
    arr; // [1, 2, 'A'] 
    //空数组继续pop不会报错，而是返回undefined`

11. **unshift和shift**:如果要往Array的头部添加若干元素，使用unshift()方法，shift()方法则把Array的第一个元素删掉
      `var arr = [1, 2];
      arr.unshift('A', 'B'); // 返回Array新的长度: 4
      arr; // ['A', 'B', 1, 2]
      arr.shift(); // 'A'
      arr; // ['B', 1, 2]`

12. **sort**: 可以对当前Array进行排序，它会直接修改当前Array的元素位置，直接调用时，按照默认顺序排序：
      `var arr = ['B', 'C', 'A'];
      arr.sort();
      arr; // ['A', 'B', 'C']`

13. **reverse**:reverse()把整个Array的元素给调个个，也就是反转：
      `var arr = ['one', 'two', 'three'];
      arr.reverse(); 
      arr; // ['three', 'two', 'one']`

14. **splice**:它可以从指定的索引开始删除若干元素，然后再从该位置添加若干元素：
      `var arr = ['Microsoft', 'Apple', 'Yahoo', 'AOL', 'Excite', 'Oracle'];
      // 从索引2开始删除3个元素,然后再添加两个元素:
      arr.splice(2, 3, 'Google', 'Facebook'); // 从第二个数开始，删除3个。返回删除的元素 ['Yahoo', 'AOL', 'Excite']
      arr; // ['Microsoft', 'Apple', 'Google', 'Facebook', 'Oracle']
      // 只删除,不添加:
      arr.splice(2, 2); // 从第二个数开始，删除两个 ['Google', 'Facebook'] 
      arr; // ['Microsoft', 'Apple', 'Oracle']
      // 只添加,不删除:
      arr.splice(2, 0, 'Google', 'Facebook'); //从第二个数开始，删除0个。 返回[],因为没有删除任何元素
      arr; // ['Microsoft', 'Apple', 'Google', 'Facebook', 'Oracle']`

15. **concat**:concat()方法把当前的Array和另一个Array连接起来，并返回一个新的Array：
    `var arr = ['A', 'B', 'C'];
    var added = arr.concat([1, 2, 3]);
    added; // ['A', 'B', 'C', 1, 2, 3] 添加到了added 数组里
    arr; // ['A', 'B', 'C'] concat()方法并没有修改当前Array，而是返回了一个新的Array。`
    实际上，concat()方法可以接收任意个元素和Array，并且自动把Array拆开，然后全部添加到新的Array里:
    `var arr = ['A', 'B', 'C'];
    b=arr.concat(1, 2, [3, 4]); // ['A', 'B', 'C', 1, 2, 3, 4]`

16. **join**:把当前Array的每个元素都用指定的字符串连接起来，然后返回连接后的字符串,如果Array的元素不是字符串，将自动转换为字符串后再连接：
    `var arr = ['A', 'B', 'C', 1, 2, 3];
    arr.join('-'); // 'A-B-C-1-2-3'`

17. **多维数组**
    如果数组的某个元素又是一个Array，则可以形成多维数组，例如：
    `var arr = [[1, 2, 3], [400, 500, 600], '-'];`
    <font color='red'> var arr = [[1, 2, 3], [400, 500, 600], '-'];
    arr[0,1] // [400, 500, 600] why???</font>
18. `a='welcome'+arr.sort().slice(0,3)+'and'+arr.sort().slice(3)
'welcome大军,小明,小红and阿黄'`

**对象**
1. JavaScript的对象是一种无序的集合数据类型，它由若干**键值对**组成。{}
`var xiaoming = {
    name: '小明', //key:value
    birth: 1990,
    school: 'No.1 Middle School',
    height: 1.70,
    weight: 65,
    score: null
};
xiaoming.name; // '小明'`
2. 访问属性是通过.操作符完成的，但这要求属性名必须是一个有效的变量名。如果属性名包含特殊字符，就必须用''括起来：
`var xiaohong = {
    name: '小红',
    'middle-school': 'No.1 Middle School'
};`
xiaohong的属性名middle-school不是一个有效的变量，就需要用''括起来。访问这个属性也无法使用.操作符，**必须用['xxx']来访问**：
`xiaohong['middle-school']; // 'No.1 Middle School'
xiaohong['name']; // '小红'//注意区别！！
xiaohong.name; // '小红'`
3. 由于JavaScript的对象是动态类型，你可以自由地给一个对象添加或删除属性：
`var xiaoming = {
    name: '小明'
};
xiaoming.age; // undefined
xiaoming.age = 18; // 新增一个age属性
delete xiaoming.age; // 删除age属性
xiaoming.age; // undefined
delete xiaoming.school; // 删除一个不存在的school属性也不会报错`
4. 如果我们要检测xiaoming是否拥有某一属性，可以用in操作符：
`'name' in xiaoming; // true
'grade' in xiaoming; // false`
不过要小心，如果in判断一个属性存在，这个属性不一定是xiaoming的，它可能是xiaoming继承得到的：`'toString' in xiaoming; // true`因为toString定义在object对象中，而所有对象最终都会在原型链上指向object，所以xiaoming也拥有toString属性。
要判断一个属性是否是xiaoming自身拥有的，而不是继承得到的，可以用**hasOwnProperty()方法**：
`var xiaoming = {
    name: '小明'
};
xiaoming.hasOwnProperty('name'); // true
xiaoming.hasOwnProperty('toString'); // false`

**条件判断**
`var age = 3;
if (age >= 18) {
    alert('adult');
} else if (age >= 6) {
    alert('teenager');
} else {
    alert('kid');
}`
**JavaScript把null、undefined、0、NaN和空字符串''视为false，其他值一概视为true**

**循环**
1. 遍历数组：
    `var arr = ['Apple', 'Google', 'Microsoft'];
    var i, x;
    for (i=0; i<arr.length; i++) {
   x = arr[i];
   console.log(x);
    }`

2. for循环的3个条件都是可以省略的，如果没有退出循环的判断条件，就必须使用break语句退出循环，否则就是死循环：
    var x = 0;
    `for (;;) { // 将无限循环下去
   if (x > 100) {
       break; // 通过if判断来退出循环
   }
   x ++;
    }`

3. for...in: for循环的一个变体是for ... in循环，它可以把一个对象的所有属性依次循环出来:
    `var o = {
   name: 'Jack',
   age: 20,
   city: 'Beijing'
    };
    for (var key in o) {
   if (o.hasOwnProperty(key)) {//要过滤掉对象继承的属性，用hasOwnProperty()来实现：
       console.log(key); // 'name', 'age', 'city'
   }
    }`

4. 由于Array也是对象，而它的每个元素的索引被视为对象的属性，因此，for ... in循环可以直接循环出Array的索引：
`var a = ['A', 'B', 'C'];
for (var i in a) {
    console.log(i); // '0', '1', '2'
    console.log(a[i]); // 'A', 'B', 'C'
}`
**请注意，`for ... in`对`Array(数组）`的循环得到的是`String`而不是`Number`。**

5. while:
    `var x = 0;
    var n = 99;
    while (n > 0) {
   x = x + n;
   n = n - 2;//在循环内部变量n不断自减，直到变为-1时，不再满足while条件，循环退出
    }
    x; // 2500`

6. do...while:它和while循环的唯一区别在于，不是在每次循环开始的时候判断条件，而是**在每次循环完成的时候判断条件**。 用do { ... } while()循环要小心，循环体会至少执行1次，而for和while循环则可能一次都不执行：
    `var n = 0;
    do {
   n = n + 1;//至少执行一次
    } while (n < 100);
    n; // 100`
    **Map**:JavaScript的默认对象表示方式{}键必须是字符串。但实际上Number或者其他数据类型作为键也是非常合理的。Map是一组键值对的结构，具有极快的查找速度。
    `var m = new Map([['Michael', 95], ['Bob', 75], ['Tracy', 85]]);
    m.get('Michael'); // 95`

7. 初始化Map需要一个二维数组，或者直接初始化一个空Map。Map具有以下方法：
    `var m = new Map(); // 空Map
    m.set('Adam', 67); // 添加新的key-value
    m.set('Bob', 59);
    m.has('Adam'); // 是否存在key 'Adam': true
    m.get('Adam'); // 67
    m.delete('Adam'); // 删除key 'Adam'
    m.get('Adam'); // undefined`
    **由于一个key只能对应一个value，所以，多次对一个key放入value，后面的值会把前面的值冲掉**
    **Set**
    Set和Map类似，也是一组key的集合，但不存储value。由于key不能重复，所以，在Set中，没有重复的key。要创建一个Set，需要提供一个Array作为输入，或者直接创建一个空Set：
    `var s1 = new Set(); // 空Set
    var s2 = new Set([1, 2, 3]); // 含1, 2, 3`
    重复元素在Set中自动被过滤：
    `var s = new Set([1, 2, 3, 3, '3']);
    s; // Set {1, 2, 3, "3"}`
    通过add(key)方法可以添加元素到Set中，可以重复添加，但不会有效果：
    `s.add(4);
    s; // Set {1, 2, 3, 4}
    s.add(4);
    s; // 仍然是 Set {1, 2, 3, 4}`
    通过delete(key)方法可以删除元素：`s.delete(3);`
    **iterable**: 遍历Array可以采用下标循环，遍历Map和Set就无法使用下标。为了统一集合类型，ES6标准引入了新的iterable类型，Array、Map和Set都属于iterable类型。具有iterable类型的集合可以通过新的for ... of循环来遍历。
    `var m = new Map([[1, 'x'], [2, 'y'], [3, 'z']]);
    for (var x of m) { // 遍历Map
   console.log(x[0] + '=' + x[1]);
    }`
    直接使用iterable内置的forEach方法，它接收一个函数，每次迭代就自动回调该函数:
    arrary:
    `a.forEach(function (element, index, array) {
   // element: 指向当前元素的值
   // index: 指向当前索引
   // array: 指向Array对象本身
   console.log(element + ', index = ' + index);
    });`
    set:
    `var s = new Set(['A', 'B', 'C']);
    s.forEach(function (element, sameElement, set) {
   console.log(element);
    });`
    map:
    `var m = new Map([[1, 'x'], [2, 'y'], [3, 'z']]);
    m.forEach(function (value, key, map) {
   console.log(value);
    });`

**函数**
1. JavaScript的函数也是一个对象,abs()函数实际上是一个函数对象:
`function abs(x) { //function指出这是一个函数定义；
    if (x >= 0) { //abs是函数的名称；
        return x; //(x)括号内列出函数的参数，多个参数以,分隔；
    } else {      //函数体内部的语句在执行时，一旦执行到return时，函数就执行完毕，并将结果返回.如果没有return语句，函数执行完毕后也会返回结果，只是结果为undefined。
        return -x;
    }
}`
function (x) { ... }是一个匿名函数，它没有函数名。但是，**这个匿名函数赋值给了变量abs，所以，通过变量abs就可以调用该函数**:
`var abs = function (x) {
    if (x >= 0) {
        return x;
    } else {
        return -x;
    }
};`
上述两种定义完全等价，注意第二种方式按照完整语法需要在函数体末尾加一个;，表示赋值语句结束。
2. 调用函数:abs(10);
可以对参数进行检查：
`function abs(x) {
    if (typeof x !== 'number') {//typeof 检测变量的数据类型
        throw 'Not a number';
    }
    if (x >= 0) {
        return x;
    } else {
        return -x;
    }
}`
3. arguments：**它只在函数内部起作用**，并且永远指向当前函数的调用者传入的所有参数。arguments类似Array但它不是一个Array：
`function foo(x) {
    console.log('x = ' + x); // 10
    for (var i=0; i<arguments.length; i++) {
        console.log('arg ' + i + ' = ' + arguments[i]); // 10, 20, 30
    }
}
foo(10, 20, 30);`
利用arguments，你可以获得调用者传入的所有参数。也就是说，即使函数不定义任何参数，还是可以拿到参数的值：
function abs() {
    if (arguments.length === 0) {
        return 0;
    }
    var x = arguments[0];
    return x >= 0 ? x : -x;//if 语句的简捷形式,true执行x，false执行-x
}
abs(); // 0
abs(10); // 10
abs(-9); // 9
arguments最常用于判断传入参数的个数。你可能会看到这样的写法：
`// foo(a[, b], c)
// 接收2~3个参数，b是可选参数，如果只传2个参数，b默认为null：
function foo(a, b, c) {
    if (arguments.length === 2) {
        // 实际拿到的参数是a和b，c为undefined
        c = b; // 把b赋给c
        b = null; // b变为默认值
    }
    // ...
}`要把中间的参数b变为“可选”参数，就只能通过arguments判断，然后重新调整参数并赋值。
4. rest参数：
rest参数只能写在最后，前面用...标识，从运行结果可知，传入的参数先绑定a、b，多余的参数以数组形式交给变量rest:
`function foo(a, b, ...rest) {
    console.log('a = ' + a);
    console.log('b = ' + b);
    console.log(rest);
}
foo(1, 2, 3, 4, 5);
// 结果:
// a = 1
// b = 2
// Array [ 3, 4, 5 ]
foo(1);
// 结果:
// a = 1
// b = undefined`
**由于JavaScript引擎在行末自动添加分号的机制,正确的多行写法是：**
`function foo() {
    return { // 这里不会自动加分号，因为{表示语句尚未结束,加{
        name: 'foo'
    };
}`
**变量作用域与解构赋值**
1. `function foo() {
    var x = 1;
    function bar() {
        var y = x + 1; // bar可以访问foo的变量x!
    }
    var z = y + 1; // ReferenceError! foo不可以访问bar的变量y!
    }`
2. JavaScript的函数在查找变量时从自身函数定义开始，从“内”向“外”查找。如果内部函数定义了与外部函数重名的变量，则内部函数的变量将“屏蔽”外部函数的变量。
3. 变量提升
JavaScript的函数定义有个特点，它会先扫描整个函数体的语句，把所有申明的变量“提升”到函数顶部：
'use strict';
function foo() {
    var x = 'Hello, ' + y;
    console.log(x);
    var y = 'Bob';
}
foo();
虽然是strict模式，但语句var x = 'Hello, ' + y;并不报错，原因是变量y在稍后申明了。但是console.log显示Hello, undefined，说明变量y的值为undefined。**这正是因为JavaScript引擎自动提升了变量y的声明，但不会提升变量y的赋值。**
**我们在函数内部定义变量时，请严格遵守“在函数内部首先申明所有变量”这一规则。最常见的做法是用一个var申明函数内部用到的所有变量：**
`function foo() {
    var
        x = 1, // x初始化为1
        y = x + 1, // y初始化为2
        z, i; // z和i为undefined
    // 其他语句:
    for (i=0; i<100; i++) {
        ...
    }
}`
4. 全局作用域: 不在任何函数内定义的变量就具有全局作用域。实际上，JavaScript默认有一个全局对象window，全局作用域的变量实际上被绑定到window的一个属性, 因此，直接访问全局变量course和访问window.course是完全一样的：
`var course = 'Learn JavaScript';
alert(course); // 'Learn JavaScript'
alert(window.course); // 'Learn JavaScript'`
JavaScript实际上只有一个全局作用域。任何变量（函数也视为变量），如果没有在当前函数作用域中找到，就会继续往上查找，最后如果在全局作用域中也没有找到，则报ReferenceError错误。
5. 名字空间：全局变量会绑定到window上，不同的JavaScript文件如果使用了相同的全局变量，或者定义了相同名字的顶层函数，都会造成命名冲突，并且很难被发现。减少冲突的一个方法是把自己的所有变量和函数全部绑定到一个全局变量中。**把自己的代码全部放入唯一的名字空间MYAPP中，会大大减少全局变量冲突的可能。**例如：
// 唯一的全局变量MYAPP:
`var MYAPP = {};
// 其他变量:
MYAPP.name = 'myapp';
MYAPP.version = 1.0;
// 其他函数:
MYAPP.foo = function () {
    return 'foo';
};`
6. 局部作用域： 由于JavaScript的变量作用域实际上是函数内部，我们在for循环等语句块中是无法定义具有局部作用域的变量的：
function foo() {
`    for (var i=0; i<100; i++) {
        //
    }
    i += 100; // 仍然可以引用变量i
}`
为了解决块级作用域，ES6引入了新的关键字let，用let替代var可以申明一个块级作用域的变量：
`function foo() {
    var sum = 0;
    for (let i=0; i<100; i++) {
        sum += i;
    }
    // SyntaxError:
    i += 1;
}`
7. 常量: 由于var和let(let 声明的变量只在 let 命令所在的代码块内有效)申明的是变量，如果要申明一个常量，在ES6之前是不行的，我们通常用全部大写的变量来表示“这是一个常量，不要修改它的值”：`var PI = 3.14;`
ES6标准引入了新的关键字const来定义常量，const与let都具有块级作用域：
`const PI = 3.14;
PI = 3; // 某些浏览器不报错，但是无效果！`
8. 解构赋值:可以同时对一组变量进行赋值。
传统做法：
`var array = ['hello', 'JavaScript', 'ES6'];
var x = array[0];
var y = array[1];
var z = array[2];`
ES6做法：`var [x, y, z] = ['hello', 'JavaScript', 'ES6'];`
`let [x, [y, z]] = ['hello', ['JavaScript', 'ES6']];`
**解构赋值还可以忽略某些元素**：`let [, , z] = ['hello', 'JavaScript', 'ES6']; // 忽略前两个元素，只对z赋值第三个元素`
**对一个对象进行解构赋值时，同样可以直接对嵌套的对象属性进行赋值:**
`var person = {
    name: '小明',
    age: 20,
    gender: 'male',
    passport: 'G-12345678',
    school: 'No.4 middle school',
    address: {
        city: 'Beijing',
        street: 'No.1 Road',
        zipcode: '100001'
    }
};
var {name, address: {city, zip}} = person;
name; // '小明'
city; // 'Beijing'
zip; // undefined, 因为属性名是zipcode而不是zip
// 注意: address不是变量，而是为了让city和zip获得嵌套的address对象的属性:
address; // Uncaught ReferenceError: address is not defined`
**如果要使用的变量名和属性名不一致，可以用下面的语法获取：**
`var person = {
    name: '小明',
    age: 20,
    gender: 'male',
    passport: 'G-12345678',
    school: 'No.4 middle school'
};
// 把passport属性赋值给变量id:
let {name, passport:id} = person;
name; // '小明'
id; // 'G-12345678'
// 注意: passport不是变量，而是为了让变量id获得passport属性:
passport; // Uncaught ReferenceError: passport is not defined`
**解构赋值还可以使用默认值，这样就避免了不存在的属性返回undefined的问题：**
`var person = {
    name: '小明',
    age: 20,
    gender: 'male',
    passport: 'G-12345678'
};
// 如果person对象没有single属性，默认赋值为true:
var {name, single=true} = person;
name; // '小明'
single; // true`

**有些时候，如果变量已经被声明了，再次赋值的时候，正确的写法也会报语法错误：**
`// 声明变量:
var x, y;
// 解构赋值:
{x, y} = { name: '小明', x: 100, y: 200};
// 语法错误: Uncaught SyntaxError: Unexpected token =`
这是因为JavaScript引擎把{开头的语句当作了块处理，于是=不再合法。解决方法是用小括号括起来：`({x, y} = { name: '小明', x: 100, y: 200});`
**解构赋值的使用场景**
解构赋值在很多时候可以大大简化代码。例如，交换两个变量x和y的值，可以这么写，不再需要临时变量：
`var x=1, y=2;
[x, y] = [y, x]`
快速获取当前页面的域名和路径：`var {hostname:domain, pathname:path} = location;`
如果一个函数接收一个对象作为参数，那么，可以使用解构直接把对象的属性绑定到变量中。例如，下面的函数可以快速创建一个Date对象：
`function buildDate({year, month, day, hour=0, minute=0, second=0}) {
    return new Date(year + '-' + month + '-' + day + ' ' + hour + ':' + minute + ':' + second);
}`
它的方便之处在于传入的对象只需要year、month和day这三个属性：
`buildDate({ year: 2017, month: 1, day: 1 });
// Sun Jan 01 2017 00:00:00 GMT+0800 (CST)`
也可以传入hour、minute和second属性：
`buildDate({ year: 2017, month: 1, day: 1, hour: 20, minute: 15 });
// Sun Jan 01 2017 20:15:00 GMT+0800 (CST)`

**方法**:在一个**对象**中绑定**函数**，称为这个**对象**的**方法**。
1. 
`var xiaoming={ //xiaoming是个变量，指向对象{}
    name:'ming',
    birth:1990,//birth是属性
    age:function(){
        var y=new Date().getFullYear();//Date 对象用于处理日期与时间。
        return y-this.birth;//在这个对象里面call，用this
    }
};
xiaoming.age; // function xiaoming.age()
xiaoming.age(); // 今年调用是25,明年调用就变成26了`
在一个方法内部，this是一个特殊变量，它始终指向当前对象，也就是**xiaoming这个变量**。所以，this.birth可以拿到xiaoming的**birth属性**。
**Note:this:
1. 如果以对象的方法形式调用，比如xiaoming.age()，该函数的this指向被调用的对象，也就是xiaoming，这是符合我们预期的。如果单独调用函数，比如getAge()，此时，该函数的this指向全局对象，也就是window。
2. 要保证this指向正确，必须用obj.xxx()的形式调用！**
`'use strict';
var xiaoming = {
    name: '小明',
    birth: 1990,
    age: function () {
        var that = this; // 在方法内部一开始就捕获this
        function getAgeFromBirth() {
            var y = new Date().getFullYear();
            return y - that.birth; // 用that而不是this
        }
        return getAgeFromBirth();
    }
};
xiaoming.age(); // 25`
**用var that = this;，你就可以放心地在方法内部定义其他函数，而不是把所有语句都堆到一个方法中。**
2. **apply**
要指定函数的this指向哪个对象，可以用函数本身的apply方法，它接收两个参数，**第一个参数就是需要绑定的this变量，第二个参数是Array，表示函数本身的参数**。
用apply修复getAge()调用：
`function getAge() {
    var y = new Date().getFullYear();
    return y - this.birth;
}
var xiaoming = {
    name: '小明',
    birth: 1990,
    age: getAge
};
xiaoming.age(); // 25
getAge.apply(xiaoming, []); // 25, this指向xiaoming, 参数为空`
3. **call**: 另一个与apply()类似的方法是call()，唯一区别是：apply()把参数打包成Array再传入；call()把参数按顺序传入。
`Math.max.apply(null, [3, 5, 4]); // 5
Math.max.call(null, 3, 5, 4); // 5 对普通函数调用，我们通常把this绑定为null。`
4. **装饰器**：利用apply()，我们还可以动态改变函数的行为。JavaScript的所有对象都是动态的，即使内置的函数，我们也可以重新指向新的函数：
现在假定我们想统计一下代码一共调用了多少次parseInt()，可以把所有的调用都找出来，然后手动加上count += 1，不过这样做太傻了。最佳方案是用我们自己的函数替换掉默认的parseInt()：
`'use strict';
var count = 0;
var oldParseInt = parseInt; // 保存原函数
window.parseInt = function () {
    count += 1;
    return oldParseInt.apply(null, arguments); // 调用原函数
};
// 测试:
parseInt('10');
parseInt('20');
parseInt('30');
console.log('count = ' + count); // 3`
**高阶函数**： JavaScript的函数其实都指向某个变量。既然变量可以指向函数，函数的参数能接收变量，那么一个函数就可以接收另一个函数作为参数，这种函数就称之为高阶函数。
`function add(x, y, f) {
    return f(x) + f(y);
}`
1. **map**: 由于map()方法定义在JavaScript的Array中，我们调用Array的map()方法，传入我们自己的函数，就得到了一个新的Array作为结果:
`function pow(x) {
    return x * x;
}
var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9];
var results = arr.map(pow); // [1, 4, 9, 16, 25, 36, 49, 64, 81]
console.log(results);`
Array的所有数字转为字符串：
`var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9];
arr.map(String); // ['1', '2', '3', '4', '5', '6', '7', '8', '9']`
2. **reduce**: Array的reduce()把一个函数作用在这个Array的[x1, x2, x3...]上，这个函数必须**接收两个参数**，reduce()把结果继续和序列的下一个元素做**累积计算**:
`[x1, x2, x3, x4].reduce(f) = f(f(f(x1, x2), x3), x4)`
对一个Array求和:
`var arr = [1, 3, 5, 7, 9];
arr.reduce(function (x, y) {
    return x + y;
}); // 25`
**WHY???**
![image-20220523190430257](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220523190430257.png)
**Map & Reduce 习题：**
1. 利用reduce()求积：
`var arr=[1, 3, 5, 7, 9];
var n=arr.reduce(function(x,y){
    return x*y;
})
console.log(n)`
2. 把一个字符串13579先变成Array——[1, 3, 5, 7, 9]，再利用reduce()就可以写出一个把字符串转换为Number的函数。
`var arr="13579";
var n=arr.split("");//变成Array[1, 3, 5, 7, 9]
console.log(n)
var k=n.reduce(function( x,y){
    return x+y;
})//字符串转换为Number的函数
console.log(k)`
3. 把用户输入的不规范的英文名字，变为首字母大写，其他小写的规范名字, 输入：['adam', 'LISA', 'barT']，输出：['Adam', 'Lisa', 'Bart']。:
`function normalize(arr) {
    var brr = arr.map(function(x){
        return x[0].toUpperCase() + x.substring(1).toLowerCase();
    });
    return brr;
}
console.log(normalize(['adam', 'LISA', 'barT']))`

**filter**:它用于把Array的某些元素过滤掉，然后返回剩下的元素。和map()类似，Array的filter()也接收一个函数。和map()不同的是，filter()把传入的函数依次作用于每个元素，然后根据返回值是true还是false决定保留还是丢弃该元素。
1. 在一个Array中，删掉偶数，只保留奇数，可以这么写：
`var arr = [1, 2, 4, 5, 6, 9, 10, 15];
var r = arr.filter(function (x) {
    return x % 2 !== 0;
});`
2. 把一个Array中的空字符串删掉，可以这么写:
`var arr = ['A', '', 'B', null, undefined, 'C', '  '];
var r = arr.filter(function (s) {
    return s && s.trim(); // 注意：IE9以下的版本没有trim()方法
});`
3. filter()接收的回调函数，其实可以有多个参数。通常我们仅使用第一个参数，表示Array的某个元素。回调函数还可以接收另外两个参数，表示元素的**位置**和**数组本身**：
`var arr = ['A', 'B', 'C'];
var r = arr.filter(function (element, index, self) {
    console.log(element); // 依次打印'A', 'B', 'C'
    console.log(index); // 依次打印0, 1, 2
    console.log(self); // self就是变量arr
    return true;
});`
4. 利用filter，可以巧妙地去除Array的重复元素：
`r = arr.filter(function (element, index, self) {
    return self.indexOf(element) === index;
});//去除重复元素依靠的是indexOf总是返回第一个元素的位置，后续的重复元素位置与indexOf返回的位置不相等，因此被filter滤掉了。`
**sort 排序算法**:sort() 方法用于对数组的元素进行排序。默认排序顺序为按**字母**升序。使用数字排序，你必须通过一个函数作为参数来调用。默认情况下，对字符串排序，是按照ASCII的大小比较的
1. 按数字大小排序
`var arr = [10, 20, 1, 2];
arr.sort(function(x,y){
    if (x<y) {
        return -1;
    }
    if (x<y){
        return 1;
    }
    return 0;
});//[1, 2, 10, 20]`
如果要倒序排序，我们可以把大的数放前面：
`var arr = [10, 20, 1, 2];
arr.sort(function (x, y) {
    if (x < y) {
        return 1;
    }
    if (x > y) {
        return -1;
    }
    return 0;
}); // [20, 10, 2, 1]`
2. 忽略大小写对字符串排序：
`var arr = ['Google', 'apple', 'Microsoft'];
arr.sort(function (s1, s2) {
    x1 = s1.toUpperCase();
    x2 = s2.toUpperCase();
    if (x1 < x2) {
        return -1;
    }
    if (x1 > x2) {
        return 1;
    }
    return 0;
}); // ['apple', 'Google', 'Microsoft']`
**every()**可以判断**数组**的**所有元素**是否满足测试条件：
`var arr = ['Apple', 'pear', 'orange'];
console.log(arr.every(function (s) {
    return s.length > 0;
})); // true, 因为每个元素都满足s.length>0

console.log(arr.every(function (s) {
    return s.toLowerCase() === s;
})); // false, 因为不是每个元素都全部是小写`
**find**:查找符合条件的**第一个**元素，如果找到了，返回这个元素，否则，返回undefined
`var arr = ['Apple', 'pear', 'orange'];
console.log(arr.find(function (s) {
    return s.toLowerCase() === s;
})); // 'pear', 因为pear全部是小写

console.log(arr.find(function (s) {
    return s.toUpperCase() === s;
})); // undefined, 因为没有全部是大写的元素`
**findIndex**:findIndex()和find()类似，也是查找符合条件的**第一个**元素，不同之处在于findIndex()会返回这个元素的**索引**，如果没有找到，返回-1：
`var arr = ['Apple', 'pear', 'orange'];
console.log(arr.findIndex(function (s) {
    return s.toLowerCase() === s;
})); // 1, 因为'pear'的索引是1

console.log(arr.findIndex(function (s) {
    return s.toUpperCase() === s;
})); // -1`
**forEach**: forEach()和map()类似，它也把每个元素依次作用于传入的函数，但**不会返回新的数组。**forEach()常用于遍历数组，因此，传入的函数**不需要返回值**：

**闭包**高阶函数除了可以接受函数作为参数外，还可以把**函数作为结果值返回**。
`function lazy_sum(arr) {
    var sum = function () {
        return arr.reduce(function (x, y) {
            return x + y;
        });
    }
    return sum;
}`
当我们调用lazy_sum()时，返回的并不是求和结果，而是求和函数：
`var f = lazy_sum([1, 2, 3, 4, 5]); // function sum()`
调用函数f时，才真正计算求和的结果：`f(); // 15`
在这个例子中，我们在函数lazy_sum中又定义了函数sum，并且，内部函数sum可以引用外部函数lazy_sum的参数和局部变量，当lazy_sum返回函数sum时，相关参数和变量都保存在返回的函数中，这种称为“闭包（Closure）”的程序结构拥有极大的威力。
**返回闭包时牢记的一点就是：返回函数不要引用任何循环变量，或者后续会发生变化的变量。**
**如果一定要引用循环变量怎么办？方法是再创建一个函数，用该函数的参数绑定循环变量当前的值，无论该循环变量后续如何更改，已绑定到函数参数的值不变：**
`function count() {
    var arr = [];
    for (var i=1; i<=3; i++) {
        arr.push((function (n) {
            return function () {
                return n * n;
            }
        })(i));//i这里相当于创建一个匿名函数并立刻执行，见Note
    }
    return arr;
}
var results = count();
var f1 = results[0];
var f2 = results[1];
var f3 = results[2];
console.log(f1(),f2(),f3()); // 1
Note：
(function (x) {
    return x * x;
})(3); // 9`
借助闭包，同样可以封装一个私有变量. 创建一个计数器:
`function create_counter(initial) {
    var x = initial || 0;//x要么是传进来initial的值，要么默认为0
    return {
        inc: function () {
            x += 1;
            return x;
        }
    }
}
var c2 = create_counter(10);
c2.inc(); // 11
c2.inc(); // 12
c2.inc(); // 13`
在返回的对象中，实现了一个闭包，该闭包携带了局部变量x，并且，从外部代码根本无法访问到变量x。换句话说，闭包就是携带状态的函数，并且它的状态可以完全对外隐藏起来。

闭包还可以把**多参数的函数**变成**单参数的函数**:
`function make_pow(n) {
    return function (x) {
        return Math.pow(x, n);//本来是x,n两个参数，现在闭包成只有n
    }
}
// 创建两个新函数:
var pow2 = make_pow(2);
var pow3 = make_pow(3);
console.log(pow2(5)); // 25
console.log(pow3(7)); // 343`

**箭头函数**
箭头函数相当于匿名函数，并且简化了函数定义。箭头函数有两种格式，一种只包含一个表达式，连{ ... }和return都省略掉了。
`x => x * x`就是：
`function (x) {
    return x * x;
}`
还有一种可以包含**多条语句**，这时候就不能省略{ ... }和return：
`x => {
    if (x > 0) {
        return x * x;
    }
    else {
        return - x * x;
    }
}`
如果参数**不是一个**，就需要用括号()括起来：
`// 两个参数:
(x, y) => x * x + y * y
// 无参数:
() => 3.14
// 可变参数:
(x, y, ...rest) => {
    var i, sum = x + y;
    for (i=0; i<rest.length; i++) {
        sum += rest[i];
    }
    return sum;
}`
如果要返回**一个对象**:`x => ({ foo: x })`
箭头函数完全修复了this的指向，this总是指向**词法作用域**，也就是**外层调用者obj**：
`var obj = {
    birth: 1990,
    getAge: function () {
        var b = this.birth; // 1990
        var fn = () => new Date().getFullYear() - this.birth; // this指向obj对象
        return fn();
    }
};
obj.getAge(); // 25`
由于this在箭头函数中已经按照词法作用域绑定了，所以，用call()或者apply()调用箭头函数时，无法对this进行绑定，即传入的第一个参数被忽略：
`var obj = {
    birth: 1990,
    getAge: function (year) {
        var b = this.birth; // 1990
        var fn = (y) => y - this.birth; // this.birth仍是1990
        return fn.call({birth:2000}, year);
    }
};
obj.getAge(2015); // 25`
使用箭头函数数字排序：
`var arr = [10, 20, 1, 2];
arr.sort((x,y)=> y-x)`
**generator**:generator（生成器）是ES6标准引入的新的数据类型。一个generator看上去像一个函数，但**可以返回多次**。
generator由function*定义（注意多出的*号），并且，除了return语句，还可以用**yield返回多次**.
yield 相当于设置了一个断点，执行到这就暂停当前函数的运行，并返回值或执行语句的结果value。它和return的区别在于，return的返回意味着函数生命周期的结束，而yield的返回只是挂起了函数的运行。
`function* foo(x) {
    yield x + 1;
    yield x + 2;
    return x + 3;
}`
斐波那契数列:
`function* fib(max){
    var
        t,
        a=0,b=1,n=0;
    while(n<max){
        yield a;
        [a,b]=[b,a+b];
        n++;
    }
    return;
}
fib(5);//创建了一个generator对象，还没有去执行它`
调用方式：
next()方法会执行generator的代码，然后，每次遇到yield x;就返回一个对象{value: x, done: true/false}，然后“暂停”。返回的value就是yield的返回值，done表示这个generator是否已经执行结束了。如果done为true，则value就是return的返回值。当执行到done为true时，这个generator对象就已经全部执行完毕，不要再继续调用next()了。
`var f = fib(5);
f.next(); // {value: 0, done: false}`
用for ... of循环迭代generator对象，这种方式不需要我们自己判断done:
`for (var x of fib(10)) {
    console.log(x); // 依次输出0, 1, 1, 2, 3, ...
}`
自递增id例子：
`function* next_id(max){
    var
        current_id=0;
    for (n=0;n<max;n++){
        current_id++;
        yield current_id;
    }
    return;
}
var a=next_id(10)
console.log(a.next());`

**包装对象**
var n = new Number(123); // 123,生成了新的包装类型
typeof new Number(123); // 'object'
new Number(123) === 123; // false//new Number 生成的是object
没有写new的话：
var n = Number('123'); // 123，相当于parseInt()或parseFloat()
typeof n; // 'number'
**Note**:
1. 不要使用new Number()、new Boolean()、new String()创建包装对象；

2. 用parseInt()或parseFloat()来转换任意类型到number；

3. 用String()来转换任意类型到string，或者直接调用某个对象的toString()方法；

4. 通常不必把任意类型转换为boolean再判断，因为可以直接写if (myVar) {...}；

5. typeof操作符可以判断出number、boolean、string、function和undefined；

6. 判断Array要使用Array.isArray(arr)；

7. 判断null请使用myVar === null；

8. 判断某个全局变量是否存在用typeof window.myVar === 'undefined'；

9. 函数内部判断某个变量是否存在用typeof myVar === 'undefined'。

10. 123..toString(); // '123', 注意是两个点！
    **Date**
    
11. 获取当前时间：
      `var now = new Date();
      now; // Wed Jun 24 2015 19:49:22 GMT+0800 (CST)
      now.getFullYear(); // 2015, 年份`
    
12. 创建一个指定日期和时间的Date对象： 
      `var d = new Date(2015, 5, 19, 20, 15, 30, 123);//表示6月，我们传入的是5
      d; // Fri Jun 19 2015 20:15:30 GMT+0800 (CST)`
    
13. 创建一个指定日期和时间的方法是解析一个符合ISO 8601格式的字符串
      `var d = Date.parse('2015-06-24T19:49:22.875+08:00');
      d; // 1435146562875 //返回的不是Date对象，而是一个时间戳
      var d = new Date(1435146562875); //时间戳转换为一个Date
      d; // Wed Jun 24 2015 19:49:22 GMT+0800 (CST)
      d.getMonth(); // 5`
    使用Date.parse()时传入的字符串使用实际月份01~12，转换为Date对象后getMonth()获取的月份值为0~11。
    **RegExp正则表达式**：如果直接给出字符，就是精确匹配。用\d可以匹配一个数字，\w可以匹配一个字母或数字，.可以匹配任意字符，\s可以匹配一个空格（也包括Tab等空白符）
    要匹配变长的字符，在正则表达式中，用*表示任意个字符（包括0个），用+表示至少一个字符，用?表示0个或1个字符，用{n}表示n个字符，用{n,m}表示n-m个字符
    \d{3}\+\d{3,8} ：\d{3}表示匹配3个数字，例如'010',\s可以匹配一个空格（也包括Tab等空白符），所以\s+表示至少有一个空格，例如匹配' '，'\t\t'等,\d{3,8}表示3-8个数字，例如'1234567'
    ![image-20220524234052391](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220524234052391.png)
    ![image-20220524234214044](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220524234214044.png)
    **JavaScript有两种方式创建一个正则表达式**
    第一种：直接通过/正则表达式/写出来
    第二种：new RegExp('正则表达式')创建一个RegExp对象
    `var re1 = /ABC\-001/;
    var re2 = new RegExp('ABC\\-001');
    re1; // /ABC\-001/
    re2; // /ABC\-001/`  //使用第二种写法，因为字符串的转义问题，字符串的两个\\实际上是一个\
    **判断正则表达式是否匹配：**
    `var re = /^\d{3}\-\d{3,8}$/;
    re.test('010-12345'); // true
    re.test('010-1234x'); // false //RegExp对象的test()方法用于测试给定的字符串是否符合条件。`
    **正则表达式切分字符串:**
    `a b   c'.split(/\s+/); // ['a', 'b', 'c']`
    `'a,b;; c  d'.split(/[\s\,\;]+/); // ['a', 'b', 'c', 'd']`
    **分组**用()表示的就是要提取的分组（Group）,如果正则表达式中定义了组，就可以在RegExp对象上用exec()方法提取出子串来
    `var re = /^(\d{3})-(\d{3,8})$/;
    re.exec('010-12345'); // ['010-12345', '010', '12345']
    re.exec('010 12345'); // null exec()方法在匹配失败时返回null。`
    **贪婪匹配**正则匹配默认是贪婪匹配，也就是匹配尽可能多的字符
    `var re = /^(\d+)(0*)$/;
    re.exec('102300'); // ['102300', '102300', ''] 由于\d+采用贪婪匹配，直接把后面的0全部匹配了，结果0*只能匹配空字符串了。`
    必须让\d+采用非贪婪匹配（也就是尽可能少匹配），才能把后面的0匹配出来，加个?就可以让\d+采用非贪婪匹配：
    `var re = /^(\d+?)(0*)$/;
    re.exec('102300'); // ['102300', '1023', '00']`
    **全局搜索** g，表示全局匹配。全局匹配可以多次执行exec()方法来搜索一个匹配的字符串。当我们指定g标志后，每次运行exec()，正则表达式本身会更新lastIndex属性，表示上次匹配到的最后索引。全局匹配类似搜索，因此不能使用/^...$/，那样只会最多匹配一次。正则表达式还可以指定i标志，表示忽略大小写，m标志，表示执行多行匹配。：
    var r1 = /test/g;
    // 等价于:
    var r2 = new RegExp('test', 'g');
    ![image-20220525000139446](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220525000139446.png)
    **JSON**(JavaScript Object Notation) JSON实际上是JavaScript的一个子集。数据类型：
    number：和JavaScript的number完全一致；
    boolean：就是JavaScript的true或false；
    string：就是JavaScript的string；
    null：就是JavaScript的null；
    array：就是JavaScript的Array表示方式——[]；
    object：就是JavaScript的{ ... }表示方式。
    JSON的字符串规定必须用双引号""，Object的键也必须用双引号""
    **序列化：**JavaScript变JSON
    `var xiaoming = {
    name: '小明',
    age: 14,
    gender: true,
    height: 1.65,
    grade: null,
    'middle-school': '\"W3C\" Middle School',
    skills: ['JavaScript', 'Java', 'Python', 'Lisp']
    };
    var s=JSON.stringify(xiaoming,null,' '); //按缩进输出
    console.log(s)`
    第二个参数用于控制如何筛选对象的键值，如果我们只想输出指定的属性，可以传入Array
    `JSON.stringify(xiaoming, ['name', 'skills'], '  ');`
    还可以传入一个函数，这样对象的每个键值对都会被函数先处理：
    `function convert(key, value) {
    if (typeof value === 'string') {
        return value.toUpperCase();
    }
    return value;
    }
    JSON.stringify(xiaoming, convert, '  '); //把所有属性值都变成大写`
    如果我们还想要精确控制如何序列化小明，可以给xiaoming定义一个toJSON()的方法，直接返回JSON应该序列化的数据：
    `var xiaoming = {
    name: '小明',
    age: 14,
    gender: true,
    height: 1.65,
    grade: null,
    'middle-school': '\"W3C\" Middle School',
    skills: ['JavaScript', 'Java', 'Python', 'Lisp'],
    toJSON: function () {
        return { // 只输出name和age，并且改变了key：
            'Name': this.name,
            'Age': this.age
        };
    }
    };
    JSON.stringify(xiaoming); // '{"Name":"小明","Age":14}'`
    **反序列化**： JSON格式的字符串，我们直接用JSON.parse()把它变成一个JavaScript对象
    `JSON.parse('[1,2,3,true]'); // [1, 2, 3, true]`
    JSON.parse()还可以接收一个函数，用来转换解析出的属性：
    `var obj = JSON.parse('{"name":"小明","age":14}', function (key, value) {
    if (key === 'name') {
        return value + '同学';
    }
    return value;
    });
    console.log(JSON.stringify(obj)); // {name: '小明同学', age: 14}`
    **面向对象编程**
    JavaScript不区分类（class)和实例(instance)的概念，而是通过原型（prototype)来实现面向对象编程。JavaScript的原型链和Java的Class区别就在，它没有“Class”的概念，所有对象都是实例，所谓继承关系不过是把一个对象的原型指向另一个对象而已。在JavaScrip代码运行时期，你可以把xiaoming从Student变成Bird，或者变成任何对象。
    `xiaoming.__proto__ = Student;`xiaoming的原型指向了对象Student，看上去xiaoming仿佛是从Student继承下来的
    `// 原型对象:
    var Student = {
    name: 'Robot',
    height: 1.2,
    run: function () {
        console.log(this.name + ' is running...');
    }
    };
    function createStudent(name) {
    // 基于Student原型创建一个新对象:
    var s = Object.create(Student);
    // 初始化新对象:
    s.name = name;
    return s;
    }
    var xiaoming = createStudent('小明');
    xiaoming.run(); // 小明 is running...
    xiaoming.__proto__ === Student; // true`
    
    **创建对象** 构造函数：除了直接用{ ... }创建一个对象外，JavaScript还可以用一种构造函数的方法来创建对象。它的用法是，先定义一个构造函数：
    `function Student(name) {
    this.name = name;
    this.hello = function () {
        console.log('Hello, ' + this.name + '!');
    }
    }`
    用关键字new来调用这个函数，并返回一个对象。如果不写new，这就是一个普通函数，它返回undefined。但是，如果写了new，它就变成了一个构造函数，它绑定的this指向新创建的对象，**并默认返回this**，也就是说，**不需要在最后写return this**;：
    `var xiaoming = new Student('小明');
    xiaoming.hello(); // Hello, 小明!`
    用new Student()创建的对象还从原型上获得了一个**constructor**属性，它指向函数Student本身：
    `xiaoming.constructor === Student.prototype.constructor; // true
    Student.prototype.constructor === Student; // true
    Object.getPrototypeOf(xiaoming) === Student.prototype; // true
    xiaoming instanceof Student; // true`

![image-20220525183604015](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220525183604015.png)
`xiaoming.hello === xiaohong.hello; // false`xiaoming和xiaohong各自的name不同。如果我们通过new Student()创建了很多对象，这些对象的hello函数实际上只需要共享同一个函数就可以了，这样可以节省很多内存。要让创建的对象共享一个hello函数，根据对象的属性查找原则，我们只要把hello函数移动到xiaoming、xiaohong这些**对象共同的原型**上就可以了，也就是Student.prototype：    
`function Student(props){
    this.name=props.name||'N/A';
    this.grade=props.grade||1;
}
Student.prototype.hello=function(){
    console.log('hello'+this.name);
};
function createStudent(props){
    return new Student(props||{})
}
var xiaoming=createStudent({
    name:'asher'
    grade:11
});
console.log(xiaoming.hello)`
**原型继承**
我们希望的原型链：new PrimaryStudent() ----> PrimaryStudent.prototype ----> Student.prototype ----> Object.prototype ----> null
把继承这个动作用一个inherits()函数封装起来，还可以隐藏F的定义：
`function inherits(Child, Parent) {
    var F = function () {}; // 空函数F
    F.prototype = Parent.prototype;// 把F的原型指向Student.prototype(parent)
    Child.prototype = new F();// 把child的原型指向一个新的F对象，F对象的原型正好指向parent.prototype:
    Child.prototype.constructor = Child;//把child原型的构造函数修复为child
}
function Student(props) {
    this.name = props.name || 'Unnamed';
}
Student.prototype.hello = function () {
    alert('Hello, ' + this.name + '!');
}
function PrimaryStudent(props) {
    Student.call(this, props);//定义新的构造函数，并在内部用call()调用希望“继承”的构造函数，并绑定this
    this.grade = props.grade || 1;
}
// 实现原型继承链:
inherits(PrimaryStudent, Student);
// 绑定其他方法到PrimaryStudent原型:
PrimaryStudent.prototype.getGrade = function () {
    return this.grade;
};`
**Class继承**
用新的class关键字来编写Student：
`class Student {
    constructor(name) {
        this.name = name;
    }
    hello() {
        alert('Hello, ' + this.name + '!');
    }
}`
比较一下就可以发现，class的定义包含了构造函数constructor和定义在原型对象上的函数hello()（注意没有function关键字），这样就避免了Student.prototype.hello = function () {...}这样分散的代码。
class继承:
`class PrimaryStudent extends Student {
    constructor(name, grade) {
        super(name); // 记得用super调用父类的构造方法（函数）!
        this.grade = grade;
    }
    myGrade() {
        alert('I am at grade ' + this.grade);
    }
}`
注意PrimaryStudent的定义也是class关键字实现的，而extends则表示原型链对象来自Student。子类的构造函数可能会与父类不太相同，例如，PrimaryStudent需要name和grade两个参数，并且需要通过super(name)来调用父类的构造函数，否则父类的name属性无法正常初始化。
PrimaryStudent已经自动获得了父类Student的hello方法，我们又在子类中定义了新的myGrade方法。
**浏览器对象**
window对象不但充当全局作用域，而且表示浏览器窗口。window对象有**innerWidth**和**innerHeight**属性，可以获取浏览器窗口的内部宽度和高度。内部宽高是指除去菜单栏、工具栏、边框等占位元素后，用于显示网页的净宽高。**outerWidth**和**outerHeight**属性，可以获取浏览器窗口的整个宽高。
**navigator.appName**：浏览器名称；
**navigator.appVersion**：浏览器版本；
**navigator.language**：浏览器设置的语言；
**navigator.platform**：操作系统类型；
**navigator.userAgent**：浏览器设定的User-Agent字符串。
**screen.width**：**屏幕**宽度，以像素为单位；
**screen.height**：屏幕高度，以像素为单位；
**screen.colorDepth**：返回颜色位数，如8、16、24。
**location.href**获取完整URL
**location.protocol**; // 'http'
**location.host**; // 'www.example.com'
**location.port**; // '8080'
**location.pathname**; // '/path/index.html'
**location.search**; // '?a=1&b=2'
**location.hash**; // 'TOP'
要加载一个新页面，可以调用location.assign()。如果要重新加载当前页面，调用location.reload()：
`if (confirm('重新加载当前页' + location.href + '?')) {
    location.reload();
} else {
    location.assign('/'); // 设置一个新的URL地址
}`
**document**对象表示**当前页面**。由于HTML在浏览器中以DOM形式表示为树形结构，document对象就是整个DOM树的根节点。
document的title属性是从HTML文档中的<title>xxx</title>读取的，但是可以动态改变：
`document.title = '努力学习JavaScript!';`
用document对象提供的getElementById()和getElementsByTagName()可以按ID获得一个DOM节点和按Tag名称获得一组DOM节点：
![image-20220526231627908](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220526231627908.png)

**JS HTML DOM**通过 HTML DOM，可访问 JavaScript HTML 文档的所有元素。当网页被加载时，浏览器会创建页面的文档对象模型（Document Object Model)。
![image-20220526230710134](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220526230710134.png)
**更新**：更新该DOM节点的内容，相当于更新了该DOM节点表示的HTML的内容；
**遍历**：遍历该DOM节点下的子节点，以便进行进一步操作；
**添加**：在该DOM节点下新增一个子节点，相当于动态增加了一个HTML节点；
**删除**：将该节点从HTML中删除，相当于删掉了该DOM节点的内容以及它包含的所有子节点。
**通过可编程的对象模型，JavaScript 获得了足够的能力来创建动态的 HTML:**
JavaScript 能够改变页面中的所有 HTML 元素
JavaScript 能够改变页面中的所有 HTML 属性
JavaScript 能够改变页面中的所有 CSS 样式
JavaScript 能够对页面中的所有事件做出反应

**查找 HTML 元素:**
通过 id 找到 HTML 元素: 
`var x=document.getElementById("intro");//查找 id="intro" 元素`
通过标签名找到 HTML 元素
`var x=document.getElementById("main");
var y=x.getElementsByTagName("p"); //查找 id="main" 的元素，然后查找 id="main" 元素中的所有 <p> 元素`
通过类名找到 HTML 元素:
`var x=document.getElementsByClassName("intro");//通过 getElementsByClassName 函数来查找 class="intro" 的元素`
**// 获取节点test下的所有直属子节点:**
`var cs = test.children;`
**// 获取节点test下第一个、最后一个子节点：**
`var first = test.firstElementChild;
var last = test.lastElementChild;`
**使用querySelector()和querySelectorAll()**
`// 通过querySelector获取ID为q1的节点：
var q1 = document.querySelector('#q1');`
// 通过querySelectorAll获取q1节点内的符合条件的所有节点：
`var ps = q1.querySelectorAll('div.highlighted > p');`
**更新DOM**
**innerHTML** 不但可以修改一个DOM节点的文本内容，还可以直接通过HTML片段修改DOM节点内部的子树：
`// 获取<p id="p-id">...</p>
var p = document.getElementById('p-id');
// 设置文本为abc:
p.innerHTML = 'ABC'; // <p id="p-id">ABC</p>
// 设置HTML:
p.innerHTML = 'ABC <span style="color:red">RED</span> XYZ';
// <p>...</p>的内部结构已修改`
修改**innerText或textContent**属性，可以自动对字符串进行HTML编码，保证无法设置任何HTML标签。
`// 获取<p id="p-id">...</p>
var p = document.getElementById('p-id');
// 设置文本:
p.innerText = '<script>alert("Hi")</script>';
// HTML被自动编码，无法设置一个<script>节点:
// <p id="p-id">&lt;script&gt;alert("Hi")&lt;/script&gt;</p>`

**插入DOM**
如果这个DOM节点是空的，例如，<div></div>，那么，直接使用innerHTML = '<span>child</span>'就可以修改DOM节点的内容，相当于“插入”了新的DOM节点。如果这个DOM节点不是空的，那就不能这么做，因为innerHTML会直接替换掉原来的所有子节点.
有两个办法可以插入新的节点。**一个是使用appendChild**，把一个子节点添加到父节点的最后一个子节点。:
`<p id="js">JavaScript</p>
<div id="list">
    <p id="java">Java</p>
    <p id="python">Python</p>
    <p id="scheme">Scheme</p>
</div>`
把<p id="js">JavaScript</p>添加到<div id="list">的最后一项：
`var
    js = document.getElementById('js'),
    list = document.getElementById('list');
list.appendChild(js);`
现在，HTML结构变成了这样：
`<div id="list">
    <p id="java">Java</p>
    <p id="python">Python</p>
    <p id="scheme">Scheme</p>
    <p id="js">JavaScript</p>
</div>`因为我们插入的js节点已经存在于当前的文档树，因此这个节点首先会从原先的位置删除，再插入到新的位置。
更多的时候我们会**从零创建一个新的节点**，然后**插入到指定位置**：
`var
    list = document.getElementById('list'),
    haskell = document.createElement('p');
haskell.id = 'haskell';
haskell.innerText = 'Haskell';
list.appendChild(haskell);`
这样我们就动态添加了一个新的节点：
`<!-- HTML结构 -->
<div id="list">
    <p id="java">Java</p>
    <p id="python">Python</p>
    <p id="scheme">Scheme</p>
    <p id="haskell">Haskell</p>
</div>`
**insertBefore**把子节点插入到指定的位置.可以使用parentElement.insertBefore(newElement, referenceElement);，子节点会插入到referenceElement之前。
`var
    list = document.getElementById('list'),//把Haskell插入到Python之前
    ref = document.getElementById('python'),
    haskell = document.createElement('p');
haskell.id = 'haskell';
haskell.innerText = 'Haskell';
list.insertBefore(haskell, ref);`
**循环一个父节点的所有子节点，可以通过迭代children属性实现：**
`var
    i, c,
    list = document.getElementById('list');
for (i = 0; i < list.children.length; i++) {
    c = list.children[i]; // 拿到第i个子节点
}`
**按字符串顺序重新排序DOM节点：**
`<!-- HTML结构 -->
<ol id="test-list">
    <li class="lang">Scheme</li>
    <li class="lang">JavaScript</li>
    <li class="lang">Python</li>
    <li class="lang">Ruby</li>
    <li class="lang">Haskell</li>
</ol>`
`var arr_list=Array.from(document.getElementById('test-list').children)
var arr_lang=Array.from(document.getElementsByClassName("lang"),item=>item.innerText)
arr_lang.sort();
arr_list.map((x,i)=>{x.innerText=arr_lang[i]})
//Array.from可以用扩展运算符[...]代替`
**删除DOM**
要删除一个节点，首先要获得该节点本身以及它的父节点，然后，调用父节点的removeChild把自己删掉。
`// 拿到待删除节点:
var self = document.getElementById('to-be-removed');
// 拿到父节点:
var parent = self.parentElement;
// 删除:
var removed = parent.removeChild(self);
removed === self; // true`
注意到删除后的节点虽然不在文档树中了，但其实它还在内存中，可以随时再次被添加到别的位置。
当你遍历一个父节点的子节点并进行删除操作时，要注意，**children属性是一个只读属性，并且它在子节点变化时会实时更新。**例如：
`var parent = document.getElementById('parent');
parent.removeChild(parent.children[0]);
parent.removeChild(parent.children[1]); // <-- 浏览器报错`
浏览器报错：parent.children[1]不是一个有效的节点。原因就在于，当<p>First</p>节点被删除后，parent.children的节点数量已经从2变为了1，索引[1]已经不存在了。
**Cookie**是由服务器发送的key-value标示符。因为HTTP协议是无状态的，但是服务器要区分到底是哪个用户发过来的请求，就可以用Cookie来区分。当一个用户成功登录后，服务器发送一个Cookie给浏览器，例如user=ABC123XYZ(加密的字符串)...，此后，浏览器访问该网站时，会在请求头附上这个Cookie，服务器根据Cookie即可区分出用户。Cookie还可以存储网站的一些设置，例如，页面显示的语言等等。
通过document.cookie读取到当前页面的Cookie：`document.cookie; // 'v=123; remember=true; prefer=zh'`
**操作表单**
用JavaScript来操作表单，可以获得用户输入的内容，或者对一个输入框设置新的内容。
**HTML表单的输入控件主要有以下几种：**
文本框，对应的<input type="text">，用于输入文本；
口令框，对应的<input type="password">，用于输入口令；
单选框，对应的<input type="radio">，用于选择一项；
复选框，对应的<input type="checkbox">，用于选择多项；
下拉框，对应的<select>，用于选择一项；
隐藏文本，对应的<input type="hidden">，用户不可见，但表单提交时会把隐藏文本发送到服务器
**获取值**如果我们获得了一个<input>节点的引用，就可以直接调用value获得对应的用户输入值。此方式可以应用于**text、password、hidden以及select**
`// <input type="text" id="email">
var input = document.getElementById('email');
input.value; // '用户输入的值'`
但是，对于单选框和复选框，value属性返回的永远是HTML预设的值，而我们需要获得的实际是用户是否“勾上了”选项，所以应该用**checked**：
`// <label><input type="radio" name="weekday" id="monday" value="1"> Monday</label>
// <label><input type="radio" name="weekday" id="tuesday" value="2"> Tuesday</label>
var mon = document.getElementById('monday');
var tue = document.getElementById('tuesday');
mon.value; // '1'
tue.value; // '2'
mon.checked; // true或者false
tue.checked; // true或者false`
**设置值**
设置值和获取值类似，对于text、password、hidden以及select，直接设置value就可以。对于单选框和复选框，设置checked为true或false即可：
`// <input type="text" id="email">
var input = document.getElementById('email');
input.value = 'test@example.com'; // 文本框的内容已更新`
**HTML5控件**
![image-20220528002150616](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220528002150616.png)
**提交表单**JavaScript可以以两种方式来处理表单的提交（AJAX方式在后面章节介绍）。方式一是通过<form>元素的submit()方法提交一个表单，例如，响应一个<button>的click事件，在JavaScript代码中提交表单
`<!-- HTML -->

<form id="test-form">
    <input type="text" name="test">
    <button type="button" onclick="doSubmitForm()">Submit</button>
</form>
<script>
function doSubmitForm() {
    var form = document.getElementById('test-form');
    // 可以在此修改form的input...
    // 提交form:
    form.submit();
}
</script>`
这种方式的缺点是扰乱了浏览器对form的正常提交。浏览器默认点击<button type="submit">时提交表单，或者用户在最后一个输入框按回车键。因此，**第二种方式**是响应<form>本身的onsubmit事件，在提交form时作修改：
`<!-- HTML -->

<form id="test-form" onsubmit="return checkForm()">
    <input type="text" name="test">
    <button type="submit">Submit</button>
</form>
<script>
function checkForm() {
    var form = document.getElementById('test-form');
    // 可以在此修改form的input...
    // 继续下一步:
    return true;
}
</script>`注意要return true来告诉浏览器继续提交，如果return false，浏览器将不会继续提交form，这种情况通常对应用户输入有误，提示用户错误信息后终止提交form。
安全考虑，提交表单时不传输明文口令，而是口令的MD5。要想不改变用户的输入，可以利用<input type="hidden">实现：
`<!-- HTML -->
<form id="login-form" method="post" onsubmit="return checkForm()">
    <input type="text" id="username" name="username">
    <input type="password" id="input-password">
    <input type="hidden" id="md5-password" name="password">
    <button type="submit">Submit</button>
</form>
<script>
function checkForm() {
    var input_pwd = document.getElementById('input-password');
    var md5_pwd = document.getElementById('md5-password');
    // 把用户输入的明文变为MD5:
    md5_pwd.value = toMD5(input_pwd.value);
    // 继续下一步:
    return true;
}
</script>`
注意到id为md5-password的<input>标记了name="password"，而用户输入的id为input-password的<input>没有name属性。没有name属性的<input>的数据不会被提交。
**操作报表实例**：
利用JavaScript检查用户注册信息是否正确，在以下情况不满足时报错并阻止提交表单：
用户名必须是3-10位英文字母或数字；口令必须是6-20位；两次输入口令必须一致。
`<!-- HTML结构 -->
<form id="test-register" action="#" target="_blank" onsubmit="return checkRegisterForm()">
    <p id="test-error" style="color:red"></p>
    <p>
        用户名: <input type="text" id="username" name="username">
    </p>
    <p>
        口令: <input type="password" id="password" name="password">
    </p>
    <p>
        重复口令: <input type="password" id="password-2">
    </p>
    <p>
        <button type="submit">提交</button> <button type="reset">重置</button>
    </p>
</form>`
`var checkRegisterForm=function(){
    var p=document.getElementById('username');
    var q=document.getElementById('password');
    var o=document.getElementById('password-2');
    var t=document.getElementById('test-error');
    var s=/\w{3,10}/;
    var r=/.{6,20}/;
    if ((s.test(p.value))&&(r.test(q.value))&&(o.value==q.value)){
        var form=document.getElementById('test-register');}
    else {
        t.innerText='<script>alert("error")</script>';
    return true;
    }
}`

**操作文件**
在HTML表单中，可以上传文件的唯一控件就是`<input type="file">`。*注意*：当一个表单包含`<input type="file">`时，表单的`enctype`必须指定为`multipart/form-data`，`method`必须指定为`post`，浏览器才能正确编码并以`multipart/form-data`格式发送表单的数据。出于安全考虑，浏览器只允许用户点击`<input type="file">`来选择本地文件，用JavaScript对`<input type="file">`的`value`赋值是没有任何效果的。当用户选择了上传某个文件后，JavaScript也无法获得该文件的真实路径。JavaScript可以在提交表单时对文件扩展名做检查，以便防止用户上传无效格式的文件：
`var f = document.getElementById('test-file-upload');
var filename = f.value; // 'C:\fakepath\test.png'
if (!filename || !(filename.endsWith('.jpg') || filename.endsWith('.png') || filename.endsWith('.gif'))) {
    alert('Can only upload image file.');
    return false;
}`
**File API**允许JavaScript读取文件内容，获得更多的文件信息。HTML5的File API提供了File和FileReader两个主要对象，可以获得文件信息并读取文件。
演示了如何读取用户选取的图片文件，并在一个<div>中预览图像：
`var
    fileInput = document.getElementById('test-image-file'),
    info = document.getElementById('test-file-info'),
    preview = document.getElementById('test-image-preview');
// 监听change事件:
fileInput.addEventListener('change', function () {
    // 清除背景图片:
    preview.style.backgroundImage = '';
    // 检查文件是否选择:
    if (!fileInput.value) {
        info.innerHTML = '没有选择文件';
        return;
    }
    // 获取File引用:
    var file = fileInput.files[0];
    // 获取File信息:
    info.innerHTML = '文件: ' + file.name + '<br>' +
                     '大小: ' + file.size + '<br>' +
                     '修改: ' + file.lastModified;
    if (file.type !== 'image/jpeg' && file.type !== 'image/png' && file.type !== 'image/gif') {
        alert('不是有效的图片文件!');
        return;
    }
    // 读取文件:
    var reader = new FileReader();
    reader.onload = function(e) {
        var
            data = e.target.result; // 'data:image/jpeg;base64,/9j/4AAQSk...(base64编码)...'   
        preview.style.backgroundImage = 'url(' + data + ')';
    };
    // 以DataURL的形式读取文件:
    reader.readAsDataURL(file);
});`
上面的代码演示了如何通过HTML5的File API读取文件内容。以DataURL的形式读取到的文件是一个字符串，类似于data:image/jpeg;base64,/9j/4AAQSk...(base64编码)...，常用于设置图像。如果需要服务器端处理，把字符串base64,后面的字符发送给服务器并用Base64解码就可以得到原始文件的二进制内容。
上面的代码还演示了JavaScript的一个重要的特性就是单线程执行模式。在JavaScript中，浏览器的JavaScript执行引擎在执行JavaScript代码时，总是以单线程模式执行，也就是说，任何时候，JavaScript代码都不可能同时有多于1个线程在执行。
你可能会问，单线程模式执行的JavaScript，如何处理多任务？
在JavaScript中，执行多任务实际上都是异步调用，比如上面的代码：reader.readAsDataURL(file);
就会发起一个异步操作来读取文件内容。因为是异步操作，所以我们在JavaScript代码中就不知道什么时候操作结束，因此需要先设置一个回调函数：
reader.onload = function(e) {
    // 当文件读取完成后，自动调用此函数:
};
当文件读取完成后，JavaScript引擎将自动调用我们设置的回调函数。执行回调函数时，文件已经读取完毕，所以我们可以在回调函数内部安全地获得文件内容。
**AJAX(没看懂）**JavaScript执行异步网络请求
如果要让用户留在当前页面中，同时发出新的HTTP请求，就必须用JavaScript发送这个新请求，接收到数据后，再用JavaScript更新页面，这样一来，用户就感觉自己仍然停留在当前页面，但是数据却可以不断地更新。AJAX请求是异步执行的，也就是说，要通过回调函数获得响应。
**Promise**
![image-20220528200659620](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220528200659620.png)
**Promise异步执行**
`//清除log：
var logging = document.getElementById('test-promise2-log');
while (logging.children.length > 1) {
    logging.removeChild(logging.children[logging.children.length - 1]);
}
//输出log到页面
function log(s) {
    var p = document.createElement('p');
    p.innerHTML = s;
    logging.appendChild(p);
}
new Promise(function (resolve, reject) {
    log('start new Promise...');
    var timeOut = Math.random() * 2;
    log('set timeout to: ' + timeOut + ' seconds.');
    setTimeout(function () {
        if (timeOut < 1) {
            log('call resolve()...');
            resolve('200 OK');
        }
        else {
            log('call reject()...');
            reject('timeout in ' + timeOut + ' seconds.');
        }
    }, timeOut * 1000);
}).then(function (r) {
    log('Done: ' + r);
}).catch(function (reason) {
    log('Failed: ' + reason);
});`
**如何串行执行一系列需要异步计算获得结果的任务：**
`//清除log：
var logging = document.getElementById('test-promise2-log');
while (logging.children.length > 1) {
    logging.removeChild(logging.children[logging.children.length - 1]);
}
//输出log到页面
function log(s) {
    var p = document.createElement('p');
    p.innerHTML = s;
    logging.appendChild(p);
}
// 0.5秒后返回input*input的计算结果:
function multiply(input) {
    return new Promise(function (resolve, reject) {
        log('calculating ' + input + ' x ' + input + '...');
        setTimeout(resolve, 500, input * input);
    });//setTimeout:在指定的毫秒数后调用函数或计算表达式
}
// 0.5秒后返回input+input的计算结果:
function add(input) {
    return new Promise(function (resolve, reject) {
        log('calculating ' + input + ' + ' + input + '...');
        setTimeout(resolve, 500, input + input);
    });
}
var p = new Promise(function (resolve, reject) {
    log('start new Promise...');
    resolve(123);
});
p.then(multiply)
    .then(add)
    .then(multiply)
    .then(add)
    .then(function (result) {
        log('Got value: ' + result);
    });`
**Promise并行执行异步任务**
试想一个页面聊天系统，我们需要从两个不同的URL分别获得用户的个人信息和好友列表，这两个任务是可以并行执行的，用**Promise.all()**实现如下：
`var p1 = new Promise(function (resolve, reject) {
    setTimeout(resolve, 500, 'P1');
});
var p2 = new Promise(function (resolve, reject) {
    setTimeout(resolve, 600, 'P2');
});
// 同时执行p1和p2，并在它们都完成后执行then:
Promise.all([p1, p2]).then(function (results) {
    console.log(results); // 获得一个Array: ['P1', 'P2']
});`
有些时候，多个异步任务是为了容错。比如，同时向两个URL读取用户的个人信息，只需要获得先返回的结果即可。这种情况下，用**Promise.race()**实现：
`var p1 = new Promise(function (resolve, reject) {
    setTimeout(resolve, 500, 'P1');
});
var p2 = new Promise(function (resolve, reject) {
    setTimeout(resolve, 600, 'P2');
});
Promise.race([p1, p2]).then(function (result) {
    console.log(result); // 'P1'
});//由于p1执行较快，Promise的then()将获得结果'P1'。p2仍在继续执行，但执行结果将被丢弃。`
**Canvas**是HTML5新增的组件，它就像一块幕布，可以用JavaScript在上面绘制各种图表、动画等。一个Canvas定义了一个指定尺寸的矩形框，在这个范围内我们可以随意绘制：
`<canvas id="test-canvas" width="300" height="200"></canvas>`
getContext('2d')方法让我们拿到一个**CanvasRenderingContext2D对象**，所有的绘图操作都需要通过这个对象完成:
`var ctx = canvas.getContext('2d');`
**允许在Canvas中绘制3D图形**：`gl = canvas.getContext("webgl");`
我们可以在Canvas上绘制各种形状。在绘制前，我们需要先了解一下Canvas的**坐标系统**：
![image-20220528232932965](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220528232932965.png)
Canvas的坐标以左上角为原点，水平向右为X轴，垂直向下为Y轴，以像素为单位，所以每个点都是非负整数。
`context.arc(x,y,r,sAngle,eAngle,counterclockwise);`
![image-20220528233803733](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220528233803733.png)
`var
    canvas = document.getElementById('test-shape-canvas'),
    ctx = canvas.getContext('2d');//拿到一个CanvasRenderingContext2D对象
ctx.clearRect(0, 0, 200, 200); // 擦除(0,0)位置大小为200x200的矩形，擦除的意思是把该区域变为透明
ctx.fillStyle = '#dddddd'; // 设置颜色
ctx.fillRect(10, 10, 130, 130); // 把(10,10)位置大小为130x130的矩形涂色
// 利用Path绘制复杂路径:
var path=new Path2D();
path.arc(75, 75, 50, 0, Math.PI*2, true);
path.moveTo(110,75);//moveTo() 方法可把窗口的左上角移动到一个指定的坐标。
path.arc(75, 75, 35, 0, Math.PI, false);
path.moveTo(65, 65);
path.arc(60, 65, 5, 0, Math.PI*2, true);
path.moveTo(95, 65);
path.arc(90, 65, 5, 0, Math.PI*2, true);
ctx.strokeStyle = '#0000ff';
ctx.stroke(path);`
![image-20220528234101680](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220528234101680.png)

`var
    canvas = document.getElementById('test-text-canvas'),
    ctx = canvas.getContext('2d');
ctx.clearRect(0, 0, canvas.width, canvas.height);
ctx.shadowOffsetX = 2;
ctx.shadowOffsetY = 2;
ctx.shadowBlur = 2;
ctx.shadowColor = '#666666';
ctx.font = '24px Arial';
ctx.fillStyle = '#333333';
ctx.fillText('带阴影的文字', 20, 40);`
![image-20220528234332787](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220528234332787.png)
Canvas除了能绘制基本的形状和文本，还可以实现动画、缩放、各种滤镜和像素转换等高级操作。如果要实现非常复杂的操作，考虑以下优化方案：
通过创建一个不可见的Canvas来绘图，然后将最终绘制结果复制到页面的可见Canvas中；
尽量使用整数坐标而不是浮点数；
可以创建多个重叠的Canvas绘制不同的层，而不是在一个Canvas中绘制非常复杂的图；
背景图片如果不变可以直接用<img>标签并放到最底层。
**jQuery**
消除浏览器差异：你不需要自己写冗长的代码来针对不同的浏览器来绑定事件，编写AJAX等代码；
简洁的操作DOM的方法：写`$('#test')`肯定比`document.getElementById('test')`来得简洁；
轻松实现动画、修改CSS等各种操作。
使用jQuery只需要在页面的<head>引入jQuery文件即可:
![image-20220529113508011](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220529113508011.png)
**$符号:**$是著名的jQuery符号。实际上，jQuery把所有功能全部封装在一个全局变量jQuery中，而$也是一个合法的变量名，它是变量jQuery的别名：
`window.jQuery; // jQuery(selector, context)
window.$; // jQuery(selector, context)
$ === jQuery; // true
typeof($); // 'function'//$本质上就是一个函数，但是函数也是对象，于是$除了可以直接调用外，也可以有很多其他属性。`
注意，你看到的$函数名可能不是jQuery(selector, context)，因为很多JavaScript压缩工具可以对函数名和参数改名，所以压缩过的jQuery源码$函数可能变成a(b, c)。
绝大多数时候，我们都直接用$（因为写起来更简单嘛）。但是，如果$这个变量不幸地被占用了，而且还不能改，那我们就只能让jQuery把$变量交出来，然后就只能使用**jQuery**这个变量。这种黑魔法的原理是jQuery在占用$之前，先在内部保存了原来的$, 调用jQuery.noConflict()时会把原来保存的变量还原。：
`$; // jQuery(selector, context)
jQuery.noConflict();//noConflict() 方法会释放对 $ 标识符的控制
$; // undefined
jQuery; // jQuery(selector, context)`
**选择器**：jQuery的选择器就是帮助我们快速定位到一个或多个DOM节点。
<u>按ID查找</u>，如果某个DOM节点有id属性，利用jQuery查找如下：
`// 查找<div id="abc">:
var div = $('#abc'); #abc以#开头。返回的对象是jQuery对象(jQuery对象类似数组，它的每个元素都是一个引用了DOM节点的对象。)`
以上面的查找为例，如果id为abc的<div>存在，返回的jQuery对象如下：`[<div id="abc">...</div>]`如果id为abc的<div>不存在，返回的jQuery对象如下：`[]`。jQuery的选择器不会返回undefined或者null，这样的好处是你不必在下一行判断if (div === undefined)。
jQuery对象和DOM对象之间可以互相转化：
`var div = $('#abc'); // jQuery对象
var divDom = div.get(0); // 假设存在div，获取第1个DOM元素
var another = $(divDom); // 重新把DOM包装为jQuery对象`
<u>按tag查找</u>:按tag查找只需要写上tag名称就可以了:
`var ps = $('p'); // 返回所有<p>节点
ps.length; // 数一数页面有多少个<p>节点`
<u>按class查找</u>:按class查找注意在class名称前加一个.
`var a = $('.red'); // 所有节点包含`class="red"`都将返回
// 例如:
// <div class="red">...</div>
// <p class="green red">...</p>`
通常很多节点有多个class，我们可以查找同时包含red和green的节点：
`var a = $('.red.green'); // 注意没有空格！
// 符合条件的节点：
// <div class="red green">...</div>
// <div class="blue green red">...</div>`
<u>按属性查找</u>一个DOM节点除了id和class外还可以有很多属性，很多时候按属性查找会非常方便，比如在一个表单中按属性来查找：
`var email = $('[name=email]'); // 找出<??? name="email">
var passwordInput = $('[type=password]'); // 找出<??? type="password">
var a = $('[items="A B"]'); // 找出<??? items="A B">//当属性的值包含空格等特殊字符时，需要用双引号括起来。`
按属性查找还可以使用前缀查找或者后缀查找：
`var icons = $('[name^=icon]'); // 找出所有name属性值以icon开头的DOM
// 例如: name="icon-1", name="icon-2"
var names = $('[name$=with]'); // 找出所有name属性值以with结尾的DOM
// 例如: name="startswith", name="endswith"`
这个方法尤其适合通过class属性查找，且不受class包含多个名称的影响：
`var icons = $('[class^="icon-"]'); // 找出所有class包含至少一个以`icon-`开头的DOM
// 例如: class="icon-clock", class="abc icon-home"`
<u>组合查找</u>:组合查找就是把上述简单选择器组合起来使用。如果我们查找$('[name=email]')，很可能把表单外的<div name="email">也找出来，但我们只希望查找<input>，就可以这么写：
`var emailInput = $('input[name=email]'); // 不会找出<div name="email">`
同样的，根据tag和class来组合查找也很常见：
`var tr = $('tr.red'); // 找出<tr class="red ...">...</tr>`
<u>多项选择器</u>多项选择器就是把多个选择器用`,`组合起来一块选:
`$('p,div'); // 把<p>和<div>都选出来
$('p.red,p.green'); // 把<p class="red">和<p class="green">都选出来`
要注意的是，选出来的元素是按照它们在HTML中出现的顺序排列的，而且不会有重复元素。例如，<p class="red green">不会被上面的$('p.red,p.green')选择两次。
<u>练习</u>
`<!-- HTML结构 -->
<div id="test-jquery">
    <p id="para-1" class="color-red">JavaScript</p>
    <p id="para-2" class="color-green">Haskell</p>
    <p class="color-red color-green">Erlang</p>
    <p name="name" class="color-black">Python</p>
    <form class="test-form" target="_blank" action="#0" onsubmit="return false;">
        <legend>注册新用户</legend>
        <fieldset>
            <p><label>名字: <input name="name"></label></p>
            <p><label>邮件: <input name="email"></label></p>
            <p><label>口令: <input name="password" type="password"></label></p>
            <p><button type="submit">注册</button></p>
        </fieldset>
    </form>
</div>`
`// 仅选择JavaScript
selected = $('#para-1');
selected = $('[class=color-red]');  // 完全匹配的方式
//仅选择Erlang
selected = $('[class="color-red color-green"]')
selected = $('.color-red.color-green')
//选择JavaScript和Erlang
selected = $('.color-red');
//选择所有编程语言
selected = $('[class^="color-"]');
//选择名字input
selected = $('input[name=name]');
//选择邮件和名字input
selected = $('input[name=name],input[name=email]');`
**层级选择器**如果两个DOM元素具有**层级关系**，就可以用$('ancestor descendant')来选择，层级之间用空格隔开。例如：
`<!-- HTML结构 -->
<div class="testing">
    <ul class="lang">
        <li class="lang-javascript">JavaScript</li>
        <li class="lang-python">Python</li>
        <li class="lang-lua">Lua</li>
    </ul>
</div>`
选出JavaScript，可以用层级选择器：
`$('ul.lang li.lang-javascript'); // [<li class="lang-javascript">JavaScript</li>]
$('div.testing li.lang-javascript'); // [<li class="lang-javascript">JavaScript</li>]`
因为<div>和<ul>都是<li>的**祖先节点**，所以上面两种方式都可以选出相应的<li>节点。
选择所有的<li>节点: `$('ul.lang li');`
`$('form[name=upload] input');//把选择范围限定在name属性为upload的表单里。如果页面有很多表单，其他表单的<input>不会被选择。`
`$('form.test p input'); // 在form表单选择被<p>包含的<input>`
**子选择器**
子选择器$('parent>child')类似层级选择器，但是限定了层级关系必须是父子关系，就是<child>节点必须是<parent>节点的直属子节点。还是以上面的例子：
`$('ul.lang>li.lang-javascript'); // 可以选出[<li class="lang-javascript">JavaScript</li>]
$('div.testing>li.lang-javascript'); // [], 无法选出，因为<div>和<li>不构成父子关系`
**过滤器**过滤器一般不单独使用，它通常附加在选择器上，帮助我们更精确地定位元素。观察过滤器的效果：
`$('ul.lang li'); // 选出JavaScript、Python和Lua 3个节点
$('ul.lang li:first-child'); // 仅选出JavaScript
$('ul.lang li:last-child'); // 仅选出Lua
$('ul.lang li:nth-child(2)'); // 选出第N个元素，N从1开始
$('ul.lang li:nth-child(even)'); // 选出序号为偶数的元素
$('ul.lang li:nth-child(odd)'); // 选出序号为奇数的元素`
**表单相关**针对表单元素，jQuery还有一组特殊的选择器：
<u>:input</u>：可以选择<input>，<textarea>，<select>和<button>；
<u>:file</u>：可以选择<input type="file">，和input[type=file]一样；
<u>:checkbox</u>：可以选择复选框，和input[type=checkbox]一样；
<u>:radio</u>：可以选择单选框，和input[type=radio]一样；
<u>:focus</u>：可以选择当前输入焦点的元素，例如把光标放到一个<input>上，用$('input:focus')就可以选出；
<u>:checked</u>：选择当前勾上的单选框和复选框，用这个选择器可以立刻获得用户选择的项目，如$('input[type=radio]:checked')；
<u>:enabled</u>：可以选择可以正常输入的<input>、<select> 等，也就是没有灰掉的输入；
<u>:disabled</u>：和:enabled正好相反，选择那些不能输入的。
此外，jQuery还有很多有用的选择器，例如，选出可见的或隐藏的元素：
`$('div:visible'); // 所有可见的div
$('div:hidden'); // 所有隐藏的div`

**Underscore**提供了一套完善的函数式编程的接口，让我们更方便地在JavaScript中实现函数式编程。underscore会把自身绑定到唯一的全局变量_上。http://underscorejs.org/
**怎么实现underscore插件？？**

**Collections**

map/filter: 和Array的map()与filter()类似，但是underscore的map()和filter()可以作用于Object。当作用于Object时，传入的函数为function (value, key)，第一个参数接收value，第二个参数接收key。

```
var upper = _.map(obj, function (value, key) {
    return value.toUpperCase();
});
["BOB","NO.1 MIDDLE SCHOOL","XUEYUAN ROAD"]//返回的是array

var upper = _.mapObject(obj, function (value, key) {
    return value.toUpperCase();
});
{"name":"BOB","school":"NO.1 MIDDLE SCHOOL","address":"XUEYUAN ROAD"}//返回object
```
every / some： 当集合的所有元素都满足条件时，_.every()函数返回true，当集合的至少一个元素满足条件时，_.some()函数返回true
```
// 所有元素都大于0？
_.every([1, 4, 7, -3, -9], (x) => x > 0); // false
// 至少一个元素大于0？
_.some([1, 4, 7, -3, -9], (x) => x > 0); // true
```
```
// 判断key和value是否全部是小写：
var r1 = _.every(obj, function (value, key) {
    return key.toLowerCase() === key && value.toLowerCase() === value;
});
var r2 = _.some(obj, function (value, key) {
    return key==key.toLowerCase() ||value==value.toLowerCase();
});
```
max / min

```
'use strict';
var arr = [3, 5, 7, 9];
_.max(arr); // 9
_.min(arr); // 3

// 空集合会返回-Infinity和Infinity，所以要先判断集合不为空：
_.max([])
-Infinity
_.min([])
Infinity
```
如果集合是Object，max()和min()只作用于value，忽略掉key：

```
'use strict';
_.max({ a: 1, b: 2, c: 3 }); // 3
```

groupBy 把集合的元素按照key归类，key由传入的函数返回：

```
var scores = [20, 81, 75, 40, 91, 59, 77, 66, 72, 88, 99];
var groups = _.groupBy(scores, function (x) {
    if (x < 60) {
        return 'C';
    } else if (x < 80) {
        return 'B';
    } else {
        return 'A';
    }
});
// 结果:
// {
//   A: [81, 91, 88, 99],
//   B: [75, 77, 66, 72],
//   C: [20, 40, 59]
// }
```

shuffle:用洗牌算法随机打乱一个集合

```
// 注意每次结果都不一样：
_.shuffle([1, 2, 3, 4, 5, 6]); // [3, 5, 4, 6, 2, 1]
```

`sample()`则是随机选择一个或多个元素：

```
// 注意每次结果都不一样：
// 随机选1个：
_.sample([1, 2, 3, 4, 5, 6]); // 2
// 随机选3个：
_.sample([1, 2, 3, 4, 5, 6], 3); // [6, 1, 4]
```

**Arrays**
first / last: 这两个函数分别取第一个和最后一个元素
```
var arr = [2, 4, 6, 8];
_.first(arr); // 2
_.last(arr); // 8
```
flatten()接收一个Array，无论这个Array里面嵌套了多少个Array，flatten()最后都把它们变成一个一维数组：

```
_.flatten([1, [2], [3, [[4], [5]]]]); // [1, 2, 3, 4, 5]
```

`zip()`把两个或多个数组的所有元素按索引对齐，然后按索引合并成新数组。例如，你有一个`Array`保存了名字，另一个`Array`保存了分数，现在，要把名字和分数给对上，用`zip()`轻松实现：

```
var names = ['Adam', 'Lisa', 'Bart'];
var scores = [85, 92, 59];
_.zip(names, scores);
// [['Adam', 85], ['Lisa', 92], ['Bart', 59]]
```

`unzip()`则是反过来：

```
var namesAndScores = [['Adam', 85], ['Lisa', 92], ['Bart', 59]];
_.unzip(namesAndScores);
// [['Adam', 'Lisa', 'Bart'], [85, 92, 59]]
```

有时候你会想，与其用`zip()`，为啥不把名字和分数直接对应成Object呢？别急，`object()`函数就是干这个的：

```
var names = ['Adam', 'Lisa', 'Bart'];
var scores = [85, 92, 59];
_.object(names, scores);
// {Adam: 85, Lisa: 92, Bart: 59}
//注意_.object()是一个函数，不是JavaScript的Object对象。
```

`range()`让你快速生成一个序列，不再需要用`for`循环实现了：

```
// 从0开始小于10:
_.range(10); // [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

// 从1开始小于11：
_.range(1, 11); // [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

// 从0开始小于30，步长5:
_.range(0, 30, 5); // [0, 5, 10, 15, 20, 25]

// 从0开始大于-10，步长-1:
_.range(0, -10, -1); // [0, -1, -2, -3, -4, -5, -6, -7, -8, -9]
```

使用`_.uniq`对数组元素进行*不区分大小写*去重:

```
var result = _.uniq(arr, _.iteratee(function(a){
    return a.toLowerCase();
}));
```

`bind()`可以帮我们把`s`对象直接绑定在`fn()`的`this`指针上:

```
var s = ' Hello  ';
var fn = _.bind(s.trim, s);
fn();
// 输出Hello.结论：当用一个变量fn指向一个对象的方法时，直接调用fn()是不行的，因为丢失了this对象的引用。用bind可以修复这个问题
```

`partial()`就是为一个函数创建偏函数。假设我们经常计算2y，每次都写`Math.pow(2, y)`就比较麻烦，如果创建一个新的函数能直接这样写`pow2N(y)`就好了，这个新函数`pow2N(y)`就是根据`Math.pow(x, y)`创建出来的**偏函数**，它固定住了原函数的第一个参数（始终为2）:

```
var pow2N = _.partial(Math.pow, 2);
pow2N(3); // 8
pow2N(5); // 32
pow2N(10); // 1024
```

想固定第二个参数怎么办？比如，希望创建一个偏函数`cube(x)`，计算x3，可以用`_`作占位符，固定住第二个参数：

```
var cube = _.partial(Math.pow, _, 3);
cube(3); // 27
cube(5); // 125
cube(10); // 1000
```

创建偏函数的目的是将原函数的某些参数固定住，可以降低新函数调用的难度

`once()`保证某个函数执行且仅执行一次。如果你有一个方法叫`register()`，用户在页面上点两个按钮的任何一个都可以执行的话，就可以用`once()`保证函数仅调用一次，无论用户点击多少次：
```
var register = _.once(function () {
    alert('Register ok!');
});
```

`delay()`可以让一个函数延迟执行，效果和`setTimeout()`是一样的:

```
// 2秒后调用alert():
_.delay(alert, 2000);
```

如果要延迟调用的函数有参数，把参数也传进去：

```
var log = _.bind(console.log, console);
_.delay(log, 2000, 'Hello,', 'world!');
// 2秒后打印'Hello, world!':
```

**object**

`keys()`可以非常方便地返回一个object自身所有的key，但不包含从原型链继承下来的：

```
function Student(name, age) {
    this.name = name;
    this.age = age;
}

var xiaoming = new Student('小明', 20);
_.keys(xiaoming); // ['name', 'age']
```

`allKeys()`除了object自身的key，还包含从**原型链**继承下来的：

```
function Student(name, age) {
    this.name = name;
    this.age = age;
}
Student.prototype.school = 'No.1 Middle School';
var xiaoming = new Student('小明', 20);
_.allKeys(xiaoming); // ['name', 'age', 'school']
```

和`keys()`类似，`values()`返回object自身但不包含原型链继承的所有值：

```
var obj = {
    name: '小明',
    age: 20
};

_.values(obj); // ['小明', 20]
```

`mapObject()`就是针对object的map版本：

```
var obj = { a: 1, b: 2, c: 3 };
// 注意传入的函数签名，value在前，key在后:
_.mapObject(obj, (v, k) => 100 + v); // { a: 101, b: 102, c: 103 }
```

`invert()`把object的每个key-value来个交换，key变成value，value变成key：

```
var obj = {
    Adam: 90,
    Lisa: 85,
    Bart: 59
};
_.invert(obj); // { '59': 'Bart', '85': 'Lisa', '90': 'Adam' }
```

`extend()`把多个object的key-value合并到第一个object并返回：

```
var a = {name: 'Bob', age: 20};
_.extend(a, {age: 15}, {age: 88, city: 'Beijing'}); // {name: 'Bob', age: 88, city: 'Beijing'}
// 变量a的内容也改变了：
a; // {name: 'Bob', age: 88, city: 'Beijing'}//注意：如果有相同的key，后面的object的value将覆盖前面的object的value。
```

`extendOwn()`和`extend()`类似，但获取属性时忽略从原型链继承下来的属性。

如果我们要复制一个object对象，就可以用`clone()`方法，它会把原有对象的所有属性都复制到新的对象中：var copied = _.clone(source);

注意，`clone()`是“浅复制”。所谓“浅复制”就是说，两个对象相同的key所引用的value其实是同一对象。也就是说，修改`source.skills`会影响`copied.skills`：

```
source.skills === copied.skills; // true
```

`isEqual()`对两个object进行**深度比较**，如果内容完全相同，则返回`true`：

```
var o1 = { name: 'Bob', skills: { Java: 90, JavaScript: 99 }};
var o2 = { name: 'Bob', skills: { JavaScript: 99, Java: 90 }};

o1 === o2; // false
_.isEqual(o1, o2); // true
```

`isEqual()`其实对`Array`也可以比较

```
var o1 = ['Bob', { skills: ['Java', 'JavaScript'] }];
var o2 = ['Bob', { skills: ['Java', 'JavaScript'] }];

o1 === o2; // false 虽然内容是相同的，但是是2个不同的对象啊，有不同的存储地址
_.isEqual(o1, o2); // true
```

**Chaining**

```
_.filter(_.map([1, 4, 9, 16, 25], Math.sqrt), x => x % 2 === 1);
// [1, 3, 5]
```

underscore提供了把对象包装成能进行链式调用的方法，就是`chain()`函数
```
var r = _.chain([1, 4, 9, 16, 25])
         .map(Math.sqrt)
         .filter(x => x % 2 === 1)
         .value();//因为每一步返回的都是包装对象，所以最后一步的结果需要调用value()获得最终结果。
```

**Node.js**

**fs**
npm其实是Node.js的包管理工具（package manager）
我们在Node.js上开发时，会用到很多别人写的JavaScript代码。如果我们要使用别人写的某个包，每次都根据名称搜索一下官方网站，下载代码，解压，再使用，非常繁琐。于是一个集中管理的工具应运而生：大家都把自己开发的模块打包后放到npm官网上，如果要使用，直接通过npm安装就可以直接用，不用管代码存在哪，应该从哪下载。
更重要的是，如果我们要使用模块A，而模块A又依赖于模块B，模块B又依赖于模块X和模块Y，npm可以根据依赖关系，把所有依赖的包都下载下来并管理起来。否则，靠我们自己手动管理，肯定既麻烦又容易出错。

```
'use strict';
var s = 'Hello';
function greet(name) {
    console.log(s + ', ' + name + '!');
}
module.exports = greet;//在hello.js里创造的函数greet
```
在main.js里用:
```
'use strict';
var greet=require('./hello');// 不要忘了写相对目录!
var s='asher';
greet(s);//hello模块用Node提供的require函数
```

JavaScript有且仅有一个全局对象，在浏览器中，叫`window`对象。而在Node.js环境中，也有唯一的全局对象，但不叫`window`，而叫`global`，这个对象的属性和方法也和浏览器环境的`window`不同。进入Node.js交互环境，可以直接输入 `global.console`

`process`也是Node.js提供的一个对象，它代表当前Node.js进程。通过`process`对象可以拿到许多有用信息：

```
> process === global.process;
true
> process.version;
'v5.2.0'
> process.platform;
'darwin'
> process.arch;
'x64'
> process.cwd(); //返回当前工作目录
'/Users/michael'
> process.chdir('/private/tmp'); // 切换当前工作目录
undefined
> process.cwd();
'/private/tmp'
```

JavaScript程序是由事件驱动执行的单线程模型，Node.js也不例外。Node.js不断执行响应事件的JavaScript函数，直到没有任何响应事件的函数可以执行时，Node.js就退出了。

如果我们想要在下一次事件响应中执行代码，可以调用`process.nextTick()`：

```
// process.nextTick()将在下一轮事件循环中调用:
process.nextTick(function () {
    console.log('nextTick callback!');
});
console.log('nextTick was set!');

//nextTick was set!
//nextTick callback!
```

Node.js进程本身的事件就由`process`对象来处理。如果我们响应`exit`事件，就可以在程序即将退出时执行某个回调函数：

```
// 程序即将退出时的回调函数:
process.on('exit', function (code) {
    console.log('about to exit with code: ' + code);
});//about to exit with code: 0
```

有很多JavaScript代码既能在浏览器中执行，也能在Node环境执行，但有些时候，程序本身需要判断自己到底是在什么环境下执行的，常用的方式就是根据浏览器和Node环境提供的全局变量名称来判断：

```
if (typeof(window) === 'undefined') {
    console.log('node.js');
} else {
    console.log('browser');
}
```

Node.js内置的`fs`模块就是文件系统模块，负责读写文件。`fs`模块同时提供了异步和同步的方法

异步读文件：异步读取时，传入的回调函数接收两个参数，当正常读取时，`err`参数为`null`，`data`参数为读取到的String。当读取发生错误时，`err`参数代表一个错误对象，`data`为`undefined`。这也是Node.js标准的回调函数：第一个参数代表错误信息，第二个参数代表结果。

```
'use strict';

var fs = require('fs');
//请注意，sample.txt文件必须在当前目录下，且文件编码为utf-8。
fs.readFile('sample.txt', 'utf-8', function (err, data) {
    if (err) {// 出错了
        console.log(err);
    } else { // 正常
        console.log(data);
    }
});
```
读取一个图片（二进制文件）

当读取二进制文件时，不传入文件编码时，回调函数的`data`参数将返回一个`Buffer`对象。在Node.js中，`Buffer`对象就是一个包含零个或任意个字节的数组（注意和Array不同）。

`Buffer`对象可以和String作转换，例如，把一个`Buffer`对象转换成String：

```
// Buffer -> String
var text = data.toString('utf-8');
console.log(text);
```
或者把一个String转换成Buffer：

```
// String -> Buffer
var buf = Buffer.from(text, 'utf-8');
console.log(buf);
```

```
'use strict';

var fs = require('fs');

fs.readFile('sample.png', function (err, data) {
    if (err) {
        console.log(err);
    } else {
        console.log(data);
        console.log(data.length + ' bytes');
    }
});
```
同步读文件

同步读取的函数和异步函数相比，多了一个`Sync`后缀，并且不接收回调函数，函数直接返回结果。

```
'use strict';//用fs模块同步读取一个文本文件的代码如下：
var fs=require('fs');
try {
    var data=fs.readFileSync('js_txt.txt','utf-8');
    console.log(data);
} catch (err){
    console.log('error');//用try...catch捕获错误
}
```
写文件: 将数据写入文件是通过fs.writeFile()实现的

```
'use strict';

var fs = require('fs');

var data = 'Hello, Node.js';
fs.writeFile('output.txt', data, function (err) {
    if (err) {
        console.log(err);
    } else {
        console.log('ok.');
    }
});
writeFile()的参数依次为文件名、数据和回调函数。如果传入的数据是String，默认按UTF-8编码写入文本文件，如果传入的参数是Buffer，则写入的是二进制文件。回调函数由于只关心成功与否，因此只需要一个err参数。
```

同步写文件：writeFileSync()

```
'use strict';

var fs = require('fs');

var data = 'Hello, Node.js';
fs.writeFileSync('output.txt', data);
```

stat: 如果我们要获取文件大小，创建时间等信息，可以使用`fs.stat()`，它返回一个`Stat`对象，能告诉我们文件或目录的详细信息:

```
var fs = require('fs');
fs.stat('sample.txt', function (err, stat) {
    if (err) {
        console.log(err);
    } else {
        // 是否是文件:
        console.log('isFile: ' + stat.isFile());
        // 是否是目录:
        console.log('isDirectory: ' + stat.isDirectory());
        if (stat.isFile()) {
            // 文件大小:
            console.log('size: ' + stat.size);
            // 创建时间, Date对象:
            console.log('birth time: ' + stat.birthtime);
            // 修改时间, Date对象:
            console.log('modified time: ' + stat.mtime);
        }
    }
});
```

绝大部分需要在服务器运行期反复执行业务逻辑的代码，*必须使用异步代码*
服务器启动时如果需要读取配置文件，或者结束时需要写入到状态文件时，可以使用同步代码，因为这些代码只在启动和结束时执行一次，不影响服务器正常运行时的异步执行。

**stream**是Node.js提供的又一个仅在**服务区端**可用的模块，目的是支持**流**这种数据结构。
什么是流？有些流用来读取数据，比如从文件读取数据时，可以打开一个文件流，然后从文件流中不断地读取数据。有些流用来写入数据，比如向文件写入数据时，只需要把数据不断地往文件流中写进去就可以了。在Node.js中，流也是一个对象，我们只需要响应流的事件就可以了：data事件表示流的数据已经可以读取了，end事件表示这个流已经到末尾了，没有数据可以读取了，error事件表示出错了。

所有可以读取数据的流都继承自`stream.Readable`，所有可以写入的流都继承自`stream.Writable`

下面是一个从文件流读取文本内容的示例：

```
'use strict';

var fs = require('fs');

// 打开一个流:
var rs = fs.createReadStream('sample.txt', 'utf-8');

rs.on('data', function (chunk) {
    console.log('DATA:')
    console.log(chunk);
});

rs.on('end', function () {
    console.log('END');
});

rs.on('error', function (err) {
    console.log('ERROR: ' + err);
});//要注意，data事件可能会有多次，每次传递的chunk是流的一部分数据。
```

要以流的形式写入文件，只需要不断调用`write()`方法，最后以`end()`结束：

```
'use strict';

var fs = require('fs');

var ws1 = fs.createWriteStream('output1.txt', 'utf-8');
ws1.write('使用Stream写入文本数据...\n');
ws1.write('END.');
ws1.end();

var ws2 = fs.createWriteStream('output2.txt');
ws2.write(new Buffer('使用Stream写入二进制数据...\n', 'utf-8'));
ws2.write(new Buffer('END.', 'utf-8'));
ws2.end();
```
**pipe**就像可以把两个水管串成一个更长的水管一样，两个流也可以串起来。一个Readable流和一个Writable流串起来后，所有的数据自动从Readable流进入Writable流，这种操作叫pipe

```
'use strict';//读一个文件然后写进另一个文件

var fs = require('fs');

var rs = fs.createReadStream('sample.txt');
var ws = fs.createWriteStream('copied.txt');

rs.pipe(ws);
```

默认情况下，当`Readable`流的数据读取完毕，`end`事件触发后，将自动关闭`Writable`流。如果我们不希望自动关闭`Writable`流，需要传入参数：

```
readable.pipe(writable, { end: false });
```

**http**

`request`对象封装了HTTP请求，我们调用`request`对象的属性和方法就可以拿到所有HTTP请求的信息

`response`对象封装了HTTP响应，我们操作`response`对象的方法，就可以把HTTP响应返回给浏览器。

用Node.js实现一个HTTP服务器程序hello.js，它对于所有请求，都返回`Hello world!`：

```
'use strict';
// 导入http模块:
var http = require('http');
// 创建http server，并传入回调函数:
var server = http.createServer(function (request, response) {
    // 回调函数接收request和response对象,
    // 获得HTTP请求的method和url:
    console.log(request.method + ': ' + request.url);
    // 将HTTP响应200写入response, 同时设置Content-Type: text/html:
    response.writeHead(200, {'Content-Type': 'text/html'});
    // 将HTTP响应的HTML内容写入response:
    response.end('<h1>Hello world!</h1>');
});
// 让服务器监听8080端口:
server.listen(8080);
console.log('Server is running at http://127.0.0.1:8080/');
```

文件服务器: 可以设定一个目录，然后让Web程序变成一个文件服务器。要实现这一点，我们只需要解析request.url中的路径，然后在本地找到对应的文件，把文件内容发送出去就可以了。解析URL需要用到Node.js提供的url模块，它使用起来非常简单，通过parse()将一个字符串解析为一个Url对象.

```
'use strict';
var url = require('url');
console.log(url.parse('http://user:pass@host.com:8080/path/to/file?query=string#hash'));
```

处理本地文件目录需要使用Node.js提供的`path`模块，它可以方便地构造目录：

```
'use strict';

var path = require('path');

// 解析当前目录:
var workDir = path.resolve('.'); // '/Users/michael'

// 组合完整的文件路径:当前目录+'pub'+'index.html':
var filePath = path.join(workDir, 'pub', 'index.html');
// '/Users/michael/pub/index.html'
//使用path模块可以正确处理操作系统相关的文件路径。在Windows系统下，返回的路径类似于C:\Users\michael\static\index.html，这样，我们就不关心怎么拼接路径了。
```

实现一个文件服务器`file_server.js`：

```
'use strict';

var
    fs = require('fs'),
    url = require('url'),
    path = require('path'),
    http = require('http');

// 从命令行参数获取root目录，默认是当前目录:
var root = path.resolve(process.argv[2] || '.');

console.log('Static root dir: ' + root);

// 创建服务器:
var server = http.createServer(function (request, response) {
    // 获得URL的path，类似 '/css/bootstrap.css':
    var pathname = url.parse(request.url).pathname;
    // 获得对应的本地文件路径，类似 '/srv/www/css/bootstrap.css':
    var filepath = path.join(root, pathname);
    // 获取文件状态:
    fs.stat(filepath, function (err, stats) {
        if (!err && stats.isFile()) {
            // 没有出错并且文件存在:
            console.log('200 ' + request.url);
            // 发送200响应:
            response.writeHead(200);
            // 将文件流导向response:
            fs.createReadStream(filepath).pipe(response);
        } else {
            // 出错了或者文件不存在:
            console.log('404 ' + request.url);
            // 发送404响应:
            response.writeHead(404);
            response.end('404 Not Found');
        }
    });
});

server.listen(8080);

console.log('Server is running at http://127.0.0.1:8080/');
//在命令行运行node file_server.js /path/to/dir，把/path/to/dir改成你本地的一个有效的目录，然后在浏览器中输入http://localhost:8080/index.html
```

**crypto**
MD5和SHA1:MD5是一种常用的哈希算法，用于给任意数据一个“签名”。这个签名通常用一个**十六进制**的字符串表示：

```
const crypto = require('crypto');
const hash = crypto.createHash('md5');//计算SHA1，只需要把'md5'改成'sha1',//还可以使用更安全的sha256和sha512
// 可任意多次调用update():
hash.update('Hello, world!');
hash.update('Hello, nodejs!');
console.log(hash.digest('hex')); // 7e1977739c748beac0c0fd14fd26a544
```
**Hmac**它可以利用MD5或SHA1等哈希算法。不同的是，Hmac还需要一个密钥

```
const crypto = require('crypto');
const hmac = crypto.createHmac('sha256', 'secret-key');

hmac.update('Hello, world!');
hmac.update('Hello, nodejs!');

console.log(hmac.digest('hex')); // 80f7e22570...
```
AES是一种常用的对称加密算法，加解密都用同一个密钥。crypto模块提供了AES支持，但是需要自己封装好函数

```
const crypto = require('crypto');

function aesEncrypt(data, key) {
    const cipher = crypto.createCipher('aes192', key);
    var crypted = cipher.update(data, 'utf8', 'hex');
    crypted += cipher.final('hex');
    return crypted;
}

function aesDecrypt(encrypted, key) {
    const decipher = crypto.createDecipher('aes192', key);
    var decrypted = decipher.update(encrypted, 'hex', 'utf8');
    decrypted += decipher.final('utf8');
    return decrypted;
}

var data = 'Hello, this is a secret message!';
var key = 'Password!';
var encrypted = aesEncrypt(data, key);
var decrypted = aesDecrypt(encrypted, key);

console.log('Plain text: ' + data);
console.log('Encrypted text: ' + encrypted);
console.log('Decrypted text: ' + decrypted);
```

注意到AES有很多不同的算法，如`aes192`，`aes-128-ecb`，`aes-256-cbc`等，AES除了密钥外还可以指定IV（Initial Vector），不同的系统只要IV不同，用相同的密钥加密相同的数据得到的加密结果也是不同的。加密结果通常有两种表示方法：hex和base64，这些功能Nodejs全部都支持，但是在应用中要注意，如果加解密双方一方用Nodejs，另一方用Java、PHP等其它语言，需要仔细测试。如果无法正确解密，要确认双方是否遵循同样的AES算法，字符串密钥和IV是否相同，加密后的数据是否统一为hex或base64格式。

Diffie-Hellman
DH算法是一种密钥交换协议，它可以让双方在不泄漏密钥的情况下协商出一个密钥来。DH算法基于数学原理，比如小明和小红想要协商一个密钥，可以这么做：
小明先选一个素数和一个底数，例如，素数p=23，底数g=5（底数可以任选），再选择一个秘密整数a=6，计算A=g^a mod p=8，然后大声告诉小红：p=23，g=5，A=8；
小红收到小明发来的p，g，A后，也选一个秘密整数b=15，然后计算B=g^b mod p=19，并大声告诉小明：B=19；
小明自己计算出s=B^a mod p=2，小红也自己计算出s=A^b mod p=2，因此，最终协商的密钥s为2。
在这个过程中，密钥2并不是小明告诉小红的，也不是小红告诉小明的，而是双方协商计算出来的。第三方只能知道p=23，g=5，A=8，B=19，由于不知道双方选的秘密整数a=6和b=15，因此无法计算出密钥2。
用crypto模块实现DH算法如下：

```
const crypto = require('crypto');

// xiaoming's keys:
var ming = crypto.createDiffieHellman(512);
var ming_keys = ming.generateKeys();

var prime = ming.getPrime();
var generator = ming.getGenerator();

console.log('Prime: ' + prime.toString('hex'));
console.log('Generator: ' + generator.toString('hex'));

// xiaohong's keys:
var hong = crypto.createDiffieHellman(prime, generator);
var hong_keys = hong.generateKeys();

// exchange and generate secret:
var ming_secret = ming.computeSecret(hong_keys);
var hong_secret = hong.computeSecret(ming_keys);

// print secret:
console.log('Secret of Xiao Ming: ' + ming_secret.toString('hex'));
console.log('Secret of Xiao Hong: ' + hong_secret.toString('hex'));
```

运行后，可以得到如下输出：

```
$ node dh.js 
Prime: a8224c...deead3
Generator: 02
Secret of Xiao Ming: 695308...d519be
Secret of Xiao Hong: 695308...d519be//注意每次输出都不一样，因为素数的选择是随机的。
```

证书： crypto模块也可以处理数字证书。数字证书通常用在SSL连接，也就是Web的https连接。一般情况下，https连接只需要处理服务器端的单向认证，如无特殊需求（例如自己作为Root给客户发认证证书），建议用反向代理服务器如Nginx等Web服务器去处理证书。

**Web开发**（先不学）

Koa2

