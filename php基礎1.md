# 变量

## <span id='jingtai'>静态变量</span>

```static``` 来定义 可同时赋值

+ 是在函数内部定义的变量，用来实现 跨(同一个)函数共享数据的变量，
+ staic定义的变量 多次调用 值会继承 而不会初始化

```php
function  rf(){
     $local = 1 ;
 static $static = 1;
    echo $local++,$static++,'</<br>>';
 }
rf();   // 11
rf();   // 12
rf();   // 13
```

## 变量传递

```php
<?php
//值传递
 $a = 10;
 $b = $a;
 $b = 5;
 echo $a,$b,'<br>';      //10 5
//引用传递
$c = 10;
$d = &$c;       //使$d $c指向同一个地方
$d = 5;
echo $c,$d,'<br>';     // 5  5
```

# ！常量

## 定义形式

```php
define('name',value)
```

```php
const name = value
```

```php
//特殊常量
define('-_-',smile);  // OK
const -_- = smile ;    // error
```

## 常量使用

+ 不可改变    定义时必须赋值

+ 注意特殊常量的访问方式     ```echo constant('-_-')```

## 系统常量
+ PHP_VERSION     

+ PHP_INT_SIZE            整形所占用的字节 4  

+ PHP_INT_MAX   最大整数（  允许出现负数，带符号）

+ php特殊常量  \_\_常量名\_\_

  - \_\_DIR\_\_     当前被执行的脚本的  绝对路径
  -  _\_FILE\_\_    当前被执行的脚本的  绝对路径 带文件名
  -  _\_LINE\_\_   当前所属的行数
  -  _\_NAMESPACE\_\_   当前所属的命名空间
  -  _\_CLASS\_\_     当前所属的类
  - _\_METHOD\_\_    当前所属的方法
  
# 超全局变量&系统常量*
<table>
<thead>
<tr>
<th align="center">常量名</th>
<th align="center" style="width:100px">类型</th>
<th align="center">用途</th>
</tr>
</thead>
<tbody>
<tr>
<td align="center">_<em>FILE</em>_</td>
<td align="center">系统常量</td>
<td align="center">当前PHP文件的相对路径</td>
</tr>
<tr>
<td align="center">_<em>LINE</em>_</td>
<td align="center">系统常量</td>
<td align="center">当前PHP文件中所在的行号</td>
</tr>
<tr>
<td align="center">_<em>CLASS</em>_</td>
<td align="center">系统常量</td>
<td align="center">当前类名，只对类起作用</td>
</tr>
<tr>
<td align="center">DIRECTORY_SEPARATOR</td>
<td align="center">系统常量</td>
<td align="center">目录分隔符，windows下为\，linux下为/</td>
</tr>
<tr>
<td align="center">PHP_EOL</td>
<td align="center">系统常量</td>
<td align="center">换行符</td>
</tr>
<tr>
<td align="center">PHP_VERSION</td>
<td align="center">系统常量</td>
<td align="center">php版本号</td>
</tr>
<tr>
<td align="center">PHP_OS</td>
<td align="center">系统常量</td>
<td align="center">当前操作系统</td>
</tr>
<tr>
<td align="center">M_PI</td>
<td align="center">系统常量</td>
<td align="center">圆周率常量值</td>
</tr>
<tr>
<td align="center">M_E</td>
<td align="center">系统常量</td>
<td align="center">科学常数e</td>
</tr>
<tr>
<td align="center">M_LOG2E</td>
<td align="center">系统常量</td>
<td align="center">代表log<sub>2</sub>e，以2为底e的对数</td>
</tr>
<tr>
<td align="center">M_LN2</td>
<td align="center">系统常量</td>
<td align="center">2的自然对数</td>
</tr>
<tr>
<td align="center">M_LN10</td>
<td align="center">系统常量</td>
<td align="center">10的自然对数</td>
</tr>
<tr>
<td align="center">E_ERROR</td>
<td align="center">系统常量</td>
<td align="center">最近的错误之处</td>
</tr>
<tr>
<td align="center">E_WARNING</td>
<td align="center">系统常量</td>
<td align="center">最近的警告之处</td>
</tr>
<tr>
<td align="center">E_PARSE</td>
<td align="center">系统常量</td>
<td align="center">剖析语法有潜在问题之处</td>
</tr>
<tr>
<td align="center">_<em>METHOD</em>_</td>
<td align="center">系统常量</td>
<td align="center">表示类方法名，比如B::test</td>
</tr>
<tr>
<td align="center">$_SERVER</td>
<td align="center">全局变量</td>
<td align="center">返回服务器相关信息，返回一个数组</td>
</tr>
<tr>
<td align="center">$_GET</td>
<td align="center">全局变量</td>
<td align="center">所有GET请求过来的参数</td>
</tr>
<tr>
<td align="center">$_POST</td>
<td align="center">全局变量</td>
<td align="center">所有POST过来的参数</td>
</tr>
<tr>
<td align="center">$_COOKIE</td>
<td align="center">全局变量</td>
<td align="center">所有HTTP提交过来的cookie</td>
</tr>
<tr>
<td align="center">$_FILES</td>
<td align="center">全局变量</td>
<td align="center">所有HTTP提交过来的文件</td>
</tr>
<tr>
<td align="center">$_ENV</td>
<td align="center">全局变量</td>
<td align="center">当前的执行环境信息</td>
</tr>
<tr>
<td align="center">$_REQUEST</td>
<td align="center">全局变量</td>
<td align="center">相当于$_POST、$_GET、$_COOKIE提交过来的数据，因此这个变量不值得信任</td>
</tr>
<tr>
<td align="center">$_SESSION</td>
<td align="center">全局变量</td>
<td align="center">session会话变量</td>
</tr>
 <tr>
<td align="center">$GLOBALS</td>
<td align="center">全局变量</td>
<td align="center">一个包含了全部变量的全局组合数组。变量的名字就是数组的键 不加$</td>
</tr>   
</tbody>
</table>

# 数据类型*

## PHP 8种数据类型
  三大类 八小类
+ 简单(基本)数据类型
  - 整型 ： int/integer  系统分配4字节存储 ， 表示整数类型
  - 浮点型 ： float/double 系统分配8字节存储 表示小数或者整形存不下的整数
  - 字符串 ： string
  - 布尔类型 ： bool/boolean
+ 复合数据类型
  - 对象类型 ： obj
  - 数组类型 ： arrary
+ 特殊数据类型
  - 资源类型  resource  存放资源数据( db , file ……)
  - 空类型 NULL
##数据类型转换

自动转换 ： php7 error             

手动转换    ：```(float)$a```     括号，要转的类型，要转的变量    **不会改变数据类型**  与**settype()**不同

+ 其他转**布尔**

  - False ： ""   null  $x  undefined  false   0  "0"  array() 
  - True : 其余

+ 其他转**NUM**

  - true ： 1      false：0

  - 字母开头的字符串 永为0

  - 以数字开头的String ，取到碰到字符串为止（不会同时包含两个小数点）

    ```php
     $a = "abc1.1.1";
     $b = "33.3.3abx";
    echo(float)$a,'<br/>',(float)$b;
    //0    33.3
    ```

## 类型判断

+ 判断函数 ```is_XXX(变量名)```       return 相同为true

+ **bool不能echo查询 因为不能判断是bool的true 还是别的类型的true​**

  请用```var_dump()```  用于输出变量的相关信息     

  ```php
   $a = [13,'hello',"22",true];
   var_dump($a);    //传几个都无所谓
  ///Users/cno.107/Desktop/untitled/a.php:4:
  //array (size=4)
  //  0 => int 13
  //  1 => string 'hello' (length=5)
  //  2 => string '22' (length=2)
  //  3 => boolean true
  ```

+ **```gettype(变量名)```**   获取类型 得到的事该类型对应的字符串

+ **```settypte(变量名,类型)```** 设定类型 **会改变数据类型**        与手动转换不同

  ```php
  $a ="22";
  echo (float)$a,'</br>';   //22
  echo gettype($a);         //String
  var_dump($a);            //string '22' (length=2)
  echo  gettype($a);       //String
  settype($a,"int");
  echo  gettype($a);        //interger
  ```

+ **empty()**

+ **isset()**   检测变量是否设置，并且不是 NULL

  ```php
  $a ;
   $b = null;        
   var_dump(isset($a),isset($b));   //false false   undefined的元素也为false
  ```

## int类型

整型 ： int/integer  系统分配4字节存储 ， 表示整数类型

- 一个字节8位 最大32位   32个1 ---->(42億)  
-  php中包含负数所以只能显示21億
- 四种整形的定义方式
  - 10進数　　　$a = 120;
  - 2進数             **$a = 0b110**
  - 8進数           **$a = 0110** 
  - 16進数              **$a = 0x110**

-  进制转换

  - **decbin()**     10 ——>  2 

  - **decoct()**      10 ———>8

  - **dechec()**     10 ———> 16  

  - **bindec()**       2  ———> 10 

    

## float类型

精度范围大概在 15 个有效数字左右

+ float数域大 精度低

  ```php
   $a = 2.1;
   $b = 0.7;
   $c = $a/3;
   echo $b," ",$c;
   var_dump($b === $c);       //0.7  0.7 false
  ```

  

+ 两种定义方式

  ```php
   $a = 1.23;
   $b = 1.23e5; //12300000
   $c = PHP_INT_MAX + 1;    //超出最大后 会用浮点型存储
  ```
##Boolean类型
 + empty() 判断数据的值是否为'空'  不是NULL 空则T 不空则F
 + isset() 判断数据存储的变量本身是否存在(已设置),存在变量T 不存在F
## 伪类型

Mixed： 混合，可以是多种php的数据类型

Number ：数值 ，可以是任意的int或者float

# 运算符
# 运算符
## 连接运算符号   .
  + .  将俩String连一块
  + .= 左右连起来 并赋值给左边
    ```php
     $a = 2.1;
     $c = 2;
     $b = "cno";
    
     echo $c.$a; //22.1
     echo 2.$a;  //error
    echo  2.1.$a; //2.12.1
    ```
## 错误抑制符   @
## 自操作运算符 ++
```php
 $a = 10 ;
 $b = 10 ;
 $c = $a++;   //先赋值 后计算
 $d = ++$b;   //先计算 后赋值
 echo 'c:'.$c.'~~d:'.$d;      //c:10~~d:11
```
##位运算符(同ES6)
取出计算机中最小的单位进行计算(位bit)进行计算   **比较的是补码 if<0 需要变回去**
+ &　按位与，两个位都为1 则结果为1 反之0　<span id='weiyunsuan'></span>

+ |      或    两个有一个为1 则为1

+ ~     非    一个位为1  则为0

+ ^    异或  俩相同为0  不同为1

  ```php
  10 ^  -10       //-4
  10 二进制    00001010    //正数不变  原码==补码
  -10二进制。  10001010(原码)  ---> 11110101(反码) ---->(+1)  11110110(补码) 
  比较补码
       00001010
       11110110
  所以  11111100(补码)     因为符号位为1 所以为负数 需要变回去 -1 取反 ---> 10000100 --> -4
  ```

+ <<    左移 整个位(4*8)，左移一位 右补0

+ \>>     右移 整个位(4*8)，右移一位 左补符号位
  左移相当于\*2。  右移相当于/2 
### **计算机码**
数值本身最左边一位用来充当符号位 ：正数 0~~~~~~负数 1
 + 原码true code
   + data从10进制变成2进制的结果
   + 正数： 左边符号位为0
   + 负数： 左边符号位为1
 + 反码ones-complement code   针对负数

    + 符号位不变 其余取反  
 + 补码complemental code   针对负数

   + 反码+1

 + System中有两个0   +0  -0
   + +0 ： 00000000
   + -0 ： 10000000  true code
     反码 111111111
     补码 11111111+1  --> 00000000 所以两个0相等 
### 位运算の応用

<https://blog.csdn.net/zmazon/article/details/8262185>

+ **交换两个数**

  ```php
  a = a ^ b ;
  b = a ^ b ;
  a = a ^ b ;       // n^m^m=n
  ```

+ ***2    /2    *2的m次方**

  ```php
  n << 1     // 左移*2
  n >> 1     //右移 /2 
  n << m     
  ```

+ **判断奇偶**

  ```php
  a & 1 == 0   // even   理由 &表示两者都为1时结果才为1 其他为0
  a & 1 == 1   // odd    1二进制前面补0 所以出现0了 &结果必为0 所以只需要比较最后一位即可
  ```

+ **if(x == a) x = b; if(x == b) x = a;**

  ```php
  x = a ^ b ^ x;
  ```

+ 取绝对值

  ```php
  (n ^ (n >> 31)) - (n >> 31)
  ```

  

##运算符优先级

| 结合方向 | 运算符                                                  | 附加信息                                                    |
| -------- | ------------------------------------------------------- | ----------------------------------------------------------- |
| 无       | clone new                                               | clone 和 new                                                |
| 左       | [                                                       | array()                                                     |
| 右       | ++ — ~ (int) (float) (string) (array) (object) (bool) @ | 类型和递增／递减                                            |
| 无       | instanceof                                              | 类型                                                        |
| 右       | !                                                       | [逻辑运算符](http://www.php.cn/wiki/100.html)               |
| 左       | * / %                                                   | [算术运算符](http://www.php.cn/wiki/84.html)                |
| 左       | + – .                                                   | 算术运算符和[字符串运算符](http://www.php.cn/wiki/101.html) |
| 左       | << >>                                                   | 位运算符                                                    |
| 无       | == != === !== <>                                        | 比较运算符                                                  |
| 左       | &                                                       | 位运算符和引用                                              |
| 左       | ^                                                       | 位运算符                                                    |
| 左       | \|                                                      | 位运算符                                                    |
| 左       | &&                                                      | 逻辑运算符                                                  |
| 左       | \|\|                                                    | 逻辑运算符                                                  |
| 左       | ? :                                                     | 三元运算符                                                  |
| 右       | = += -= *= /= .= %= &= \|= ^= <<= >>= =>                | [赋值运算符](http://www.php.cn/wiki/86.html)                |
| 左       | and                                                     | 逻辑运算符                                                  |
| 左       | xor                                                     | 逻辑运算符                                                  |
| 左       | or                                                      | 逻辑运算符                                                  |
| 左       | ,                                                       | 多处用到                                                    |



# 文件包含*

## 文件包含四种形式

+ **require：**require函数一般放在PHP脚本的最前面，PHP执行前就会先读入require指定引入的文件，包含并尝试执行引入的脚本文件。require的工作方式是提高PHP的执行效率，当它在同一个网页中解释过一次后，第二次便不会解释。但同样的，正因为它不会重复解释引入文件，所以当PHP中使用循环或条件语句来引入文件时，需要用到include
+ **include：**可以放在PHP脚本的任意位置，一般放在流程控制的处理部分中。当PHP脚本执行到include指定引入的文件时，才将它包含并尝试执行。这种方式可以把程序执行时的流程进行简单化。当第二次遇到相同文件时，PHP还是会重新解释一次，include相对于require的执行效率下降很多，同时在引入文件中包含用户自定义函数时，PHP在解释过程中会发生函数重复定义问题
+ **require_once / include_once：**分别与require / include作用相同，不同的是他们在执行到时会先检查目标内容是不是在之前已经导入过，如果导入过了，那么便不会再次重复引入其同样的内容

## 文件加载原理

+ php代码之行流程

  - read file code （php）
  - compaile ： 将php转换为字节码(生成opcode)
  - zendengine来解析opcode 按照字节码进行逻辑运算
  - 转换为html代码

+ 加载原理

  - php被包含的file是单独进行编译的(⬆️)

    php file在编译过程中出现语法错误，会报错不执行

    如果被包含的文件有错，会在执行到include时才报错

## include和require区别

+ ### **include和include_once：**

  ​    include载入的文件不会判断是否重复，只要有include语句，就会载入一次（即使可能出现重复载入）。而include_once载入文件时会有内部判断机制判断前面代码是否已经载入过。这里需要注意的是include_once是根据前面有无引入相同路径的文件为判断的，而不是根据文件中的内容（即两个待引入的文件内容相同，使用include_once还是会引入两个）

+ ### **include和require：**

  include报错会继续执行。（错误较轻）

  require报错会停止执行。  （错误较重）

  

 ## 文件加载路径

+ 绝对path 用系统常量来找

  _\_DIR\_\_     当前被执行的脚本的  绝对路径

  ```php
  define('DS',DIRECTORY_SEPARATOR);   //把系统分隔符定义为DS
  
  include __DIR__ . DS . 'test2.php';
  
  //也可以用全局变量 $_SERVER 获取网站根目录
  ```

  

#  Function

+ Arguments default value

  ```php
  //JS也可以
  function poi($n ,$m=3){
       echo 'i am '.($n+$m).' poi function';
   }
  poi(1);   //1+3 = 4
  ```

## 引用传递内部参数变化影响外部

```php
$x = 9;
function add($num){
    $num += 1;
    echo 'function :i am '.$num.'</br>';     // 10
}
add($x);
echo 'out :i am '.$x;      // 9
```

```php
$x = 9;
function add(&$num){  // &+变量  不可以传实际值
    $num += 1;
    echo 'function :i am '.$num.'</br>';    //10
}
add($x);    
echo 'out :i am '.$x;     //10
```

## Scope

+ 全局          ：usr自己定义的
  - 脚本周期 ： 直到脚本运行结束
+ 局部
  + 函数周期    ： fun执行结束 
+ 超全局空间     ：  系统定义的  没有访问限制

```php
 $abc = 123;
  echo $GLOBALS['abc'];    //123 注意不要加$  only key
```

```php
 $abc = 123;
function xxx(){
      $inner = __FUNCTION__;

      echo $abc;    //局部 访问不了  全局变量
  }
  xxx();
  echo $inner;     // 全局 访问不了  局部变量
```

为了解决 <font color=red>局部 访问不了  全局变量</font> 可以使用超全局变量

```php
  $abc = 123;
  echo $GLOBALS['abc'];

  function xxx(){
      //      var_dump($GLOBALS);
      echo $GLOBALS['abc'];    // 超全局 🐂🍺
  }

xxx();
```

那么除了 $GLOBALS 呢   废话当然也除了 变量传递と引用传递

```php
//在局部使用 global 定义变量
//不能在用global声明变量的同时给变量赋值
$a = 10;
function  rf(){
     global $a;     //相当于定义一个变量 然后再让她升级为 global
     echo $a;
    global $b;
     $b = 7;
 }
 rf();
 echo $b;
//这样全局可以访问局部。局部也可以访问全局
```

## [静态变量](#jingtai)

## 可变函数

```php
$a = function(){}
$a();
```

## 闭包函数

```php
//和js不同 访问不到外部变量
<?php

   function aaa(){
       $name = __FUNCTION__;
       $innerfun = function (){
             echo $name;   //和js不同 访问不到外部变量
       }
       $innerfun();
   }
   aaa();
```

和js不同 访问不到外部变量  用 use（ ）解决

```php
 function aaa(){
       $name = __FUNCTION__;
       $age = 20;
       $job = 'studen';
       $innerfun = function($age) use ($name){    //use (变量)
             echo $name; 
             echo $age;
             echo $job;  //undefined
       };
       $innerfun(name);
   }
   aaa();
```

Php和js闭包比较

```php+HTML
//php
<?php
   function aaa(){
       $num =1 ;
       $innerfun = function() use ($num){
           echo $num++;
       };
      return $innerfun;
   }

   $bbb = aaa();
   $bbb();  //1
   $bbb();  //1
//js
<script>
   function  fun() {
   let name = 'adc';
   let num = 1;
   let inner = () => {
       console.log(num++)
   }
  return  inner;
}
let a = fun();
a();  //1
a();  //2 
</script>
```
# 系统常用関数*

## 出力

```php
print()      //返回值为1   echo print('a')   ----> a1
print_r()    //类似于var_dump
echo
var_dump()
 
1.echo 和 print 的区别

共同点：首先echo 和 print 都不是严格意义上的函数，他们都是 语言结构;他们都只能输出 字符串，整型跟int型浮点型数据。不能打印复合型和资源型数据；
而区别是：echo 可以连续输出多个变量，而print只能一次输出一个变量。print打印的值能直接复制给一个变量，如 $a = print “123”;
而echo 不可以，它没有像函数的行为，所以不能用于函数的上下文。在使用时，echo() 函数比 print()速度稍快。

 2.var_dump()和print_r()的区别
共同点：两者都可以打印数组，对象之类的复合型变量。
区别：print_r() 只能打印一些易于理解的信息，且print_r()在打印数组时，会将把数组的指针移到最后边，使用 reset() 可让指针回到开始处。 而var_dump()不但能打印复合类型的数据，还能打印资源类型的变量。且var_dump()输出的信息则比较详细，一般调试时用得多    
```

## date

```php
date()    //传字符串
    echo date('Y 年 m 月 d 日 H:i:s');   //current
    echo date('Y 年 m 月 d 日 H:i:s',12345678);  //第二个参数为指定的timestamp
time()     //get current timestamp
microtime()  //前面是小数点后8位时间。后面是timestamp  0.16998800 1556031031
strtotime()  //贵定格式的String ---> timestamp    
```

## 数学函数

```php
min();
max();
rand();  //得到指定区间的随机整数
mt_rand() //同上 底层不同 建议使用        $int = mt_rand(4,10);
round();
ceil();
floor();
pow();  // pow(2,10) == 2^10 == 1024
abs(); //absolute
sqrt();  
```

## 有关函数的函数

```php
//function_exists();   判断是否存在
// func_get_arg();     获取指定argument
// func_get_args();    获取全部arguments (arr)
// func_num_args();    获取arguments数量
echo '<pre>';
   function test($a,$b) {
       var_dump(func_get_arg(1));   // 'b' 
       var_dump(func_get_args());   // ''
       echo func_num_args();        // 3
   }

   function_exists('test') && test('a','b','c');
```

#ERROR

##错误处理

+ 分类：  
  - 语法错误 ： Parse error
  - 运行时错误： runtime error
  - 逻辑错误：  与预想结果不一样
+ Error code：
  - ：system error
     - E_PARSEP : complie err,code can't run
     - E_ERROR : 致命错误，会导致卡在当前代码处 无法继续
     - E_WARNING: 可能与预想结果不一样
     - E_NOTICE
  - :Usr error 
     -  E_USER_ERROR;E_USER_NOTICE;E_USER_WARNING
  - : Other: E_ALL 所有错误 建议开发环境使用
+ 所有以E开头的错误常量其实都是由一个字节存储的，每一种err占据一个对应的位

 if想进行一些err控制 可以采用[位运算](#weiyunsuan)进行操作

       ```php
E_ALL & ~E_NOTICE    //排除notice 级别

//原理：E_All全是 1      E_NOTICE有一位是1  ～取反 --->   有一位是0
//& 相同取1 不同为0  所以只有notice那块不同 取0 所以结果 排除notice   
    
    
E_WARNING | E_NOTICE  //只要这俩   因为(两个有一个为1 则为1) 
       ```

## 触发错误

```php
trigger_error(errormsg,errortype);  //手动触发  E_USER_ERROR;E_USER_NOTICE;E_USER_WARNING

 trigger_error('あら',E_USER_WARNING); //默认notice
```

用此来控制 代码是否继续进行

## 错误设置

显示：

+ Error_reporting():
+ ini_set('配置文件中的option','value'):

```php
ini_set( 'error_reporting','E_All' );  //显示什么级别的错误
ini_set( 'display', 1 ); // on/off     是否显示错误
```

```php
<?php
 // 关闭错误报告
 error_reporting(0);

 // 报告 runtime 错误
 error_reporting(E_ERROR | E_WARNING | E_PARSE);

 // 报告所有错误
 error_reporting(E_ALL);

 // 等同 error_reporting(E_ALL);
 ini_set("error_reporting", E_ALL);

 // 报告 E_NOTICE 之外的所有错误
 error_reporting(E_ALL & ~E_NOTICE);
```

###**日志log设置**：

  1.不友好 2.不安全(暴露site info)

```php
//首先通过Phpstorm来确定当前加载的php-cgi所在位置
//我应该是放在了  /Applications/MAMP/bin/php/php7.1.1/
//在此目录下  bin/php-cgi
//           conf/php.ini       这个是配置文件 通过vim来改变里面error_log的出力路径
//           /logs/php_error.log    用来保存logs
 error_log(msgStr,type); //type默认为0 本地保存
```

##自定义错误处理

+ 最简单的错误处理 ```trigger_error(errormsg,errortype)```
+ php系统提供了一种用户处理错误的机制：用户DIY错误处理函数，然后

将其添加到System 错误处理当中去，**然后以后碰到的所有错误，都会触发这个自定义错误函数**

1. ```set_error_handler（ cb ）```

   ```php
   function myErr($errno,$errstr,$errfile,$errline){
          if(!(error_reporting()  & $errno )){  //有$errno则结果为1
              echo '不存在这种错误'; //排除当前系统里没有的错误类型(展示不出来的错误类型)
          }
          //开始判断
          switch($errno){
              case E_ERROR:
              case E_USER_ERROR:
                  echo '这嘎达有错误'.$errfile.'在第'.$errline.'行'.'<br/>';
                  echo '错误信息:'.$errstr;break;
              case E_WARNING:
              case E_USER_WARNING:
                  echo '这嘎达有警告'.$errfile.'在第'.$errline.'行'.'<br/>';
                  echo '错误信息:'.$errstr;break;
              case E_NOTICE:
              case E_USER_NOTICE:
                  echo '这嘎达有注意'.$errfile.'在第'.$errline.'行'.'<br/>';
                  echo '错误信息:'.$errstr;break;
   
          }
    };
   
     echo $a;   //初始
     set_error_handler('myErr');
     echo $a;    //自定义的
   ```

   

   

​    


​      






















































