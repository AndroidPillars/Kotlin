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

# Properties with Getters and Setters

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
