# String

## 字符串定义

+ 引号：```$a = "cno107"```

+ nowdoc结构 :  没有使用单引号的单引号字符串

  ```php
   $str = <<<cno107
      ???what is this
  cno107;
   echo $str;  //???what is this
  ```

+ heredoc结构 :    没有使用双引号的双引号字符串

  ```php
   $str = <<<'cno107'
      1
     2
    3 
  cno107;
   echo $str;  
  ```

+ 结构化自定义字符要求：

  - 上边界符后面不可加任何东西

  - 下边界符必须顶格，后面只能跟分号

    ```php
    $a = 'cno107';
    
    $str  = <<<qqq
        <script>
        alert('{$a}hkjhk');
        </script>    
    qqq;
    echo $str;
    ```

+ 结构命名中 结构会保持不变 
  **但但但但但是**  第二行(1所在)无论从哪开始都会无视前面空格？？？？？？

  ```
  1
     2
    3 
  ```

## 字符串转义

```php
$a = 'abc\r\ndef\tkljk\'\"jn,\$hkjh`a';   //单引号只能识别 \'  
$b = "abc\r\ndef\tkljk\'\"jn,\$hkjh`b";   //双引号不能识别 \"

echo $a,'<br/>',$b;
```

newdoc ,heredoc同理

```php
//单双引号中 加入变量
$x = 107;
$a = 'acno $x';   // acno $x
$b = "bcno $x 2";  // bcno 107 2   双引号可以转义
$c = "bcno $x2";  //error 无法区分变量
$d = 'd{$x}d';    // 用 {$x}
```

## 字符串长度

+ 基本函数 ```strlen()```  得到长度(字节为单位)

  ```php
  $str = 'as';
  $str1 = 'あいぁ春123';  //utf8下汉字占3字节
  
  echo strlen($str);   //2
  echo '~~~';
  echo strlen($str1);  //15     
  ```

+ 多字节字符串拓展模块： mbstring拓展 （multi bytes）

首先需要在php.ini中开启mbstring    可以用```mb_```函数 ```mb_strlen()```

```php
$str1 = 'あいぁ春123?';
echo mb_strlen($str1);  //8
echo mb_strlen($str1,'utf-8');  //8  也可以传编码类型

```

## 相关函数

###连接/切分：

- implode(glue, arr)    用链接符来**连接一个arr**    返回一个str

  ```php
  $b = ['a','b','c'];
  $c = array('Hello','World!','Beautiful','Day!');
  $dd = implode('~',$b);
  var_dump($dd);   //string(5) "a~b~c"
  ```

- explode(delimiter，str, [显示个数])  用切分符来**切分一个str**。返回一个arr

  ```php
  $x = "abacadaeafag";
  $dd = explode('a',$x);
  var_dump($dd);
  //大于 0 - 返回包含最多 limit 个元素的数组
  //小于 0 - 返回包含除了最后的 -limit 个元素以外的所有元素的数组    相当于删除
  //0 - 会被当做 1, 返回包含一个元素的数组
  ```

- str_split(str , length)    每length个一组来**切分str**  返回一个arr

  ```php
  $a = '1234567890';
  $dd = str_split($a,'3');
  ```

###Trim字符串去除:

- trim(str ，charlist)    去除字符串 首尾 空白等特殊符号或指定字符序列   

  ```php
  //默认去除两边所有空格
  $a = "1123456789101111111";
  $dd = trim($a,'1');
  echo $dd;  //2345678910  从两边循环剔除，直到不是为止
  ```

- ltrim()   去除字符串 首 空白等特殊符号或指定字符序列

- rtrim()   去除字符串 尾 空白等特殊符号或指定字符序列

###大小转换函数:

- strtolower( str )
- strtoupper( str )
- ucfirst( str )   首字母大写    --->lcfirst 首字母小写
- ucwords() - 把字符串中每个单词的首字符转换为大写

###strpos查找函数；

- strpos()        查找字符串在另一字符串中第一次出现的位置（区分大小写）
- strrpos()      查找字符串在另一字符串中最后一次出现的位置（区分大小写）
- stripos()       查找字符串在另一字符串中第一次出现的位置（不区分大小写）
- strripos()      查找字符串在另一字符串中最后一次出现的位置（不区分大小写）

```php
//  rr  最后一次
//   i  不区分大小写
$a = "PhpYou love php, I love php too Php!";
echo mb_strlen($a);  //36  index:0~35
echo strpos($a,"php").'~';    //12
echo strrpos($a,'php').'~';   //24
echo stripos($a,'php').'~';   //0
echo strripos($a,'php').'~';  //32
```

###str_replace函数

- str_replace( search , replace , str , [$count] )   

  在str中查找search并替换为replace，把替换的个数放到变量\$count中去

```php
$a = "PhpYou love php, I love php too Php!";
$dd = str_replace('php',"js",$a,$count);
echo $dd.'---'.$count;
```

###printf関数

- printf()     类似于c      **返回值**：返回被输出字符串的长度

  ```php
  $a =12.346;
  printf('i am %.2f',$a);   //12.35
  echo printf('i am %.2f',$a);
  ```

- sprintf()   返回已格式化的字符串

###Other

- str_repeat(str , 次数)     str重复n次 并返回  
- str_shuffle(str)        随机打乱str  并返回

# Array

+ 定义

  - ```$arr1 = array(1,2,3);```

  - ```$arr2 = [4,5,6];```

  - $arr[]  = 1;       开起默认配列

    ```php
     $arr[] = 'a';
        $arr[10] = 17;
        $arr[] = 'b';    //会从11开始  且会被 后面的[11] 覆盖
        $arr['key'] = 'value';  //不会被 [12] 覆盖
        $arr[11] = 'c';
        $arr[12] = 'd';
      $arr[3] = '333';  //并不会被放到前面
        var_dump($arr); 
    //array(5) { [0]=> string(1) "a" [10]=> int(17) [11]=> string(1) "c" ["key"]=> string(5) "value" [12]=> string(1) "d" [3]=> string(3) "333"}
    
    ```

+ 数组特殊下标 的转换

  ```php
  $arr[False] = false;
      $arr[True] = true;
      $arr[Null] = Null;
     
      var_dump($arr); //array(3) { [0]=> bool(false) [1]=> bool(true) [""]=> NULL }
  ```

+ php数组中 没有类型限制，没长度限制
  存放在heap

 ## 多维数组

不建议三维以上 增加访问难度 降低访问效率

+ 二维数组：

  ```php
   $info = array(
          array('name' => 'jim','age' => 30),
          array('name' => 'jim','age' => 30),
          array('name' => 'jim','age' => 30)
      );
  
      print_r($info);
  ```

+ 异形数组（不规则数组）： 有普通变量也有嵌套
  不建议使用 

## 遍历Traversal--foreach

+ 基本查找

  ```php
  $ii = array(
          0 => array('name' => 'jim','age' => 30) ,
          1 => array('name' => 'bob','age' => 25) ,
          2 => array('name' => 'php','age' => 20) ,
  
      );
  print_r($ii[2]['name']);    
  ```

+ foreach遍历语法

  ```php
  // lv1  只有数值
  $arr = [1,2,3,4,5,6,7];
  foreach ($arr as $value ){
        echo $value;
     };
  
  // lv2  输出key(index)和value
  foreach ($arr as $key => $value ){      ////////////////
        echo $key.':'.$value."\n";
     };
  ```

  二维数组的话 通常不会两个维度下标都为数字 一般是一维为数字(默认)， 二维为字符串(db表字段)

  所以遍历的时候一般只针对一维遍历，然后取到二维数组元素 再通过下标去访问

  ```php
  foreach ($ii as $key => $value ){
         //1.可以继续foreach来遍历 $value
         //2. 通过下标访问
        echo 'name:'.$value['name']."\n";
     };
  ```

+ foreach遍历原理 ：利用指针获取数据 同时移动指针

  1. foreach会重置指针：指向第一个

  2. 进入foreach循环： 通过指针获取当前第一个元素，                                                                                       然后将下标取出放到对应的下标变量\$key中去(if exist)，将值取出放到对应的值变量$value中去

  3. 进入到循环内部，开始执行

  4. 重复2&3 直到2的时候遇到指针取不到内容(指针指向数组最后)
###for

```php
for($i = 0; $i < count($arr); $i++){
         //问题 相当于每次比较时都调用了 count函数 效率低
         //所以应该 在前先定义一下长度 for($i = 0,$ll = count($arr); $i< $ll ;$i++)
      echo 'index is '.$i.' and value is '.$arr[$i]."\n";
  }
```

###while each list  

+ While 没啥说的就是while 可以配合each和list

+ each：能够从一个数组中获取当前数组指针所指向的元素的下标和值   
              拿到之后数组指针下移 **同时拿到一个有四个元素的的数组返回**

  ```php
   0   => 下标      //
   1   =>  值
  key  => 下标
  value => 值
       
  print_r(each($arr));
  print_r(each($arr));  // 指针不会重置
  print_r(each($arr));     
  
  
  function fun_adm_each(&$array){
     $res = array();
     $key = key($array);
     if($key !== null){
         next($array); 
         $res[1] = $res['value'] = $array[$key];
         $res[0] = $res['key'] = $key;
     }else{
         $res = false;
     }
     return $res;
  }
  ```

+ list结构

  ```php
   $arr = array(1, 2=>'cno107');  //这有一个坑 k:0,v:1 ; k:1,v:NULL ; k:2;v:'cno107'
  
  list($first,$second,$third) = $arr;
  
   var_dump($first,$second,$third,$fourth);
  //int(1)         
  //NULL
  //string(6) "cno107"
  //NULL
  ```

+ While + each + list

  ```php
  $arr = [1,2,'name' => 'TOM',3,'age' => 30,4];
  
  while( list($k,$v) = each($arr) ){
           
     echo 'key is '.$k.' value is '.$v."\n";
  }
  ```

## 排序Sort

按照ASCII码进行比较，对原数组进行排序 引用传递

+ sort( )  顺 （下标重排）
+ rsort( ) 逆
+ asort( ) 顺  （下标保留）
+ arsort( ) 
+ ksort( )  按key名排序
+ krsort( ) 
+ shuffle( ) 打乱

## 指针pointer

+ reset( )  重置指针 到首位
+ end( )   重置到末尾
+ next( )   
+ prev( )
+ current( )   当前指针的value
+ key( )      当前指针的key
+ 注意next prev会离开数组 且回不来
  比如 最后一个 时next之后再prev 回不来滴 必须reset/end

## 相关函数

+ count ( )
+ array_push ( )
+ array_pop( )
+ array_reversel
+ array_shift( )   array_unshift( ) 
+ in_array( )
+ array_keys( )
+ array_values( )
+ array_slice (arr , start , end ).      切分数组(include start ,but no end)

#再帰ーRecursive

```php
function fei($tar){
    $arr[0] = 1;
    $arr[1] = 1;
    if($tar === 1 || $tar === 0){
        return 1;
    }
    return fei($tar-1) + fei($tar-2);
}

print_r(fei(15));   //num　　其实是第16位    
```

     ```php
//  递推  
function fei($tar){
        $arr[0] = 1;
        $arr[1] = 1;
        for($i = 2 ; $i < $tar ; $i++){
            $arr[$i] = $arr[$i-1] + $arr[$i-2];
        }
        return $arr;
    }

    print_r(fei(16));   //arrary   
     ```

# アルゴリズムとsort

## Bubble Sort

```php
//相邻俩比较
function bubbleSort($arr){
   $len = count($arr);
  for($j=0;$j<$len;$j++){
     for($i=0;$i<$len-$j;$i++){
         if($arr[$i] < $arr[$i+1]){
            //换位 可用位运算
         }
     }
  }
  return $arr;
}
$a = [7,5,6,9,3,1,2,1,1];
print_r(bubbleSort($a));   //arrary
```

## Selection Sort

```php
//第一个和剩下的比 第二个在和右边剩下的比
function SelctionSort($arr){
   $len = count($arr);
 for($i=0;$i<$len-1;$i++){
     $min = $i;
   for($j=$i;$j<$len;$j++){
      if($arr[$min] > $arr[$j]){
          $min = $j;
       }
   }

   if($min !== $i){
        //$arr[$min] and $arr[$i]交换
     }

 }
  return $arr;
}
$a = [3,2,1,4,6,5,9,7,8];
print_r(SelctionSort($a));   //arrary
```

## Insert Sort

+ 思路：  两部分 比较大小 后移 插入
  - 从数组中先取出第二个数 (记录k  &  v)
  - 让它和第一个数比较 如果它小
  - 变成它左边的值   且序号k-1   (这两步就是数字后移一位)
  - 这时候两个数会变成一样
  - 给序号在k-1的重新赋值  ， 值为当初取出来的v （在k-1处插入）

```php
function InsertSort($arr){
   $len = count($arr);
  for($i=1;$i<$len;$i++){
      $value = $arr[$i];  //current index's value  （拿出一个数）
      $key = $i;     //current index(key)
   while($key > 0 && $value > $arr[$key-1]){ //当前序号大于0 且左边比他大时
        $arr[$key] = $arr[$key-1];   //变成它左边的值
        $key--;                      //序号-1
                                      //这两步就是数字后移一位
   }                               
    $arr[$key] = $value;         //在key这个需要填值，值为当初拿出的数
  }
  return $arr;
}
$a = [3,2,1,4,6,5,9,7,8];
print_r(InsertSort($a));   //arrary
```

## Merge Sort

+ 二路归并  **（得是两个有序数列）**

```php
$arr1 =[1,3,5];
$arr2 =[2,4,6];

$arr3 = [];  //开启一个默认数组  把1,2合并过来

while(count($arr1) && count($arr2)){      
    $arr3[] = $arr1[0] < $arr2[0] ? array_shift($arr1) : array_shift($arr2);
    //进行比较把小的那个 从数组中取出 加到3里。 直到一个数组为空(另一个数组至少还剩一个)
}
$arr3 = array_merge($arr3,$arr2,$arr1);  //2,1有一个为空 但不能确定
 //因为1,2是有序数组 所以不管哪个剩2+的数据时 都已经是最大的了 所以直接拼在新数组后面就可以了
print_r($arr3);
```

+ merge sort

  1. 将arr拆成两个数组

  2. 重复1直到最小单元

  3. 申请空间 使其大小为两个已经排序数列之和 (该空间用来存放合并后的数组)

  4. 设两个指针，分别指向两个已经排序数列的起始位置

  5. 比较指针所指向的元素，选小的放到合并空间 并将指针移动到下一位

  6. 重复 直到某一指针超出序列尾

  7. 将另一个序列剩下的所有元素直接复制到合并序列尾
```php
function mergeSort($arr){
    //exit
    $len = count($arr);
    if($len <=1) return $arr;

    //slice arr
    $middle = ceil($len/2);  //index
    $left = array_slice($arr,0,$middle);   //  array 不包括结尾
    $right = array_slice($arr,$middle);

    //再帰点 $left和$right都没有排好序 而且可能是有多个元素的数组
     $left = mergeSort($left);

     $right = mergeSort($right);

    //二路归并
    $merge = [];
    while(count($left) && count($right)){
        $merge[] = $left[0] < $right[0] ? array_shift($left) : array_shift($right);

    }
    $merge = array_merge($merge,$left,$right);
    return $merge;
}

print_r($merge);

```


















