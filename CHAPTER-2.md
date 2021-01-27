# Kotlin Functions

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
