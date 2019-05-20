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



 



















