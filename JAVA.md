# Java Interview Questions and Answers

This document contains 300 technical questions and answers for interviewing Java developers. The questions range from basic to advanced concepts and are designed to help assess a candidate's Java knowledge and expertise.

## Core Java Concepts

### 1. What is Java?

**Answer:**
Java is a high-level, class-based, object-oriented programming language that is designed to have as few implementation dependencies as possible. It follows the "Write Once, Run Anywhere" (WORA) principle, meaning compiled Java code can run on all platforms that support Java without recompilation. Java applications are compiled to bytecode that can run on any Java Virtual Machine (JVM) regardless of the underlying computer architecture.

### 2. What are the main features of Java?

**Answer:**
- **Object-Oriented:** Based on the concept of objects that contain data and methods
- **Platform Independent:** Java bytecode can run on any device with a JVM
- **Simple:** Designed to be easy to learn and use
- **Secure:** Runs in a virtual machine sandbox with security manager
- **Architecture-neutral:** No implementation-dependent features
- **Portable:** Same code works on any platform with a JVM
- **Robust:** Strong memory management, exception handling, type checking
- **Multithreaded:** Built-in support for concurrent programming
- **Distributed:** Designed with network capabilities
- **Dynamic:** Code is loaded on demand during runtime

### 3. What is the difference between JDK, JRE, and JVM?

**Answer:**
- **JVM (Java Virtual Machine):** An abstract machine that provides a runtime environment for Java bytecode to execute. It converts Java bytecode into machine language.
- **JRE (Java Runtime Environment):** Contains the JVM, libraries, and other components to run applications written in Java. It doesn't contain tools for Java development like compilers and debuggers.
- **JDK (Java Development Kit):** A software development kit that includes the JRE, compilers, debuggers, and other tools needed for developing Java applications.

### 4. What are the primitive data types in Java?

**Answer:**
Java has eight primitive data types:
- **byte:** 8-bit signed integer (-128 to 127)
- **short:** 16-bit signed integer (-32,768 to 32,767)
- **int:** 32-bit signed integer (-2^31 to 2^31-1)
- **long:** 64-bit signed integer (-2^63 to 2^63-1)
- **float:** 32-bit floating point
- **double:** 64-bit floating point
- **char:** 16-bit Unicode character (0 to 65,535)
- **boolean:** true or false

### 5. What is the difference between an interface and an abstract class?

**Answer:**
| Feature | Abstract Class | Interface |
|---------|---------------|-----------|
| Methods | Can have abstract and concrete methods | Before Java 8: Only abstract methods<br>Java 8+: Can have default and static methods<br>Java 9+: Can have private methods |
| Variables | Can have instance variables | Only constants (public static final) |
| Constructor | Can have constructors | Cannot have constructors |
| Inheritance | A class can extend only one abstract class | A class can implement multiple interfaces |
| Access Modifiers | Can use any access modifier | Methods are implicitly public |
| Purpose | For code reuse and establishing a base for subclasses | For defining a contract that classes must implement |

### 6. What is the difference between method overloading and method overriding?

**Answer:**
**Method Overloading:**
- Occurs within the same class
- Methods have the same name but different parameters (number, type, or order)
- Return type can be different, but it's not considered for overloading
- Resolved at compile time (static binding)
- Example: `add(int a, int b)` and `add(int a, int b, int c)`

**Method Overriding:**
- Occurs in two classes with an inheritance relationship
- Subclass provides a specific implementation of a method already defined in the parent class
- Method signature (name and parameters) must be the same
- Return type must be the same or a subtype (covariant return)
- Access modifier must be the same or less restrictive
- Resolved at runtime (dynamic binding)
- Example: `toString()` in a subclass

### 7. What is the difference between == and equals() method?

**Answer:**
- **== operator:** Compares object references (checks if both references point to the same memory location)
- **equals() method:** Compares the content/values of objects

For primitive types, == compares values. For objects, == compares references unless the equals() method is overridden to compare content. The String class, for example, overrides equals() to compare the actual string content rather than references.

### 8. What is the purpose of the final keyword?

**Answer:**
The final keyword can be applied to:
- **Variables:** Makes the variable a constant that cannot be reassigned
- **Methods:** Prevents method overriding in subclasses
- **Classes:** Prevents the class from being subclassed/extended

### 9. What is the difference between String, StringBuilder, and StringBuffer?

**Answer:**
- **String:** Immutable (once created, cannot be modified). Each operation creates a new String object.
- **StringBuilder:** Mutable, not thread-safe, better performance in single-threaded scenarios.
- **StringBuffer:** Mutable, thread-safe (synchronized methods), slightly slower than StringBuilder due to synchronization overhead.

Performance: StringBuilder > StringBuffer > String (for multiple modifications)

### 10. What is the difference between checked and unchecked exceptions?

**Answer:**
**Checked Exceptions:**
- Subclasses of Exception (excluding RuntimeException)
- Must be either caught (try-catch) or declared (throws)
- Checked at compile time
- Examples: IOException, SQLException

**Unchecked Exceptions:**
- Subclasses of RuntimeException
- Don't need to be caught or declared
- Checked at runtime
- Examples: NullPointerException, ArrayIndexOutOfBoundsException

### 11. What is the purpose of the static keyword?

**Answer:**
The static keyword can be applied to:
- **Variables:** Creates class variables shared across all instances
- **Methods:** Creates class methods that can be called without creating an instance
- **Blocks:** Static initialization blocks run when the class is loaded
- **Nested Classes:** Creates static nested classes that don't need an instance of the outer class

Static members belong to the class rather than to instances of the class.

### 12. What is the purpose of the this keyword?

**Answer:**
The this keyword refers to the current object instance. It can be used to:
- Refer to instance variables when they're shadowed by method parameters
- Call another constructor in the same class (constructor chaining)
- Return the current object instance (for method chaining)
- Pass the current object as a parameter to another method

### 13. What is the purpose of the super keyword?

**Answer:**
The super keyword refers to the parent class. It can be used to:
- Call the parent class constructor
- Access parent class methods that have been overridden in the subclass
- Access parent class variables

### 14. What is the difference between an abstract class and a concrete class?

**Answer:**
- **Abstract Class:**
  - Can have abstract methods (methods without implementation)
  - Cannot be instantiated directly
  - May have constructors
  - Subclasses must implement all abstract methods or be declared abstract themselves
  - Used when you want to provide a common base with some default functionality

- **Concrete Class:**
  - All methods must have implementations
  - Can be instantiated directly
  - Represents a complete implementation that can be used as is

### 15. What is the difference between composition and inheritance?

**Answer:**
- **Inheritance ("is-a" relationship):**
  - A subclass inherits properties and behaviors from a superclass
  - Creates a tightly coupled relationship
  - Supports code reuse through extending functionality
  - Example: Car is a Vehicle

- **Composition ("has-a" relationship):**
  - A class contains objects of other classes as instance variables
  - Creates a loosely coupled relationship
  - Supports code reuse through delegation
  - More flexible than inheritance
  - Example: Car has an Engine

### 16. What is the purpose of the package statement?

**Answer:**
The package statement defines the namespace in which the class or interface belongs. It helps to:
- Organize related classes and interfaces
- Prevent naming conflicts
- Control access through package-private access level
- Create a hierarchical structure for code organization

### 17. What is the purpose of the import statement?

**Answer:**
The import statement allows you to use classes or interfaces from other packages without specifying their fully qualified names. Types of imports:
- **Single-type import:** `import java.util.ArrayList;`
- **On-demand type import (wildcard):** `import java.util.*;`
- **Static import:** `import static java.lang.Math.PI;`

### 18. What is the difference between instance variables and local variables?

**Answer:**
| Feature | Instance Variables | Local Variables |
|---------|-------------------|----------------|
| Declaration | Declared inside a class but outside methods | Declared inside methods, constructors, or blocks |
| Scope | Available throughout the class | Limited to the method, constructor, or block where declared |
| Default Values | Have default values (0, false, null) | No default values, must be initialized before use |
| Lifetime | Exist as long as the object exists | Exist only while the method is being executed |
| Access Modifiers | Can have access modifiers | Cannot have access modifiers |
| Storage | Stored in heap memory | Stored in stack memory |

### 19. What is the difference between method parameters and arguments?

**Answer:**
- **Parameters:** Variables defined in the method declaration
- **Arguments:** Actual values passed to the method when it is called

Example:
```java
// x and y are parameters
public int add(int x, int y) {
    return x + y;
}

// 5 and 10 are arguments
int result = add(5, 10);
```

### 20. What is the purpose of the transient keyword?

**Answer:**
The transient keyword is used to indicate that a field should not be serialized when the object is converted to a byte stream. It's useful for:
- Excluding sensitive data (passwords, encryption keys)
- Excluding derived data that can be recalculated
- Excluding non-serializable objects
- Reducing the size of serialized objects

When a transient field is deserialized, it will be initialized with the default value for its type.

### 21. What is the purpose of the volatile keyword?

**Answer:**
The volatile keyword is used to indicate that a variable's value may be changed by multiple threads simultaneously. It ensures:
- Changes to the variable are immediately visible to all threads
- Reads and writes to the variable are atomic
- Prevents compiler optimizations that could cause thread safety issues

It's useful for flag variables that indicate status changes across threads, but it doesn't provide atomicity for compound operations.

### 22. What is the purpose of the synchronized keyword?

**Answer:**
The synchronized keyword is used to control access to critical sections of code or objects in multi-threaded environments. It can be applied to:
- **Methods:** The entire method becomes a critical section, locked on the current object (this)
- **Static methods:** The entire method becomes a critical section, locked on the class object
- **Code blocks:** Only the block becomes a critical section, locked on the specified object

It ensures that only one thread can execute the synchronized code at a time, preventing race conditions.

### 23. What is the difference between a shallow copy and a deep copy?

**Answer:**
- **Shallow Copy:** Creates a new object but copies references to the same objects contained in the original. Changes to nested objects affect both copies.
- **Deep Copy:** Creates a new object and recursively copies all objects referenced by the original. Changes to nested objects in one copy don't affect the other.

Java's clone() method performs a shallow copy by default. For deep copying, you need to override clone() or use serialization/deserialization.

### 24. What is the purpose of the instanceof operator?

**Answer:**
The instanceof operator checks if an object is an instance of a specific class, subclass, or interface. It returns true if the object is an instance of the specified type, false otherwise. It's commonly used:
- Before casting objects to prevent ClassCastException
- In polymorphic code to determine the specific type of an object
- In equals() methods to ensure objects are of the same type

Example:
```java
if (obj instanceof String) {
    String str = (String) obj;
    // Process string
}
```

### 25. What is the difference between break and continue statements?

**Answer:**
- **break:** Terminates the loop or switch statement and transfers execution to the statement immediately following the loop or switch.
- **continue:** Skips the current iteration of a loop and continues with the next iteration.

### 26. What is the purpose of the assert statement?

**Answer:**
The assert statement is used to test assumptions about the program during development. It takes the form:
```java
assert condition;
// or
assert condition : errorMessage;
```

If the condition is false, an AssertionError is thrown. Assertions are disabled by default at runtime and need to be enabled with the -ea (enable assertions) JVM flag. They should be used for development-time verification, not for validating user input or enforcing business rules.

### 27. What is the purpose of the try-with-resources statement?

**Answer:**
The try-with-resources statement automatically closes resources that implement the AutoCloseable or Closeable interface at the end of the statement. It ensures resources are properly closed even if an exception occurs.

Example:
```java
try (FileInputStream fis = new FileInputStream("file.txt");
     BufferedReader br = new BufferedReader(new InputStreamReader(fis))) {
    // Use the resources
} // Resources automatically closed here
```

Benefits:
- Cleaner code (no need for finally block with close statements)
- Safer (resources are closed even if an exception occurs)
- Multiple resources can be managed in one statement

### 28. What is the difference between throw and throws keywords?

**Answer:**
- **throw:** Used to explicitly throw an exception within a method or block
  ```java
  throw new IllegalArgumentException("Invalid parameter");
  ```

- **throws:** Used in method declaration to indicate that the method might throw certain exceptions that must be caught or declared by the caller
  ```java
  public void readFile(String path) throws IOException {
      // Method implementation
  }
  ```

### 29. What is the purpose of the finalize() method?

**Answer:**
The finalize() method is called by the garbage collector before reclaiming the memory of an object. It gives the object a last chance to clean up resources that aren't handled by try-with-resources or explicit close methods.

However, it's considered poor practice to rely on finalize() because:
- There's no guarantee when or if it will be called
- It can significantly impact performance
- It was deprecated in Java 9
- Better alternatives exist (try-with-resources, Cleaner API)

### 30. What is the purpose of the Object class?

**Answer:**
The Object class is the root class of the Java class hierarchy. Every class in Java implicitly extends Object if it doesn't explicitly extend another class. It provides several methods that are available to all Java objects:

- **equals(Object obj):** Compares objects for equality
- **hashCode():** Returns a hash code value for the object
- **toString():** Returns a string representation of the object
- **getClass():** Returns the runtime class of the object
- **clone():** Creates and returns a copy of the object
- **finalize():** Called by the garbage collector before reclaiming memory
- **wait(), notify(), notifyAll():** Used for thread synchronization

### 31. What is autoboxing and unboxing?

**Answer:**
- **Autoboxing:** Automatic conversion of primitive types to their corresponding wrapper classes
  ```java
  Integer num = 100; // Autoboxing: int to Integer
  ```

- **Unboxing:** Automatic conversion of wrapper class objects to their corresponding primitive types
  ```java
  int value = new Integer(100); // Unboxing: Integer to int
  ```

This feature simplifies code when working with collections that can only store objects, not primitives.

### 32. What is the difference between a static class and a singleton?

**Answer:**
- **Static Class:**
  - Can only be created as a nested class
  - Cannot be instantiated
  - All members must be static
  - No instance state
  - Used for utility methods and constants

- **Singleton:**
  - A design pattern that restricts instantiation to one instance
  - Can have instance state
  - Can implement interfaces and extend classes
  - Can be lazy-initialized
  - Provides global access point to the instance

### 33. What is the purpose of the enum type?

**Answer:**
Enum types in Java are special classes that represent a group of constants. They provide:
- Type-safety (only predefined enum values can be used)
- Built-in methods (values(), valueOf(), ordinal(), name())
- The ability to add fields, methods, and constructors
- Implementation of interfaces
- Switch statement compatibility

Example:
```java
enum Day {
    MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY;
}
```

### 34. What is the difference between a static method and an instance method?

**Answer:**
| Feature | Static Method | Instance Method |
|---------|--------------|-----------------|
| Belongs to | Class | Object instance |
| Called using | Class name or instance | Object instance |
| Access to | Static members only | Both static and instance members |
| this reference | Not available | Available |
| Overriding | Not possible | Possible |
| Memory | Single copy in memory | One copy per instance |
| When to use | Functionality not dependent on instance state | Functionality dependent on instance state |

### 35. What is the purpose of the default keyword in interfaces?

**Answer:**
The default keyword, introduced in Java 8, allows interfaces to have method implementations. Default methods enable:
- Adding new methods to interfaces without breaking existing implementations
- Multiple inheritance of behavior (not state)
- Backward compatibility when evolving APIs

Example:
```java
interface Vehicle {
    void start();

    default void honk() {
        System.out.println("Beep beep!");
    }
}
```

Classes implementing this interface must implement start() but can inherit or override honk().

### 36. What is the purpose of the static keyword in interfaces?

**Answer:**
Static methods in interfaces, introduced in Java 8, provide utility methods related to the interface without requiring an instance. They:
- Cannot be overridden by implementing classes
- Are called using the interface name
- Cannot access instance methods or variables
- Are useful for providing helper methods for default methods

Example:
```java
interface MathOperations {
    static int add(int a, int b) {
        return a + b;
    }
}

// Called as:
int result = MathOperations.add(5, 10);
```

### 37. What is the purpose of the private methods in interfaces?

**Answer:**
Private methods in interfaces, introduced in Java 9, allow code reuse within the interface without exposing the methods to implementing classes. They can be:
- **Private instance methods:** Used by default methods
- **Private static methods:** Used by both default and static methods

They help avoid code duplication in default methods and keep the interface's public API clean.

Example:
```java
interface Vehicle {
    default void startDriving() {
        initializeComponents();
        System.out.println("Vehicle is moving");
    }

    private void initializeComponents() {
        System.out.println("Initializing components");
    }
}
```

### 38. What is the difference between an anonymous class and a lambda expression?

**Answer:**
| Feature | Anonymous Class | Lambda Expression |
|---------|----------------|-------------------|
| Syntax | More verbose | More concise |
| this reference | Refers to the anonymous class instance | Refers to the enclosing class instance |
| Creating instances | Can implement interfaces with multiple methods | Only for functional interfaces (single abstract method) |
| Variables | Can shadow variables from the enclosing scope | Cannot shadow variables from the enclosing scope |
| Access to local variables | Can access final or effectively final variables | Same restriction |
| Memory usage | Creates a new .class file | Does not create a new .class file |

Example:
```java
// Anonymous class
Runnable r1 = new Runnable() {
    @Override
    public void run() {
        System.out.println("Anonymous class");
    }
};

// Lambda expression
Runnable r2 = () -> System.out.println("Lambda expression");
```

### 39. What is a functional interface?

**Answer:**
A functional interface is an interface that contains exactly one abstract method. It can have any number of default or static methods. Functional interfaces are the basis for lambda expressions in Java.

Java provides the @FunctionalInterface annotation to indicate that an interface is intended to be a functional interface. The compiler will generate an error if the interface doesn't meet the requirements.

Examples from the java.util.function package:
- Predicate<T>: Takes a value and returns a boolean
- Consumer<T>: Takes a value and performs an action
- Function<T,R>: Takes a value and returns a result
- Supplier<T>: Takes no input and returns a value

### 40. What is method reference in Java?

**Answer:**
Method references provide a shorthand notation for lambda expressions that call a single existing method. They make the code more readable and concise.

Types of method references:
1. **Static method reference:** `ClassName::staticMethodName`
2. **Instance method reference of a particular object:** `objectReference::instanceMethodName`
3. **Instance method reference of an arbitrary object of a particular type:** `ClassName::instanceMethodName`
4. **Constructor reference:** `ClassName::new`

Example:
```java
// Lambda expression
Function<String, Integer> parser1 = s -> Integer.parseInt(s);

// Method reference
Function<String, Integer> parser2 = Integer::parseInt;
```

### 41. What is the Stream API?

**Answer:**
The Stream API, introduced in Java 8, provides a functional approach to processing collections of objects. It allows operations on data in a declarative way, similar to SQL statements.

Key characteristics:
- Not a data structure, but a view of the data
- Doesn't modify the source data
- Lazy evaluation (intermediate operations aren't executed until a terminal operation is invoked)
- Can be parallel or sequential
- Can be used only once

Stream operations:
- **Intermediate operations:** Return a new stream (filter, map, sorted, etc.)
- **Terminal operations:** Produce a result or side effect (collect, forEach, reduce, etc.)

Example:
```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie", "David");
List<String> filteredNames = names.stream()
    .filter(name -> name.length() > 4)
    .map(String::toUpperCase)
    .sorted()
    .collect(Collectors.toList());
```

### 42. What is the Optional class?

**Answer:**
Optional<T> is a container object introduced in Java 8 to represent a value that may or may not be present. It's designed to:
- Provide a clear way to represent optional values
- Avoid null pointer exceptions
- Force explicit handling of the absence of a value

Key methods:
- **of(T value):** Creates an Optional with a non-null value
- **ofNullable(T value):** Creates an Optional with a value that may be null
- **empty():** Creates an empty Optional
- **isPresent():** Checks if a value is present
- **ifPresent(Consumer<T> consumer):** Executes the consumer if a value is present
- **orElse(T other):** Returns the value if present, otherwise returns other
- **orElseGet(Supplier<T> supplier):** Returns the value if present, otherwise invokes supplier
- **orElseThrow(Supplier<X> exceptionSupplier):** Returns the value if present, otherwise throws the exception

Example:
```java
Optional<String> optional = Optional.ofNullable(getName());
String name = optional.orElse("Unknown");
```

### 43. What is the difference between Collection and Collections?

**Answer:**
- **Collection:** An interface that represents a group of objects. It's the root interface in the collection hierarchy.
- **Collections:** A utility class that contains static methods for operating on collections, such as sorting, searching, and synchronizing.

Example:
```java
// Collection interface
Collection<String> names = new ArrayList<>();
names.add("Alice");

// Collections utility class
Collections.sort(names);
```

### 44. What is the difference between List, Set, and Map?

**Answer:**
| Feature | List | Set | Map |
|---------|------|-----|-----|
| Duplicates | Allowed | Not allowed | Not allowed for keys, allowed for values |
| Order | Maintains insertion order (most implementations) | May or may not maintain order (depends on implementation) | May or may not maintain order (depends on implementation) |
| Null elements | Allowed (most implementations) | At most one null (most implementations) | One null key at most, multiple null values allowed |
| Common implementations | ArrayList, LinkedList, Vector | HashSet, LinkedHashSet, TreeSet | HashMap, LinkedHashMap, TreeMap |
| Use case | When order matters and duplicates are allowed | When uniqueness matters | When key-value pairs are needed |

### 45. What is the difference between ArrayList and LinkedList?

**Answer:**
| Feature | ArrayList | LinkedList |
|---------|-----------|------------|
| Implementation | Dynamic array | Doubly linked list |
| Random access | O(1) time complexity | O(n) time complexity |
| Insertion/deletion at beginning/middle | O(n) time complexity (requires shifting elements) | O(1) time complexity (only requires changing references) |
| Memory overhead | Less (only stores elements) | More (stores elements and references) |
| Iteration speed | Faster (better locality of reference) | Slower |
| Use case | Frequent random access, rare insertions/deletions | Frequent insertions/deletions, rare random access |

### 46. What is the difference between HashMap and Hashtable?

**Answer:**
| Feature | HashMap | Hashtable |
|---------|---------|-----------|
| Synchronization | Not synchronized (not thread-safe) | Synchronized (thread-safe) |
| Null keys/values | Allows one null key and multiple null values | Does not allow null keys or values |
| Performance | Generally better due to lack of synchronization | Slower due to synchronization |
| Iterator | Fail-fast iterator | Enumerator (not fail-fast) |
| Introduction | Java 1.2 | Java 1.0 (legacy class) |
| Modern alternative | ConcurrentHashMap for thread safety | - |

### 47. What is the difference between HashMap and TreeMap?

**Answer:**
| Feature | HashMap | TreeMap |
|---------|---------|---------|
| Implementation | Hash table | Red-black tree |
| Order | No guaranteed order | Sorted according to the natural ordering of keys or a provided comparator |
| Performance | O(1) for get/put operations | O(log n) for get/put operations |
| Null keys | Allows one null key | Does not allow null keys if natural ordering is used |
| Memory usage | Less | More |
| Use case | When order doesn't matter and performance is critical | When sorted order is required |

### 48. What is the difference between HashSet and TreeSet?

**Answer:**
| Feature | HashSet | TreeSet |
|---------|---------|---------|
| Implementation | Backed by HashMap | Backed by TreeMap |
| Order | No guaranteed order | Sorted according to the natural ordering of elements or a provided comparator |
| Performance | O(1) for add/remove/contains operations | O(log n) for add/remove/contains operations |
| Null elements | Allows one null element | Does not allow null elements if natural ordering is used |
| Use case | When order doesn't matter and performance is critical | When sorted order is required |

### 49. What is the Comparable interface?

**Answer:**
The Comparable interface is used to define the natural ordering of objects. A class that implements Comparable can be sorted using Collections.sort() or Arrays.sort() without providing a separate comparator.

Key points:
- Has a single method: `int compareTo(T o)`
- Returns negative if this object is less than the specified object
- Returns zero if they're equal
- Returns positive if this object is greater than the specified object
- Should be consistent with equals() (a.equals(b) should return the same as a.compareTo(b) == 0)

Example:
```java
public class Student implements Comparable<Student> {
    private String name;
    private int id;

    @Override
    public int compareTo(Student other) {
        return this.id - other.id; // Sort by ID
    }
}

// Usage
List<Student> students = new ArrayList<>();
Collections.sort(students); // Uses natural ordering
```

### 50. What is the Comparator interface?

**Answer:**
The Comparator interface is used to define custom ordering for objects. It allows sorting objects that don't implement Comparable or sorting them in an order different from their natural ordering.

Key points:
- Has a primary method: `int compare(T o1, T o2)`
- Returns negative if o1 is less than o2
- Returns zero if they're equal
- Returns positive if o1 is greater than o2
- Can be implemented as a separate class or as a lambda expression

Example:
```java
// Using a separate class
class NameComparator implements Comparator<Student> {
    @Override
    public int compare(Student s1, Student s2) {
        return s1.getName().compareTo(s2.getName());
    }
}

// Using a lambda expression
Comparator<Student> byName = (s1, s2) -> s1.getName().compareTo(s2.getName());

// Usage
Collections.sort(students, byName);
### 51. What is the Iterator interface?

**Answer:**
The Iterator interface provides a way to traverse through a collection of objects sequentially. It's part of the Java Collections Framework and is the basis for the enhanced for loop.

Key methods:
- **hasNext():** Returns true if there are more elements
- **next():** Returns the next element
- **remove():** Removes the last element returned by next() (optional operation)
- **forEachRemaining(Consumer<? super E> action):** Performs the given action for each remaining element

Example:
```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
Iterator<String> iterator = names.iterator();
while (iterator.hasNext()) {
    String name = iterator.next();
    System.out.println(name);
}
```

### 52. What is the difference between fail-fast and fail-safe iterators?

**Answer:**
- **Fail-Fast Iterators:**
  - Throw ConcurrentModificationException if the collection is modified while iterating
  - Don't create a copy of the collection
  - More memory efficient
  - Examples: Iterators from ArrayList, HashMap, Vector

- **Fail-Safe Iterators:**
  - Work on a copy of the collection, so modifications to the original don't affect iteration
  - Don't throw ConcurrentModificationException
  - Less memory efficient
  - May not reflect the latest state of the collection
  - Examples: Iterators from ConcurrentHashMap, CopyOnWriteArrayList

### 53. What is the purpose of the java.util.concurrent package?

**Answer:**
The java.util.concurrent package provides utility classes for concurrent programming. It was introduced in Java 5 to simplify the development of concurrent applications. Key components include:

- **Concurrent Collections:** Thread-safe collection implementations (ConcurrentHashMap, CopyOnWriteArrayList)
- **Executors Framework:** For managing thread pools and asynchronous tasks
- **Synchronizers:** Tools for thread coordination (CountDownLatch, CyclicBarrier, Semaphore)
- **Atomic Variables:** Classes for lock-free thread-safe programming (AtomicInteger, AtomicReference)
- **Locks:** More flexible alternatives to synchronized blocks (ReentrantLock, ReadWriteLock)
- **BlockingQueues:** Thread-safe queues that support operations that wait for the queue to become non-empty or non-full
- **CompletableFuture:** For asynchronous programming

### 54. What is a thread in Java?

**Answer:**
A thread is the smallest unit of execution within a process. Java provides built-in support for multi-threaded programming. Threads allow a program to perform multiple tasks concurrently.

Ways to create a thread:
1. **Extending Thread class:**
   ```java
   class MyThread extends Thread {
       public void run() {
           // Thread code
       }
   }
   MyThread t = new MyThread();
   t.start();
   ```

2. **Implementing Runnable interface:**
   ```java
   class MyRunnable implements Runnable {
       public void run() {
           // Thread code
       }
   }
   Thread t = new Thread(new MyRunnable());
   t.start();
   ```

3. **Using lambda expression (Java 8+):**
   ```java
   Thread t = new Thread(() -> {
       // Thread code
   });
   t.start();
   ```

### 55. What is the difference between the start() and run() methods in Thread?

**Answer:**
- **start():** Creates a new thread and makes it runnable. The JVM calls the run() method on the new thread.
- **run():** Contains the code that constitutes the new thread. If called directly, it runs on the same thread and no new thread is created.

Example:
```java
Thread t = new Thread(() -> System.out.println("Thread is running"));

// This creates a new thread and executes run() in that thread
t.start();

// This executes run() in the current thread, no new thread is created
t.run();
```

### 56. What is thread synchronization?

**Answer:**
Thread synchronization is the process of controlling the access of multiple threads to shared resources. It's necessary to prevent thread interference and memory consistency errors in concurrent programs.

Methods of synchronization in Java:
1. **Synchronized methods:** Using the synchronized keyword on methods
   ```java
   public synchronized void increment() {
       count++;
   }
   ```

2. **Synchronized blocks:** Using the synchronized keyword on blocks of code
   ```java
   public void increment() {
       synchronized(this) {
           count++;
       }
   }
   ```

3. **Locks:** Using explicit lock objects from java.util.concurrent.locks
   ```java
   private Lock lock = new ReentrantLock();

   public void increment() {
       lock.lock();
       try {
           count++;
       } finally {
           lock.unlock();
       }
   }
   ```

4. **Atomic variables:** Using thread-safe atomic operations
   ```java
   private AtomicInteger count = new AtomicInteger(0);

   public void increment() {
       count.incrementAndGet();
   }
   ```

### 57. What is a deadlock?

**Answer:**
A deadlock is a situation where two or more threads are blocked forever, each waiting for the other to release a resource. Deadlocks occur when four conditions are met simultaneously:

1. **Mutual Exclusion:** Resources cannot be shared
2. **Hold and Wait:** Threads hold resources while waiting for others
3. **No Preemption:** Resources cannot be forcibly taken from threads
4. **Circular Wait:** A circular chain of threads, each waiting for a resource held by the next

Example:
```java
public void method1() {
    synchronized(lockA) {
        // Do something
        synchronized(lockB) {
            // Do something else
        }
    }
}

public void method2() {
    synchronized(lockB) {
        // Do something
        synchronized(lockA) {
            // Do something else
        }
    }
}
```

If thread 1 calls method1() and thread 2 calls method2(), a deadlock can occur.

### 58. What is a thread pool?

**Answer:**
A thread pool is a collection of pre-initialized, reusable threads that are available to perform tasks. Instead of creating a new thread for each task, tasks are submitted to the pool, and executed by one of the available threads in the pool.

Benefits:
- **Better performance:** Reusing threads reduces the overhead of thread creation
- **Resource management:** Limits the number of threads that can exist simultaneously
- **Improved responsiveness:** Tasks can be executed immediately by available threads
- **Controlled system degradation:** When all threads are busy, new tasks wait in a queue

Java provides thread pools through the Executor framework:
```java
// Fixed thread pool with 5 threads
ExecutorService executor = Executors.newFixedThreadPool(5);

// Submit tasks
executor.submit(() -> System.out.println("Task executed"));

// Shutdown the executor
executor.shutdown();
```

### 59. What is the difference between the Executor and ExecutorService interfaces?

**Answer:**
- **Executor:** A simple interface with a single method `execute(Runnable)` for executing tasks.
- **ExecutorService:** Extends Executor and provides additional methods for managing tasks and the executor itself:
  - `submit()`: Submits tasks that can return results (using Callable) or provide completion notification
  - `shutdown()`: Initiates an orderly shutdown
  - `shutdownNow()`: Attempts to stop all actively executing tasks
  - `invokeAll()`: Executes a collection of tasks and returns a list of Futures
  - `invokeAny()`: Executes a collection of tasks and returns the result of one that completes successfully

Example:
```java
ExecutorService service = Executors.newFixedThreadPool(10);

// Submit a task that returns a result
Future<String> future = service.submit(() -> "Task result");

// Get the result (blocks until available)
String result = future.get();

// Shutdown the service
service.shutdown();
```

### 60. What is the difference between the wait() and sleep() methods?

**Answer:**
| Feature | wait() | sleep() |
|---------|--------|---------|
| Package | java.lang.Object | java.lang.Thread |
| Purpose | Thread synchronization | Thread execution pausing |
| Lock | Releases the lock on the object | Keeps the lock on the object |
| Waking up | Can be woken up by notify()/notifyAll() | Can only be woken up by interruption or time completion |
| Usage context | Must be called from a synchronized context | Can be called from anywhere |
| Exception | InterruptedException (checked) | InterruptedException (checked) |

Example:
```java
// wait() example
synchronized(obj) {
    while(condition) {
        obj.wait(); // Releases lock and waits
    }
}

// sleep() example
Thread.sleep(1000); // Current thread sleeps for 1 second
```

### 61. What is the difference between notify() and notifyAll() methods?

**Answer:**
Both notify() and notifyAll() are methods of the Object class used to wake up threads that are waiting on an object's monitor.

- **notify():** Wakes up a single thread that is waiting on the object's monitor. If multiple threads are waiting, one is chosen arbitrarily.
- **notifyAll():** Wakes up all threads that are waiting on the object's monitor.

When to use which:
- Use notify() when you know exactly one thread needs to be awakened and any thread will do.
- Use notifyAll() when multiple threads might need to be awakened or when you're not sure which thread should be awakened.

Example:
```java
synchronized(obj) {
    // Change state that might affect waiting threads
    obj.notify(); // Wake up one waiting thread
    // or
    obj.notifyAll(); // Wake up all waiting threads
}
```

### 62. What is a daemon thread?

**Answer:**
A daemon thread is a low-priority thread that runs in the background to perform tasks such as garbage collection. The JVM does not wait for daemon threads to complete before exiting.

Key characteristics:
- Created by calling `setDaemon(true)` before starting the thread
- Automatically terminates when all non-daemon threads finish
- Used for background tasks that shouldn't prevent the application from exiting
- Cannot be converted to a non-daemon thread once started

Example:
```java
Thread daemonThread = new Thread(() -> {
    while (true) {
        // Background task
        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            break;
        }
    }
});
daemonThread.setDaemon(true); // Must be called before start()
daemonThread.start();
```

### 63. What is thread starvation?

**Answer:**
Thread starvation occurs when a thread is unable to gain regular access to shared resources and is unable to make progress. This happens when other threads monopolize the resources.

Causes:
- Threads with high priority preventing lower priority threads from executing
- Threads holding locks for extended periods
- Poorly designed resource management
- Inefficient scheduling algorithms

Prevention:
- Use fair locks (ReentrantLock with fairness parameter set to true)
- Avoid indefinite locks
- Use time-bounded resource waits
- Implement resource pooling
- Consider thread priorities carefully

### 64. What is a ThreadLocal variable?

**Answer:**
ThreadLocal provides thread-local variables, which are variables that are local to each thread. Each thread has its own, independently initialized copy of the variable, invisible to other threads.

Use cases:
- Storing user identification for a particular thread
- Transaction contexts in multi-threaded applications
- Thread-specific date formats
- Thread-specific random number generators

Example:
```java
public class UserContext {
    private static ThreadLocal<User> userThreadLocal = new ThreadLocal<>();

    public static void setUser(User user) {
        userThreadLocal.set(user);
    }

    public static User getUser() {
        return userThreadLocal.get();
    }

    public static void clear() {
        userThreadLocal.remove();
    }
}
```

### 65. What is the ForkJoinPool?

**Answer:**
ForkJoinPool is a specialized implementation of ExecutorService introduced in Java 7 for executing ForkJoinTasks. It's designed for work-stealing, where idle threads can steal tasks from busy threads' queues.

Key features:
- **Work-stealing algorithm:** Balances workload across threads
- **Recursive task decomposition:** Breaks large tasks into smaller subtasks
- **Efficient for divide-and-conquer algorithms:** Like merge sort, quick sort
- **Supports parallel streams:** Used by the Stream API for parallel operations

Example:
```java
class SumTask extends RecursiveTask<Long> {
    private final long[] numbers;
    private final int start;
    private final int end;
    private final int threshold = 10000;

    // Constructor and implementation...

    @Override
    protected Long compute() {
        if (end - start <= threshold) {
            // Sequential computation
            long sum = 0;
            for (int i = start; i < end; i++) {
                sum += numbers[i];
            }
            return sum;
        } else {
            // Fork the task
            int middle = (start + end) / 2;
            SumTask leftTask = new SumTask(numbers, start, middle);
            SumTask rightTask = new SumTask(numbers, middle, end);
            leftTask.fork();
            long rightResult = rightTask.compute();
            long leftResult = leftTask.join();
            return leftResult + rightResult;
        }
    }
}

// Usage
ForkJoinPool pool = new ForkJoinPool();
long result = pool.invoke(new SumTask(numbers, 0, numbers.length));
```

### 66. What is the CompletableFuture class?

**Answer:**
CompletableFuture is a class introduced in Java 8 that represents a future result of an asynchronous computation. It provides a rich set of methods for composing, combining, and handling asynchronous operations.

Key features:
- **Completion stages:** Chain multiple asynchronous operations
- **Exception handling:** Handle exceptions in asynchronous code
- **Combining futures:** Combine results from multiple futures
- **Timeout handling:** Specify timeouts for operations
- **Execution control:** Specify which thread pool to use

Example:
```java
CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
    // Asynchronous operation
    return "Hello";
}).thenApply(s -> {
    // Transform the result
    return s + " World";
}).thenApply(String::toUpperCase);

// Get the result (blocks until available)
String result = future.get(); // "HELLO WORLD"
```

### 67. What is the difference between CountDownLatch and CyclicBarrier?

**Answer:**
Both are synchronization aids in the java.util.concurrent package, but they serve different purposes:

| Feature | CountDownLatch | CyclicBarrier |
|---------|---------------|---------------|
| Purpose | Allows one or more threads to wait until a set of operations in other threads completes | Allows a set of threads to wait for each other to reach a common barrier point |
| Reusability | Cannot be reset | Can be reset and reused |
| Counter | Decrements when tasks complete | Increments when threads arrive |
| Trigger | Releases waiting threads when count reaches zero | Releases all threads when all arrive |
| Action on completion | None | Can execute a barrier action when all threads arrive |

Example:
```java
// CountDownLatch
CountDownLatch latch = new CountDownLatch(3);
// Threads call latch.countDown() when done
// Main thread calls latch.await() to wait for all to finish

// CyclicBarrier
CyclicBarrier barrier = new CyclicBarrier(3, () -> {
    // This runs when all threads reach the barrier
    System.out.println("All threads have reached the barrier");
});
// Threads call barrier.await() to wait for others
```

### 68. What is a Semaphore?

**Answer:**
A Semaphore is a synchronization aid that controls access to a shared resource through the use of a counter. If the counter is greater than zero, access is allowed; if it is zero, access is denied.

Key features:
- **Permits:** The counter represents the number of permits available
- **acquire():** Decrements the counter or blocks until a permit is available
- **release():** Increments the counter, releasing a permit
- **Fairness option:** Can be configured for fair or non-fair access ordering

Use cases:
- Limiting concurrent access to resources
- Implementing bounded collections
- Implementing producer-consumer patterns
- Rate limiting

Example:
```java
// Semaphore with 3 permits
Semaphore semaphore = new Semaphore(3);

// Acquire a permit
semaphore.acquire();
try {
    // Access the shared resource
} finally {
    // Release the permit
    semaphore.release();
}
```

### 69. What is the difference between process and thread?

**Answer:**
| Feature | Process | Thread |
|---------|---------|--------|
| Definition | An instance of a program in execution | A lightweight sub-process, a unit of execution within a process |
| Memory | Has its own memory space | Shares memory space with other threads in the same process |
| Communication | Inter-process communication (IPC) mechanisms required | Direct communication through shared memory |
| Creation | More resource-intensive | Less resource-intensive |
| Isolation | Isolated from other processes | Not isolated from other threads in the same process |
| Switching cost | Higher context switching cost | Lower context switching cost |
| Failure impact | Failure of one process doesn't affect others | Failure of one thread can affect the entire process |

### 70. What is the Callable interface?

**Answer:**
The Callable interface is similar to Runnable, but it can return a result and throw checked exceptions. It was introduced in Java 5 along with the ExecutorService framework.

Key differences from Runnable:
- Callable has a call() method that returns a value, while Runnable's run() method returns void
- call() can throw checked exceptions, while run() cannot
- Callable is often used with ExecutorService and Future

Example:
```java
Callable<Integer> task = () -> {
    // Perform computation
    return 42;
};

ExecutorService executor = Executors.newSingleThreadExecutor();
Future<Integer> future = executor.submit(task);

// Get the result
Integer result = future.get();
```

### 71. What is the Future interface?

**Answer:**
The Future interface represents the result of an asynchronous computation. It provides methods to check if the computation is complete, wait for its completion, and retrieve the result.

Key methods:
- **get():** Waits if necessary for the computation to complete, then retrieves its result
- **get(long timeout, TimeUnit unit):** Waits for the result with a timeout
- **cancel(boolean mayInterruptIfRunning):** Attempts to cancel execution
- **isCancelled():** Returns true if the task was cancelled
- **isDone():** Returns true if the task completed

Limitations:
- Cannot be manually completed
- Cannot be chained or combined
- Limited exception handling
- No support for callbacks

These limitations are addressed by CompletableFuture in Java 8+.

### 72. What is the difference between the Runnable and Callable interfaces?

**Answer:**
| Feature | Runnable | Callable |
|---------|----------|----------|
| Package | java.lang | java.util.concurrent |
| Method | run() | call() |
| Return type | void | Generic type V |
| Exceptions | Cannot throw checked exceptions | Can throw checked exceptions |
| Introduction | Java 1.0 | Java 5 |
| Use with | Thread, ExecutorService | ExecutorService |
| Result handling | None | Returns Future object |

Example:
```java
// Runnable
Runnable runnable = () -> System.out.println("Runnable task");
Thread thread = new Thread(runnable);
thread.start();

// Callable
Callable<String> callable = () -> {
    return "Callable result";
};
ExecutorService executor = Executors.newSingleThreadExecutor();
Future<String> future = executor.submit(callable);
String result = future.get();
```

### 73. What is the difference between the submit() and execute() methods in ExecutorService?

**Answer:**
Both methods are used to assign tasks to an ExecutorService, but they differ in their return values and the types of tasks they accept:

| Feature | execute() | submit() |
|---------|-----------|----------|
| Return type | void | Future<?> |
| Task type | Only Runnable | Runnable, Callable, or any value-returning task |
| Result tracking | No way to track completion | Returns a Future to track completion and get results |
| Exception handling | Uncaught exceptions go to the UncaughtExceptionHandler | Exceptions are stored in the Future and thrown when get() is called |

Example:
```java
ExecutorService executor = Executors.newFixedThreadPool(2);

// execute() with Runnable
executor.execute(() -> System.out.println("Task executed"));

// submit() with Runnable
Future<?> future1 = executor.submit(() -> System.out.println("Task submitted"));

// submit() with Callable
Future<String> future2 = executor.submit(() -> "Result");
String result = future2.get();
```

### 74. What is the difference between the newFixedThreadPool(), newCachedThreadPool(), and newSingleThreadExecutor() methods?

**Answer:**
These are factory methods in the Executors class that create different types of thread pools:

- **newFixedThreadPool(int nThreads):**
  - Creates a thread pool with a fixed number of threads
  - If all threads are active, new tasks wait in a queue
  - Good for limiting resource usage and when you know the optimal thread count

- **newCachedThreadPool():**
  - Creates a thread pool that creates new threads as needed
  - Reuses previously constructed threads when available
  - Terminates unused threads after 60 seconds
  - Good for many short-lived tasks and when the workload is unpredictable

- **newSingleThreadExecutor():**
  - Creates an executor with a single worker thread
  - Tasks are executed sequentially
  - If the thread dies, a new one is created
  - Good for tasks that must be executed sequentially

Example:
```java
// Fixed thread pool with 5 threads
ExecutorService fixed = Executors.newFixedThreadPool(5);

// Cached thread pool
ExecutorService cached = Executors.newCachedThreadPool();

// Single thread executor
ExecutorService single = Executors.newSingleThreadExecutor();
```

### 75. What is the difference between the ScheduledThreadPoolExecutor and Timer classes?

**Answer:**
Both are used for scheduling tasks to run after a delay or periodically, but they have several differences:

| Feature | ScheduledThreadPoolExecutor | Timer |
|---------|----------------------------|-------|
| Thread model | Uses a pool of threads | Uses a single thread |
| Error handling | Task failures don't affect other tasks | One task failure cancels all tasks |
| Scheduling precision | More precise | Less precise |
| Flexibility | Supports both Runnable and Callable | Supports only TimerTask |
| Cancellation | Individual tasks can be cancelled | Individual tasks can be cancelled |
| Thread safety | Thread-safe | Thread-safe |
| Introduction | Java 5 | Java 1.3 |

Example:
```java
// ScheduledThreadPoolExecutor
ScheduledExecutorService scheduler = Executors.newScheduledThreadPool(2);
scheduler.schedule(() -> System.out.println("Delayed task"), 1, TimeUnit.SECONDS);
scheduler.scheduleAtFixedRate(() -> System.out.println("Periodic task"), 0, 1, TimeUnit.SECONDS);

// Timer
Timer timer = new Timer();
timer.schedule(new TimerTask() {
    @Override
    public void run() {
        System.out.println("Timer task");
    }
}, 1000, 1000); // Delay 1s, period 1s
```

### 76. What is the difference between the scheduleAtFixedRate() and scheduleWithFixedDelay() methods?

**Answer:**
Both methods in ScheduledExecutorService are used for periodic task execution, but they differ in how they schedule subsequent executions:

- **scheduleAtFixedRate(Runnable command, long initialDelay, long period, TimeUnit unit):**
  - Executes tasks at approximately regular intervals
  - The period is measured from the start time of one execution to the start time of the next
  - If a task takes longer than the period, subsequent executions may start late but won't overlap
  - Good for tasks that need to run at specific intervals regardless of execution time

- **scheduleWithFixedDelay(Runnable command, long initialDelay, long delay, TimeUnit unit):**
  - Executes tasks with a fixed delay between the end of one execution and the start of the next
  - The delay is measured from the completion time of one execution to the start time of the next
  - Ensures a minimum time gap between executions
  - Good for tasks where you want to ensure a minimum pause between executions

Example:
```java
ScheduledExecutorService scheduler = Executors.newScheduledThreadPool(1);

// Tasks execute every 1 second (measured from start to start)
scheduler.scheduleAtFixedRate(task, 0, 1, TimeUnit.SECONDS);

// Tasks execute with 1 second gap between executions
scheduler.scheduleWithFixedDelay(task, 0, 1, TimeUnit.SECONDS);
```

### 77. What is the ReentrantLock class?

**Answer:**
ReentrantLock is an implementation of the Lock interface that provides the same basic behavior and semantics as the synchronized keyword, but with extended capabilities.

Key features:
- **Reentrant:** A thread can acquire the same lock multiple times
- **Fairness option:** Can be configured for fair ordering of lock acquisition
- **Timed lock attempts:** tryLock() with timeout
- **Interruptible lock acquisition:** lockInterruptibly()
- **Condition variables:** Support for multiple wait-sets per lock

Example:
```java
ReentrantLock lock = new ReentrantLock();

lock.lock();
try {
    // Critical section
} finally {
    lock.unlock(); // Always release in a finally block
}

// With timeout
if (lock.tryLock(1, TimeUnit.SECONDS)) {
    try {
        // Critical section
    } finally {
        lock.unlock();
    }
} else {
    // Could not acquire lock within timeout
}
```

### 78. What is the ReadWriteLock interface?

**Answer:**
ReadWriteLock is an interface that maintains a pair of locks: one for read-only operations and one for write operations. Multiple threads can hold the read lock simultaneously, but the write lock is exclusive.

Key features:
- **Increased concurrency:** Multiple readers can access shared resources simultaneously
- **Write exclusivity:** Writers get exclusive access
- **Downgrading:** A thread holding the write lock can acquire the read lock and then release the write lock
- **Upgrading:** Not directly supported (can lead to deadlocks)

Implementation: ReentrantReadWriteLock

Example:
```java
ReadWriteLock rwLock = new ReentrantReadWriteLock();
Lock readLock = rwLock.readLock();
Lock writeLock = rwLock.writeLock();

// Reading (multiple threads can read simultaneously)
readLock.lock();
try {
    // Read from shared resource
} finally {
    readLock.unlock();
}

// Writing (exclusive access)
writeLock.lock();
try {
    // Modify shared resource
} finally {
    writeLock.unlock();
}
```

### 79. What is the StampedLock class?

**Answer:**
StampedLock is a capability-based lock introduced in Java 8 that supports read, write, and optimistic read modes. It's an alternative to ReadWriteLock with better performance in some scenarios.

Key features:
- **Stamped return values:** Lock acquisition methods return a stamp that is used for unlocking or converting between modes
- **Optimistic reading:** Allows reading without acquiring a lock (but must be validated)
- **No reentrant support:** Unlike ReentrantReadWriteLock, it's not reentrant
- **No fairness mode:** No support for fair ordering of lock acquisition
- **Better throughput:** Often provides better throughput than ReentrantReadWriteLock

Example:
```java
StampedLock lock = new StampedLock();

// Write lock
long writeStamp = lock.writeLock();
try {
    // Write to shared resource
} finally {
    lock.unlockWrite(writeStamp);
}

// Read lock
long readStamp = lock.readLock();
try {
    // Read from shared resource
} finally {
    lock.unlockRead(readStamp);
}

// Optimistic read
long stamp = lock.tryOptimisticRead();
// Read from shared resource
if (!lock.validate(stamp)) {
    // Resource was modified, fallback to read lock
    stamp = lock.readLock();
    try {
        // Re-read from shared resource
    } finally {
        lock.unlockRead(stamp);
    }
}
```

### 80. What is the ConcurrentHashMap class?

**Answer:**
ConcurrentHashMap is a thread-safe implementation of the Map interface designed for high concurrency. It allows multiple threads to read and write concurrently with minimal blocking.

Key features:
- **Segment locking:** Uses multiple locks, each for a different segment of the map (pre-Java 8)
- **Node locking:** Uses a more granular approach with node-level locking (Java 8+)
- **Concurrent retrieval operations:** Read operations don't block
- **Weakly consistent iterators:** Reflect the state of the map at some point during iteration
- **Null prohibition:** Does not allow null keys or values
- **Atomic operations:** Provides atomic compound operations like putIfAbsent(), replace()

Performance advantages over Hashtable:
- Better concurrency: Multiple threads can access different segments simultaneously
- Better read performance: Reads don't require locking
- Scalability: Performance scales with the number of CPUs

Example:
```java
ConcurrentHashMap<String, Integer> map = new ConcurrentHashMap<>();
map.put("one", 1);
map.put("two", 2);

// Atomic operations
map.putIfAbsent("three", 3); // Only puts if key doesn't exist
map.replace("two", 2, 22); // Replaces only if current value matches

// Concurrent iteration
for (Map.Entry<String, Integer> entry : map.entrySet()) {
    // Safe for concurrent modification
}
```

### 81. What is the CopyOnWriteArrayList class?

**Answer:**
CopyOnWriteArrayList is a thread-safe variant of ArrayList where all mutative operations (add, set, remove, etc.) create a fresh copy of the underlying array.

Key features:
- **Thread safety:** All operations are thread-safe
- **No synchronization for reads:** Readers don't block
- **Copy-on-write semantics:** Modifications create a new copy of the array
- **Weakly consistent iterators:** Reflect the state of the list at the time the iterator was created
- **No concurrent modification exceptions:** Iterators are never invalidated

Best used for:
- Lists that are primarily read and rarely modified
- Observer lists where listeners are rarely added or removed
- Small lists where the copy overhead is acceptable

Not suitable for:
- Large lists with frequent modifications
- High-performance scenarios where copying is too expensive

Example:
```java
CopyOnWriteArrayList<String> list = new CopyOnWriteArrayList<>();
list.add("one");
list.add("two");

// Safe iteration during concurrent modification
for (String item : list) {
    System.out.println(item);
    // Another thread can modify the list here without affecting this iteration
}
```

### 82. What is the BlockingQueue interface?

**Answer:**
BlockingQueue is an interface that represents a queue that additionally supports operations that wait for the queue to become non-empty when retrieving an element, and wait for space to become available when storing an element.

Key methods:
- **put(E e):** Adds an element, waiting if necessary for space to become available
- **take():** Retrieves and removes the head of the queue, waiting if necessary until an element becomes available
- **offer(E e, long timeout, TimeUnit unit):** Adds an element, waiting up to the specified time if necessary
- **poll(long timeout, TimeUnit unit):** Retrieves and removes the head of the queue, waiting up to the specified time if necessary

Implementations:
- **ArrayBlockingQueue:** Bounded, array-backed implementation
- **LinkedBlockingQueue:** Optionally bounded, linked-node implementation
- **PriorityBlockingQueue:** Unbounded priority