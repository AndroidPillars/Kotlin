
# Kotlin

## What is Kotlin?

- Kotlin is an open-source statically typed programming language. 
- It runs on JVM and can be used anywhere Java is used today. 
- It can be used to develop Android apps, server-side apps and much more.
- Kotlin was developed by JetBrains team.
- The project was started in 2010 to develop the language and officially, first released in February 2016. 
- Kotlin was developed under the Apache 2.0 license.

## Installation

- Install the Java JDK using this link https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html
- Install the Android Studio using this link https://developer.android.com/studio/install

## Kotlin Editor

- Kotlin REPL (Read Evaluate Print Loop) -> It's like a console that allows you to write expressions.
- To Enable -> Tools -> Kotlin -> Kotlin REPL

## Kotlin Data Type

- Data type refers to type and size of data associated with variables and functions.

__Variable__

- Variable refers to a memory location. 
- It is used to store data. 
- The data of variable can be changed and reused depending on condition or on information passed to the program.
- Kotlin is a statically typed language, which makes it different from the dynamically typed JavaScript.
- We don't require specifying the type of variable explicitly.
```ruby
var name ="Android"  
val age = 10  
```
- We can also explicitly specify the type of variable while declaring it.
```ruby
var name: String ="Android"  
val age: Int = 10
```
- var (Mutable variable) -> We can change the value of variable declared using var keyword later in the program.
- val (Immutable variable) -> We cannot change the value of variable which is declared using val keyword.

## Null Safety

- Kotlin's type system is aimed at eliminating the danger of null references from code.
- Types -> Nullable Types and Non-Nullable Types

__Nullable Types__

- Nullable types are declared by putting a ? behind the String.

```ruby
var name: String? = "Android"  
name = null
```

__Non Nullable Types__

- Non nullable types are normal strings which are declared as String.

```ruby
val name: String = null // compile error  
```

__Null checks(!!)__

- The null check operator !! is used to inform the compiler that the property or variable is null or not. 
- If it is null then it will throw some NullPointerException.

```ruby
studentA!!.giveGoodies() //works fine if studentA is not null
```

__Safe call (?.)__

- In the below example, If any of the value is null i.e. if either of studentA, courseName, instructor is null then the whole expression will return null.

```ruby
studentA?.courseName?.instructor?.name 
```

__Safe call (?.) vs Null checks(!!)__

- The basic difference between the Safe call and Null check is that we use Null checks (!!) only when we are confident that the property can’t have a null value. 
- If we are not sure that the value of the property is null or not then we prefer to use Safe calls(?.).

__Elvis Operator (?:)__

- Elvis operator (?:) is used to return the not null value even the conditional expression is null. 
- It is also used to check the null safety of values.

```ruby
var name: String? = null  
var company: String? = "May be declare nullable string"  
var nameLength:  Int = name ?.length ?: -1  
var companyLength:  Int = company ?.length ?:  -1  
```

## Kotlin Operators

__Kotlin if Expression__

- In Kotlin, if is an expression is which returns a value.

```ruby
 val num1 = 10  
 val num2 =20  
 val result = if (num1 > num2) {  
      "$num1 is greater than $num2"  
 } else {  
      "$num1 is smaller than $num2"  
 }  
 println(result)  
```

__Kotlin when Expression__

- Kotlin, when expression is a conditional expression which returns the value and it is the replacement of switch statement.

```ruby
var number = 4
when(number) {
    1 -> println("One")
    2 -> {
        println("Two")
        println("Two-Two")
    }
    4, 8, 9 -> println("Three")
    in 1..5 -> println("Four")
    5 + 6 -> println("Five")
    !in 1..5 -> println("Five")
    else -> println("invalid number")
} 
```

__Kotlin for Loop Expression__

- The for loop in Kotlin iterates through anything that provides an iterator.

```ruby
for (i in 1..10){
     print("$i ")
 }
```

```ruby
val languages = arrayOf("Android","Kotlin","Flutter")
 for(lang in languages){
     println(lang + ",")
 }
```

```ruby
for (i in 10 downTo 1){
     print("$i ")
 }
```

```ruby
for (i in 10 downTo 1 step 2){
     print("$i ")
 }
```

__Kotlin while Loop Expression__

- The while loop is used to iterate a part of program several time.

```ruby
var i = 1
 while (i<=10){
     println("$i ")
     i++
 }
```

__Kotlin do-while Loop__

- The do-while loop is similar to while loop except one key difference. 
- A do-while loop first execute the body of do block after that it check the condition of while.

```ruby
var i = 1
 do {
     println("$i ")
     i++
 }
 while (i<=20)
```

## Kotlin Collections

- Collections in Kotlin are used to store group of related objects in a single unit. 
- By using collection, we can store, retrieve manipulate and aggregate data.
- Two Types -> Immutable Collection and Mutable Collection

__Immutable Collection__

- Immutable collection also called Collection supports read only functionalities.

```ruby
List<int>
```

__Mutable Collection__

- Mutable collections supports both read and write functionalities. 

```ruby
MutableList<int>
```

__Examples__

```ruby
val array = arrayOf(2, 3, 4, 5)
 array.joinToString()
```

```ruby
val array = intArrayOf(2, 3, 4, 5)
 array.joinToString()
```

```ruby
val array = listOf(2, 3, 4, 5)
 array.joinToString()
```

```ruby
val array = mutableListOf(2, 3, 4, 5)
 array[0] = 1
 array
```

```ruby
val array = setOf(2, 2, 3, 4, 5)
 array
```

```ruby
val array = mutableSetOf(2, 2, 3, 4, 5)
 array
```

```ruby
val map = mapOf(Pair(1, "Android"), Pair(2, "Kotlin"))
 map
```

```ruby
val map = mutableMapOf(1 to "Android", 2 to "Kotlin")
 map
```
