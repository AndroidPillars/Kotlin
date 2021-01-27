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
