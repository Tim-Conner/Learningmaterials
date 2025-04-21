[TOC]













在 Python 中，`import` 和 `from` 是用于导入模块和模块成员的关键字，它们的核心区别在于 **引入作用域的方式**。以下是详细对比和解释：

---

# 一、`import` 的用法和作用

#### 1. 基本语法

```python
import module_name          # 导入整个模块
import module_name as alias # 导入模块并设置别名
```

#### 2. 作用

- **导入整个模块**，所有成员需通过模块名前缀访问
- **不污染当前命名空间**，避免命名冲突
- **明确标识来源**，提高代码可读性

#### 3. 示例

```python
import math

print(math.sqrt(16))  # 4.0
print(math.pi)        # 3.141592653589793
```

---

### 二、`from ... import` 的用法和作用

#### 1. 基本语法

```python
from module import name          # 导入特定成员
from module import name as alias # 导入并设置别名
from module import *            # 导入所有公共成员（不推荐）
```

#### 2. 作用

- **直接引入模块中的特定成员**到当前命名空间
- **减少代码冗余**（无需写模块名前缀）
- 但可能引发命名冲突（需谨慎使用）

#### 3. 示例

```python
from math import sqrt, pi

print(sqrt(16))  # 4.0（无需前缀）
print(pi)        # 3.141592653589793
```

---

### 三、关键区别对比

| 特性             | `import module`              | `from module import ...`   |
| ---------------- | ---------------------------- | -------------------------- |
| **命名空间**     | 保留模块名作为前缀           | 直接引入成员到当前命名空间 |
| **代码冗余**     | 需要写模块前缀（如 `m.f()`） | 可直接使用成员（如 `f()`） |
| **命名冲突风险** | 低                           | 高（尤其是 `import *`）    |
| **内存占用**     | 相同（模块只加载一次）       | 相同                       |
| **推荐场景**     | 需要明确来源的大多数情况     | 需要简化代码的少量成员导入 |

---

### 四、高级用法和注意事项

#### 1. 导入多个模块/成员

```python
# 多个模块导入
import math, sys, os

# 多个成员导入
from math import sqrt, pi, sin
```

#### 2. 别名设置（解决命名冲突）

```python
from my_module import long_function_name as lfn
import pandas as pd  # 常用别名
```

#### 3. 动态导入（`importlib`）

```python
import importlib

module_name = "math"
math = importlib.import_module(module_name)
print(math.sqrt(9))  # 3.0
```

#### 4. `import *` 的风险

```python
# 不推荐！可能覆盖已有名称
from numpy import *  
from math import *

print(sqrt(4))  # 哪个 sqrt？numpy 还是 math？
```

---

### 五、最佳实践

1. **优先使用 `import module`**  
   明确来源且避免冲突，适合大型项目。

2. **谨慎使用 `from ... import`**  
   仅在需要简化代码时导入少量明确成员：

   ```python
   from django.shortcuts import render
   ```

3. **绝对不要在生产代码中使用 `import *`**  
   除非明确知道所有引入的成员（如某些测试场景）。

4. **处理长模块名时使用别名**  

   ```python
   import tensorflow as tf
   import matplotlib.pyplot as plt
   ```

5. **注意循环导入问题**  
   如果模块 A 导入模块 B，而模块 B 又导入模块 A，会导致导入错误。

---

### 六、底层原理

1. **模块缓存机制**  
   Python 的 `sys.modules` 字典会缓存已导入的模块：

   ```python
   import sys
   print(sys.modules.keys())  # 查看所有已加载模块
   ```

2. **导入顺序**  
   Python 按以下顺序搜索模块：

   - 当前目录
   - 环境变量 `PYTHONPATH` 中的路径
   - 标准库路径
   - 第三方库路径（如 `site-packages`）

3. `__init__.py` 的作用  
   在包（目录）中标记该目录为 Python 包，可以包含初始化代码或定义 `__all__` 列表（控制 `from package import *` 的行为）。

---

通过合理选择 `import` 和 `from` 的使用方式，可以让代码既保持清晰可读性，又避免潜在的命名冲突问题。















# 一、算术运算符

### 1. 加法（`+`）

```python
a = 5
b = 3
result = a + b  # 结果为 8
print(result)  # 输出 8
```

### 2. 减法（`-`）

```python
a = 5
b = 3
result = a - b  # 结果为 2
print(result)  # 输出 2
```

### 3. 乘法（`*`）

```python
a = 5
b = 3
result = a * b  # 结果为 15
print(result)  # 输出 15
```

### 4. 除法（`/`）

```python
a = 10
b = 3
result = a / b  # 结果为 3.3333333333333335（浮点数除法）
print(result)  # 输出 3.3333333333333335
```

### 5. 整除（`//`）

```python
a = 10
b = 3
result = a // b  # 结果为 3（整数除法，向下取整）
print(result)  # 输出 3
```

### 6. 取余（`%`）

```python
a = 10
b = 3
result = a % b  # 结果为 1（取余数）
print(result)  # 输出 1
```

### 7. 幂运算（`**`）

```python
a = 2
b = 3
result = a ** b  # 结果为 8（2 的 3 次方）
print(result)  # 输出 8
```

# 二、比较运算符

### 1. 大于（`>`）

```python
a = 5
b = 3
result = a > b  # 结果为 True
print(result)  # 输出 True
```

### 2. 小于（`<`）

```python
a = 5
b = 3
result = a < b  # 结果为 False
print(result)  # 输出 False
```

### 3. 等于（`==`）

```python
a = 5
b = 5
result = a == b  # 结果为 True
print(result)  # 输出 True
```

### 4. 不等于（`!=`）

```python
a = 5
b = 3
result = a != b  # 结果为 True
print(result)  # 输出 True
```

### 5. 大于等于（`>=`）

```python
a = 5
b = 3
result = a >= b  # 结果为 True
print(result)  # 输出 True
```

### 6. 小于等于（`<=`）

```python
a = 5
b = 3
result = a <= b  # 结果为 False
print(result)  # 输出 False
```

# 三、逻辑运算符

### 1. 逻辑与（`and`）

```python
a = True
b = False
result = a and b  # 结果为 False
print(result)  # 输出 False
```

### 2. 逻辑或（`or`）

```python
a = True
b = False
result = a or b  # 结果为 True
print(result)  # 输出 True
```

### 3. 逻辑非（`not`）

```python
a = True
result = not a  # 结果为 False
print(result)  # 输出 False
```

### 4. 综合示例

```python
a = 5
b = 3
c = 10

# 判断 a 是否大于 b 且 c 是否小于 10
result = (a > b) and (c < 10)  # 结果为 False
print(result)  # 输出 False

# 判断 a 是否大于 b 或 c 是否小于 10
result = (a > b) or (c < 10)  # 结果为 True
print(result)  # 输出 True

# 判断 a 是否不等于 b
result = a != b  # 结果为 True
print(result)  # 输出 True
```

### 5、综合示例

以下是一个综合示例，结合了算术运算符、比较运算符和逻辑运算符：

```python
# 用户输入两个数字
num1 = float(input("请输入第一个数字："))
num2 = float(input("请输入第二个数字："))

# 计算加法、减法、乘法和除法
sum_result = num1 + num2
diff_result = num1 - num2
prod_result = num1 * num2
quot_result = num1 / num2 if num2 != 0 else "除数不能为零"

# 输出结果
print(f"加法结果：{sum_result}")
print(f"减法结果：{diff_result}")
print(f"乘法结果：{prod_result}")
print(f"除法结果：{quot_result}")

# 比较两个数字
if num1 > num2:
    print(f"{num1} 大于 {num2}")
elif num1 < num2:
    print(f"{num1} 小于 {num2}")
else:
    print(f"{num1} 等于 {num2}")

# 判断两个数字是否相等
if num1 == num2:
    print(f"{num1} 和 {num2} 相等")
else:
    print(f"{num1} 和 {num2} 不相等")

# 使用逻辑运算符
if num1 > 0 and num2 > 0:
    print("两个数字都是正数")
elif num1 < 0 and num2 < 0:
    print("两个数字都是负数")
else:
    print("一个数字是正数，另一个是负数或零")
```

### 示例运行

#### 输入

```
请输入第一个数字：5
请输入第二个数字：3
```

#### 输出

```
加法结果：8.0
减法结果：2.0
乘法结果：15.0
除法结果：1.6666666666666667
5 大于 3
5 和 3 不相等
两个数字都是正数
```

通过这些示例，你可以更好地理解算术运算符、比较运算符和逻辑运算符的用法和特点。











```python
# 提示用户输入温度值，并将输入存储到变量 data 中
data = input("请输入你的温度值：")

# 判断输入的温度单位是否为华氏度（F 或 f）
if data[-1] in {'F', 'f'}:  
    # 如果是华氏度，提取数值部分（去掉最后一个字符），并将其转换为数值类型
    # 使用 eval() 函数可以将字符串表达式转换为数值
    result = (eval(data[0:-1]) - 32) * (5 / 9)  
    # 将华氏度转换为摄氏度，并将结果存储到变量 result 中
    # 格式化输出结果，保留两位小数，并在末尾添加摄氏度单位 C
    print("温度转换的结果为：{:.2f}C".format(result))  
else:  
    # 如果输入的温度单位不是华氏度，继续判断是否为摄氏度（C 或 c）
    if data[-1] in {'C', 'c'}:  
        # 如果是摄氏度，提取数值部分（去掉最后一个字符），并将其转换为数值类型
        result = eval(data[0:-1]) * (9 / 5) + 32  
        # 将摄氏度转换为华氏度，并将结果存储到变量 result 中
        # 格式化输出结果，保留两位小数，并在末尾添加华氏度单位 F
        print("温度转换的结果为：{:.2f}F".format(result))  
```

### 

# 四 格式化方法

## 一、`%` 格式化（旧式格式化）

`%` 格式化是 Python 最早的字符串格式化方法，使用 `%` 操作符将值插入到字符串中。

### 1. 基本用法

```python
name = "Alice"
age = 25
message = "Hello, %s. You are %d years old." % (name, age)
print(message)  # 输出: Hello, Alice. You are 25 years old.





```

### 2. 格式化符号

- `%s`：字符串格式化
- `%d`：十进制整数
- `%f`：浮点数
- `%x`：十六进制整数
- `%o`：八进制整数
- `%e`：科学计数法表示的浮点数

### 3. 示例

```python
pi = 3.1415926
print("The value of pi is approximately %.2f." % pi)  # 输出: The value of pi is approximately 3.14.
```

## 二、`str.format()` 方法（新式格式化）

`str.format()` 是一种更灵活的字符串格式化方法，通过 `{}` 占位符和 `.format()` 方法将值插入到字符串中。

### 1. 基本用法

```python
name = "Alice"
age = 25
message = "Hello, {}. You are {} years old.".format(name, age)
print(message)  # 输出: Hello, Alice. You are 25 years old.
```

### 2. 指定位置

可以通过在 `{}` 中指定位置来控制值的插入顺序。

```python
message = "Hello, {0}. You are {1} years old. Nice to meet you, {0}.".format(name, age)
print(message)  # 输出: Hello, Alice. You are 25 years old. Nice to meet you, Alice.
```

### 3. 格式化数字和字符串

```python
pi = 3.1415926
print("The value of pi is approximately {:.2f}.".format(pi))  # 输出: The value of pi is approximately 3.14.
```

### 4. 填充和对齐

```python
print("{:10}".format("apple"))  # 左对齐，总宽度为 10
print("{:>10}".format("apple"))  # 右对齐，总宽度为 10
print("{:^10}".format("apple"))  # 居中对齐，总宽度为 10
```

### 5. 示例

```python
name = "Alice"
age = 25
height = 165.5
print("Name: {0}, Age: {1}, Height: {2:.2f} cm".format(name, age, height))
# 输出: Name: Alice, Age: 25, Height: 165.50 cm
```

## 三、f-string（格式化字符串字面量）

f-string 是 Python 3.6 引入的一种新的字符串格式化方法，通过在字符串前加 `f` 或 `F`，并在字符串中使用 `{}` 来嵌入表达式。

### 1. 基本用法

```python
name = "Alice"
age = 25
message = f"Hello, {name}. You are {age} years old."
print(message)  # 输出: Hello, Alice. You are 25 years old.
```

### 2. 格式化数字和字符串

```python
pi = 3.1415926
print(f"The value of pi is approximately {pi:.2f}.")  # 输出: The value of pi is approximately 3.14.
```

### 3. 填充和对齐

```python
print(f"{name:>10}")  # 右对齐，总宽度为 10
print(f"{name:^10}")  # 居中对齐，总宽度为 10
```

### 4. 表达式支持

f-string 支持在 `{}` 中直接写表达式。

```python
a = 5
b = 10
print(f"The sum of {a} and {b} is {a + b}.")  # 输出: The sum of 5 and 10 is 15.
```

### 5. 示例

```python
name = "Alice"
age = 25
height = 165.5
print(f"Name: {name}, Age: {age}, Height: {height:.2f} cm")
# 输出: Name: Alice, Age: 25, Height: 165.50 cm
```

## 四、格式化控制的对比

### 1. `%` 格式化

- **优点**：简单易用，适合快速格式化。
- **缺点**：不够灵活，可读性较差，容易出错。

### 2. `str.format()` 方法

- **优点**：灵活强大，支持复杂的格式化操作。
- **缺点**：代码较长，可读性稍差。

### 3. f-string

- **优点**：语法简洁，可读性强，支持表达式，性能最优。
- **缺点**：仅在 Python 3.6 及以上版本支持。





# 五、Python 列表的基本概念



## 一、Python 列表的基本概念

列表（List）是一种有序的集合，可以存储任意类型的对象，包括数字、字符串、其他列表等。列表是可变的，可以随时添加、删除或修改其中的元素。

例如：

```python
my_list = [1, 2, 3, "Alice", [4, 5]]
```

在这个列表中，`1`、`2`、`3`、`"Alice"` 和 `[4, 5]` 都是列表的元素。

## 二、列表的创建

### （一）使用方括号创建

```python
empty_list = []  # 创建一个空列表
numbers = [1, 2, 3, 4, 5]
```

### （二）使用 list() 函数创建

- **从可迭代对象创建**

```python
numbers = list(range(1, 6))  # 从 range 对象创建列表
print(numbers)  # 输出 [1, 2, 3, 4, 5]
```

- **从字符串创建**

```python
chars = list("hello")  # 从字符串创建列表
print(chars)  # 输出 ['h', 'e', 'l', 'l', 'o']
```

## 三、列表的访问

### （一）通过索引访问

列表的索引从 0 开始，可以通过索引访问列表中的元素。

```python
numbers = [1, 2, 3, 4, 5]
print(numbers[0])  # 输出 1
print(numbers[-1])  # 输出 5，负索引表示从列表末尾开始计数
```

### （二）切片访问

可以使用切片语法访问列表的一部分。

```python
print(numbers[1:3])  # 输出 [2, 3]，从索引 1 到索引 3（不包括 3）
print(numbers[:3])  # 输出 [1, 2, 3]，从开头到索引 3（不包括 3）
print(numbers[3:])  # 输出 [4, 5]，从索引 3 到结尾
print(numbers[::2])  # 输出 [1, 3, 5]，每隔一个元素取一个
```

## 四、列表的更新

### （一）修改元素

可以通过索引直接修改列表中的元素。

```python
numbers[0] = 10  # 修改索引为 0 的元素
print(numbers)  # 输出 [10, 2, 3, 4, 5]
```

### （二）添加元素

- **使用 append() 方法添加单个元素**

```python
numbers.append(6)  # 在列表末尾添加元素 6
print(numbers)  # 输出 [10, 2, 3, 4, 5, 6]
```

- **使用 extend() 方法添加多个元素**

```python
numbers.extend([7, 8])  # 在列表末尾添加多个元素
print(numbers)  # 输出 [10, 2, 3, 4, 5, 6, 7, 8]
```

- **使用 insert() 方法在指定位置插入元素**

```python
numbers.insert(1, 11)  # 在索引 1 的位置插入元素 11
print(numbers)  # 输出 [10, 11, 2, 3, 4, 5, 6, 7, 8]
```

## 五、列表的删除

### （一）删除指定元素

- **使用 remove() 方法删除第一个匹配的元素**

```python
numbers.remove(11)  # 删除第一个值为 11 的元素
print(numbers)  # 输出 [10, 2, 3, 4, 5, 6, 7, 8]
```

如果元素不存在，会抛出 `ValueError`。

### （二）删除指定索引的元素

- **使用 del 语句删除指定索引的元素**

```python
del numbers[0]  # 删除索引为 0 的元素
print(numbers)  # 输出 [2, 3, 4, 5, 6, 7, 8]
```

### （三）使用 pop() 方法删除并返回元素

```python
last_element = numbers.pop()  # 删除并返回最后一个元素
print(last_element)  # 输出 8
print(numbers)  # 输出 [2, 3, 4, 5, 6, 7]
```

也可以指定索引删除并返回特定位置的元素：

```python
first_element = numbers.pop(0)  # 删除并返回索引为 0 的元素
print(first_element)  # 输出 2
print(numbers)  # 输出 [3, 4, 5, 6, 7]
```

### （四）清空列表

```python
numbers.clear()  # 清空列表
print(numbers)  # 输出 []
```

## 六、列表的遍历

### （一）使用 for 循环遍历

```python
for num in numbers:
    print(num)
```

### （二）使用索引遍历

```python
for i in range(len(numbers)):
    print(numbers[i])
```

### （三）使用 enumerate() 函数遍历

```python
for index, value in enumerate(numbers):
    print(index, value)
```

## 七、列表的常用方法

### （一）len()

```python
print(len(numbers))  # 返回列表的长度
```

### （二）index()

```python
print(numbers.index(5))  # 返回值为 5 的元素的索引
```

如果元素不存在，会抛出 `ValueError`。

### （三）count()

```python
print(numbers.count(5))  # 返回值为 5 的元素的数量
```

### （四）sort() 和 sorted()

- **sort() 方法对列表进行原地排序**

```python
numbers.sort()  # 升序排序
print(numbers)  # 输出 [3, 4, 5, 6, 7]
numbers.sort(reverse=True)  # 降序排序
print(numbers)  # 输出 [7, 6, 5, 4, 3]
```

- **sorted() 函数返回排序后的列表副本，不改变原列表**

```python
sorted_numbers = sorted(numbers)  # 升序排序
print(sorted_numbers)  # 输出 [3, 4, 5, 6, 7]
```

### （五）reverse()

```python
numbers.reverse()  # 反转列表
print(numbers)  # 输出 [3, 6, 5, 4, 7]
```

### （六）copy()

```python
numbers_copy = numbers.copy()  # 创建列表的浅拷贝
```

## 八、列表的高级用法

### （一）列表推导式

列表推导式是一种简洁的创建列表的方法。

```python
squares = [x * x for x in range(10)]  # 创建一个列表，元素为 0 到 9 的平方
print(squares)  # 输出 [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

也可以添加条件语句：

```python
even_squares = [x * x for x in range(10) if x % 2 == 0]  # 只取偶数的平方
print(even_squares)  # 输出 [0, 4, 16, 36, 64]
```

### （二）嵌套列表

列表可以包含其他列表，形成嵌套结构。

```python
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
print(matrix[0][2])  # 输出 3，访问第一行第三列的元素
```

### （三）列表的解包

可以将列表中的元素解包到多个变量中。

```python
a, b, c = [1, 2, 3]
print(a, b, c)  # 输出 1 2 3
```

也可以使用 `_` 忽略某些元素：

```python
a, _, c = [1, 2, 3]
print(a, c)  # 输出 1 3
```

列表是 Python 中最基本且最常用的数据结构之一，广泛应用于各种场景，如存储数据、处理序列等。掌握列表的操作和方法对于编写高效的 Python 程序非常重要。







# 六、Python 元组的基本概念





## 一、Python 元组的基本概念

元组（Tuple）是一种不可变的有序集合，可以存储任意类型的对象，包括数字、字符串、列表等。一旦创建，元组中的元素不能被修改（如添加、删除或修改元素）。元组通常用于存储一组固定的数据，比如二维坐标、日期等。

例如：

```python
my_tuple = (1, 2, 3, "Alice", [4, 5])
```

在这个元组中，`1`、`2`、`3`、`"Alice"` 和 `[4, 5]` 都是元组的元素。

## 二、元组的创建

### （一）使用圆括号创建

```python
empty_tuple = ()  # 创建一个空元组
numbers = (1, 2, 3, 4, 5)
```

### （二）省略圆括号创建

如果元组中只有一个元素，需要在元素后面加一个逗号，否则会被当作普通表达式。

```python
single_element_tuple = 1,  # 创建一个只有一个元素的元组
print(single_element_tuple)  # 输出 (1,)
```

### （三）使用 tuple() 函数创建

- **从可迭代对象创建**

```python
numbers = tuple(range(1, 6))  # 从 range 对象创建元组
print(numbers)  # 输出 (1, 2, 3, 4, 5)
```

- **从字符串创建**

```python
chars = tuple("hello")  # 从字符串创建元组
print(chars)  # 输出 ('h', 'e', 'l', 'l', 'o')
```

## 三、元组的访问

### （一）通过索引访问

元组的索引从 0 开始，可以通过索引访问元组中的元素。

```python
numbers = (1, 2, 3, 4, 5)
print(numbers[0])  # 输出 1
print(numbers[-1])  # 输出 5，负索引表示从元组末尾开始计数
```

### （二）切片访问

可以使用切片语法访问元组的一部分。

```python
print(numbers[1:3])  # 输出 (2, 3)，从索引 1 到索引 3（不包括 3）
print(numbers[:3])  # 输出 (1, 2, 3)，从开头到索引 3（不包括 3）
print(numbers[3:])  # 输出 (4, 5)，从索引 3 到结尾
print(numbers[::2])  # 输出 (1, 3, 5)，每隔一个元素取一个
```

## 四、元组的更新（不可变性）

元组是不可变的，不能直接修改元组中的元素。但可以通过以下方式“间接”更新元组：

### （一）重新赋值

可以将一个新元组赋值给原来的变量名。

```python
numbers = (1, 2, 3)
numbers = (4, 5, 6)  # 重新赋值
print(numbers)  # 输出 (4, 5, 6)
```

### （二）拼接元组

可以将多个元组合并成一个新的元组。

```python
numbers1 = (1, 2, 3)
numbers2 = (4, 5, 6)
new_tuple = numbers1 + numbers2  # 拼接元组
print(new_tuple)  # 输出 (1, 2, 3, 4, 5, 6)
```

### （三）修改元组中的可变对象

如果元组中包含可变对象（如列表），可以修改这些可变对象的内容。

```python
my_tuple = (1, 2, [3, 4])
my_tuple[2][0] = 10  # 修改元组中的列表
print(my_tuple)  # 输出 (1, 2, [10, 4])
```

## 五、元组的删除

### （一）删除整个元组

可以使用 `del` 语句删除整个元组，但不能删除元组中的某个元素。

```python
numbers = (1, 2, 3)
del numbers  # 删除整个元组
# print(numbers)  # 报错：NameError，因为 numbers 已被删除
```

## 六、元组的遍历

### （一）使用 for 循环遍历

```python
for num in numbers:
    print(num)
```

### （二）使用索引遍历

```python
for i in range(len(numbers)):
    print(numbers[i])
```

### （三）使用 enumerate() 函数遍历

```python
for index, value in enumerate(numbers):
    print(index, value)
```

## 七、元组的常用方法

### （一）len()

```python
print(len(numbers))  # 返回元组的长度
```

### （二）index()

```python
print(numbers.index(3))  # 返回值为 3 的元素的索引
```

如果元素不存在，会抛出 `ValueError`。

### （三）count()

```python
print(numbers.count(3))  # 返回值为 3 的元素的数量
```

## 八、元组的高级用法

### （一）元组解包

可以将元组中的元素解包到多个变量中。

```python
a, b, c = (1, 2, 3)
print(a, b, c)  # 输出 1 2 3
```

也可以使用 `_` 忽略某些元素：

```python
a, _, c = (1, 2, 3)
print(a, c)  # 输出 1 3
```

### （二）元组作为函数返回值

函数可以返回一个元组，这样可以同时返回多个值。

```python
def get_user_info():
    return ("Alice", 25, "New York")

name, age, city = get_user_info()
print(name, age, city)  # 输出 Alice 25 New York
```

### （三）元组作为字典的键

由于元组是不可变的，可以作为字典的键。

```python
my_dict = {(1, 2): "A", (3, 4): "B"}
print(my_dict[(1, 2)])  # 输出 A
```

## 九、元组与列表的区别

### （一）可变性

- **列表**：可变，可以随时添加、删除或修改元素。
- **元组**：不可变，一旦创建，不能修改元素。

### （二）性能

- **列表**：由于可变性，操作相对复杂，性能稍逊。
- **元组**：由于不可变性，内存占用更小，性能更好。

### （三）用途

- **列表**：适合存储动态变化的数据，如用户输入的数据列表。
- **元组**：适合存储固定不变的数据，如二维坐标、日期等。

元组是 Python 中一种非常重要的数据结构，虽然它的不可变性限制了它的使用场景，但也为它带来了性能和安全性的优势。在需要存储固定数据时，元组是一个非常好的选择。





# 七、Python字典的基本概念

## 一、Python字典的基本概念

字典（Dictionary）是一种可变容器模型，且可存储任意类型对象。字典的每个键值 key=>value 对用冒号 : 分割，每个对之间用逗号分割，整个字典包括在花括号 {} 中。键必须是唯一的，但值则不必。值可以取任何数据类型，但键必须是不可变的，如字符串、数字或元组。

例如：

```python
my_dict = {"name": "Alice", "age": 25, "is_student": False}
```

在这个字典中，`"name"`、`"age"`、`"is_student"` 是键（key），`"Alice"`、`25`、`False` 是对应的值（value）。

## 二、字典的创建

### （一）使用花括号创建

```python
empty_dict = {}  # 创建一个空字典
person = {"name": "Bob", "age": 30, "city": "New York"}
```

### （二）使用 dict() 函数创建

- **从键值对序列创建**

```python
person = dict([("name", "Bob"), ("age", 30), ("city", "New York")])
```

- **从关键字参数创建**

```python
person = dict(name="Bob", age=30, city="New York")
```

## 三、字典的访问

### （一）通过键访问值

```python
person = {"name": "Bob", "age": 30, "city": "New York"}
print(person["name"])  # 输出 Bob
```

如果访问的键不存在，会抛出 `KeyError`。

### （二）使用 get() 方法访问

```python
print(person.get("name"))  # 输出 Bob
print(person.get("gender"))  # 输出 None，因为没有 "gender" 这个键
print(person.get("gender", "Unknown"))  # 输出 Unknown，可以指定默认值
```

## 四、字典的更新

### （一）添加键值对

```python
person = {"name": "Bob", "age": 30, "city": "New York"}
person["gender"] = "Male"  # 添加新的键值对
```

### （二）修改键值对

```python
person["age"] = 31  # 修改已有的键值对
```

### （三）更新多个键值对

```python
person.update({"age": 32, "city": "Los Angeles"})
```

## 五、字典的删除

### （一）删除指定键值对

```python
del person["city"]  # 删除键为 "city" 的键值对
```

### （二）使用 pop() 方法删除并返回值

```python
age = person.pop("age")  # 删除键为 "age" 的键值对，并返回它的值
print(age)  # 输出 32
```

### （三）清空字典

```python
person.clear()  # 清空字典，使其变为 {}
```

## 六、字典的遍历

### （一）遍历键

```python
for key in person.keys():
    print(key)
```

### （二）遍历值

```python
for value in person.values():
    print(value)
```

### （三）遍历键值对

```python
for key, value in person.items():
    print(key, value)
```

## 七、字典的常用方法

### （一）keys()、values()、items()

- `keys()` 返回字典的键列表。
- `values()` 返回字典的值列表。
- `items()` 返回键值对的元组列表。

### （二）len()

```python
print(len(person))  # 返回字典中键值对的数量
```

### （三）in 和 not in

```python
print("name" in person)  # 判断键是否在字典中
print("age" not in person)  # 判断键是否不在字典中
```

### （四）fromkeys()

```python
new_dict = dict.fromkeys(["a", "b", "c"], 0)  # 创建一个新字典，所有键的值都为 0
print(new_dict)  # 输出 {'a': 0, 'b': 0, 'c': 0}
```

### （五）copy()

```python
person_copy = person.copy()  # 创建字典的浅拷贝
```

## 八、字典的高级用法

### （一）字典推导式

```python
squares = {x: x*x for x in range(10)}  # 创建一个字典，键是数字，值是数字的平方
print(squares)
```

### （二）嵌套字典

```python
nested_dict = {
    "person1": {"name": "Alice", "age": 25},
    "person2": {"name": "Bob", "age": 30}
}
print(nested_dict["person1"]["name"])  # 输出 Alice
```

字典是 Python 中非常灵活且强大的数据结构，广泛应用于各种场景，如存储配置信息、处理数据映射等。





# 八、Python 集合的基本概念





## 一、Python 集合的基本概念

集合（Set）是一种无序的、不重复的数据结构，用于存储唯一的数据项。集合中的元素必须是不可变类型（如整数、浮点数、字符串、元组等），但集合本身是可变的，可以随时添加或删除元素。

### 主要特点

1. **无序性**：集合中的元素没有固定的顺序，不能通过索引访问。
2. **唯一性**：集合中的元素必须是唯一的，重复的元素会被自动忽略。
3. **可变性**：集合本身是可变的，可以添加或删除元素。

## 二、集合的创建

### 1. 使用花括号创建

```python
my_set = {1, 2, 3, "Alice"}
print(my_set)  # 输出：{1, 2, 3, 'Alice'}
```

注意：创建空集合时不能使用 `{}`，因为 `{}` 表示一个空字典。创建空集合需要使用 `set()`。

### 2. 使用 `set()` 函数创建

- **从可迭代对象创建**

```python
numbers = set([1, 2, 3, 4, 5])  # 从列表创建集合
print(numbers)  # 输出：{1, 2, 3, 4, 5}

chars = set("hello")  # 从字符串创建集合
print(chars)  # 输出：{'h', 'e', 'l', 'o'}，注意重复的 'l' 被忽略
```

## 三、集合的基本操作

### 1. 添加元素

- **使用 `add()` 方法添加单个元素**

```python
my_set = {1, 2, 3}
my_set.add(4)  # 添加元素 4
print(my_set)  # 输出：{1, 2, 3, 4}
```

### 2. 删除元素

- **使用 `remove()` 方法删除指定元素**

```python
my_set = {1, 2, 3, 4}
my_set.remove(3)  # 删除元素 3
print(my_set)  # 输出：{1, 2, 4}
```

如果元素不存在，会抛出 `KeyError`。

- **使用 `discard()` 方法删除指定元素**

```python
my_set = {1, 2, 3, 4}
my_set.discard(3)  # 删除元素 3
print(my_set)  # 输出：{1, 2, 4}
```

如果元素不存在，不会抛出错误。

- **使用 `pop()` 方法随机删除一个元素**

```python
my_set = {1, 2, 3, 4}
popped_element = my_set.pop()  # 随机删除一个元素
print(popped_element)  # 输出：随机删除的元素
print(my_set)  # 输出：剩余的元素
```

### 3. 清空集合

```python
my_set = {1, 2, 3, 4}
my_set.clear()  # 清空集合
print(my_set)  # 输出：set()
```

## 四、集合的遍历

### 1. 使用 `for` 循环遍历

```python
my_set = {1, 2, 3, 4}
for element in my_set:
    print(element)
```

输出顺序可能不同，因为集合是无序的。

## 五、集合的常用方法

### 1. `len()`：获取集合的长度

```python
my_set = {1, 2, 3, 4}
print(len(my_set))  # 输出：4
```

### 2. `in` 和 `not in`：判断元素是否在集合中

```python
my_set = {1, 2, 3, 4}
print(3 in my_set)  # 输出：True
print(5 not in my_set)  # 输出：True
```

### 3. 集合运算

#### （1）并集（`union()` 或 `|`）

```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}
union_set = set1.union(set2)  # 或使用 set1 | set2
print(union_set)  # 输出：{1, 2, 3, 4, 5}
```

#### （2）交集（`intersection()` 或 `&`）

```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}
intersection_set = set1.intersection(set2)  # 或使用 set1 & set2
print(intersection_set)  # 输出：{3}
```

#### （3）差集（`difference()` 或 `-`）

```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}
difference_set = set1.difference(set2)  # 或使用 set1 - set2
print(difference_set)  # 输出：{1, 2}
```

#### （4）对称差集（`symmetric_difference()` 或 `^`）

```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}
symmetric_difference_set = set1.symmetric_difference(set2)  # 或使用 set1 ^ set2
print(symmetric_difference_set)  # 输出：{1, 2, 4, 5}
```

### 4. 子集和超集

#### （1）判断子集（`issubset()`）

```python
set1 = {1, 2}
set2 = {1, 2, 3, 4}
print(set1.issubset(set2))  # 输出：True
```

#### （2）判断超集（`issuperset()`）

```python
set1 = {1, 2, 3, 4}
set2 = {1, 2}
print(set1.issuperset(set2))  # 输出：True
```

## 六、集合的高级用法

### 1. 集合推导式

集合推导式是一种简洁的创建集合的方法。

```python
squares = {x * x for x in range(10)}
print(squares)  # 输出：{0, 1, 4, 9, 16, 25, 36, 49, 64, 81}
```

### 2. 去重

集合可以用于去除重复的元素。

```python
numbers = [1, 2, 2, 3, 4, 4, 5]
unique_numbers = list(set(numbers))
print(unique_numbers)  # 输出：[1, 2, 3, 4, 5]
```

## 七、集合与其他数据结构的对比

### 1. 与列表的对比

- **列表**：有序，可重复，可变，支持索引和切片。
- **集合**：无序，唯一，可变，不支持索引和切片。

### 2. 与字典的对比

- **字典**：无序，键唯一，值可重复，可变，基于键值对存储。
- **集合**：无序，元素唯一，可变，基于单个元素存储。

### 3. 与元组的对比

- **元组**：有序，可重复，不可变，支持索引和切片。
- **集合**：无序，唯一，可变，不支持索引和切片。

## 八、应用场景

### 1. 去重

集合可以快速去除重复的元素，非常适合用于处理数据中的重复项。

### 2. 集合运算

利用集合的交集、并集、差集等运算，可以方便地处理数据的集合关系，例如：

- 找出两个列表中的共同元素（交集）。
- 合并两个列表中的所有唯一元素（并集）。
- 找出一个列表中不在另一个列表中的元素（差集）。

### 3. 成员检查

集合的成员检查（`in` 和 `not in`）操作效率很高，适合用于快速判断某个元素是否存在于集合中。

集合是 Python 中一种非常强大的数据结构，适用于处理唯一数据和集合运算。掌握集合的操作和方法可以让你在处理数据时更加高效和灵活。



# 九、定义自定义函数



## 一、定义自定义函数

在 Python 中，使用 `def` 关键字定义一个函数。函数的基本结构如下：

```python
def function_name(parameters):
    """
    函数文档字符串（可选，用于描述函数的功能和参数）
    """
    # 函数体
    # 执行逻辑
    return value  # 返回值（可选）
```

### 1. 简单示例

定义一个简单的函数，用于计算两个数的和：

```python
def add_numbers(a, b):
    """
    计算两个数的和
    :param a: 第一个数
    :param b: 第二个数
    :return: 两个数的和
    """
    result = a + b
    return result

# 调用函数
sum_result = add_numbers(5, 3)
print(sum_result)  # 输出：8
```

### 2. 无参数函数

定义一个不接受任何参数的函数：

```python
def greet():
    """
    打印问候语
    """
    print("Hello, welcome to our program!")

# 调用函数
greet()  # 输出：Hello, welcome to our program!
```

### 3. 无返回值函数

定义一个不返回任何值的函数：

```python
def print_info(name, age):
    """
    打印用户信息
    :param name: 用户名
    :param age: 年龄
    """
    print(f"Name: {name}, Age: {age}")

# 调用函数
print_info("Alice", 25)
# 输出：Name: Alice, Age: 25
```

## 二、函数参数

### 1. 位置参数

位置参数是按照参数的位置传递的，调用函数时，参数的顺序必须与定义时一致。

```python
def subtract_numbers(a, b):
    return a - b

result = subtract_numbers(10, 5)  # 10 和 5 按位置传递
print(result)  # 输出：5
```

### 2. 关键字参数

关键字参数是通过参数名传递的，调用函数时，可以指定参数名，顺序可以不同。

```python
def greet(name, greeting="Hello"):
    print(f"{greeting}, {name}!")

greet(name="Alice")  # 使用关键字参数
greet(greeting="Hi", name="Bob")  # 使用关键字参数，顺序可以不同
```

### 3. 默认参数

默认参数是在定义函数时为参数指定默认值。如果调用函数时没有提供该参数的值，则使用默认值。

```python
def greet(name, greeting="Hello"):
    print(f"{greeting}, {name}!")

greet("Alice")  # 使用默认值 "Hello"
greet("Bob", greeting="Hi")  # 指定关键字参数
```

### 4. 可变参数

#### （1）`*args`（位置参数列表）

`*args` 允许函数接受任意数量的位置参数，这些参数会被收集到一个元组中。

```python
def sum_numbers(*args):
    total = 0
    for num in args:
        total += num
    return total

result = sum_numbers(1, 2, 3, 4, 5)
print(result)  # 输出：15
```

#### （2）`**kwargs`（关键字参数字典）

`**kwargs` 允许函数接受任意数量的关键字参数，这些参数会被收集到一个字典中。

```python
def print_info(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")

print_info(name="Alice", age=25, city="New York")
# 输出：
# name: Alice
# age: 25
# city: New York
```

## 三、函数返回值

函数可以返回一个值，也可以返回多个值（实际上是返回一个元组）。

### 1. 返回单个值

```python
def multiply(a, b):
    return a * b

result = multiply(5, 3)
print(result)  # 输出：15
```

### 2. 返回多个值

```python
def get_user_info():
    return "Alice", 25, "New York"

name, age, city = get_user_info()
print(name, age, city)  # 输出：Alice 25 New York
```

## 四、函数的高级用法

### 1. 闭包

闭包是一个函数对象，它记住了在其定义时的上下文环境（包括变量）。闭包可以用于封装状态。

```python
def outer_function(x):
    def inner_function(y):
        return x + y
    return inner_function

closure = outer_function(10)
print(closure(5))  # 输出：15
```

### 2. 装饰器

装饰器是一种设计模式，用于在不修改函数本身的情况下，增加函数的功能。装饰器本质上是一个函数，它接受一个函数作为参数，并返回一个新的函数。

```python
def my_decorator(func):
    def wrapper():
        print("Something is happening before the function is called.")
        func()
        print("Something is happening after the function is called.")
    return wrapper

@my_decorator
def say_hello():
    print("Hello!")

say_hello()
# 输出：
# Something is happening before the function is called.
# Hello!
# Something is happening after the function is called.

def log_decorator(func):
    def wrapper(*args, **kwargs):
        start_time = time.time()  # 记录调用开始时间
        result = func(*args, **kwargs)  # 调用原函数
        end_time = time.time()  # 记录调用结束时间
        print(f"Function {func.__name__} called with args {args} and kwargs {kwargs}.")
        print(f"Execution time: {end_time - start_time:.4f} seconds.")
        return result
    return wrapper

@log_decorator
def ss(b,a):
    print(type(a))

```

### 3. 递归函数

递归函数是指函数调用自身。递归通常用于解决可以分解为更小子问题的问题。

```python
def factorial(n):
    if n == 0:
        return 1
    else:
        return n * factorial(n - 1)

print(factorial(5))  # 输出：120
```

## 五、函数的命名和文档字符串

### 1. 函数命名

函数名应简洁明了，使用小写字母和下划线分隔单词，避免使用 Python 的保留字。

```python
def calculate_sum(a, b):
    return a + b
```

### 2. 文档字符串

文档字符串（docstring）是函数的第一行字符串，用于描述函数的功能、参数和返回值。文档字符串可以通过 `help()` 函数或 `.__doc__` 属性访问。

```python
def calculate_sum(a, b):
    """
    计算两个数的和
    :param a: 第一个数
    :param b: 第二个数
    :return: 两个数的和
    """
    return a + b

help(calculate_sum)
# 输出：
# Help on function calculate_sum in module __main__:
# calculate_sum(a, b)
#     计算两个数的和
#     :param a: 第一个数
#     :param b: 第二个数
#     :return: 两个数的和
```

## 六、函数的实际应用示例

以下是一个实际应用示例，展示如何使用自定义函数处理用户输入并执行特定逻辑。

### 示例：温度转换函数

```python
def convert_temperature(value, unit):
    """
    转换温度值
    :param value: 温度值
    :param unit: 单位（'C' 或 'F'）
    :return: 转换后的温度值和单位
    """
    if unit.upper() == 'C':
        # 摄氏度转华氏度
        result = value * (9 / 5) + 32
        return result, 'F'
    elif unit.upper() == 'F':
        # 华氏度转摄氏度
        result = (value - 32) * (5 / 9)
        return result, 'C'
    else:
        raise ValueError("Invalid unit. Use 'C' for Celsius or 'F' for Fahrenheit.")

# 用户输入
value = float(input("请输入温度值："))
unit = input("请输入单位（C 或 F）：")

try:
    converted_value, converted_unit = convert_temperature(value, unit)
    print(f"转换后的温度为：{converted_value:.2f}{converted_unit}")
except ValueError as e:
    print(e)
```

### 示例运行

#### 输入

```
请输入温度值：37
请输入单位（C 或 F）：C
```

#### 输出

```
转换后的温度为：98.60F
```

通过定义和使用自定义函数，你可以将复杂的逻辑分解为可重用的模块，使代码更加清晰、简洁和易于维护。





# 十、zip/enumerate/eval函数





## 一、`zip()` 函数

### 1. **作用**

`zip()` 函数用于将多个可迭代对象（如列表、元组等）的元素打包成一个个元组，然后返回一个由这些元组组成的迭代器。如果可迭代对象的长度不同，`zip()` 会以最短的可迭代对象为准。

### 2. **语法**

```python
zip(iterable1, iterable2, ...)
```

### 3. **示例**

#### 示例 1：打包两个列表

```python
numbers = [1, 2, 3]
letters = ['a', 'b', 'c']
zipped = zip(numbers, letters)

# 将结果转换为列表
zipped_list = list(zipped)
print(zipped_list)  # 输出：[(1, 'a'), (2, 'b'), (3, 'c')]
```

#### 示例 2：打包多个列表

```python
numbers = [1, 2, 3]
letters = ['a', 'b', 'c']
symbols = ['!', '@', '#']
zipped = zip(numbers, letters, symbols)

# 将结果转换为列表
zipped_list = list(zipped)
print(zipped_list)  # 输出：[(1, 'a', '!'), (2, 'b', '@'), (3, 'c', '#')]
```

#### 示例 3：长度不同的可迭代对象

```python
numbers = [1, 2, 3, 4]
letters = ['a', 'b']
zipped = zip(numbers, letters)

# 将结果转换为列表
zipped_list = list(zipped)
print(zipped_list)  # 输出：[(1, 'a'), (2, 'b')]
```

### 4. **应用场景**

- **并行迭代**：在循环中同时遍历多个列表。
- **数据打包**：将多个列表的数据打包成元组，方便后续处理。

#### 示例：并行迭代

```python
numbers = [1, 2, 3]
letters = ['a', 'b', 'c']

for number, letter in zip(numbers, letters):
    print(f"Number: {number}, Letter: {letter}")
```

#### 输出

```
Number: 1, Letter: a
Number: 2, Letter: b
Number: 3, Letter: c
```

## 二、`enumerate()` 函数

### 1. **作用**

`enumerate()` 函数用于将一个可迭代对象（如列表、元组等）的元素和它们的索引打包成一个个元组，然后返回一个由这些元组组成的迭代器。这在需要同时获取元素和索引时非常有用。

### 2. **语法**

```python
enumerate(iterable, start=0)
```

- `iterable`：需要遍历的对象。
- `start`：索引的起始值，默认为 0。

### 3. **示例**

#### 示例 1：基本用法

```python
letters = ['a', 'b', 'c']
enumerated = enumerate(letters)

# 将结果转换为列表
enumerated_list = list(enumerated)
print(enumerated_list)  # 输出：[(0, 'a'), (1, 'b'), (2, 'c')]
```

#### 示例 2：指定起始索引

```python
letters = ['a', 'b', 'c']
enumerated = enumerate(letters, start=1)

# 将结果转换为列表
enumerated_list = list(enumerated)
print(enumerated_list)  # 输出：[(1, 'a'), (2, 'b'), (3, 'c')]
```

### 4. **应用场景**

- **索引遍历**：在循环中同时获取元素和索引。
- **数据处理**：处理需要索引信息的数据。

#### 示例：索引遍历

```python
letters = ['a', 'b', 'c']

for index, letter in enumerate(letters, start=1):
    print(f"Index: {index}, Letter: {letter}")
```

#### 输出

```
Index: 1, Letter: a
Index: 2, Letter: b
Index: 3, Letter: c
```

## 三、`eval()` 函数

### 1. **作用**

`eval()` 函数用于将字符串作为代码执行。它可以将字符串中的表达式计算为 Python 表达式，并返回结果。

### 2. **语法**

```python
eval(expression, globals=None, locals=None)
```

- `expression`：需要执行的字符串表达式。
- `globals`：全局变量字典。
- `locals`：局部变量字典。

### 3. **示例**

#### 示例 1：基本用法

```python
expression = "2 + 3 * 4"
result = eval(expression)
print(result)  # 输出：14
```

#### 示例 2：使用变量

```python
a = 5
b = 3
expression = "a + b"
result = eval(expression)
print(result)  # 输出：8
```

#### 示例 3：使用 `globals` 和 `locals`

```python
a = 5
b = 3
expression = "a + b"
globals_dict = {"a": a, "b": b}
result = eval(expression, globals_dict)
print(result)  # 输出：8
```

### 4. **应用场景**

- **动态计算**：在运行时动态计算字符串表达式。
- **代码生成**：生成并执行动态代码。

### 5. **注意事项**

- **安全性**：`eval()` 函数非常危险，因为它可以执行任意代码。如果用户输入的内容不可控，可能会导致安全问题。因此，尽量避免使用 `eval()`，除非你完全信任输入的内容。
- **替代方案**：如果需要计算数学表达式，可以使用 `ast.literal_eval()` 或第三方库（如 `numexpr`）。

#### 示例：安全的替代方案

```python
import ast

expression = "2 + 3 * 4"
result = ast.literal_eval(expression)
print(result)  # 输出：14
```

## 四、总结

### 1. **`zip()`**

- **作用**：将多个可迭代对象的元素打包成元组。
- **应用场景**：并行迭代、数据打包。

### 2. **`enumerate()`**

- **作用**：将可迭代对象的元素和索引打包成元组。
- **应用场景**：索引遍历、数据处理。

### 3. **`eval()`**

- **作用**：将字符串作为代码执行。
- **应用场景**：动态计算、代码生成。
- **注意事项**：使用时需谨慎，避免安全问题。

希望这些解释和示例能帮助你更好地理解 `zip()`、`enumerate()` 和 `eval()` 的用法和应用场景。如果有任何疑问，欢迎随时提问！









# 十一、JSON 数据处理



---

### 一、JSON 简介

JSON（JavaScript Object Notation）是一种轻量级的数据交换格式，特点：

- 人类可读，键值对结构
- 支持嵌套对象和数组
- 独立于编程语言（广泛用于网络传输和配置文件）

示例 JSON：

```json
{
  "name": "Alice",
  "age": 30,
  "hobbies": ["reading", "hiking"],
  "address": {
    "city": "Beijing",
    "zip": "100000"
  }
}
```

---

### 二、Python 的 `json` 模块

## 1. JSON与Python字典的相互转换

### 将JSON字符串转换为Python字典

python

复制

```python
import json  # 导入Python内置的json模块

# 定义一个JSON格式的字符串
# JSON字符串使用双引号，这是JSON标准要求的
json_str = '{"name": "Alice", "age": 25, "city": "New York"}'

# 使用json.loads()方法将JSON字符串解析为Python字典
# loads = "load string" 表示从字符串加载
data_dict = json.loads(json_str)

# 打印转换后的结果
print(data_dict)  # 输出: {'name': 'Alice', 'age': 25, 'city': 'New York'}

# 查看转换后的数据类型
print(type(data_dict))  # 输出: <class 'dict'>
# 确认已成功转换为Python字典
```

### 将Python字典转换为JSON字符串

python

复制

```python
import json

# 定义一个Python字典
# 字典中可以包含各种数据类型：字符串、数字、列表等
data_dict = {
    "name": "Bob",
    "age": 30,
    "city": "London",
    "hobbies": ["reading", "traveling"]  # 包含列表
}

# 使用json.dumps()方法将Python字典序列化为JSON字符串
# dumps = "dump string" 表示转储为字符串
# indent参数用于美化输出，指定缩进空格数
json_str = json.dumps(data_dict, indent=2)

# 打印转换后的JSON字符串
print(json_str)
"""
输出:
{
  "name": "Bob",
  "age": 30,
  "city": "London",
  "hobbies": [
    "reading",
    "traveling"
  ]
}
"""

# 查看转换后的数据类型
print(type(json_str))  # 输出: <class 'str'>
# 确认已成功转换为JSON格式字符串
```

## 2. 从JSON文件中读取数据

python

复制

```python
import json

# 使用with语句打开文件，确保文件操作完成后自动关闭
# encoding='utf-8'确保正确处理各种字符
with open('data.json', 'r', encoding='utf-8') as file:
    # 使用json.load()方法直接从文件对象加载JSON数据
    # 会自动转换为对应的Python数据类型(通常是字典或列表)
    data = json.load(file)

# 打印从文件加载的数据
print(data)

# 假设data.json内容如下:
"""
{
    "name": "Charlie",
    "age": 35,
    "married": true,
    "children": null
}
"""
# 转换后:
# true → True, null → None, 其他保持不变
```

## 3. 将数据写入JSON文件

python

复制

```python
import json

# 定义一个嵌套结构的Python字典
data = {
    "employee": {
        "name": "John",
        "age": 30,
        "department": "IT",
        "skills": ["Python", "Java", "SQL"]  # 包含列表
    },
    "projects": ["Website", "Mobile App"]  # 顶层也包含列表
}

# 使用with语句安全地打开文件进行写入
with open('output.json', 'w', encoding='utf-8') as file:
    # 使用json.dump()方法将Python对象写入文件
    # indent=4 表示使用4个空格缩进，使文件更易读
    # ensure_ascii=False 允许非ASCII字符(如中文)原样保存
    json.dump(data, file, indent=4, ensure_ascii=False)

# 写入的output.json文件内容将是格式化的JSON:
"""
{
    "employee": {
        "name": "John",
        "age": 30,
        "department": "IT",
        "skills": [
            "Python",
            "Java",
            "SQL"
        ]
    },
    "projects": [
        "Website",
        "Mobile App"
    ]
}
"""
```

## 4. 提取和操作JSON数据

python

复制

```python
import json

# 一个多行JSON字符串，包含嵌套结构和数组
json_data = '''
{
    "company": "TechCorp",
    "employees": [
        {
            "id": 1,
            "name": "Alice",
            "position": "Developer",
            "skills": ["Python", "JavaScript"]
        },
        {
            "id": 2,
            "name": "Bob",
            "position": "Manager",
            "skills": ["Leadership", "Project Management"]
        }
    ],
    "locations": ["New York", "London", "Tokyo"],
    "active": true
}
'''

# 将JSON字符串解析为Python字典
data = json.loads(json_data)

# 访问数据 - 使用字典键和列表索引
print("公司名称:", data["company"])  # 输出: TechCorp
print("第一位员工姓名:", data["employees"][0]["name"])  # 输出: Alice
print("第二位员工的技能:", data["employees"][1]["skills"])  # 输出: ['Leadership', 'Project Management']

# 修改数据
data["employees"][1]["position"] = "Senior Manager"  # 更新职位
data["locations"].append("Berlin")  # 添加新地点

# 添加新数据
data["founded"] = 2010  # 添加成立年份
data["employees"].append({
    "id": 3,
    "name": "Charlie",
    "position": "Designer"
})  # 添加新员工

# 删除数据
del data["active"]  # 删除active字段

# 将修改后的数据转换回JSON字符串，并进行美化输出
updated_json = json.dumps(data, indent=2)
print("\n更新后的JSON数据:")
print(updated_json)
```

## 5. 处理复杂的JSON数据结构

python

复制

```python
import json

# 定义一个深度嵌套的复杂JSON数据
complex_data = {
    "organization": "OpenAI",
    "departments": {
        "research": {
            "team_lead": "Ilya",
            "members": 50,
            "projects": ["GPT", "DALL-E", "Codex"]
        },
        "engineering": {
            "team_lead": "Greg",
            "members": 120,
            "subteams": {
                "backend": 40,
                "frontend": 30,
                "devops": 20
            }
        }
    },
    "locations": [
        {
            "city": "San Francisco",
            "country": "USA",
            "employees": 200
        },
        {
            "city": "London",
            "country": "UK",
            "employees": 50
        }
    ]
}

# 递归函数，打印JSON数据的结构
def print_json_structure(data, indent=0):
    """
    递归打印JSON数据的结构
    :param data: 要分析的JSON数据(Python字典)
    :param indent: 当前缩进级别，用于格式化输出
    """
    # 如果是字典类型
    if isinstance(data, dict):
        for key, value in data.items():
            # 打印键名
            print(' ' * indent + str(key), end=': ')
            if isinstance(value, dict):
                # 如果值是字典，换行后递归处理
                print()
                print_json_structure(value, indent + 4)
            elif isinstance(value, list) and value and isinstance(value[0], dict):
                # 如果值是包含字典的列表
                print(f"[list of {len(value)} dicts]")
                # 打印列表中第一个元素的结构作为示例
                print_json_structure(value[0], indent + 4)
            else:
                # 其他类型直接打印值(截断长字符串)
                print(str(value)[:50] + ('...' if len(str(value)) > 50 else ''))
    else:
        # 如果不是字典，直接打印
        print(' ' * indent + str(data))

# 使用示例
print("复杂JSON数据结构分析:")
print_json_structure(complex_data)
```

## 6. 处理JSON中的特殊数据类型

python

复制

```python
import json
from datetime import datetime, date
import decimal

# 定义一个包含Python特殊类型的字典
data = {
    "event": "Python Conference",
    "date": datetime.now(),  # datetime对象
    "price": decimal.Decimal("99.99"),  # Decimal对象
    "schedule": {
        "start": date(2023, 10, 1),  # date对象
        "end": date(2023, 10, 3)
    }
}

# 自定义JSON编码器，处理Python特殊类型
class CustomEncoder(json.JSONEncoder):
    """
    自定义JSON编码器，处理Python的特殊数据类型
    继承自json.JSONEncoder并重写default方法
    """
    def default(self, obj):
        # 处理datetime对象
        if isinstance(obj, datetime):
            return obj.isoformat()  # 转换为ISO8601格式字符串
        # 处理date对象
        elif isinstance(obj, date):
            return obj.isoformat()
        # 处理Decimal对象
        elif isinstance(obj, decimal.Decimal):
            return float(obj)  # 转换为浮点数
        # 其他类型使用父类默认处理
        return super().default(obj)

# 使用自定义编码器序列化数据
json_str = json.dumps(data, cls=CustomEncoder, indent=2)
print("包含特殊类型的JSON输出:")
print(json_str)

# 输出示例:
"""
{
  "event": "Python Conference",
  "date": "2023-07-15T14:30:45.123456",
  "price": 99.99,
  "schedule": {
    "start": "2023-10-01",
    "end": "2023-10-03"
  }
}
"""
```

## 7. 处理大型JSON文件

python

复制

```python
import ijson  # 需要安装: pip install ijson

# 处理大型JSON文件的推荐方法 - 使用ijson进行流式解析
def process_large_json(file_path):
    """
    流式处理大型JSON文件，避免内存不足的问题
    :param file_path: JSON文件路径
    """
    with open(file_path, 'rb') as file:  # 以二进制模式打开
        # 使用ijson.parse逐步解析JSON文件
        # 这会生成(prefix, event, value)三元组
        for prefix, event, value in ijson.parse(file):
            # prefix表示当前路径，如 'employees.item.name'
            # event表示事件类型，如 'start_map', 'end_map', 'start_array', 'end_array', 'map_key', 'string', 'number'等
            # value是当前的值
            
            # 示例：只处理特定的键
            if event == 'map_key' and value == 'name':
                # 下一个事件将是该键对应的值
                # 我们可以通过检查prefix来定位特定的name字段
                print(f"Found name at path: {prefix}")
            
            # 示例：处理所有字符串值
            if event == 'string':
                print(f"String value at {prefix}: {value}")
            
            # 在实际应用中，可以根据需要筛选和处理特定数据
            # 这样可以避免一次性加载整个大文件到内存

# 使用示例
# process_large_json('very_large_file.json')

# 另一种方法：使用ijson.items提取特定数组元素
def extract_employees(file_path):
    """
    从大型JSON文件中提取employees数组的每个元素
    """
    with open(file_path, 'rb') as file:
        # 使用ijson.items按需加载数组元素
        for employee in ijson.items(file, 'employees.item'):
            # 每次只处理一个员工对象，内存友好
            print(f"Processing employee: {employee['name']}")
            # 在这里进行实际的数据处理
            
# 使用示例
# extract_employees('large_company_data.json')
```

## 关键点总结

1. **基本转换**:
   - `json.loads()` - 从JSON字符串到Python对象
   - `json.dumps()` - 从Python对象到JSON字符串
   - `json.load()` - 从JSON文件到Python对象
   - `json.dump()` - 从Python对象到JSON文件
2. **数据类型映射**:
   - JSON对象 → Python字典
   - JSON数组 → Python列表
   - JSON字符串 → Python字符串
   - JSON数字 → Python整数或浮点数
   - JSON true/false → Python True/False
   - JSON null → Python None
3. **高级技巧**:
   - 使用`indent`参数美化JSON输出
   - 使用`ensure_ascii=False`处理非ASCII字符
   - 自定义编码器处理特殊Python类型
   - 使用ijson库流式处理大型JSON文件
4. **最佳实践**:
   - 总是使用`with`语句处理文件
   - 处理用户提供的JSON时要考虑异常处理
   - 大型文件使用流式处理避免内存问题
   - 考虑使用`try-except`捕获JSON解析错误

Python 内置 `json` 模块提供 JSON 编码（序列化）和解码（反序列化）功能。

## 三. 核心函数

| 函数                 | 作用                           | 常用参数                                         |
| -------------------- | ------------------------------ | ------------------------------------------------ |
| `json.dumps(obj)`    | 将 Python 对象转为 JSON 字符串 | `indent`, `sort_keys`, `ensure_ascii`, `default` |
| `json.loads(s)`      | 将 JSON 字符串转为 Python 对象 | `object_hook`                                    |
| `json.dump(obj, fp)` | 将对象序列化并写入文件         | 同 `dumps`                                       |
| `json.load(fp)`      | 从文件读取并反序列化           | 同 `loads`                                       |

## 四、数据类型对照表

| JSON 类型     | Python 类型 |
| ------------- | ----------- |
| object        | dict        |
| array         | list        |
| string        | str         |
| number (int)  | int         |
| number (real) | float       |
| true/false    | True/False  |
| null          | None        |

##### 注意差异：

- JSON 的键**必须是字符串**，Python 字典键可以是多种类型（但序列化时会强制转为字符串）
- Python 的元组(`tuple`) 会被转为 JSON 数组，反序列化时变回列表
- JSON 没有`bytes`类型，需手动编码/解码（如 Base64）

---





# 十二、文件读取写入



## 1. 文件打开模式

首先了解文件操作的基本模式：

| 模式 | 描述                         |
| :--- | :--------------------------- |
| 'r'  | 只读（默认）                 |
| 'w'  | 写入（会覆盖已有文件）       |
| 'x'  | 独占创建（文件已存在则失败） |
| 'a'  | 追加（在文件末尾添加）       |
| 'b'  | 二进制模式                   |
| 't'  | 文本模式（默认）             |
| '+'  | 更新（可读可写）             |

## 2. 基本文件读取操作

### 读取整个文件内容

python

复制

```python
# 方法1：使用read()读取全部内容
with open('example.txt', 'r', encoding='utf-8') as file:
    content = file.read()
    print(content)

# 方法2：使用readlines()读取为行列表
with open('example.txt', 'r', encoding='utf-8') as file:
    lines = file.readlines()  # 每行作为列表的一个元素
    for line in lines:
        print(line, end='')  # end=''避免print自带的换行
```

### 逐行读取文件

python

复制

```python
# 方法1：直接迭代文件对象（内存效率高）
with open('example.txt', 'r', encoding='utf-8') as file:
    for line in file:  # 每次读取一行
        print(line.strip())  # strip()去除首尾空白字符

# 方法2：使用readline()逐行读取
with open('example.txt', 'r', encoding='utf-8') as file:
    while True:
        line = file.readline()
        if not line:  # 到达文件末尾
            break
        print(line.strip())
```

## 3. 基本文件写入操作

### 写入新文件（覆盖）

python

复制

```python
# 使用'w'模式会覆盖已有文件
with open('output.txt', 'w', encoding='utf-8') as file:
    file.write("第一行内容\n")
    file.write("第二行内容\n")
    # writelines()可以写入字符串列表
    lines = ["第三行内容\n", "第四行内容\n"]
    file.writelines(lines)
```

### 追加内容到文件

python

复制

```python
# 使用'a'模式在文件末尾追加
with open('output.txt', 'a', encoding='utf-8') as file:
    file.write("这是追加的内容\n")
    file.write("这是另一行追加内容\n")
```

## 4. 高级文件操作

### 同时读写文件（'r+'模式）

python

复制

```python
# 使用'r+'模式可以同时读写
with open('example.txt', 'r+', encoding='utf-8') as file:
    # 先读取内容
    content = file.read()
    
    # 移动指针到文件开头
    file.seek(0)
    
    # 写入新内容（会覆盖开头部分）
    file.write("新的开头内容\n")
    
    # 再写入原始内容
    file.write(content)
```

### 二进制文件操作

python

复制

```python
# 读取二进制文件（如图片）
with open('image.jpg', 'rb') as file:
    binary_data = file.read()
    # 处理二进制数据...

# 写入二进制文件
with open('copy.jpg', 'wb') as file:
    file.write(binary_data)
```

## 5. 文件内容替换与修改

### 替换文件中特定内容

python

复制

```python
# 方法1：读取全部内容后替换
with open('example.txt', 'r', encoding='utf-8') as file:
    content = file.read()

# 替换所有"旧文本"为"新文本"
new_content = content.replace("旧文本", "新文本")

with open('example.txt', 'w', encoding='utf-8') as file:
    file.write(new_content)
```

### 修改文件中的特定行

python

复制

```python
# 修改第三行内容
line_number = 3
new_text = "这是新的第三行内容\n"

with open('example.txt', 'r', encoding='utf-8') as file:
    lines = file.readlines()

# 确保行号有效
if 0 < line_number <= len(lines):
    lines[line_number-1] = new_text  # 列表索引从0开始

with open('example.txt', 'w', encoding='utf-8') as file:
    file.writelines(lines)
```

## 6. 文件与目录操作

### 检查文件/目录是否存在

python

复制

```python
import os
import os.path

# 检查文件是否存在
if os.path.exists('example.txt'):
    print("文件存在")
else:
    print("文件不存在")

# 检查是否是文件
if os.path.isfile('example.txt'):
    print("这是一个文件")

# 检查是否是目录
if os.path.isdir('some_directory'):
    print("这是一个目录")
```

### 文件删除与重命名

python

复制

```python
import os

# 删除文件
try:
    os.remove('file_to_delete.txt')
    print("文件删除成功")
except FileNotFoundError:
    print("文件不存在")
except PermissionError:
    print("没有删除权限")

# 重命名文件
try:
    os.rename('old_name.txt', 'new_name.txt')
    print("文件重命名成功")
except FileNotFoundError:
    print("原文件不存在")
```

### 目录操作

python

复制

```python
import os

# 创建目录
os.makedirs('new_directory', exist_ok=True)  # exist_ok=True避免目录存在时报错

# 列出目录内容
for item in os.listdir('.'):  # '.'表示当前目录
    print(item)

# 删除目录（必须为空）
os.rmdir('empty_directory')
```

## 7. 临时文件操作

python

复制

```python
import tempfile

# 创建临时文件
with tempfile.NamedTemporaryFile(mode='w+', delete=False) as temp_file:
    temp_file.write("临时文件内容\n")
    temp_path = temp_file.name  # 获取临时文件路径
    print(f"临时文件创建在: {temp_path}")

# 临时文件默认会自动删除，设置delete=False可以保留
# 需要手动删除保留的临时文件
if os.path.exists(temp_path):
    os.remove(temp_path)
```

## 8. 文件操作最佳实践

1. **总是使用with语句**：
   - 自动处理文件关闭
   - 即使发生异常也能保证文件正确关闭
2. **明确指定编码**：
   - 特别是处理文本文件时，使用`encoding='utf-8'`
   - 避免因系统默认编码不同导致的问题
3. **处理大文件要谨慎**：
   - 使用逐行读取而不是一次性读取全部内容
   - 考虑使用生成器处理大文件
4. **异常处理**：
   - 捕获文件操作可能引发的异常（FileNotFoundError, PermissionError等）
5. **路径处理**：
   - 使用`os.path`或`pathlib`处理路径，确保跨平台兼容性

## 9. 使用pathlib模块（Python 3.4+）

python

复制

```python
from pathlib import Path

# 创建Path对象
file_path = Path('example.txt')

# 读取文件内容
content = file_path.read_text(encoding='utf-8')

# 写入文件
file_path.write_text("新的文件内容", encoding='utf-8')

# 追加内容
with file_path.open('a', encoding='utf-8') as file:
    file.write("\n追加的内容")

# 路径操作
new_file = file_path.parent / 'new_dir' / 'new_file.txt'
print(new_file)  # 输出类似: example.txt/../new_dir/new_file.txt
```

## 10. 综合示例：日志文件处理器

python

复制

```python
import os
from datetime import datetime
from pathlib import Path

class LogHandler:
    def __init__(self, log_dir="logs"):
        self.log_dir = Path(log_dir)
        self._ensure_log_dir()
        self.log_file = self._get_log_file()
        
    def _ensure_log_dir(self):
        """确保日志目录存在"""
        self.log_dir.mkdir(exist_ok=True)
        
    def _get_log_file(self):
        """根据日期创建日志文件"""
        today = datetime.now().strftime("%Y-%m-%d")
        return self.log_dir / f"{today}.log"
    
    def write_log(self, message, level="INFO"):
        """写入日志"""
        timestamp = datetime.now().strftime("%Y-%m-%d %H:%M:%S")
        log_entry = f"[{timestamp}] [{level}] {message}\n"
        
        with open(self.log_file, 'a', encoding='utf-8') as file:
            file.write(log_entry)
    
    def read_logs(self, num_lines=10):
        """读取最近的日志"""
        if not self.log_file.exists():
            return "No log file found"
            
        with open(self.log_file, 'r', encoding='utf-8') as file:
            lines = file.readlines()
            return "".join(lines[-num_lines:])
    
    def clean_logs(self, days_to_keep=7):
        """清理旧日志"""
        cutoff = datetime.now().timestamp() - days_to_keep * 86400
        
        for log in self.log_dir.glob("*.log"):
            if log.stat().st_mtime < cutoff:
                log.unlink()
                print(f"Deleted old log: {log.name}")

# 使用示例
logger = LogHandler()
logger.write_log("Application started")
logger.write_log("User logged in", "DEBUG")
print("Recent logs:")
print(logger.read_logs(5))
logger.clean_logs()
```

# 十三、csv文件读取写入

## 1. CSV文件读取

### 基本读取方法

python

复制

```python
import csv

# 方法1：使用csv.reader
with open('data.csv', 'r', encoding='utf-8') as file:
    csv_reader = csv.reader(file)
    for row in csv_reader:
        print(row)  # 每行作为一个列表返回

# 方法2：使用csv.DictReader（推荐）
with open('data.csv', 'r', encoding='utf-8') as file:
    csv_reader = csv.DictReader(file)
    for row in csv_reader:
        print(row)  # 每行作为一个有序字典返回，键为列名
        print(row['name'], row['age'])  # 通过列名访问数据
```

### 处理不同格式的CSV

python

复制

```python
# 处理不同分隔符的文件（如TSV）
with open('data.tsv', 'r', encoding='utf-8') as file:
    csv_reader = csv.reader(file, delimiter='\t')  # 指定制表符分隔
    for row in csv_reader:
        print(row)

# 处理有引号的字段
with open('quoted_data.csv', 'r', encoding='utf-8') as file:
    csv_reader = csv.reader(file, quotechar='"', quoting=csv.QUOTE_MINIMAL)
    for row in csv_reader:
        print(row)
```

## 2. CSV文件写入

### 基本写入方法

python

复制

```python
import csv

data = [
    ['name', 'age', 'city'],
    ['Alice', 25, 'New York'],
    ['Bob', 30, 'London'],
    ['Charlie', 35, 'Tokyo']
]

# 方法1：使用csv.writer
with open('output.csv', 'w', encoding='utf-8', newline='') as file:
    csv_writer = csv.writer(file)
    csv_writer.writerows(data)  # 写入多行

# 方法2：逐行写入
with open('output2.csv', 'w', encoding='utf-8', newline='') as file:
    csv_writer = csv.writer(file)
    csv_writer.writerow(['name', 'age', 'city'])  # 写入标题
    csv_writer.writerow(['Alice', 25, 'New York'])
    csv_writer.writerow(['Bob', 30, 'London'])
```

### 使用DictWriter写入（推荐）

python

复制

```python
import csv

data = [
    {'name': 'Alice', 'age': 25, 'city': 'New York'},
    {'name': 'Bob', 'age': 30, 'city': 'London'},
    {'name': 'Charlie', 'age': 35, 'city': 'Tokyo'}
]

fieldnames = ['name', 'age', 'city']

with open('dict_output.csv', 'w', encoding='utf-8', newline='') as file:
    writer = csv.DictWriter(file, fieldnames=fieldnames)
    writer.writeheader()  # 写入列名
    writer.writerows(data)  # 写入多行数据
```

## 3. CSV文件修改与更新

### 修改CSV文件内容

python

复制

```python
import csv
from tempfile import NamedTemporaryFile
import shutil

filename = 'employees.csv'
tempfile = NamedTemporaryFile(mode='w', delete=False, newline='')

# 修改特定行的数据
with open(filename, 'r', encoding='utf-8') as csvfile, tempfile:
    reader = csv.DictReader(csvfile)
    fieldnames = reader.fieldnames
    writer = csv.DictWriter(tempfile, fieldnames=fieldnames)
    writer.writeheader()
    
    for row in reader:
        if row['id'] == '103':  # 找到ID为103的员工
            row['salary'] = '55000'  # 更新薪资
        writer.writerow(row)

# 替换原文件
shutil.move(tempfile.name, filename)
```

### 向CSV文件追加数据

python

复制

```python
import csv

new_data = [
    {'name': 'David', 'age': 28, 'city': 'Berlin'},
    {'name': 'Eve', 'age': 32, 'city': 'Paris'}
]

# 追加数据到现有CSV文件
with open('dict_output.csv', 'a', encoding='utf-8', newline='') as file:
    writer = csv.DictWriter(file, fieldnames=['name', 'age', 'city'])
    writer.writerows(new_data)
```

## 4. CSV文件过滤与处理

### 过滤CSV数据

python

复制

```python
import csv

# 筛选年龄大于30的记录
with open('data.csv', 'r', encoding='utf-8') as infile:
    reader = csv.DictReader(infile)
    filtered_data = [row for row in reader if int(row['age']) > 30]

# 将筛选结果写入新文件
with open('filtered.csv', 'w', encoding='utf-8', newline='') as outfile:
    writer = csv.DictWriter(outfile, fieldnames=reader.fieldnames)
    writer.writeheader()
    writer.writerows(filtered_data)
```

### 计算CSV统计数据

python

复制

```python
import csv

total_age = 0
count = 0

with open('data.csv', 'r', encoding='utf-8') as file:
    reader = csv.DictReader(file)
    for row in reader:
        total_age += int(row['age'])
        count += 1

average_age = total_age / count if count > 0 else 0
print(f"平均年龄: {average_age:.1f}")
```

## 5. 处理大型CSV文件

### 分块处理大型CSV

python

复制

```python
import csv

def process_large_csv(file_path, chunk_size=1000):
    """分块处理大型CSV文件"""
    with open(file_path, 'r', encoding='utf-8') as file:
        reader = csv.DictReader(file)
        chunk = []
        
        for i, row in enumerate(reader):
            chunk.append(row)
            
            if len(chunk) == chunk_size:
                # 处理当前块
                process_chunk(chunk)
                chunk = []
        
        # 处理剩余的最后一块
        if chunk:
            process_chunk(chunk)

def process_chunk(chunk):
    """处理数据块"""
    print(f"处理包含 {len(chunk)} 行的数据块")
    # 这里添加实际的数据处理逻辑
```

### 使用pandas处理CSV（适合数据分析）

python

复制

```python
import pandas as pd

# 读取CSV文件
df = pd.read_csv('large_data.csv')

# 查看前5行
print(df.head())

# 筛选数据
filtered_df = df[df['age'] > 30]

# 计算统计信息
print(df.describe())

# 写入新CSV文件
filtered_df.to_csv('filtered_pandas.csv', index=False)
```

## 6. CSV高级操作

### 处理非标准CSV文件

python

复制

```python
import csv

# 处理有不同换行符的CSV
with open('nonstandard.csv', 'r', encoding='utf-8') as file:
    # 指定不同的行结束符和引号规则
    reader = csv.reader(file, lineterminator='\r\n',
                       quotechar="'", quoting=csv.QUOTE_NONNUMERIC)
    for row in reader:
        print(row)
```

### CSV与其他格式转换

python

复制

```python
import csv
import json

# CSV转JSON
csv_data = []
with open('data.csv', 'r', encoding='utf-8') as csvfile:
    reader = csv.DictReader(csvfile)
    for row in reader:
        csv_data.append(row)

with open('data.json', 'w', encoding='utf-8') as jsonfile:
    json.dump(csv_data, jsonfile, indent=2)

# JSON转CSV
with open('data.json', 'r', encoding='utf-8') as jsonfile:
    json_data = json.load(jsonfile)

if json_data:
    with open('from_json.csv', 'w', encoding='utf-8', newline='') as csvfile:
        writer = csv.DictWriter(csvfile, fieldnames=json_data[0].keys())
        writer.writeheader()
        writer.writerows(json_data)
```

## 7. CSV操作最佳实践

1. **始终指定编码**：使用`encoding='utf-8'`避免编码问题
2. **使用`newline=''`**：防止写入CSV时出现空行
3. **处理大文件要谨慎**：考虑分块处理或使用生成器
4. **验证数据**：处理前检查CSV格式是否一致
5. **使用DictReader/DictWriter**：使代码更易读和维护
6. **备份原始文件**：修改前先备份重要数据
7. **异常处理**：捕获可能的文件操作异常

## 8. 综合示例：员工管理系统

python

复制

```python
import csv
import os
from tempfile import NamedTemporaryFile

class EmployeeCSVManager:
    def __init__(self, filename='employees.csv'):
        self.filename = filename
        self._ensure_file_exists()
    
    def _ensure_file_exists(self):
        """确保CSV文件存在并包含正确的列名"""
        if not os.path.exists(self.filename):
            with open(self.filename, 'w', newline='') as file:
                writer = csv.DictWriter(file, fieldnames=['id', 'name', 'department', 'salary'])
                writer.writeheader()
    
    def add_employee(self, emp_id, name, department, salary):
        """添加新员工"""
        with open(self.filename, 'a', newline='') as file:
            writer = csv.DictWriter(file, fieldnames=['id', 'name', 'department', 'salary'])
            writer.writerow({
                'id': emp_id,
                'name': name,
                'department': department,
                'salary': salary
            })
    
    def update_salary(self, emp_id, new_salary):
        """更新员工薪资"""
        tempfile = NamedTemporaryFile(mode='w', delete=False)
        
        with open(self.filename, 'r') as csvfile, tempfile:
            reader = csv.DictReader(csvfile)
            writer = csv.DictWriter(tempfile, fieldnames=reader.fieldnames)
            writer.writeheader()
            
            updated = False
            for row in reader:
                if row['id'] == str(emp_id):
                    row['salary'] = new_salary
                    updated = True
                writer.writerow(row)
        
        if updated:
            os.replace(tempfile.name, self.filename)
        else:
            os.unlink(tempfile.name)
            print(f"未找到ID为 {emp_id} 的员工")
    
    def get_department_stats(self, department):
        """获取部门统计信息"""
        total_salary = 0
        count = 0
        
        with open(self.filename, 'r') as file:
            reader = csv.DictReader(file)
            for row in reader:
                if row['department'] == department:
                    total_salary += float(row['salary'])
                    count += 1
        
        return {
            'department': department,
            'employee_count': count,
            'avg_salary': total_salary / count if count > 0 else 0
        }
    
    def export_to_json(self, json_filename):
        """将CSV导出为JSON"""
        employees = []
        
        with open(self.filename, 'r') as csvfile:
            reader = csv.DictReader(csvfile)
            for row in reader:
                employees.append(row)
        
        with open(json_filename, 'w') as jsonfile:
            json.dump(employees, jsonfile, indent=2)

# 使用示例
manager = EmployeeCSVManager()

# 添加员工
manager.add_employee(101, 'Alice', 'Engineering', 75000)
manager.add_employee(102, 'Bob', 'Marketing', 65000)
manager.add_employee(103, 'Charlie', 'Engineering', 80000)

# 更新薪资
manager.update_salary(102, 68000)

# 获取部门统计
stats = manager.get_department_stats('Engineering')
print(f"工程部统计: {stats}")

# 导出为JSON
manager.export_to_json('employees.json')
```



# 十四、特殊函数lambda/filter/map

## 1. lambda 函数（匿名函数）

`lambda` 用于创建小型匿名函数（没有名称的函数），通常用于需要一个简单函数但不想正式定义它的场景。

### 基本语法

python

复制

```python
lambda arguments: expression
```

### 特点

- 可以接受任意数量的参数，但只能有一个表达式
- 表达式的结果就是函数的返回值
- 不需要 `return` 语句

### 使用示例

python

复制

```python
# 普通函数定义
def square(x):
    return x ** 2

# 等效的lambda表达式
square_lambda = lambda x: x ** 2

print(square(5))        # 输出: 25
print(square_lambda(5)) # 输出: 25
```

### 常见应用场景

1. **作为参数传递给高阶函数**：

python

复制

```python
# 对列表按绝对值排序
numbers = [-3, 2, -1, 5, -4]
sorted_numbers = sorted(numbers, key=lambda x: abs(x))
print(sorted_numbers)  # 输出: [-1, 2, -3, -4, 5]
```

1. **在 GUI 编程中作为回调函数**：

python

复制

```python
# 假设有一个按钮点击事件
button.clicked.connect(lambda: print("Button clicked!"))
```

1. **简单的数据转换**：

python

复制

```python
# 将字符串列表转换为长度列表
words = ["apple", "banana", "cherry"]
lengths = list(map(lambda word: len(word), words))
print(lengths)  # 输出: [5, 6, 6]
```

## 2. filter 函数

`filter()` 函数用于过滤序列，过滤掉不符合条件的元素，返回一个迭代器对象。

### 基本语法

python

复制

```python
filter(function, iterable)
```

### 特点

- 第一个参数是函数，第二个参数是可迭代对象
- 函数应返回 `True` 或 `False`
- 返回一个包含所有使函数返回 `True` 的元素的迭代器

### 使用示例

python

复制

```python
# 过滤出偶数
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
even_numbers = list(filter(lambda x: x % 2 == 0, numbers))
print(even_numbers)  # 输出: [2, 4, 6, 8, 10]

# 过滤掉空字符串
words = ["hello", "", "world", " ", "python", ""]
non_empty = list(filter(lambda x: x.strip() != "", words))
print(non_empty)  # 输出: ['hello', 'world', 'python']
```

### 常见应用场景

1. **数据清洗**：

python

复制

```python
# 从数据中过滤掉无效值
data = [10, 0, 20, None, 30, 0, 40]
valid_data = list(filter(lambda x: x is not None and x != 0, data))
print(valid_data)  # 输出: [10, 20, 30, 40]
```

1. **条件筛选**：

python

复制

```python
# 筛选出成绩及格的学生
students = [
    {"name": "Alice", "score": 85},
    {"name": "Bob", "score": 45},
    {"name": "Charlie", "score": 72},
    {"name": "David", "score": 58}
]
passed = list(filter(lambda s: s["score"] >= 60, students))
print(passed)
# 输出: [{'name': 'Alice', 'score': 85}, {'name': 'Charlie', 'score': 72}]
```

## 3. map 函数

`map()` 函数将一个函数应用于可迭代对象的每一项，并返回一个结果迭代器。

### 基本语法

python

复制

```python
map(function, iterable, ...)
```

### 特点

- 第一个参数是函数，后面的参数是一个或多个可迭代对象
- 函数会并行地从各个可迭代对象中取出元素作为参数
- 返回一个将函数作用于每个元素后的结果迭代器

### 使用示例

python

复制

```python
# 将列表中的每个数字平方
numbers = [1, 2, 3, 4, 5]
squares = list(map(lambda x: x ** 2, numbers))
print(squares)  # 输出: [1, 4, 9, 16, 25]

# 将两个列表对应位置相加
list1 = [1, 2, 3]
list2 = [4, 5, 6]
sums = list(map(lambda x, y: x + y, list1, list2))
print(sums)  # 输出: [5, 7, 9]
```

### 常见应用场景

1. **数据转换**：

python

复制

```python
# 将字符串列表转换为大写
words = ["hello", "world", "python"]
upper_words = list(map(lambda x: x.upper(), words))
print(upper_words)  # 输出: ['HELLO', 'WORLD', 'PYTHON']
```

1. **多列表操作**：

python

复制

```python
# 计算多个列表中对应位置的乘积
prices = [10.5, 22.3, 15.0]
quantities = [3, 5, 2]
totals = list(map(lambda p, q: p * q, prices, quantities))
print(totals)  # 输出: [31.5, 111.5, 30.0]
```

1. **类型转换**：

python

复制

```python
# 将字符串列表转换为整数
str_numbers = ["1", "2", "3", "4"]
int_numbers = list(map(int, str_numbers))
print(int_numbers)  # 输出: [1, 2, 3, 4]
```

## 4. 组合使用 lambda、filter 和 map

这些函数经常一起使用，可以实现强大的数据处理功能。

### 示例1：处理学生成绩

python

复制

```python
students = [
    {"name": "Alice", "score": 85},
    {"name": "Bob", "score": 45},
    {"name": "Charlie", "score": 72},
    {"name": "David", "score": 58}
]

# 获取及格学生的名字（分数≥60）
passed_names = list(map(
    lambda s: s["name"],
    filter(lambda s: s["score"] >= 60, students)
))
print(passed_names)  # 输出: ['Alice', 'Charlie']

# 给不及格的学生加10分
adjusted_scores = list(map(
    lambda s: {**s, "score": s["score"] + 10} if s["score"] < 60 else s,
    students
))
print(adjusted_scores)
# 输出: [{'name': 'Alice', 'score': 85}, 
#        {'name': 'Bob', 'score': 55}, 
#        {'name': 'Charlie', 'score': 72}, 
#        {'name': 'David', 'score': 68}]
```

### 示例2：数据处理管道

python

复制

```python
# 原始数据
data = ["10", "20", "30", "40", "50", "60", "70"]

# 数据处理流程:
# 1. 转换为整数
# 2. 过滤掉小于30的数
# 3. 将剩余数乘以2
result = list(map(
    lambda x: x * 2,
    filter(
        lambda x: x >= 30,
        map(int, data)
    )
))
print(result)  # 输出: [60, 80, 100, 120, 140]
```

## 5. 与列表推导式的比较

许多 `map` 和 `filter` 的操作可以用列表推导式更简洁地表达：

### map 等效的列表推导式

python

复制

```python
# map版本
squares = list(map(lambda x: x**2, range(10)))

# 列表推导式版本
squares = [x**2 for x in range(10)]
```

### filter 等效的列表推导式

python

复制

```python
# filter版本
evens = list(filter(lambda x: x%2 == 0, range(10)))

# 列表推导式版本
evens = [x for x in range(10) if x%2 == 0]
```

### 组合操作的列表推导式

python

复制

```python
# map和filter组合
result = list(map(lambda x: x*2, filter(lambda x: x>5, range(10))))

# 列表推导式版本
result = [x*2 for x in range(10) if x>5]
```

## 6. 性能考虑

- 对于简单操作，列表推导式通常比 `map` 和 `filter` 更快
- `map` 和 `filter` 返回迭代器，可以节省内存（特别是对于大数据集）
- 当函数已经存在时（如内置函数 `str.upper`），`map` 可能比列表推导式更高效

## 7. 实际应用案例

### 案例1：处理CSV数据

python

复制

```python
import csv

# 读取CSV并处理数据
with open('data.csv') as f:
    reader = csv.DictReader(f)
    # 过滤掉空行，并将特定列转换为浮点数
    processed_data = [
        {k: float(v) if k in ['price', 'quantity'] else v 
         for k, v in row.items()
        }
        for row in reader 
        if any(row.values())  # 过滤空行
    ]
```

### 案例2：构建数据处理管道

python

复制

```python
def process_data(data):
    # 步骤1: 清理数据 - 移除非数字和空值
    cleaned = filter(lambda x: x.isdigit(), data)
    
    # 步骤2: 转换为整数
    numbers = map(int, cleaned)
    
    # 步骤3: 计算平方
    squares = map(lambda x: x**2, numbers)
    
    # 步骤4: 过滤出偶数平方
    even_squares = filter(lambda x: x % 2 == 0, squares)
    
    return list(even_squares)

data = ["1", "2", "3", "a", "", "4", "5", "6"]
print(process_data(data))  # 输出: [4, 16, 36]
```

## 总结

1. **lambda 函数**：
   - 创建小型匿名函数
   - 语法：`lambda 参数: 表达式`
   - 适用于简单的一次性函数需求
2. **filter 函数**：
   - 过滤可迭代对象中的元素
   - 返回使函数返回 `True` 的元素
   - 语法：`filter(函数, 可迭代对象)`
3. **map 函数**：
   - 将函数应用于可迭代对象的每个元素
   - 返回结果迭代器
   - 语法：`map(函数, 可迭代对象)`
4. **组合使用**：
   - 可以构建强大的数据处理管道
   - 经常与列表推导式相互转换
   - 对于复杂操作，列表推导式可能更易读
5. **选择建议**：
   - 简单操作且已有函数：使用 `map`
   - 条件过滤：使用 `filter`
   - 复杂操作：考虑列表推导式
   - 需要内存效率：使用 `map`/`filter`（返回迭代器）

# 十五、python列表推导式筛选功能详解[...for ...in .. if ...]

这个列表推导式 `[word for word in words if len(word) > 1 and word not in stopwords]` 是一个非常典型的Pythonic写法，用于对列表进行筛选和转换。下面我将详细解释它的工作原理，并给出更多类似的实用例子。

## 一、基础语法解析

### 原代码分析

python

复制

```python
[word for word in words if len(word) > 1 and word not in stopwords]
```

这个列表推导式由三部分组成：

1. **输出表达式**：`word`（保留原始元素不做转换）
2. **输入序列**：`for word in words`（遍历words列表）
3. **筛选条件**：`if len(word) > 1 and word not in stopwords`（两个条件必须同时满足）

### 等效的普通for循环

python

复制

```python
result = []
for word in words:
    if len(word) > 1 and word not in stopwords:
        result.append(word)
```

## 二、筛选条件详解

### 1. `len(word) > 1`

- 作用：过滤掉单字词（如"的"、"是"等）
- 中文处理中，单字词通常意义不大或属于停用词

### 2. `word not in stopwords`

- 作用：过滤掉停用词（如"因为"、"所以"等）
- `stopwords`是一个包含常见停用词的集合

### 3. 逻辑组合

- `and`表示两个条件必须同时满足
- 也可以使用`or`表示任一条件满足

## 三、更多实用示例

### 1. 数据清洗示例

python

复制

```python
# 示例1：过滤掉数字和空字符串
data = ["apple", "", "123", "banana", "45.6", "cherry"]
cleaned = [item for item in data if item and not item.isdigit()]
# 结果: ['apple', 'banana', 'cherry']

# 示例2：保留2-5个字符的单词
words = ["I", "love", "Python", "programming", "!"]
filtered = [word for word in words if 2 <= len(word) <= 5]
# 结果: ['love', 'Python', '!']
```

### 2. 数值处理示例

python

复制

```python
# 示例3：筛选出偶数并平方
numbers = [1, 2, 3, 4, 5, 6]
result = [x**2 for x in numbers if x % 2 == 0]
# 结果: [4, 16, 36]

# 示例4：筛选正数并转换为字符串
values = [-2.5, 3.1, 0, 4.8, -1.2]
result = [str(x) for x in values if x > 0]
# 结果: ['3.1', '4.8']
```

### 3. 字典数据处理示例

python

复制

```python
# 示例5：筛选字典中值大于阈值的项
scores = {"Alice": 85, "Bob": 62, "Charlie": 91, "David": 58}
passed = {name: score for name, score in scores.items() if score >= 60}
# 结果: {'Alice': 85, 'Bob': 62, 'Charlie': 91}

# 示例6：筛选包含特定键的字典列表
users = [
    {"name": "Alice", "age": 25, "active": True},
    {"name": "Bob", "age": 30, "active": False},
    {"name": "Charlie", "age": 35}
]
active_users = [user for user in users if user.get("active")]
# 结果: [{'name': 'Alice', 'age': 25, 'active': True}]
```

### 4. 复杂条件组合示例

python

复制

```python
# 示例7：多条件筛选
products = [
    {"name": "Laptop", "price": 1200, "stock": 5},
    {"name": "Mouse", "price": 25, "stock": 0},
    {"name": "Keyboard", "price": 80, "stock": 10}
]
available = [p for p in products if p["stock"] > 0 and p["price"] < 100]
# 结果: [{'name': 'Keyboard', 'price': 80, 'stock': 10}]

# 示例8：使用函数作为条件
def is_prime(n):
    if n < 2:
        return False
    for i in range(2, int(n**0.5)+1):
        if n % i == 0:
            return False
    return True

numbers = range(20)
primes = [x for x in numbers if is_prime(x)]
# 结果: [2, 3, 5, 7, 11, 13, 17, 19]
```

## 四、性能考虑与替代方案

### 1. 列表推导式 vs filter函数

python

复制

```python
# 列表推导式
result = [x for x in items if condition(x)]

# 等效的filter函数
result = list(filter(condition, items))
```

- 列表推导式通常更直观易读
- filter返回迭代器，内存效率更高（特别适合大数据集）

### 2. 多重条件处理

对于复杂条件，可以考虑：

python

复制

```python
# 方法1：使用多个if
result = [x for x in items if cond1(x) if cond2(x)]

# 方法2：使用and组合
result = [x for x in items if cond1(x) and cond2(x)]

# 方法3：使用函数封装
def complex_condition(x):
    return cond1(x) and cond2(x)
result = [x for x in items if complex_condition(x)]
```

## 五、实际应用案例

### 案例1：处理CSV数据

python

复制

```python
import csv

# 读取CSV并筛选特定条件的行
with open('data.csv') as f:
    reader = csv.DictReader(f)
    filtered_rows = [
        row for row in reader 
        if float(row["price"]) > 50 
        and row["category"] == "Electronics"
    ]
```

### 案例2：文本处理管道

python

复制

```python
# 多步骤文本处理
text = "Some sample text with numbers like 123 and symbols @#!"

# 1. 分词
words = text.split()
# 2. 移除数字和符号
clean_words = [
    word for word in words 
    if word.isalpha()
]
# 3. 转换为小写并过滤短词
final_words = [
    word.lower() for word in clean_words 
    if len(word) > 3
]
```

### 案例3：Pandas DataFrame筛选

python

复制

```python
import pandas as pd

# 创建DataFrame
df = pd.DataFrame({
    'Name': ['Alice', 'Bob', 'Charlie'],
    'Age': [25, 30, 35],
    'Salary': [50000, 60000, 70000]
})

# 使用列表推导式筛选符合条件的行
high_earners = [
    row for _, row in df.iterrows() 
    if row['Age'] > 28 and row['Salary'] > 55000
]
```

## 六、总结

这种列表推导式筛选写法是Python中非常强大和高效的数据处理方式，具有以下优点：

1. **简洁性**：用一行代码完成循环和条件判断
2. **可读性**：结构清晰，意图明确
3. **性能**：通常比等效的for循环更快
4. **灵活性**：可以处理各种复杂条件

记住几个关键点：

- 条件部分可以包含任意复杂的逻辑表达式
- 可以使用多个if条件进行筛选
- 可以嵌套多个for循环处理多维数据
- 输出表达式部分可以对元素进行转换

掌握这种写法能显著提高你的Python编码效率和代码质量。



# 十六、词频统计与词云



## 一、jieba分词基础

### 1. 安装jieba库

bash

复制

```python
pip install jieba
pip install wordcloud  # 词云库
pip install matplotlib  # 绘图库
```

### 2. jieba的三种分词模式

#### (1) 精确模式（默认）

python

复制

```python
import jieba

text = "我爱自然语言处理技术"
seg_list = jieba.cut(text, cut_all=False)  # cut_all=False表示精确模式
print("精确模式: " + "/".join(seg_list))
# 输出: 精确模式: 我/爱/自然语言/处理/技术
```

#### (2) 全模式

python

复制

```python
seg_list = jieba.cut(text, cut_all=True)  # cut_all=True表示全模式
print("全模式: " + "/".join(seg_list))
# 输出: 全模式: 我/爱/自然/自然语言/语言/处理/技术
```

#### (3) 搜索引擎模式

python

复制

```python
seg_list = jieba.cut_for_search(text)  # 搜索引擎模式
print("搜索引擎模式: " + "/".join(seg_list))
# 输出: 搜索引擎模式: 我/爱/自然/语言/自然语言/处理/技术
```

### 3. 模式对比与选择

| 模式         | 特点                               | 适用场景                 |
| :----------- | :--------------------------------- | :----------------------- |
| 精确模式     | 精准切分，无冗余词                 | 文本分析、词频统计       |
| 全模式       | 扫描所有可能成词，输出所有可能词语 | 实验性研究               |
| 搜索引擎模式 | 在精确模式基础上对长词再次切分     | 搜索引擎索引、短文本检索 |

## 二、词频统计完整流程

### 1. 基础词频统计

python

复制

```python
from collections import Counter

text = """自然语言处理是人工智能领域的一个重要方向。
它研究能实现人与计算机之间用自然语言进行有效通信的各种理论和方法。"""

# 分词
words = jieba.cut(text)
# 过滤单字词
words = [word for word in words if len(word) > 1]
# 统计词频
word_counts = Counter(words)

print("常见词频:")
for word, count in word_counts.most_common(5):
    print(f"{word}: {count}")
```

### 2. 加入停用词处理

python

复制

```python
# 加载停用词表
def load_stopwords(file_path):
    with open(file_path, 'r', encoding='utf-8') as f:
        return set([line.strip() for line in f])

stopwords = load_stopwords('stopwords.txt')  # 停用词表文件

# 改进的分词统计
words = jieba.cut(text)
words = [word for word in words 
         if len(word) > 1 and word not in stopwords]
word_counts = Counter(words)
```

### 3. 自定义词典增强分词

python

复制

```python
# 添加自定义词典
jieba.load_userdict("userdict.txt")  # 每行格式: 词语 词频 词性

# 或者临时添加单词
jieba.add_word("深度学习")
jieba.add_word("神经网络")
```

## 三、词云生成进阶

python

复制

```python
"""
中文词云生成完整流程
环境需求：jieba, wordcloud, matplotlib, numpy, PIL
"""

# -------------------- 第一部分：准备工作 --------------------
import jieba                     # 中文分词库
from wordcloud import WordCloud  # 词云生成库
import matplotlib.pyplot as plt  # 绘图库
from collections import Counter  # 词频统计
import numpy as np               # 矩阵处理
from PIL import Image            # 图像处理

# 设置显示中文字体（解决中文乱码关键步骤！）
plt.rcParams['font.sans-serif'] = ['SimHei']  # 设置默认字体
plt.rcParams['axes.unicode_minus'] = False    # 解决负号显示问题

# -------------------- 第二部分：数据准备 --------------------
# 读取文本文件（注意文件编码，中文常用gbk或utf-8）
with open('article.txt', 'r', encoding='utf-8') as f:
    text = f.read()  # text变量将存储整个文本内容

# 加载停用词表（需自己准备，或使用网络上的中文停用词表）
# 停用词表示例内容：
# 的 了 在 是 我 有 和 就 人 都 ...
with open('stopwords.txt', 'r', encoding='utf-8') as f:
    stopwords = set([line.strip() for line in f])

# 自定义词典（可选，针对专业领域词汇）
jieba.load_userdict('userdict.txt')  # 文件格式：每行 "词语 词频 词性"
# 例如： 区块链 10 n

# -------------------- 第三部分：分词处理 --------------------
# 使用jieba进行分词（精准模式）
# cut_all参数说明：
# - True: 全模式（所有可能的分词结果）
# - False: 默认模式（精准模式）
words = jieba.cut(text, cut_all=False)

# 清洗数据：过滤单字和停用词
# 注意：根据需求调整过滤条件
filtered_words = [
    word for word in words 
    if len(word) > 1 and               # 过滤单字词
    word not in stopwords and          # 过滤停用词
    not word.isdigit() and             # 过滤纯数字
    '\u4e00' <= word <= '\u9fff'       # 保留中文字符（过滤特殊符号）
]

# -------------------- 第四部分：词频统计 --------------------
# 统计词频（取前200个高频词）
word_counts = Counter(filtered_words)
top_words = word_counts.most_common(200)

# 打印前20个高频词
print("高频词汇TOP20:")
for word, count in top_words[:20]:
    print(f"{word}: {count}")

# -------------------- 第五部分：词云生成 --------------------
# 创建词云对象（核心参数说明）
wc = WordCloud(
    font_path='msyh.ttc',          # 字体路径（必须使用中文字体！）
    width=800,                     # 画布宽度（像素）
    height=600,                    # 画布高度
    background_color='white',      # 背景颜色
    max_words=200,                 # 最多显示词数
    max_font_size=100,             # 最大字号
    min_font_size=10,              # 最小字号
    collocations=False,            # 是否包含两个词的搭配（中文建议False）
    scale=2                        # 输出分辨率（越大越清晰，但生成越慢）
)

# 生成词云（两种方式任选其一）
# 方式1：从词频生成
word_freq = dict(top_words)
wc.generate_from_frequencies(word_freq)

# 方式2：从文本生成（自动统计词频）
# wc.generate(' '.join(filtered_words))

# -------------------- 第六部分：高级定制 --------------------
# 使用蒙版图片（需准备黑白轮廓图，如中国地图）
mask_image = np.array(Image.open('china_map.png'))  # 转换为numpy数组
wc.mask = mask_image  # 应用蒙版

# 重新生成词云（应用新参数后需要重新生成）
wc.generate_from_frequencies(word_freq)

# -------------------- 第七部分：可视化与保存 --------------------
# 创建画布
plt.figure(figsize=(12, 8))        # 设置画布尺寸（单位英寸）
plt.imshow(wc, interpolation='bilinear')  # 显示词云
plt.title('中文词云分析', fontsize=20)     # 添加标题
plt.axis('off')                    # 关闭坐标轴

# 显示颜色条（可选）
# plt.colorbar()

# 保存图片（支持png/jpg/pdf等多种格式）
wc.to_file('wordcloud.png')        # 直接保存词云对象
# plt.savefig('result.jpg', dpi=300, bbox_inches='tight')  # 保存整个画布

# 显示图像（如果在IDE中运行需要此行）
plt.show()

# -------------------- 第八部分：问题排查 --------------------
"""
常见问题解决方案：
1. 中文显示为方框：
   - 确认font_path参数指向有效的中文字体文件（如微软雅黑msyh.ttc）
   - 检查系统是否安装对应字体

2. 词云形状不符合预期：
   - 蒙版图片需要是白色背景+黑色形状
   - 图片尺寸不宜过小（建议至少500x500像素）

3. 分词效果差：
   - 添加专业词汇到userdict.txt
   - 调整停用词表
   - 尝试不同分词模式（全模式/搜索引擎模式）

4. 词云内容不合理：
   - 检查停用词表是否遗漏常见虚词
   - 过滤特殊符号和数字
   - 调整max_words参数控制显示词数
"""
```

### 关键文件说明：

1. **article.txt**：需要分析的文本文件（建议UTF-8编码）
2. **stopwords.txt**：停用词表（每行一个停用词）
3. **userdict.txt**：自定义词典（格式：`词语 词频 词性`，如`云计算 10 n`）
4. **china_map.png**：蒙版图片（白色背景+黑色形状轮廓）

### 完整执行流程：

1. 准备文本文件和停用词表
2. 安装依赖库：`pip install jieba wordcloud matplotlib numpy pillow`
3. 根据需求调整代码中的文件路径和参数
4. 运行代码查看结果
5. 根据输出调整分词策略和词云参数

## 四、完整实战案例

### 1. 中文小说分析案例

python

复制

```python
import jieba
import jieba.analyse
from collections import Counter
from wordcloud import WordCloud
import matplotlib.pyplot as plt

# 1. 读取文本
with open("novel.txt", "r", encoding='gb18030') as f:
    text = f.read()

# 2. 加载停用词
stopwords = set(line.strip() for line in open('stopwords.txt', encoding='utf-8'))

# 3. 使用TF-IDF提取关键词
keywords = jieba.analyse.extract_tags(
    text, 
    topK=200, 
    withWeight=True,
    allowPOS=('n', 'vn', 'v', 'ns', 'nr')  # 只保留特定词性
)

# 4. 词频统计
word_counts = {word: weight for word, weight in keywords}

# 5. 生成词云
wc = WordCloud(
    font_path="simhei.ttf",
    width=1000,
    height=700,
    background_color='white',
    max_words=200,
    collocations=False,
    stopwords=stopwords
).generate_from_frequencies(word_counts)

# 6. 显示结果
plt.figure(figsize=(15, 10))
plt.imshow(wc, interpolation="bilinear")
plt.axis("off")

# 7. 保存高频词表
with open("keywords.csv", "w", encoding="utf-8") as f:
    f.write("词语,权重\n")
    for word, weight in sorted(keywords, key=lambda x: x[1], reverse=True):
        f.write(f"{word},{weight}\n")
```

### 2. 微博热点分析案例

python

复制

```python
import pandas as pd

# 读取微博数据
df = pd.read_csv("weibo.csv")

# 合并所有文本
text = " ".join(df["content"].dropna())

# 使用TextRank算法提取关键词
keywords = jieba.analyse.textrank(
    text, 
    topK=100,
    withWeight=True,
    allowPOS=('n', 'vn', 'v')
)

# 生成词云时突出显示热点词
def color_func(word, font_size, position, orientation, random_state=None, **kwargs):
    colors = ["#FF0000", "#FF4500", "#FF8C00", "#FFA500"]  # 红色系表示热度
    return random.choice(colors)

wc = WordCloud(
    font_path="simhei.ttf",
    color_func=color_func,
    background_color="white",
    max_words=100
).generate_from_frequencies(dict(keywords))
```

## 五、常见问题解决

### 1. 分词不准确问题

- **解决方案**：
  - 添加自定义词典 `jieba.add_word()`
  - 调整词典词频 `jieba.suggest_freq()`
  - 使用`jieba.analyse.set_idf_path()`设置专业IDF文件

### 2. 词云显示乱码

- **确保**：
  - 指定了正确的中文字体路径
  - 文件保存时使用UTF-8编码
  - 系统安装了所需字体

### 3. 性能优化技巧

python

复制

```python
# 启用并行分词（适用于大文本）
jieba.enable_parallel(4)  # 参数为并行进程数

# 关闭并行模式
jieba.disable_parallel()
```

## 六、扩展应用

### 1. 结合情感分析

python

复制

```python
from snownlp import SnowNLP

# 对分词结果进行情感分析
sentiments = []
for word in words:
    if word not in stopwords:
        s = SnowNLP(word)
        sentiments.append((word, s.sentiments))

# 筛选积极/消极词汇
positive_words = [w for w, s in sentiments if s > 0.7]
negative_words = [w for w, s in sentiments if s < 0.3]
```

### 2. 主题建模扩展

python

复制

```python
from gensim import corpora, models

# 准备文档-词矩阵
texts = [[word for word in jieba.cut(doc) if word not in stopwords] 
         for doc in document_list]
dictionary = corpora.Dictionary(texts)
corpus = [dictionary.doc2bow(text) for text in texts]

# LDA主题模型
lda = models.LdaModel(corpus, num_topics=5, id2word=dictionary)
lda.print_topics()
```





# 十六、python乌龟

### **1. 移动控制**

- `forward(distance)`: 向前移动指定的距离。
- `backward(distance)`: 向后移动指定的距离。
- `fd(distance)`: 简化版的`forward()`。
- `bk(distance)`: 简化版的`backward()`。
- `goto(x, y)`: 移动到指定的坐标 `(x, y)`。
- `home()`: 返回海龟的初始位置（原点）。
- `circle(radius, extent=None)`: 绘制一个圆，`radius` 是半径，`extent` 是圆的角度（默认完整圆）。
- `setheading(to_angle)`: 设置海龟的朝向角度（0 朝右，90 朝上）。
- `towards(x, y)`: 返回从当前位置到 `(x, y)` 的角度。

### **2. 方向控制**

- `left(angle)`: 向左转指定的角度。
- `right(angle)`: 向右转指定的角度。
- `lt(angle)`: 简化版的`left()`。
- `rt(angle)`: 简化版的`right()`。
- `setheading(angle)`: 设置海龟的朝向为指定角度。

### **3. 笔控制**

- `penup()`: 抬起笔，移动时不绘制。
- `pendown()`: 落下笔，移动时绘制。
- `pu()`: 简化版的`penup()`。
- `pd()`: 简化版的`pendown()`。
- `isdown()`: 检查笔是否落下，返回布尔值。
- `pensize(width)`: 设置线条粗细。
- `pencolor(color)`: 设置线条颜色。
- `fillcolor(color)`: 设置填充颜色。
- `begin_fill()`: 开始填充区域。
- `end_fill()`: 结束填充区域。

### **4. 状态查询**

- `position()`: 返回当前海龟的位置 `(x, y)`。
- `heading()`: 返回当前海龟的朝向角度。
- `distance(x, y)`: 返回海龟到 `(x, y)` 的距离。
- `xcor()`: 返回当前海龟的 x 坐标。
- `ycor()`: 返回当前海龟的 y 坐标。

### **5. 屏幕控制**

- `speed(speed)`: 设置海龟的移动速度（0 最快，10 最慢）。
- `hideturtle()`: 隐藏海龟。
- `showturtle()`: 显示海龟。
- `isvisible()`: 检查海龟是否可见。
- `bgcolor(color)`: 设置背景颜色。
- `title(title)`: 设置窗口标题。
- `setup(width, height)`: 设置窗口大小。
- `tracer(n)`: 控制动画的刷新频率。
- `update()`: 更新屏幕显示（与`tracer()`配合使用）。
- `done()`: 保持窗口打开，直到用户关闭。

### **6. 事件绑定**

- `onclick(func)`: 绑定鼠标点击事件到海龟。
- `onscreenclick(func)`: 绑定鼠标点击事件到屏幕。
- `onkey(func, key)`: 绑定键盘按键事件。
- `listen()`: 启用键盘事件监听。

### **7. 其他功能**

- `stamp()`: 在当前位置留下海龟的印记。
- `clearstamp(stamp_id)`: 清除指定的印记。
- `clearstamps(n=None)`: 清除所有或指定数量的印记。
- `reset()`: 重置海龟到初始状态。
- `clear()`: 清除海龟绘制的内容，但保留位置和状态。
- `write(text, move=False, align="left", font=("Arial", 8, "normal"))`: 在当前位置写入文本。

### **示例代码**

以下是一个综合使用这些函数的示例：

Python

复制

```python
import turtle

t = turtle.Turtle()
screen = turtle.Screen()

# 设置窗口
screen.bgcolor("lightblue")
screen.title("海龟绘图示例")

# 设置海龟
t.speed(1)
t.pensize(3)
t.pencolor("red")
t.fillcolor("blue")

# 绘制一个填充的正方形
t.begin_fill()
for _ in range(4):
    t.forward(100)
    t.left(90)
t.end_fill()

# 绘制一个圆形
t.penup()
t.goto(150, 0)
t.pendown()
t.pencolor("green")
t.circle(50)

# 绑定键盘事件
def move_forward():
    t.forward(20)

def turn_left():
    t.left(30)

screen.onkey(move_forward, "Up")
screen.onkey(turn_left, "Left")
screen.listen()

# 保持窗口打开
turtle.done()
```







