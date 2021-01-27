# Kotlin Functions

- Function is a group of inter related block of code which performs a specific task. 
- Function is used to break a program into different sub module. 
- It makes reusability of code and makes program more manageable.
- In Kotlin, functions are declared using fun keyword.

```ruby
fun PermitEnterance(age: Int): Boolean {
    return age >= 18
}

PermitEnterance(21)
```

```ruby
fun PermitEnterance(age: Int): Boolean = age >= 18
```

```ruby
fun PermitEnterance(age: Int): Boolean = age >= 18

val mValue = PermitEnterance(19)

mValue
```

```ruby
fun PermitEnterance(vararg ages: Int): Boolean { 
    return ages.any {
        age -> age >= 18
    }
} 

val mValue = PermitEnterance(19, 45, 12)

mValue
```

# Kotlin Default and Named Argument

__Kotlin Default Argument__

- Kotlin provides a facility to assign default argument (parameter) in a function definition.
- If a function is called without passing any argument than default argument are used as parameter of function definition and when a function is called using argument, than the passing argument is used as parameter in function definition.

```ruby
fun main(args: Array<String>){
    run()
}

fun run(num: Int= 5, latter: Char ='x'){
    print("$num and $latter")
}
```

```ruby
fun main(args: Array<String>) {  
    run(3)  
}  

fun run(num:Int= 5, latter: Char ='x'){  
    print("$num and $latter")  
}  
```

__Kotlin Named Argument__

- A named argument is an argument in which we define the name of argument in the function call. 
- The name defined to argument of function call checks the name in the function definition and assign to it.

```ruby
fun main(args: Array<String>) {
    run(mText='a')
}

fun run(num:Int= 5, mText: Char ='x'){
    print("parameter in function definition $num and $mText")
} 
```

# Kotlin Lambdas

- Lambdas Expressions are essentially anonymous functions that we can treat as values.
- Lambda is a function which has no name. 
- Lambda is defined with a curly braces {} which takes variable as a parameter (if any) and body of function. 
- The body of function is written after variable (if any) followed by -> operator.

__syntax__
```ruby
{ variable -> body_of_function}  
```

__Normal Function__
```ruby
fun main(args: Array<String>){  
    addNumber(15,10)  
}  
fun addNumber(a: Int, b: Int){  
    val add = a + b  
    println(add)  
} 
```

__Using Lambdas__

```ruby
val greeting = { println("Hello World!")}

    greeting()
```

```ruby
val multiply =  { x: Int -> x * 2 }
   val result =  multiply(4)
    print(result)
```
```ruby
val product = { a: Int, b: Int -> a * b }
   val result = product(9, 3)
    println(result)
```

```ruby
val add: (Int, Int) -> Int = {
        x : Int, y : Int -> x + y
    }
    val result =  add(4, 5)
    print(result)
```

# Kotlin Higher Order Functions

- High order function (Higher level function) is a function which accepts function as a parameter or returns a function or can do both. 
- (i.e.) instead of passing Int, String, or other types as a parameter in a function we can pass a function as a parameter in other function.

```ruby
fun main(args: Array<String>) {
    val functionMethod:(String,String) -> String = {org, portal->"$org develop $portal"}
    functionMethod("android.org","android_pillars.com", functionMethod)
}

fun functionMethod(org: String,portal: String, fn: (String,String) -> String): Unit {
    val result = fn(org,portal)
    println(result)
}
```

```ruby
fun main(args: Array<String>) {

    var list = (1..100).toList()

    print(list.filter { element -> element % 2 == 0 })

    print(list.filter { it % 2 == 0 })

    print(list.filter { it.even() })

    print(list.filter ( ::isEven ))
}

fun isEven(i: Int) = i % 2 == 0

fun Int.even() = this % 2 == 0
```

# Exception Handling

- The Exception Handling in Java is one of the powerful technique to handle the runtime errors so that normal flow of the application can be maintained.
- In other words, Exception Handling is a mechanism to handle runtime errors such as ClassNotFoundException, IOException, SQLException, RemoteException, etc.
- In Kotlin, all exception classes are descendants of class Throwable.
- four keyword Types -> try, catch, finally and throw
- Types -> Checked Exception, Unchecked Exception and Errors

__Checked Exception__

- Checked exception is checked at compile time. 
- This exception type extends the Throwable class.
- Example: IOException, SQLException, FileNotFoundException, ClassNotFoundException etc.

```ruby
throw MyException("this throws an exception")  
```

```ruby
fun main(args: Array<String>) {
    val input = getExternalInput()
    print(input)
}

fun getExternalInput(): String{
    throw IOException("Not able to read external input")
}
```

__Unchecked Exception__

- The classes which inherit RuntimeException are known as unchecked exceptions.
- Unchecked exceptions are not checked at compile-time, but they are checked at runtime.
- Example:  ArithmeticException, NullPointerException, ArrayIndexOutOfBoundsException etc.

```ruby
fun main(args: Array<String>) {
    val input = try {
         getExternalInput()
    } catch (e: IOException){
        e.printStackTrace()
        ""
    } finally {
        print("Finish processing")
    }
    print(input)
}

fun getExternalInput(): String{
    throw IOException("Not able to read external input")
}
```

__Error__

- Error is irrecoverable.
- Example: OutOfMemoryError, VirtualMachineError, AssertionError etc.

