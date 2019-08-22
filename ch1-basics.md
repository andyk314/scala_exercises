# Chapter 1: The Basics

1. In the Scala REPL, type 3. followed by the Tab key. What methods can be applied?

    `Int class methods like +, *, toInt, toFloat`
2. In the Scala REPL, compute the square root of 3, and then square that value. By how much does the result differ from 3? (Hint: The res variables are your friend.)
    ```
      import scala.math
      math.pow(math.sqrt(3), 2) = 2.9999999999999996
    ```
3. Are the res variables val or var?

    `res variables are val. they can cannot be reassign.`

4. Scala lets you multiply a string with a number—try out "crazy" * 3 in the REPL. What does this operation do? Where can you find it in Scaladoc?

    `Returns the current string concatenated n times. This operation is define in the StringOps Class.`

5. What does 10 max 2 mean? In which class is the max method defined?

    `10 max 2 => Returns the larger value, in this case 10. the max method is defined in the RichInt class.`

6. Using BigInt, compute 2^1024.

    `BigInt(2).pow(1024) = 17976931348623159077.......`

7. What do you need to import so that you can get a random prime as probablePrime(100, Random), without any qualifiers before probablePrime and Random?
    ```
      import BigInt._
      import scala.util._
      probablePrime(100, Random) = 640842833704792951967076936589
    ```
8. One way to create random file or directory names is to produce a random BigInt and convert it to base 36, yielding a string such as "qsnvbevtomcj38o06kul". Poke around Scaladoc to find a way of doing this in Scala.
    ```
      val randomBigInt = BigInt.probablePrime(100, util.Random)
      val baseString = randomBigInt.toString(36)
    ```
    
9. How do you get the first character of a string in Scala? The last character?
    ```
      val string = "andykwong"
      val firstCharacter = string.head
      val lastCharacter = string.last
    ```

10. What do the take, drop, takeRight, and dropRight string functions do? What advantage or disadvantage do they have over using substring?
    ```
      val string = "andykwong"
      val firstTwoChar = string.take(2) = "an" #returns first two characters of string
      val withoutFirstTwoChar = string.drop(2) = "dykwong" #return rest of string without its first 2 characters
      val withoutLastTwoChr = string.dropRight(2) = "andykwo" #returns rest of string outout its last 2 characters
      val middleCharacters = string.slice(1, string.length - 1) = "ndykwon" #returns all characters except first and last characters

      Substrings is more flexible and powerful, allowing you slice a subset of data from any indices.
    ```