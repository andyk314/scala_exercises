# Chapter 6: Objects

1. Write an object Conversions with methods inchesToCentimeters, gallonsToLiters, and milesToKilometers.
    ```
      class Conversions {
        def inchesToCentimeters(inches:Double): Double = { inches * 2.54 }
        def gallonsToLiters(gallons:Double): Double = { gallons * 3.78541 }
        def milesToKilometers(miles:Double): Double = { miles * 1.60934 }
      }
    ```

2. The preceding problem wasn’t very object-oriented. Provide a general super- class UnitConversion and define objects InchesToCentimeters, GallonsToLiters, and MilesToKilometers that extend it.
    ```
      abstract class UnitConversion {
        def convert(value: Double): Double
      }

      object InchesToCentimeters extends UnitConversion {
        override def convert(value: Double) = { value * 2.54 }
      }

      object GallonsToLiters extends UnitConversion {
        override def convert(value: Double) = { value * 3.78541 }
      }

      object MilesToKilometers extends UnitConversion {
        override def convert(value: Double) = { value * 1.60934}
      }
    ```

3. Define an Origin object that extends java.awt.Point. Why is this not actually a good idea? (Have a close look at the methods of the Point class.)
    ```
      object Origin extends java.awt.Point {}
    ```

4. Define a Point class with a companion object so that you can construct Point instances as Point(3, 4), without using new.
    ```
      class Point(val x:Int, val y:Int) {}

      object Point {
        def apply(x:Int, y:Int) = new Point(x, y)
      }
    ```

5. Write a Scala application, using the App trait, that prints the command-line arguments in reverse order, separated by spaces. For example, scala Reverse Hello World should print World Hello.
    ```
      object Reverse extends App {
        if (args.length > 0) args.reverse.makeString(" ")
    ```

6. Write an enumeration describing the four playing card suits so that the toString method returns ♣, ♦, ♥, or ♠.
    ```
      object Card extends Enumeration {
        type Card = Value
        val Club = Value("♣")
        val Diamond = Value("♦")
        val Heart = Value("♥")
        val Spade = Value("♠")
      }

      for (c <- Card.values) println(c)
    ```

7. Implement a function that checks whether a card suit value from the preceding exercise is red.
    ```
      import Card._

      def isRed(cardValue:Card): Boolean = {
        (cardValue == Heart || cardValue == Diamond)
      }

      isRed(Diamond) = true
      isRed(Spade) = false
    ```

8. Write an enumeration describing the eight corners of the RGB color cube. As IDs, use the color values (for example, 0xff0000 for Red).
    ```
      object Cube extends Enumeration {
        val Red = Value(0xff0000)
        val Green = Value(0x00ff00)
        val Blue = Value(0x0000ff)
        val Yellow = Value(0xffff00)
        val Magenta = Value(0xff00ff)
        val Cyan = Value(0x00ffff)
        val Black = Value(0x000000)
        val White = Value(0xffffff) 
      }
    ```