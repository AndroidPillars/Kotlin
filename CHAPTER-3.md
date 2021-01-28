# Object Orientation in Kotlin

- Object-Oriented Programming is a methodology of designing a program using classes, objects, inheritance, polymorphism, abstraction, and encapsulation.

# Classes

- A template (blueprint) for creating objects (the real thing).
- For example, we can take a Mic -> Mic is an object.

__classes Anatomy__

- properties or attributes -> color, name, micType
- Methods -> turnOn, turnOff, setVolume(), mute()
- Objects will have those properties and methods tool (i.e.) It is a basic unit of Object Oriented Programming and represents the real life entities.

```ruby
class Microphone {

}

fun main(args: Array<String>) {

    val mMicrophone = Microphone()

}
```

__Properties with Getters and Setters__

__Example 1__

```ruby
class Microphone {

    var mName: String = ""
    var mModelNo: Int = 0

}

fun main(args: Array<String>) {

    val mMicrophone = Microphone()
    mMicrophone.mName = "Android"
    mMicrophone.mModelNo = 123456

    print(mMicrophone.mName)
    print(mMicrophone.mModelNo)

}
```
__Example 2__

```ruby
class Microphone {

    var mName: String = ""
    get() = field
    set(value) {
        if (value.isNotBlank()){
            field = value
        }
    }
    var mModelNo: Int = 0

}

fun main(args: Array<String>) {

    val mMicrophone = Microphone()
    mMicrophone.mName = "Android"
    mMicrophone.mName = " "
    mMicrophone.mModelNo = 123456

    print(mMicrophone.mName)
    print(mMicrophone.mModelNo)

}
```

__Primary and Secondary Constructors__

__Example 1__

```ruby
class Microphone(mName: String, mModelNo: Int) {

    var name: String
    var modelNo: Int
    
    init {
        name = mName
        modelNo = mModelNo
    }

}
```

- init keyword is executed whenever a new object of the class is created.

```ruby
class Microphone(mName: String, mModelNo: Int) {

    var name: String = mName
    var modelNo: Int = mModelNo

}
```

__Final Code__

```ruby
class Microphone(val name: String, val modelNo: Int) {

    constructor(name: String) :this(name, 0){

    }

}

fun main(args: Array<String>) {

    val mMicrophone = Microphone("Android", 123456)

    print(mMicrophone.name)
    print(mMicrophone.modelNo)

    val mAlteredMicrophone = Microphone("Flutter")

    print(mAlteredMicrophone.name)
    print(mAlteredMicrophone.modelNo)

}
```

__Methods__

```ruby
class Microphone(val name: String, val modelNo: Int) {

    fun getBrand(){
        print("Name: $name, ModelNo: $modelNo")
    }

    fun knowItsName() : Boolean = name.isNotBlank()

}

fun main(args: Array<String>) {

    val mMicrophone = Microphone("Android", 123456)

   if (mMicrophone.knowItsName()){
       mMicrophone.getBrand()
   }

}
```

# Extension Functions

- Kotlin extension function provides a facility to "add" methods to class without inheriting a class or using any type of design pattern. 
- The created extension functions are used as a regular function inside that class.

__Example 1__

```ruby
fun Int.isEven() = (this % 2 == 0)

fun main(args: Array<String>) {

    println(5.isEven())

    val naturals = listOf(2, 5, 11, 3, 8, 2)
    print(naturals.filter { it.isEven() })
    
}
```

__Example 2__

```ruby
class Student{  
    fun isPassed(mark: Int): Boolean{  
        return mark>40  
    }  
}

fun Student.isExcellent(mark: Int): Boolean{  
    return mark > 90  
}  

fun main(args: Array<String>){  
val student = Student()  
val passingStatus = student.isPassed(55)  
println("student passing status is $passingStatus")  
  
val excellentStatus = student.isExcellent(95)  
println("student excellent status is $excellentStatus")  
}  
```

# Data Classes

__Existing in Java__

- While building any application, we often need to create classes whose primary purpose is to hold data/state. 
- These classes generally contain the same old boilerplate code in the form of getters, setters, equals(), hashcode() and toString() methods.

__In Kotlin__

- Kotlin has a better solution for classes that are used to hold data/state and it’s called a Data Class. 
- A Data Class is like a regular class but with some additional functionalities.
- The compiler automatically derives the following functions : equals(), hashCode(), toString(), copy()

__Rules to create Data classes__

- The primary constructor needs to have at least one parameter.
- All primary constructor parameters need to be marked as val or var.
- Data classes cannot be abstract, open, sealed or inner.
- Data classes may only implement interfaces.

```ruby
// Generates hashCode(), equals(), toString(), copy(), destructuring operator
data class Microphone(var name: String, var modelNo: Int) {

}

fun main(args: Array<String>) {

    val mMicrophone = Microphone("Android", 123456)
    val mMicrophoneOne = Microphone("Android", 123456)

    // to String
    println(mMicrophone)

    // equals
    println(mMicrophone == mMicrophoneOne)

    // Referential equality
    println(mMicrophone.name === mMicrophoneOne.name)

    // Copy
    val mValue1 = mMicrophone
    println(mValue1)
    val mValue2 = mMicrophone.copy(modelNo = 65)
    println(mValue2)
    
    // Destructuring declaration
    val (name, number) = mMicrophone
    println("$name, $number")

    // Components
    println("Component1 ${mMicrophone.component1()}")
    println("Component2 ${mMicrophone.component2()}")
    
}
```

# Enums

- While developing an application, there may arise a situation where we want a variable to have a value out of a given set of allowed values only.
- for example, if we have a variable DressSize, then it should have following values: small, medium and large.
- In Kotlin, and in Java too, Enums help us achieve this.
- In Kotlin we can create an enum class with the help of enum keyword. 
- Kotlin enums can have properties, functions, can implement interfaces, etc.
- The enum data type (also known as Enumerated Data Type) is used to define an enum in Kotlin.

```ruby
enum class Days{
    SUNDAY, MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY
}

enum class Direction(val degree: Double){
    NORTH(0.0), EAST(90.0), SOUTH(180.0), WEST(270.0)
}

interface DoGender{
    fun doGender()
}

enum class Gender(val mResult: String): DoGender{
    MALE("Male"){
        override fun doGender() {
            print("Male Child")
        }
    }
}

fun main(args: Array<String>) {

    val mWorkingDays = when(Days.MONDAY){
        Days.MONDAY, Days.TUESDAY -> "Working Day"
        Days.WEDNESDAY, Days.THURSDAY, Days.FRIDAY -> "Working Day"
        Days.SATURDAY, Days.SUNDAY -> "Holiday"
    }

    println(mWorkingDays)

    println(Direction.EAST.degree)

    Gender.MALE.doGender()
}
```

# Inheritance

- Inheritance is one of the key concepts of Object Oriented Programming (OOP). 
- Inheritance enables re-usability. 
- It allows a class to inherit features (properties and methods) from another class.
- By default, all the classes in Kotlin are final (non-inheritable).
- To allow a class to be inherited by others, you must mark it with the open modifier.

```ruby
open class Shape(val name: String) {

    open fun area() = 0.0
}


class Circle(name: String, val radius: Double) : Shape(name) {

    override fun area() = Math.PI* radius.pow(2.0)
}

fun main(args: Array<String>) {

    val mSmallCircle = Circle("Large Circe", 14.0)

    println(mSmallCircle.name)
    println(mSmallCircle.radius)
    println(mSmallCircle.area())

}
```

# Abstract Classes

- A class which is declared with the abstract keyword is known as an abstract class in Java.
- It can have abstract and non-abstract methods (method with the body).
- Abstraction is a process of hiding the implementation details and showing only functionality to the user.
- There are two ways to achieve abstraction in java   
    1.Abstract class (0 to 100%)  
    2.Interface (100%)  
    
__Points to get Remember__

- If a class has an abstract property or abstract function, then class must be marked as abstract.
- An abstract class cannot be instantiated. It means we cannot create object of an abstract class.
- There is no need to add open keyword in abstract classes as they are meant to be inherited and hence by default open.
- An abstract can have both abstract and non-abstract (normally defined) functions and properties.
- An abstract function does not have body.
- In abstract class, by default all members are non-abstract. We need to add abstract keyword to make them abstract.

```ruby
abstract class Shape() {

    abstract var sides: Int
    abstract fun area(): Double

    fun sayShape() {
        println("It is a shape...")
    }
}

class Square(name: String, val radius: Double) : Shape() {
    override var sides: Int = 4
    override fun area() = Math.PI * radius.pow(2.0)
}

class Circle(name: String, val radius: Double) : Shape() {
    override var sides: Int = 0
    override fun area() = Math.PI * radius.pow(2.0)
}

fun main(args: Array<String>) {
    val square = Square("Square", 10.0)
    val circle = Circle("Circle", 100.0)
    println("Side of square: ${square.sides}")
    println("Side of Circle: ${circle.sides}")
    println(square.area())
    println(circle.area())
    square.sayShape()
    circle.sayShape()
}
```

# Interfaces

- An Interface can be considered as a fully abstract class. 
- It means by default all functions and properties of an interface are abstract.
- An interface in Kotlin is a blueprint of a class and is a mechanism to achieve abstraction.
- It is used to achieve abstraction and multiple inheritance in Java.
- Interfaces can have abstract methods and variables.

```ruby
interface A {
    fun sayHelloByA()
    fun sayByeByA() {
        println("Bye from A....")
    }
}

interface B {
    fun sayHelloByB()
    fun sayByeByB() {
        println("Bye from B....")
    }
}

class MainClass : A, B {
    override fun sayHelloByA() {
        println("Hello from overridden A....")
    }

    override fun sayHelloByB() {
        println("Hello from overridden B....")
    }
}

fun main(args: Array<String>) {
    val mainClass = MainClass()
    mainClass.sayHelloByA()
    mainClass.sayHelloByB()
    mainClass.sayByeByA()
    mainClass.sayByeByB()
}
```
