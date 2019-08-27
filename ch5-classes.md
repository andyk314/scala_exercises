# Chapter 5: Classes

1. Improve the Counter class in Section 5.1, “Simple Classes and Parameterless Methods,” on page 55 so that it doesn’t turn negative at Int.MaxValue.
    ```
      class Counter {
        private var value = 0
        def increment() = { if (value == Int.MaxValue) value else value += 1 }
        def current =  value
      }
    ```

2. Write a class BankAccount with methods deposit and withdraw, and a read-only property balance.
    ```
      class BankAccount {
        private var balance : Float = 0
        def deposit(amount: Float) = { balance += amount }
        def withdrawal(amount: Float) = { balance -= amount }
        def current = balance
      }
    ```

3. Write a class Time with read-only properties hours and minutes and a method before(other: Time): Boolean that checks whether this time comes before the other. A Time object should be constructed as new Time(hrs, min), where hrs is in military time format (between 0 and 23).
    ```
      class Time(private val _hours:Int, private val _minutes:Int) {
        def hours = _hours
        def minutes = _minutes
        def before(other: Time) : Boolean = {
          _hours < other.hours || _hours == other.hours && _minutes < other.minutes 
        }
      }
    ```

4. Reimplement the Time class from the preceding exercise so that the internal representation is the number of minutes since midnight (between 0 and 24 × 60 – 1). Do not change the public interface. That is, client code should be unaffected by your change.
  ```
      class Time(private val _hours:Int, private val _minutes:Int) {
        def hours = _hours
        def minutes = _minutes
        def timeByMinutes = _hours * 60 + _minutes
        def before(other: Time) : Boolean = {
           timeByMinutes <  other.timeByMinutes
        }
      }
  ```

5. Make a class Student with read-write JavaBeans properties name (of type String) and id (of type Long). What methods are generated? (Use javap to check.) Can you call the JavaBeans getters and setters in Scala? Should you?
    ```
      import scala.beans.BeanProperty
      class Student(@BeanProperty var name:String, @BeanProperty var id:Long) {
      }

      :javap Student =>
        public class Student {
          public java.lang.String name();
          public void name_$eq(java.lang.String);
          public long id();
          public void id_$eq(long);
          public long getId();
          public java.lang.String getName();
          public void setId(long);
          public void setName(java.lang.String);
          public Student(java.lang.String, long);
        }
    ```

6. In the Person class of Section 5.2, “Properties with Getters and Setters,” on page 56, provide a primary constructor that turns negative ages to 0.
    ```
      class Person(private var privateAge:Int) {
        def age = if (privateAge < 0) 0 else privateAge
        def age_=(newValue:Int) = {
          privateAge = newValue
        }
      }
    ```

7. Write a class Person with a primary constructor that accepts a string containing a first name, a space, and a last name, such as new Person("Fred Smith"). Supply read-only properties firstName and lastName. Should the primary constructor parameter be a var, a val, or a plain parameter? Why?
    ```
      class Person(fullName:String ) {
        private val splitName = fullName.split(" ")
        def firstName = splitName.head
        def lastName = splitName.last
      }
      The primary constructor paramter should be a plain paramter since the parameter does not require a setter/getter.
    ```

8. Make a class Car with read-only properties for manufacturer, model name, and model year, and a read-write property for the license plate. Supply four constructors. All require the manufacturer and model name. Optionally, model year and license plate can also be specified in the constructor. If not, the model year is set to -1 and the license plate to the empty string. Which constructor are you choosing as the primary constructor? Why?
    ```
      class Car(val manufacturer:String, val modelName:String) {
        private var _modelYear:Int = -1
        var licensePlate:String = ""

        def this(manufacturer:String, modelName:String, licensePlate:String ) = {
          this(manufacturer, modelName)
          this.licensePlate = licensePlate
        }

        def this(manufacturer:String, modelName:String, modelYear:Int) = {
          this(manufacturer, modelName)
          this._modelYear = modelYear
        }

        def this(manufacturer:String, modelName:String, licensePlate:String, modelYear:Int) = {
          this(manufacturer, modelName)
          this._modelYear = modelYear
          this.licensePlate = licensePlate
        }
      }
    ```

9. Reimplement the class of the preceding exercise in Java, C#, or C++ (your choice). How much shorter is the Scala class?

10. Consider the class
class Employee(val name: String, var salary: Double) { def this() { this("John Q. Public", 0.0) }
} Rewrite it to use explicit fields and a default primary constructor. Which form do you prefer? Why?
    ```
      class Employee(val name: String = "John Q. Public", var salary: Double = 0.0) {}
    ```
