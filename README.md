# Kotlin

- Kotlin is an open-source statically typed programming language. 
- It runs on JVM and can be used anywhere Java is used today. 
- It can be used to develop Android apps, server-side apps and much more.
- Kotlin was developed by JetBrains team.
- The project was started in 2010 to develop the language and officially, first released in February 2016. 
- Kotlin was developed under the Apache 2.0 license.

# Installation

- Install the Java JDK using this link https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html
- Install the Android Studio using this link https://developer.android.com/studio/install

# Kotlin Editor

- Kotlin REPL (Read Evaluate Print Loop) -> It's like a console that allows you to write expressions.
- To Enable -> Tools -> Kotlin -> Kotlin REPL

# Kotlin Data Type

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

# Null Safety

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

- The basic difference between the Safe call and Null check is that we use Null checks (!!) only when we are confident that the property can’t have a null value. 
- If we are not sure that the value of the property is null or not then we prefer to use Safe calls(?.).


