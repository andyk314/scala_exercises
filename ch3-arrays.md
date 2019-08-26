# Chapter 3: Arrays

1. Write a code snippet that sets a to an array of n random integers between 0 (inclusive) and n (exclusive).
    ```
      import util.Random
      def rand(n: Integer) = for (i <- 0 until n) yield Random.nextInt(n)
    ```

2. Write a loop that swaps adjacent elements of an array of integers. For example, Array(1, 2, 3, 4, 5) becomes Array(2, 1, 4, 3, 5).
    ```
      import collection.mutable.ArrayBuffer
      val a = Array(1, 2, 3, 4, 5)
      val result = ArrayBuffer[Int]()
      for (i <- 0 until a.length) {
        if (i == 0 || i % 2 == 0) result += a(i)
        else result.insert(i-1, a(i))
      }
      result.toArray
    ```

3. Repeat the preceding assignment, but produce a new array with the swapped values. Use for/yield.
    ```
      val a = Array(1, 2, 3, 4, 5)
      val result = for (i <- 0 until a.length) yield {
        if (i % 2 == 0 && i == a.length - 1) a(i)
        else if (i % 2 == 0) a(i+1)
        else a(i-1)
      }
      result.toArray
    ```

4. Given an array of integers, produce a new array that contains all positive values of the original array, in their original order, followed by all values that are zero or negative, in their original order.
    ```
      val a = Array(-1, 1, -2, 2, -3, 3)
      val result = Array() ++ a.filter(_ > 0) ++ a.filter(_ <= 0)
    ```

5. How do you compute the average of an Array[Double]?

    ```
      val total = Array[Double](1.0, 2.99)
      val average = total.sum / total.length
    ```

6. How do you rearrange the elements of an Array[Int] so that they appear in
reverse sorted order? How do you do the same with an ArrayBuffer[Int]?
    ```
      val a = Array(2, 3, 1, 5, 6, 8, 9)
      val aDescending = a.sortWith(_>_)

      import collection.mutable.ArrayBuffer
      val b = ArrayBuffer[Int](2, 3, 1, 5, 6, 8, 9)
      val bDescending = b.sortWith(_>_)
    ```

7. Write a code snippet that produces all values from an array with duplicates
removed. (Hint: Look at Scaladoc.)
    ```
      val a = Array(1, 1, 2, 3, 4, 5, 5)
      val noDuplicates = a.distinct
    ```

8. Rewrite the example at the end of Section 3.4, “Transforming Arrays,” on page 32. Collect indexes of the negative elements, reverse the sequence, drop the last index, and call a.remove(i) for each index. Compare the efficiency of this approach with the two approaches in Section 3.4.
    ```
      import collection.mutable.ArrayBuffer
      val a = ArrayBuffer[Int](2, 3, -3, 5, 7, -7, 11, -13, 15)
      val indexes = for (i <- 0 until a.length if a(i) < 0) yield i
      for (j <- indexes.reverse.drop(1)) a.remove(j)
    ```
