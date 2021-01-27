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
