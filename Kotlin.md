# Kotlin语法知识点大全

## 基础语法

### 入口函数

Kotlin 应用程序的入口点是 `main` 函数：

```kotlin
fun main() {
    println("Hello world!")
}
```

### 打印函数

1. `print` 将其参数在控制台打印
2. `println` 输出其参数并添加换行符，一次占据一整行

```kotlin
fun main() {
//sampleStart
    println("Hello world!")
    println(42)
//sampleEnd
}
```

## 初级语法

### 类型

在 Kotlin 中，所有东西都是对象，所以，可以调用任何变量的成员函数与属性。

```kotlin
val one = 1 // Int
val threeBillion = 3000000000 // Long
val oneLong = 1L // Long
val oneByte: Byte = 1

val pi = 3.14 // Double
// val one: Double = 1 // 错误：类型不匹配
val oneDouble = 1.0 // Double
val e = 2.7182818284 // Double
val eFloat = 2.7182818284f // Float，实际值为 2.7182817

val myTrue: Boolean = true

 val aChar: Char = 'a'
val str = "abcd"

var riversArray = arrayOf("Nile", "Amazon", "Yangtze")

 val numbers = mutableListOf("one", "two", "three", "four")
 numbers.add("five")  
```

所有数字类型都支持转换为其他类型：

- `toByte(): Byte`
- `toShort(): Short`
- `toInt(): Int`
- `toLong(): Long`
- `toFloat(): Float`
- `toDouble(): Double`

1. 字符用 `Char` 类型表示。 字符字面值用单引号括起来: `'1'`
2. 字符串值是双引号（`"`）中的字符序列
3. 数组是一种保存固定数量相同类型或其子类型的值的数据结构。 Kotlin 中最常见的数组类型是对象类型数组，由 [`Array`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-array/) 类表示。
4. 与数组相比，集合具有以下优点：
5. - 集合可以是只读的，这提供了更多的控制权而支持编写具有明确意图的健壮代码。
   - 易于对集合增删元素。相比之下，数组大小是固定的。 对数组增删元素的唯一方式是每次创建一个新数组，效率很低
   - 可以使用相等操作符（`==`）来检验两个集合是否在结构上相等。但不能对数组使用这个操作符。 相反
6. 以下是 Kotlin 相关的集合类型：
   - *List* 是一个有序集合，可通过索引（反映元素位置的整数）访问元素。 元素可以在 list 中出现多次。列表的一个示例是电话号码：有一组数字、这些数字的顺序很重要并且数字可以重复。
   - *Set* 是唯一元素的集合。它反映了集合（set）的数学抽象：一组无重复的对象。一般来说 set 中元素的顺序并不重要。例如，the numbers on lottery tickets form a set: they are unique, and their order is not important.
   - *Map*（或者*字典*）是一组键值对。键是唯一的，每个键都刚好映射到一个值。 值可以重复。map 对于存储对象之间的逻辑连接非常有用，例如，员工的 ID 与员工的位置。

<table>
<thead>
<tr>
<th>类型</th>
<th>大小（比特数）</th>
<th>最小值</th>
<th>最大值</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>Byte</code></td>
<td>8</td>
<td>-128</td>
<td>127</td>
</tr>
<tr>
<td><code>Short</code></td>
<td>16</td>
<td>-32768</td>
<td>32767</td>
</tr>
<tr>
<td><code>Int</code></td>
<td>32</td>
<td>-2,147,483,648 (-2<sup>31</sup>)</td>
<td>2,147,483,647 (2<sup>31</sup> - 1)</td>
</tr>
<tr>
<td><code>Long</code></td>
<td>64</td>
<td>-9,223,372,036,854,775,808 (-2<sup>63</sup>)</td>
<td>9,223,372,036,854,775,807 (2<sup>63</sup> - 1)</td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr>
<th>类型</th>
<th>大小（比特数）</th>
<th>有效数字比特数</th>
<th>指数比特数</th>
<th>十进制位数</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>Float</code></td>
<td>32</td>
<td>24</td>
<td>8</td>
<td>6-7</td>
</tr>
<tr>
<td><code>Double</code></td>
<td>64</td>
<td>53</td>
<td>11</td>
<td>15-16</td>
</tr>
</tbody>
</table>

### 流程控制

```kotlin
if (a > b) {
      max = a
    } else {
      max = b
    }

when (x) {
    1 -> print("x == 1")
    2 -> print("x == 2")
    else -> {
        print("x is neither 1 nor 2")
    }
}

for (item: Int in ints) {
    // ……
}
for (i in 1..3) {
        println(i)
    }
for (i in 6 downTo 0 step 2) {
        println(i)
    }

while (x > 0) {
    x--
}

do {
  val y = retrieveData()
} while (y != null) // y 在此处可见

try {
    // 一些代码
} catch (e: SomeException) {
    // 处理程序
} finally {
    // 可选的 finally 块
}
```



1. 在 Kotlin 中，`if` 是一个表达式：它会返回一个值。 因此就不需要三元运算符（`条件 ? 然后 : 否则`），因为普通的 `if` 就能胜任这个角色
2. `when` 将它的参数与所有的分支条件顺序比较，直到某个分支满足条件。相当于Java的switch
3. `while` 和 `do-while` 当循环条件满足时会持续执行它们的主体。 它们之间的区别在于条件检查的时间
4. 使用 `throw` 表达式来抛出异常

### 面向对象

```kotlin
//类
//在 Kotlin 中的一个类有一个主构造函数并可能有一个或多个次构造函数。主构造函数在类头中声明，它跟在类名与可选的类型参数后。
class InitOrderDemo(name: String) {
    val firstProperty = "First property: $name".also(::println)

    init {
        println("First initializer block that prints $name")
    }

    val secondProperty = "Second property: ${name.length}".also(::println)

    init {
        println("Second initializer block that prints ${name.length}")
    }
}
```

