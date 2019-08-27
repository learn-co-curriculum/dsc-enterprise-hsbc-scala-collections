
# Collections

## `List`

* `List` are like `java.util.List` where they are indexed collections that hold usually homogeneous data
* `List` are unlike java.util.List where they are an immutable List
* `List` generally allows duplicates

Varying Ways to create a List


```scala
val a = List(1,2,3,4,5) //What is this call?
val b = 1 :: 2 :: 3 :: 4 :: 5 :: Nil
val c = Nil:List[String]
```


    Intitializing Scala interpreter ...



    Spark Web UI available at http://32c6e00c8fb3:4043
    SparkContext available as 'sc' (version = 2.4.3, master = local[*], app id = local-1562173490938)
    SparkSession available as 'spark'
    





    a: List[Int] = List(1, 2, 3, 4, 5)
    b: List[Int] = List(1, 2, 3, 4, 5)
    c: List[String] = List()
    



## Some methods for `List`


```scala
println(a.head)
```

    1
    


```scala
println(a.tail)
```

    List(2, 3, 4, 5)
    


```scala
println(a.init)
```


```scala
println(a.last)
```


```scala
println(a(4)) //5 <--Wait what is this?
```


```scala
println(a.max)
```


```scala
println(a.min)
```


```scala
println(a.isEmpty)
```


```scala
println(a.nonEmpty)
```


```scala
println(a.updated(3, 100)) //Underused
```


```scala
println(a.mkString(",")) //available on all collections!
```


```scala
println(a.mkString("{", " ## ", "}"))
```

## `List` Conclusion

* `List` are a immutable collection, duplicates allowed
* `Nil` is an empty List
* `List` are created with the object and an apply factory
* `List` have all the functional properties as other collections have

## `Range`

### `Range` direct

Obtaining 0…​4, exclusively


```scala
val exclusive = Range(0, 4) //0,1,2,3
```

Obtaining 0…​4, inclusively


```scala
val inclusive = Range.inclusive(0, 4) //0,1,2,3,4
```

Source: https://www.scala-lang.org/api/current/scala/collection/immutable/Range$.html

### `Range` with implicit trickery

Obtaining 0…​4, exclusively


```scala
val exclusive = 0 until 4 //0,1,2,3
```




    exclusive: scala.collection.immutable.Range = Range(0, 1, 2, 3)
    



Obtaining 0…​4, inclusively


```scala
val inclusive = 0 to 4 //0,1,2,3,4
```




    inclusive: scala.collection.immutable.Range.Inclusive = Range(0, 1, 2, 3, 4)
    



Source: https://www.scala-lang.org/api/current/scala/collection/immutable/Range$.html

### `Range` exclusively with Positive Steps

Obtaining 1…​20 with a positive step of 2, exclusively, using Standard API


```scala
Range(0, 20, 2).toVector //Vector(0, 2, 4, 6, 8, 10, 12, 14, 16, 18)
```

The above obviously uses the `apply` method

Obtaining 1…​20 with a positive step of 2, exclusively, using Implicit Trickery

(0 until 20 by 2).toVector //Vector(0, 2, 4, 6, 8, 10, 12, 14, 16, 18)

### Range inclusively with Positive Steps
Obtaining 1…​20 with a positive step of 2, inclusively, using Standard API


```scala
Range.inclusive(0, 20, 2).toVector //Vector(0, 2, 4, 6, 8, 10, 12, 14, 16, 18, 20)
```




    res7: Vector[Int] = Vector(0, 2, 4, 6, 8, 10, 12, 14, 16, 18, 20)
    



The above uses the apply method

Obtaining 1…​20 with a positive step of 2, inclusively, using Implicit Trickery


```scala
(1 to 20 by 2).toVector //Vector(0, 2, 4, 6, 8, 10, 12, 14, 16, 18, 20)
```




    res8: Vector[Int] = Vector(1, 3, 5, 7, 9, 11, 13, 15, 17, 19)
    



Range exclusively with Negative Steps

Obtaining 20…​0 with a negative step of -2, exclusively, using Standard API


```scala
Range(20, 0, -2).toVector //Vector(20, 18, 16, 14, 12, 10, 8, 6, 4, 2)
```




    res9: Vector[Int] = Vector(20, 18, 16, 14, 12, 10, 8, 6, 4, 2)
    



The above uses the `apply` method

Obtaining 20…​0 with a negative step of -2, exclusively, using Implicit Trickery


```scala
(20 until 0 by -2).toVector  //Vector(20, 18, 16, 14, 12, 10, 8, 6, 4, 2)
```




    res10: Vector[Int] = Vector(20, 18, 16, 14, 12, 10, 8, 6, 4, 2)
    



### `Range` inclusively with Negative Steps

Using Standard API

Obtaining 20…​0 with a negative step of -2, inclusively, using Standard API


```scala
Range.inclusive(20, 0, -2).toVector //Vector(20, 18, 16, 14, 12, 10, 8, 6, 4, 2, 0)
```




    res6: Vector[Int] = Vector(20, 18, 16, 14, 12, 10, 8, 6, 4, 2, 0)
    



The above uses the apply method

Obtaining 20…​0 with a negative step of -2, inclusively, using Implicit Trickery


```scala
(20 to 0 by -2).toVector  //Vector(20, 18, 16, 14, 12, 10, 8, 6, 4, 2, 0)
```




    res5: Vector[Int] = Vector(20, 18, 16, 14, 12, 10, 8, 6, 4, 2, 0)
    



## `Set`

* Just like underlying Java and most programming languages, a `Set` is:
* `Collection` that doesn’t have duplicate elements
* Generally have more mathematical methods than `List`
* Doesn’t maintain order

Some of the characteristics of `Set`:

* `head`, `tail` are not available
* `apply` has a different behavior

### Creating a `Set`


```scala
val set =  Set(1,2,3,4)
val set2 = Set.apply(1,2,3,4,5)
```




    set: scala.collection.immutable.Set[Int] = Set(1, 2, 3, 4)
    set2: scala.collection.immutable.Set[Int] = Set(5, 1, 2, 3, 4)
    



Calculating the differences of a Set
The following calculates the differences of a Set


```scala
Set(1,2,3,4) diff Set(1,2,3,4,5,6,7)
```

Whereas, the opposite…​


```scala
Set(1,2,3,4,5,6,7) diff Set(1,2,3,4)
```




    res4: scala.collection.immutable.Set[Int] = Set(5, 6, 7)
    



### Calculating the `union` of two `Set`

A union will provide the combination of the two Set


```scala
Set(1,2,3,4) union Set(5,10)
```

### Calculating the `intersect` of two Set

intersect is the opposite of a diff and shows the commonality of two Set


```scala
Set(1,2,3,4) intersect Set(19,2,3,10)
```




    res2: scala.collection.immutable.Set[Int] = Set(2, 3)
    



### Using `apply` with a `Set`

`apply` will only return the same as `contains` and that is whether the element is in the `Set` or not


```scala
val set = Set(1,2,3,4)
set.apply(4) //true
set.apply(10) //false
set.contains(4) //true
```




    set: scala.collection.immutable.Set[Int] = Set(1, 2, 3, 4)
    res3: Boolean = true
    



### `Set`  Conclusion

* `Set`s are collections with no duplicate elements
* More mathematically powerful than the `List` counter part
* `Set`s have a hash order that is undetermined (if less than 5)
* `apply` will return `true` or `false`

## Using `Map`s

### `Map`s

* Called associative arrays, dictionary, or tables in other languages
* Table of keys and values
* Items are looked up by key

### Creating a Map

The following calls all create the same Map


```scala
val m = Map.apply((1, "One"), (2, "Two"), (3, "Three"))
```




    m: scala.collection.immutable.Map[Int,String] = Map(1 -> One, 2 -> Two, 3 -> Three)
    




```scala
val m = Map((1, "One"), (2, "Two"), (3, "Three"))
```




    m: scala.collection.immutable.Map[Int,String] = Map(1 -> One, 2 -> Two, 3 -> Three)
    



Reminder, on tuples, the `->` creates a `Tuple2`


```scala
val t:(Int, String) = 1 -> "One"
```




    t: (Int, String) = (1,One)
    




```scala
val m = Map(1 -> "One", 2 -> "Two", 3 -> "Three")
```




    m: scala.collection.immutable.Map[Int,String] = Map(1 -> One, 2 -> Two, 3 -> Three)
    



### `Map` safe retrieval by key
Given a Map we created previously.


```scala
val m = Map(1 -> "One", 2 -> "Two", 3 -> "Three")
```




    m: scala.collection.immutable.Map[Int,String] = Map(1 -> One, 2 -> Two, 3 -> Three)
    



To retrieve by key:


```scala
m.get(1)
```




    res11: Option[String] = Some(One)
    



When no key is available, then the result will be None


```scala
m.get(4)
```




    res12: Option[String] = None
    



### `Map` unsafe retrieval by key

Given a Map we created previously.


```scala
val m = Map(1 -> "One", 2 -> "Two", 3 -> "Three")
```




    m: scala.collection.immutable.Map[Int,String] = Map(1 -> One, 2 -> Two, 3 -> Three)
    



Calling apply will retreive the value direct without wrapping it in an Option


```scala
m.apply(1)
```




    res13: String = One
    



The problem that you will have to be careful about when calling an apply on a Map that doesn’t contain the key


```scala
m.apply(4)
```


    java.util.NoSuchElementException: key not found: 4

      at scala.collection.MapLike$class.default(MapLike.scala:228)

      at scala.collection.AbstractMap.default(Map.scala:59)

      at scala.collection.MapLike$class.apply(MapLike.scala:141)

      at scala.collection.AbstractMap.apply(Map.scala:59)

      ... 36 elided

    


### `Map` retrieval of key Iterable

Given a Map we created previously.


```scala
val m = Map(1 -> "One", 2 -> "Two", 3 -> "Three")
```




    m: scala.collection.immutable.Map[Int,String] = Map(1 -> One, 2 -> Two, 3 -> Three)
    



To retrieve an Iterable of keys


```scala
m.keys
```




    res15: Iterable[Int] = Set(1, 2, 3)
    



To retreive them as a `Set`


```scala
m.keySet
```




    res16: scala.collection.immutable.Set[Int] = Set(1, 2, 3)
    



### `Map` Conclusion

* `Map` are a table-like collection that store keys and values
* Internally, `Map`s are a collection of tuples, and can be operated on as such

## `Vector`

* `Vector` is a different kind of sequence like `List`
* Offers differing characteristics, particularly in storage using tries
* It is generally faster in many operations
* Has an API very similar to `List`


```scala
Vector(303.00, -230.2, -12, 19.0, 22.01, -132.00)
```




    res0: scala.collection.immutable.Vector[Double] = Vector(303.0, -230.2, -12.0, 19.0, 22.01, -132.0)
    



## `Stream`

* Collection that evaluates the elements when needed
* To create your own it typically requires use of the `cons` operation and perhaps `Stream.empty[A]`
* To use a `Stream`, particularly if it is infinite, requires the use of `take` which takes a certain number of elements
* In Scala 2.13, it has been replaced with `LazyList` which has nearly the same functionality but different evaluation semantics


```scala
def continuousEvens(): Stream[BigInt] = {
  def ce(n:BigInt):Stream[BigInt] = Stream.cons(n, ce(n + 2))
  ce(2)
}
continuousEvens().take(5).mkString(",")
```




    continuousEvens: ()Stream[BigInt]
    res5: String = 2,4,6,8,10
    



Cons can be expressed using the `#::` operator, and please not the colon on the right hand side


```scala
def continuousEvens(): Stream[BigInt] = {
  def ce(n:BigInt):Stream[BigInt] = n #:: ce(n + 2)
  ce(2)
}
continuousEvens().take(5).mkString(",")
```




    continuousEvens: ()Stream[BigInt]
    res6: String = 2,4,6,8,10
    



## Collection Performance

* In determine performance as to which collection you want here is a chart
* The chart is direct from https://docs.scala-lang.org/overviews/collections/performance-characteristics.html
* The notation is as follows
  * **eC** - Effectively Constants
  * **aC** - Amortized constant time, isn't always constant but over an average it comes close
  * **C** - Constant Time
  * **Log** - Logarithmic Time with the collection size.
  * **L** - Linear, propertional to size of collection
  
<img src="../images/scala_collection_performance.png" alt="Scala Collection Performance" style="width: 50%;"/>

## The Importance of a Clean API

* In Scala, methods names and parameters were curated with care
* Lesson: Once you learn most if not all methods of List you will also know
  * `Set`
  * `Map`
  * `Stream`
  * `String`
  * `Future`
  * `Option`
  * `Queue`
  * `Range`
  * `Vector`

* In some capacity that will also include mutable collections
* Knowing this the learning curve drops significantly
* This also aids in how we learn and understand Spark
