# regx-shortcut
## 正则表达式速查表

字符  | 描述 
-----|------
\    | 将下一个字符标记为或特殊字符、或原义字符、或向后引用、或八进制转义符。例如， 'n' 匹配字符 'n'。'\n' 匹配换行符。序列 '\\\\' 匹配 "\"，而 '\\(' 则匹配 "("。
^ | 匹配输入字符串的开始位置。如果设置了RegExp对象的Multiline属性，^也匹配“n”或”r”之后的位置。
$ | 匹配输入字符串的结束位置。如果设置了RegExp对象的Multiline属性，$也匹配“n”或”r”之前的位置。
* | 匹配前面的子表达式零次或多次。例如，zo*能匹配“z”以及”zoo”。*等价于{0,}。
+ | 匹配前面的子表达式一次或多次。例如，“zo+”能匹配”zo”以及”zoo”，但不能匹配”z”。+等价于{1,}。
? | 匹配前面的子表达式零次或一次。例如，“do(es)?”可以匹配”does”或”does”中的”do”。?等价于{0,1}。
{*n*} | *n*是一个非负整数。匹配确定的*n*次。例如，“o{2}”不能匹配”Bob”中的”o”，但是能匹配”food”中的两个o。
{*n*,} | *n*是一个非负整数。至少匹配*n*次。例如，“o{2,}”不能匹配”Bob”中的”o”，但能匹配”foooood”中的所有o。”o{1,}”等价于”o+”。”o{0,}”则等价于”o*”。
{*n*,*m*} | *m*和*n*均为非负整数，其中*n*<=*m*。最少匹配*n*次且最多匹配*m*次。例如，“o{1,3}”将匹配”fooooood”中的前三个o。”o{0,1}”等价于”o?”。请注意在逗号和两个数之间不能有空格。
? | 当该字符紧跟在任何一个其他限制符（\*, +, ?, {*n*}, {*n*,}，{*n*,*m*}）后面时，匹配模式是非贪婪的。非贪婪模式尽可能少的匹配所搜索的字符串，而默认的贪婪模式则尽可能多的匹配所搜索的字符串。例如，对于字符串```oooo```，```o+?```将匹配单个```o```，而```o+```将匹配所有```o```。
. | 匹配除换行符```\n```之外的任何单个字符。要匹配```.```，请使用像```\.```。
(pattern) | 匹配pattern并获取这一匹配。所获取的匹配可以从产生的Matches集合得到，在JS中则使用$0…$9属性。要匹配圆括号字符，请使用```\(```或```\)```。
(?:pattern) | 匹配pattern但不获取匹配结果，也就是说这是一个非获取匹配，不进行存储供以后使用。这在使用或字符<code>(&#124;)</code>来组合一个模式的各个部分是很有用。例如<code>industr(?:y&#124;ies)</code>就是一个比<code>industry&#124;industries</code>更简略的表达式。
(?=pattern) | 正向肯定预查，在任何匹配pattern的字符串开始处匹配查找字符串。这是一个非获取匹配，也就是说，该匹配不需要获取供以后使用。例如，<code>Windows(?=95&#124;98&#124;NT&#124;2000)</code>能匹配<code>Windows2000</code>中的<code>Windows</code>，但不能匹配<code>Windows3.1</code>中的<code>Windows</code>。预查不消耗字符，也就是说，在一个匹配发生后，在最后一次匹配之后立即开始下一次匹配的搜索，而不是从包含预查的字符之后开始。
(?!pattern) | 正向否定预查，在任何不匹配pattern的字符串开始处匹配查找字符串。这是一个非获取匹配，也就是说，该匹配不需要获取供以后使用。例如<code>Windows(?!95&#124;98&#124;NT&#124;2000)</code>能匹配<code>Windows3.1</code>中的<code>Windows</code>，但不能匹配<code>Windows2000</code>中的<code>Windows</code>。预查不消耗字符，也就是说，在一个匹配发生后，在最后一次匹配之后立即开始下一次匹配的搜索，而不是从包含预查的字符之后开始.
(?<=pattern) | 反向肯定预查，与正向肯定预查类拟，只是方向相反。例如，<code>(?<=95&#124;98&#124;NT&#124;2000)Windows</code>能匹配<code>2000Windows</code>中的<code>Windows</code>，但不能匹配<code>3.1Windows</code>中的<code>Windows</code>。
(?<!pattern) | 反向否定预查，与正向否定预查类拟，只是方向相反。例如<code>(?<!95&#124;98&#124;NT&#124;2000)Windows</code>能匹配<code>3.1Windows</code>中的<code>Windows</code>，但不能匹配<code>2000Windows</code>中的<code>Windows</code>。
x&#124;y | 匹配x或y。例如，<code>z&#124;food</code>能匹配<code>z</code>或<code>food</code>。<code>(z&#124;f)ood</code>则匹配<code>zood</code>或<code>food</code>。
[xyz] | 字符集合。匹配所包含的任意一个字符。例如，```[abc]```可以匹配```plain```中的```a```。
[^xyz] | 负值字符集合。匹配未包含的任意字符。例如，```[^abc]```可以匹配```plain```中的```p```。
[a-z] | 字符范围。匹配指定范围内的任意字符。例如，```[a-z]```可以匹配```a```到```z```范围内的任意小写字母字符。
[^a-z] | 负值字符范围。匹配任何不在指定范围内的任意字符。例如，```[^a-z]```可以匹配任何不在```a```到```z```范围内的任意字符。
\\b | 匹配一个单词边界，也就是指单词和空格间的位置。例如，```er\\b```可以匹配```never```中的```er```，但不能匹配```verb```中的```er```。
\\\B | 匹配非单词边界。```er\\B```能匹配```verb```中的```er```，但不能匹配```never```中的```er```。
\\cx | 匹配由```x```指明的控制字符。例如， ```\cM``` 匹配一个 Control-M 或回车符。```x``` 的值必须为 ```A-Z``` 或 ```a-z``` 之一。否则，将 ```c``` 视为一个原义的 ```'c'``` 字符。
\\d | 匹配一个数字字符。等价于```[0-9]```。
\\D | 匹配一个非数字字符。等价于```[^0-9]```。
\\f | 匹配一个换页符。等价于```\\x0c```和```\\cL```。
\\n | 匹配一个换行符。等价于```\\x0a```和```\\cJ```。
\\r | 匹配一个回车符。等价于 ```\\x0d``` 和 ```\\cM```。
\\s | 匹配任何空白字符，包括空格、制表符、换页符等等。等价于 ```[\\f\\n\\r\\t\\v]```。
\\S | 匹配任何非空白字符。等价于 ```[^\\f\\n\\r\\t\\v]```。
\\t | 匹配一个制表符。等价于 ```\\x09``` 和 ```\\cI```。
\\v | 匹配一个垂直制表符。等价于 ```\\x0b``` 和 ```\\cK```。
\\w | 匹配包括下划线的任何单词字符。等价于```[A-Za-z0-9_]```。
\\W | 匹配任何非单词字符。等价于```[^A-Za-z0-9_]```。

## 优先级
- \ 　　　　　　　　　　　       转义符
- (), (?:), (?=), [] 　　　　　       圆括号和方括号
- *, +, ?, {n}, {n,}, {n,m} 　        限定符
- ^, $, \anymetacharacter 　　位置和顺序
- | 　　　　　　　　　　　　　 “或”操作