# Chapter 4: Maps and Tuples

1. Set up a map of prices for a number of gizmos that you covet. Then produce a second map with the same keys and the prices at a 10 percent discount.
    ```
      val gizmos = Map("iphone" -> 1000, "tesla" -> 50000, "macbook" -> 2000)
      val discountedGizmos = for ((k, v) <- gizmos) yield (k, v * .9)
    ```

2. Write a program that reads words from a file. Use a mutable map to count how often each word appears. To read the words, simply use a java.util.Scanner:
val in = new java.util.Scanner(new java.io.File("myfile.txt"))
while (in.hasNext()) process in.next()
Or look at Chapter 9 for a Scalaesque way.
At the end, print out all words and their counts.
    ```
      val words = collection.mutable.Map[String, Int]()
      val in = new java.util.Scanner(new java.io.File("myfile.txt"))
      while (in.hasNext()) {
        var current = in.next()
        words(current) = words.getOrElse(current, 0) + 1
      }
      println(words)
    ```

3. Repeat the preceding exercise with an immutable map.
    ```
      var words = Map[String, Int]()
      val in = new java.util.Scanner(new java.io.File("myfile.txt"))
      while (in.hasNext()) {
        var current = in.next()
        println(current)
        words(current)
      }
      println(words)
    ```

4. Repeat the preceding exercise with a sorted map, so that the words are printed in sorted order.
    ```
      var bb = scala.collection.mutable.SortedMap[String, Int]()
      val in = new java.util.Scanner(new java.io.File("myfile.txt"))
      while (in.hasNext()) {
        val current = in.next()
        bb += (current -> current.size)
      }
    ```
5. Repeat the preceding exercise with a java.util.TreeMap that you adapt to the Scala API.

6. Define a linked hash map that maps "Monday" to java.util.Calendar.MONDAY, and similarly for the other weekdays. Demonstrate that the elements are visited in insertion order.
    ```
      val days = scala.collection.mutable.LinkedHashMap(
        "MONDAY" -> java.util.Calendar.MONDAY,
        "TUESDAY" -> java.util.Calendar.TUESDAY,
        "WEDNESDAY" -> java.util.Calendar.WEDNESDAY,
        "THURSDAY" -> java.util.Calendar.THURSDAY,
        "FRIDAY" -> java.util.Calendar.FRIDAY,
        "SATURDAY" -> java.util.Calendar.SATURDAY,
        "SUNDAY" -> java.util.Calendar.SUNDAY
      )
    ```

7. Print a table of all Java properties, like this:
You need to find the length of the longest key before you can print the table.
    ```
    import scala.collection.JavaConverters._
    import java.lang.System

    val properties = System.getProperties.asScala
    val maxKey = properties.keys.maxBy(p => p.length).length
    for((k, v) <- properties) println(k + " " * (maxKey - k.length) +  "|  " + v)
    ```

8. Write a function minmax(values: Array[Int]) that returns a pair containing the smallest and largest values in the array.

    ` def minmax(values: Array[Int]) = (values.min, values.max)`

9. Write a function lteqgt(values: Array[Int], v: Int) that returns a triple containing the counts of values less than v, equal to v, and greater than v.
    ```
      def lteqgt(values: Array[Int], v: Int) = {
        (
          values.count(_ < v),
          values.count(_ == v),
          values.count(_ > v)
        )
      }
    ```

10. What happens when you zip together two strings, such as "Hello".zip("World")? Come up with a plausible use case.
    ```
      "Hello".zip("World") = Array((H,W), (e,o), (l,r), (l,l), (o,d))
    ```
    Allows you to bundle or merge two sets of data together so that they can be processed together.

