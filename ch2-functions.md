# Chapter 2: Control Structures and Functions

1. The signum of a number is 1 if the number is positive, –1 if it is negative, and 0 if it is zero. Write a function that computes this value.
    ```
      if (number > 0) 1
      else if (number == 0) 0 else -1
    ```

2. What is the value of an empty block expression {}? What is its type?

    `Empty block express return (), or a Unit Type`

3. Come up with one situation where the assignment x = y = 1 is valid in Scala.
(Hint: Pick a suitable type for x.)
    ```
      var y = 0
      var x: Unit = y = 1
    ```

4. Write a Scala equivalent for the Java loop
for (int i = 10; i >= 0; i--) System.out.println(i);
    ```
      var i = 10
      while (i >= 0) {
        println(i)
        i -= 1
      }
    ```

5. Write a procedure countdown(n: Int) that prints the numbers from n to 0.
    ```
      def countdown(n: Int) {
        while (n >= 0) { println(n); n -= 1 }
      }
    ```

6. Write a for loop for computing the product of the Unicode codes of all letters in a string. For example, the product of the characters in "Hello" is 9415087488L.
    ```
      var product : Long = 1
      for (ch <- "Hello) product *= ch.toLong
    ```
    
7. Solve the preceding exercise without writing a loop. (Hint: Look at the StringOps Scaladoc.)
    ```
      "Hello".map(ch => ch.toLong).product
    ```

8. Write a function product(s : String) that computes the product, as described in the preceding exercises.
    ```
      def product(s: String) = s.map(ch => ch.toLong).product
    ```
9. Make the function of the preceding exercise a recursive function.
    ```
      def product(s: String): Long = {
        if (s.tail == "") s.head.toLong
        else s.head.toLong * product(s.tail)
      }
    ```

10. Write a function that computes x^n, where n is an integer. Use the following recursive definition:
• xn = y · y if n is even and positive, where y = xn / 2.
• xn = x · xn – 1 if n is odd and positive. • x0 = 1.
• xn = 1 / x–n if n is negative.
Don’t use a return statement.
    ```
      import scala.math.pow
      def compute(x: Double, n: Int): Double = {
        if (n > 0 && n % 2 == 0) pow(pow(x, n/2), 2)
        else if (n > 0 && n % 2 != 0) x * pow(x, n-1)
        else if (n < 0) 1 / pow(x, -n)
        else 1
      }
    ```
