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
