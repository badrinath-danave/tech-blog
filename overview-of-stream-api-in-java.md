# Stream API in Java

In Java 8, We have stream API. It has the responsibility to support sequential and parallel aggregate operations. Following is the defined signature of stream API in “[java.util.stream](http://java.util.stream)” package.

```java
public interface Stream<T>
extends BaseStream<T,Stream<T>>
```

To understand its working and to operate using streams. We must know java8 features such as “lambda expression”, and “function interface”. etc.

As You have seen in the above code, Stream is an interface that takes the generic value as T.

To perform computation operations, stream operations are composed into a stream pipeline.

Stream pipeline needs the following sources:

1. Array
    
2. List,
    
3. Collection
    
4. a generator function
    
5. I/O channel
    

Stream pipeline performs the following operations:

1. Intermediate — transform stream into another stream e.g filter(predicate)
    
2. Terminal — which produces result or side-effect, such as count() or forEach(consumer)
    

Streams are lazy. This means a computation operation is performed on source data whenever a terminal operation is initiated, as per need element consumption.

Streams do not change the source data structure, they only provide the computation result as per the pipeline methods.

Why do we need stream API.?

1. To achieve functional programming
    
2. Code reduce
    
3. To avoid collections head-on, how elements perform their computation activity.
    
4. To do the bulk operation
    

Creating Streams:

1. creating stream using op() method of stream
    

```java
Stream<Integer> stream = Stream.of(1,2,3,4,5,6,7,8,9);
stream.forEach(p -> System.out.println(p));
```

2\. creating stream using List

```java
List<Integer> list = new ArrayList<Integer>();

for(int i = 1; i< 10; i++){
      list.add(i);
}

Stream<Integer> stream = list.stream();
stream.forEach(p -> System.out.println(p));
```

3\. after performing terminal operation, stream must collect that process result into collector.

```java
List<Integer> evenNumbersList = stream.filter(i -> i%2 == 0)
                                    .collect(Collectors.toList());
System.out.print(evenNumbersList);
```

Stream API code example as follows:

```java
package java8;
import java.util.ArrayList;
import java.util.Arrays;
import java.util.HashMap;
import java.util.List;
import java.util.Map;
import java.util.stream.Collectors;
public class StreamAPIDemo {
 public static void main(String[] args) {
 List<String> list = new ArrayList<>();
 
 list.add("Rohit Sharma");
 list.add("Virat Kohali");
 list.add("Sachin Tendulkar");
 list.add("MS Dhoni");
 list.add("Babar Azam");
 
 System.out.println("*** List Example Using Stream API ***");
 list.stream().forEach(l -> System.out.println(l));
 
 System.out.println("");
 
 
 Map<Integer, String> map = new HashMap<>();
 map.put(264, "Rohit Sharma");
 map.put(184, "Virat Kohali");
 map.put(200, "Sachin Tendulkar");
 map.put(183, "MS Dhoni");
 map.put(172, "Babar Azam");
 
 System.out.println("*** Map Example Using Stream API ***");
 map.entrySet().stream().forEach((K)->System.out.println(K));
 System.out.println("");
 
 //filter - use for conditional check
 System.out.println("*** Fetching only specific record value or data from map ***");
 map.entrySet().stream().filter(K->K.getValue().startsWith("M")).forEach((K)->System.out.println(K.getValue()));
 System.out.println("");
 
 List<Integer> numList =Arrays.asList(1,1,1,2,3,6,4,5,7,8,9);
 
 System.out.println("*** Removes duplicate element using streams aggregate pipeline method***");
 numList.stream().distinct().forEach(n->System.out.println(n));
 
 System.out.println("");
 
 System.out.println("List : "+ numList.stream().distinct().collect(Collectors.toList()));
 
 
 }
}
```

Output:

```plaintext
*** List Example Using Stream API ***
Rohit Sharma
Virat Kohali
Sachin Tendulkar
MS Dhoni
Babar Azam

*** Map Example Using Stream API ***
183=MS Dhoni
264=Rohit Sharma
184=Virat Kohali
200=Sachin Tendulkar
172=Babar Azam

*** Fetching only specific record value or data from map ***
MS Dhoni

*** Removes duplicate element using streams aggregate pipeline method***
1
2
3
6
4
5
7
8
9

List : [1, 2, 3, 6, 4, 5, 7, 8, 9]
```

Please like and share.

Thank You.

Badrinath
