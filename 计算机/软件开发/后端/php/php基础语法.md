
下面是 PHP 的基础语法简介，适合初学者快速入门：

---

## 1. PHP 标签

PHP 代码写在 `<?php ... ?>` 标签内：

```php
<?php
echo "Hello, World!";
?>
```

---

## 2. 变量

变量以 `$` 开头，区分大小写，无需声明类型：

```php
<?php
$name = "小明";
$age = 18;
?>
```

---

## 3. 数据类型

- 字符串（String）：`$str = "hello";`
- 整型（Integer）：`$num = 123;`
- 浮点型（Float/Double）：`$price = 12.5;`
- 布尔型（Boolean）：`$flag = true;`
- 数组（Array）：`$arr = [1, 2, 3];`
- 对象（Object）：`$obj = new MyClass();`
- NULL：`$a = null;`

---

## 4. 输出

```php
echo "输出内容";
print "输出内容";
```

---

## 5. 注释

```php
// 单行注释
# 也是单行注释
/* 多行
   注释 */
```

---

## 6. 运算符

- 算术运算符：`+ - * / %`
- 赋值运算符：`= += -= *= /=`
- 比较运算符：`== != > < >= <=`
- 逻辑运算符：`&& || !`
- 字符串拼接：`.` 
```php
$str1 = "Hello";
$str2 = "World";
$result = $str1 . " " . $str2; // 使用 . 连接字符串
echo $result; // 输出 "Hello World"
```
---

## 7. 条件语句

```php
if ($age > 18) {
    echo "成年人";
} elseif ($age == 18) {
    echo "刚成年";
} else {
    echo "未成年";
}
```

---

## 8. 循环语句

```php
// for 循环
for ($i = 0; $i < 5; $i++) {
    echo $i;
}

// while 循环
$i = 0;
while ($i < 5) {
    echo $i;
    $i++;
}

// foreach 循环
$arr = [1, 2, 3];
foreach ($arr as $value) {
    echo $value;
}
```

---

## 9. 函数

```php
function add($a, $b) {
    return $a + $b;
}
echo add(1, 2); // 输出 3
```

---

## 10. 数组

```php
// 索引数组
$arr = [1, 2, 3];

// 关联数组
$user = [
    "name" => "小明",
    "age" => 18
];
echo $user["name"];

// 多维数组
$arr = [
    ['a' => 1, 'b' => 2],
    ['a' => 3, 'b' => 33]
];
这和 JS 的 [{a:1,b:2},{a:3,b:33}] 是一样的结构。

foreach ($users as $key => $user) {
    echo $user['name'] . "的爱好有：" . implode('、', $user['hobby']) . "\n";
}
```

---

## 11. 类与对象

```php
class Person {
    public $name;
    public function sayHello() {
        echo "你好, " . $this->name;
    }
}

$p = new Person();
$p->name = "小明";
$p->sayHello(); // 输出 你好, 小明
```

---

## 12、访问属性/方法的方式

| 场景      | 使用方式 | 实例化         | 示例              |
| ------- | ---- | ----------- | --------------- |
| 静态属性/方法 | `::` | 不需要实例化类<br> | `Cache::has()`  |
| 实例属性/方法 | `->` | 需要先创建对象     | `$user->name`   |
| 数组元素    | `[]` | /           | `$arr['key']`   |
| 字符串连接   | `.`  | /           | `$str1 . $str2` |
| 函数调用    | `()` | /           | `getData()`     |
| 变量解析    | {}   | /<br>       | "Hello {$name}" |
