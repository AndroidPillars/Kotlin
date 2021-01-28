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

- We often create classes to hold some data in it. 
- In such classes, some standard functions are often derivable from the data. 
- In Kotlin, this type of class is known as data class and is marked as data.
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
    print(mMicrophone)

    // Referential equality
    print(mMicrophone === mMicrophoneOne)

    // Structural equality
    print(mMicrophone == mMicrophoneOne)

    // Copy
    val mValue = mMicrophone.copy(modelNo = 65)
    print(mValue)

    // Destructuring Operator
    mMicrophone.component1()
    val (name, number) = mMicrophone
    print("$name, $number")

}
```
