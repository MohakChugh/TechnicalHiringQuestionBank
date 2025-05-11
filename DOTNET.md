# .NET Interview Questions and Answers

This document contains 300 technical questions and answers for interviewing .NET developers. The questions range from basic to advanced concepts and are designed to help assess a candidate's .NET knowledge and expertise.

## C# Fundamentals

### 1. What is C#?

**Answer:**
C# (pronounced "C sharp") is a modern, object-oriented programming language developed by Microsoft as part of the .NET initiative. It was designed by Anders Hejlsberg and his team and is similar to Java in many ways. C# is used to develop a wide range of applications including desktop applications, web applications, web services, mobile apps, games, and more. It combines the power and flexibility of C++ with the simplicity of Visual Basic.

### 2. What are the key features of C#?

**Answer:**
- **Object-Oriented:** Supports encapsulation, inheritance, and polymorphism
- **Type-Safe:** Strong type checking at compile time
- **Component-Oriented:** Supports component-based development
- **Structured:** Follows structured programming approach
- **Rich Standard Library:** Extensive class library through .NET Framework/Core
- **Automatic Memory Management:** Garbage collection handles memory management
- **Version Compatibility:** Good backward compatibility between versions
- **Modern Language Features:** LINQ, async/await, pattern matching, nullable types
- **Interoperability:** Can interact with code written in other languages
- **Scalability:** Suitable for everything from small applications to large enterprise systems

### 3. What is the difference between .NET Framework, .NET Core, and .NET 5/6/7?

**Answer:**
- **.NET Framework:**
  - Original implementation of .NET
  - Windows-only
  - Includes WPF, Windows Forms, ASP.NET
  - Large API surface
  - No longer being developed (maintenance mode)

- **.NET Core (1.0-3.1):**
  - Cross-platform reimplementation of .NET
  - Open-source
  - Modular and lightweight
  - High performance
  - Command-line focused

- **.NET 5/6/7:**
  - Unification of .NET Framework and .NET Core
  - Cross-platform
  - Open-source
  - Modern features
  - Single BCL (Base Class Library)
  - .NET 5 was the first unified version
  - .NET 6 added more unified libraries and improved performance
  - .NET 7 further enhanced performance and added more features

### 4. What is CLR (Common Language Runtime)?

**Answer:**
The Common Language Runtime (CLR) is the virtual machine component of the .NET framework that manages the execution of .NET programs. It provides services such as:

- **Memory Management:** Automatic garbage collection
- **Type Safety:** Enforces type safety during execution
- **Exception Handling:** Provides a structured exception handling mechanism
- **JIT Compilation:** Just-In-Time compilation of IL code to native code
- **Security:** Code access security and verification
- **Thread Management:** Manages threading and synchronization
- **Interoperability:** Enables interaction with unmanaged code

The CLR is responsible for loading and running programs and providing services that make the development process easier.

### 5. What is CTS (Common Type System)?

**Answer:**
The Common Type System (CTS) is a standard that specifies how type definitions and specific values of types are represented in the .NET Framework. It establishes a framework that enables cross-language integration, type safety, and high-performance code execution.

Key aspects of CTS:
- Defines rules that all languages must follow when creating types
- Provides a library of built-in data types
- Defines rules for creating custom value and reference types
- Enables objects written in different .NET languages to interact with each other
- Ensures type safety across different .NET languages
- Defines how types are declared, used, and managed at runtime

### 6. What is CLS (Common Language Specification)?

**Answer:**
The Common Language Specification (CLS) is a set of rules and constraints that every .NET language must follow to be fully interoperable with other .NET languages. It's a subset of the Common Type System (CTS).

Key aspects of CLS:
- Defines the minimum standards that .NET languages must meet
- Ensures cross-language compatibility
- Specifies naming conventions, data types, and language features that must be supported
- Helps developers create libraries that are accessible from all .NET languages
- CLS-compliant code can be used by any .NET language that follows the CLS rules

For example, a CLS-compliant library avoids using unsigned integers as method parameters because some .NET languages (like earlier versions of Visual Basic .NET) don't support them.

### 7. What is IL (Intermediate Language)?

**Answer:**
Intermediate Language (IL), also known as MSIL (Microsoft Intermediate Language) or CIL (Common Intermediate Language), is a CPU-independent instruction set into which .NET source code is compiled.

Key aspects of IL:
- Platform and language-independent code representation
- Similar to assembly language but with object-oriented features
- Contains instructions for loading, storing, initializing, and calling methods on objects
- Includes instructions for arithmetic and logical operations, control flow, direct memory access, exception handling
- Converted to native machine code by the Just-In-Time (JIT) compiler at runtime
- Can be inspected and disassembled using tools like ILDASM (IL Disassembler)

The compilation process:
1. Source code (.cs, .vb, etc.) → Compiler → IL code (.dll or .exe)
2. IL code → JIT Compiler → Native machine code (at runtime)

### 8. What is an Assembly in .NET?

**Answer:**
An assembly is the fundamental unit of deployment, version control, reuse, activation scoping, and security permissions in .NET. It's a compiled code library used for deployment, versioning, and security.

Key characteristics:
- **Physical structure:** One or more files (DLL or EXE)
- **Logical structure:** Contains modules, types, resources
- **Self-describing:** Contains metadata about types, members, references (manifest)
- **Version control:** Has a specific version number
- **Security boundary:** Has specific security permissions
- **Deployment unit:** Can be deployed as a unit
- **Types:** Can be private or shared (GAC)

Components of an assembly:
- **Assembly manifest:** Contains assembly metadata, version info, security info
- **Type metadata:** Information about the types
- **MSIL code:** The compiled code
- **Resources:** Images, strings, etc.

### 9. What is the difference between a Value Type and a Reference Type?

**Answer:**
| Feature | Value Type | Reference Type |
|---------|------------|---------------|
| Storage | Stored directly in the stack or inline in containing type | Reference stored on stack, object stored on heap |
| Memory allocation | Memory allocated on the stack | Memory allocated on the heap |
| Garbage collection | Not subject to garbage collection | Subject to garbage collection |
| Default initialization | Zero/null equivalent for each field | null |
| Assignment behavior | Creates a copy of the value | Creates a copy of the reference |
| Examples | int, float, char, bool, struct, enum | class, interface, delegate, string, array, object |
| Inheritance | Cannot be inherited (except for enums from System.Enum) | Can be inherited (except when sealed) |
| Nullability | Not nullable by default (can use nullable value types) | Nullable by default |

### 10. What are the different types of classes in C#?

**Answer:**
C# supports several types of classes, each with specific characteristics:

- **Standard Class:** Basic class that can be instantiated and inherited
  ```csharp
  public class MyClass { }
  ```

- **Static Class:** Cannot be instantiated, contains only static members
  ```csharp
  public static class Utilities { }
  ```

- **Abstract Class:** Cannot be instantiated, may contain abstract methods
  ```csharp
  public abstract class Shape { }
  ```

- **Sealed Class:** Cannot be inherited
  ```csharp
  public sealed class FinalClass { }
  ```

- **Partial Class:** Split across multiple source files
  ```csharp
  public partial class Customer { }
  ```

- **Nested Class:** Defined within another class
  ```csharp
  public class Container {
      private class Nested { }
  }
  ```

- **Generic Class:** Parameterized by one or more types
  ```csharp
  public class List<T> { }
  ```

- **Record Class (C# 9+):** Immutable reference type with value-based equality
  ```csharp
  public record Person(string FirstName, string LastName);
  ```

### 11. What is the difference between a Class and a Structure?

**Answer:**
| Feature | Class | Structure |
|---------|-------|-----------|
| Type | Reference type | Value type |
| Storage | Heap | Stack (or inline in containing type) |
| Default constructor | Provided if no constructor is defined | Cannot be parameterless, provided only if no constructor is defined |
| Inheritance | Can inherit from other classes | Cannot inherit from other structs, but can implement interfaces |
| Destructors | Can have destructors | Cannot have destructors |
| Assignment | Copies the reference | Copies the entire value |
| Nullability | Can be null | Cannot be null (unless nullable struct) |
| Usage | Complex objects with identity, inheritance | Small, simple objects with value semantics |
| Performance | Slower for small objects due to heap allocation | Faster for small objects due to stack allocation |

### 12. What are Properties in C#?

**Answer:**
Properties in C# are members that provide a flexible mechanism to read, write, or compute the value of a private field. They expose fields to the outside world through accessors (getters and setters) while enabling validation, computation, or other logic.

Types of properties:
- **Read-Write Property:** Has both get and set accessors
  ```csharp
  public int Age { get; set; }
  ```

- **Read-Only Property:** Has only a get accessor
  ```csharp
  public int Age { get; }
  ```

- **Write-Only Property:** Has only a set accessor
  ```csharp
  public string Password { set; }
  ```

- **Auto-Implemented Property:** Compiler creates a backing field
  ```csharp
  public string Name { get; set; }
  ```

- **Property with Backing Field:** Manually implemented with a private field
  ```csharp
  private int _age;
  public int Age {
      get { return _age; }
      set {
          if (value >= 0) _age = value;
      }
  }
  ```

- **Expression-Bodied Property (C# 6+):**
  ```csharp
  public string FullName => $"{FirstName} {LastName}";
  ```

- **Init-Only Property (C# 9+):**
  ```csharp
  public string Name { get; init; }
  ```

### 13. What are Indexers in C#?

**Answer:**
Indexers allow objects to be indexed like arrays. They provide a way to access elements of a class or struct using the array-like syntax with square brackets [].

Key features:
- Enable array-like access to objects
- Can be overloaded (multiple indexers with different parameter types)
- Can have get and set accessors
- Can take multiple parameters
- Parameters can be of any type

Example:
```csharp
public class StringCollection
{
    private string[] strings = new string[10];

    public string this[int index]
    {
        get { return strings[index]; }
        set { strings[index] = value; }
    }

    // Overloaded indexer with string parameter
    public string this[string name]
    {
        get {
            foreach (string s in strings)
            {
                if (s.Contains(name))
return s;
                }
            }
        }

        // Usage
        var collection = new StringCollection();
        collection[0] = "Hello";  // Set using int indexer
        string value = collection[0];  // Get using int indexer
        string search = collection["He"];  // Get using string indexer
    }
}
```

### 14. What are Delegates in C#?

**Answer:**
Delegates in C# are type-safe function pointers that can reference methods with compatible signatures. They enable scenarios like callbacks, events, and lambda expressions.

Key characteristics:
- Reference type that holds a reference to a method
- Type-safe (signature checking at compile time)
- Can reference both static and instance methods
- Can be chained (multicast delegates)
- Foundation for events in C#

Types of delegates:
- **Single-cast delegate:** References a single method
- **Multicast delegate:** References multiple methods
- **Generic delegates:** Action<T>, Func<T>, Predicate<T>

Example:
```csharp
// Delegate declaration
public delegate int MathOperation(int x, int y);

// Methods matching the delegate signature
public static int Add(int a, int b) => a + b;
public static int Subtract(int a, int b) => a - b;

// Usage
MathOperation operation = Add;
int result = operation(5, 3);  // result = 8

// Multicast delegate
operation += Subtract;
// When invoked, returns the result of the last method
result = operation(5, 3);  // result = 2
```

### 15. What are Events in C#?

**Answer:**
Events in C# provide a way for a class to notify other classes when something of interest occurs. They are based on the publisher-subscriber model and are built on delegates.

Key characteristics:
- Based on delegate types
- Can only be invoked from within the declaring class
- Subscribers can register and unregister handlers
- Typically follow the EventHandler pattern
- Thread-safe when properly implemented

Components:
- **Publisher:** The class that declares and raises the event
- **Subscriber:** The class that registers handlers for the event
- **Event Handler:** The method that responds to the event

Example:
```csharp
// Publisher class
public class Button
{
    // Event declaration
    public event EventHandler Click;

    // Method to raise the event
    protected virtual void OnClick(EventArgs e)
    {
        Click?.Invoke(this, e);
    }

    public void PerformClick()
    {
        OnClick(EventArgs.Empty);
    }
}

// Subscriber class
public class Form
{
    private Button button;

    public Form()
    {
        button = new Button();
        // Subscribe to the event
        button.Click += Button_Click;
    }

    // Event handler
    private void Button_Click(object sender, EventArgs e)
    {
        Console.WriteLine("Button was clicked!");
    }
}
```

### 16. What is the difference between a Delegate and an Event?

**Answer:**
| Feature | Delegate | Event |
|---------|----------|-------|
| Purpose | General-purpose method reference | Specific notification mechanism |
| Access | Can be invoked by any code that has access to it | Can only be invoked from within the declaring class |
| Assignment | Can be directly assigned a new value | Cannot be directly assigned, only += and -= operations |
| Null check | Caller must check for null before invoking | Often uses the ?. operator for null checking |
| Invocation | Directly invoked like a method | Typically invoked through a protected "On[EventName]" method |
| Declaration | `public delegate void MyDelegate();` | `public event MyDelegate MyEvent;` |
| Usage pattern | General method references, callbacks | Publisher-subscriber pattern |

### 17. What are Anonymous Methods in C#?

**Answer:**
Anonymous methods are methods without a name that can be defined inline where a delegate is expected. They were introduced in C# 2.0 and provide a way to pass code blocks as parameters.

Key features:
- Defined using the `delegate` keyword
- Can access variables from the containing scope (closure)
- Can be assigned to delegates
- No separate method declaration needed
- Precursor to lambda expressions

Example:
```csharp
// Delegate type
public delegate void PrintDelegate(string message);

// Using anonymous method
PrintDelegate print = delegate(string message) {
    Console.WriteLine(message);
};

// Invoking the delegate
print("Hello, World!");

// Anonymous method as an event handler
button.Click += delegate(object sender, EventArgs e) {
    Console.WriteLine("Button clicked!");
};

// Anonymous method with closure
int counter = 0;
Action incrementCounter = delegate() {
    counter++;  // Accessing variable from outer scope
};
```

### 18. What are Lambda Expressions in C#?

**Answer:**
Lambda expressions are a concise way to represent anonymous methods using a more readable syntax. They were introduced in C# 3.0 and are particularly useful for LINQ and functional-style programming.

Syntax:
- `(parameters) => expression` (expression lambda)
- `(parameters) => { statements; }` (statement lambda)

Key features:
- More concise than anonymous methods
- Can have zero, one, or multiple parameters
- Parameter types can often be inferred
- Can access variables from the containing scope (closure)
- Can be used with delegates, LINQ, and expression trees

Examples:
```csharp
// Expression lambda with one parameter
Func<int, int> square = x => x * x;

// Statement lambda with multiple parameters
Func<int, int, int> add = (x, y) => {
    return x + y;
};

// Lambda with no parameters
Action sayHello = () => Console.WriteLine("Hello");

// Lambda with type annotations
Func<double, double, double> divide = (double x, double y) => x / y;

// Lambda in LINQ
var evenNumbers = numbers.Where(n => n % 2 == 0);

// Lambda with closure
int factor = 5;
Func<int, int> multiply = n => n * factor;
```

### 19. What is the difference between Anonymous Methods and Lambda Expressions?

**Answer:**
| Feature | Anonymous Methods | Lambda Expressions |
|---------|-------------------|-------------------|
| Syntax | More verbose: `delegate(parameters) { statements }` | More concise: `parameters => expression` or `parameters => { statements }` |
| Introduction | C# 2.0 | C# 3.0 |
| Parameter types | Must be explicitly typed | Can be inferred |
| Expression form | Must use statement block with return | Can use expression form without return |
| Expression trees | Cannot be converted to expression trees | Can be converted to expression trees |
| Empty parameter list | `delegate() { statements }` | `() => statements` |
| Implicit parameters | Not supported | Supported (e.g., LINQ query expressions) |

### 20. What is LINQ?

**Answer:**
LINQ (Language Integrated Query) is a set of features introduced in C# 3.0 that adds native data querying capabilities to .NET languages. It provides a consistent query experience for objects (LINQ to Objects), relational databases (LINQ to SQL/Entity Framework), XML (LINQ to XML), and other data sources.

Key components:
- **Query syntax:** SQL-like syntax integrated into the language
- **Method syntax:** Extension methods like Where, Select, OrderBy
- **Query operators:** Filter, project, sort, group, join, etc.
- **Expression trees:** Represent code as data for providers to translate
- **Lambda expressions:** Concise way to write predicates and projections

Benefits:
- Type safety at compile time
- IntelliSense support
- Consistent query pattern across different data sources
- Declarative style focusing on what, not how
- Composable queries

Example (query syntax):
```csharp
var result = from p in products
             where p.Price > 100
             orderby p.Name
             select new { p.Name, p.Price };
```

Example (method syntax):
```csharp
var result = products
    .Where(p => p.Price > 100)
    .OrderBy(p => p.Name)
    .Select(p => new { p.Name, p.Price });
```

### 21. What are the different types of LINQ query operators?

**Answer:**
LINQ query operators can be categorized based on their functionality:

1. **Filtering Operators:**
   - Where: Filters based on a predicate
   - OfType: Filters based on type

2. **Projection Operators:**
   - Select: Projects each element to a new form
   - SelectMany: Projects and flattens sequences

3. **Sorting Operators:**
   - OrderBy: Sorts in ascending order
   - OrderByDescending: Sorts in descending order
   - ThenBy: Secondary sorting in ascending order
   - ThenByDescending: Secondary sorting in descending order
   - Reverse: Reverses the sequence

4. **Grouping Operators:**
   - GroupBy: Groups elements by a key
   - ToLookup: Creates a lookup from a sequence

5. **Join Operators:**
   - Join: Inner join of two sequences
   - GroupJoin: Group join of two sequences
   - Zip: Combines two sequences

6. **Set Operators:**
   - Distinct: Removes duplicates
   - Union: Combines unique elements from two sequences
   - Intersect: Common elements in two sequences
   - Except: Elements in first but not in second sequence

7. **Element Operators:**
   - First/FirstOrDefault: First element (or default if empty)
   - Last/LastOrDefault: Last element (or default if empty)
   - Single/SingleOrDefault: The only element (or default if empty)
   - ElementAt/ElementAtOrDefault: Element at specific position
   - DefaultIfEmpty: Returns default value if sequence is empty

8. **Aggregation Operators:**
   - Count/LongCount: Number of elements
   - Sum: Sum of values
   - Min/Max: Minimum/maximum value
   - Average: Average of values
   - Aggregate: Custom aggregation

9. **Quantifier Operators:**
   - Any: Tests if any element satisfies a condition
   - All: Tests if all elements satisfy a condition
   - Contains: Tests if sequence contains an element

10. **Partitioning Operators:**
    - Take: Takes a specified number of elements
    - Skip: Skips a specified number of elements
    - TakeLast: Takes last N elements
    - SkipLast: Skips last N elements
    - TakeWhile: Takes elements while condition is true
    - SkipWhile: Skips elements while condition is true

11. **Generation Operators:**
    - Range: Generates a sequence of integers
    - Repeat: Generates a sequence with repeated value
    - Empty: Returns an empty sequence

12. **Conversion Operators:**
    - ToArray: Converts to array
    - ToList: Converts to List<T>
    - ToDictionary: Converts to Dictionary<K,V>
    - ToHashSet: Converts to HashSet<T>
    - AsEnumerable: Returns as IEnumerable<T>
    - AsQueryable: Returns as IQueryable<T>

### 22. What is the difference between IEnumerable and IQueryable?

**Answer:**
| Feature | IEnumerable<T> | IQueryable<T> |
|---------|---------------|---------------|
| Namespace | System.Collections.Generic | System.Linq |
| Query execution | Client-side (in-memory) | Provider-side (e.g., database server) |
| Expression evaluation | Evaluates the entire query in memory | Can translate expressions to other query languages (e.g., SQL) |
| Performance with large data | Less efficient for large datasets from external sources | More efficient as filtering happens at the source |
| LINQ providers | LINQ to Objects | LINQ to SQL, Entity Framework, etc. |
| Expression representation | Delegates | Expression trees |
| Deferred execution | Supports deferred execution | Supports deferred execution |
| Method resolution | Resolved at compile time | Can be resolved at runtime |
| Usage | Local collections, simple scenarios | Remote data sources, databases |

Example of the difference:
```csharp
// IEnumerable - filtering happens in memory after all data is fetched
IEnumerable<Customer> customers = dbContext.Customers;
var filteredCustomers = customers.Where(c => c.Age > 30); // SQL: SELECT * FROM Customers

// IQueryable - filtering happens at the database level
IQueryable<Customer> customers = dbContext.Customers;
var filteredCustomers = customers.Where(c => c.Age > 30); // SQL: SELECT * FROM Customers WHERE Age > 30
```

### 23. What is Deferred Execution in LINQ?

**Answer:**
Deferred execution (also called lazy evaluation) is a LINQ feature where query execution is delayed until the query results are actually needed. The query is not executed when it's defined but when it's enumerated.

Key aspects:
- Query definition and execution are separate
- Query is executed when results are iterated over
- Allows for building queries in stages
- Can improve performance by avoiding unnecessary operations
- Enables composition of complex queries

Examples of deferred execution:
```csharp
// Query is defined here but not executed
var query = numbers.Where(n => n > 5).Select(n => n * 2);

// Query is executed here when results are enumerated
foreach (var item in query) {
    Console.WriteLine(item);
}

// Or when calling methods that force execution
int count = query.Count();
List<int> list = query.ToList();
int[] array = query.ToArray();
```

Operations that cause immediate execution:
- Conversion operators: ToList(), ToArray(), ToDictionary()
- Element operators: First(), Last(), Single(), ElementAt()
- Aggregate operators: Count(), Sum(), Average(), Min(), Max()

### 24. What is the difference between First(), FirstOrDefault(), Single(), and SingleOrDefault()?

**Answer:**
These LINQ methods retrieve elements from a sequence but have different behaviors:

| Method | Empty Sequence | One Element | Multiple Elements |
|--------|---------------|-------------|-------------------|
| First() | Throws InvalidOperationException | Returns the element | Returns the first element |
| FirstOrDefault() | Returns default value | Returns the element | Returns the first element |
| Single() | Throws InvalidOperationException | Returns the element | Throws InvalidOperationException |
| SingleOrDefault() | Returns default value | Returns the element | Throws InvalidOperationException |

When to use each:
- **First():** When you expect at least one element and want the first one
- **FirstOrDefault():** When you want the first element but the sequence might be empty
- **Single():** When you expect exactly one element and want to enforce this constraint
- **SingleOrDefault():** When you expect zero or one element and want to enforce this constraint

Example:
```csharp
var numbers = new[] { 1, 2, 3, 4, 5 };

// First/FirstOrDefault
var first = numbers.First(); // 1
var firstEven = numbers.First(n => n % 2 == 0); // 2
var firstOrDefault = numbers.FirstOrDefault(n => n > 10); // 0 (default)

// Single/SingleOrDefault
var single = numbers.Where(n => n == 3).Single(); // 3
var singleOrDefault = numbers.SingleOrDefault(n => n == 6); // 0 (default)
// This will throw: var error = numbers.Single(); // Error: Sequence contains more than one element
```

### 25. What are Extension Methods in C#?

**Answer:**
Extension methods allow you to add methods to existing types without modifying the original type, creating a derived type, or using interfaces. They are static methods defined in static classes but called as if they were instance methods.

Key characteristics:
- Defined in static classes
- First parameter has the `this` modifier
- Called like instance methods on the extended type
- Cannot override existing methods
- Can extend interfaces
- Commonly used in LINQ (e.g., Where, Select)

Example:
```csharp
// Extension method definition
public static class StringExtensions
{
    public static bool IsNullOrEmpty(this string str)
    {
        return string.IsNullOrEmpty(str);
    }

    public static string Reverse(this string str)
    {
        if (string.IsNullOrEmpty(str)) return str;

        char[] chars = str.ToCharArray();
        Array.Reverse(chars);
        return new string(chars);
    }
}

// Usage
string name = "John";
bool isEmpty = name.IsNullOrEmpty(); // false
string reversed = name.Reverse(); // "nhoJ"
```

### 26. What is the difference between "throw" and "throw ex" in exception handling?

**Answer:**
Both `throw` and `throw ex` are used to propagate exceptions, but they behave differently regarding the stack trace:

- **throw:** Re-throws the current exception preserving the original stack trace
- **throw ex:** Throws the exception again but resets the stack trace to the current location

Example:
```csharp
try
{
    // Some code that throws an exception
    int result = 10 / 0; // Throws DivideByZeroException
}
catch (DivideByZeroException ex)
{
    // Option 1: Preserves original stack trace
    throw; // Stack trace shows the original error at 10/0

    // Option 2: Resets stack trace to this location
    throw ex; // Stack trace shows the error at this line, original location is lost
}
```

Best practice:
- Use `throw` when you want to preserve the original error context
- Use `throw ex` only when you deliberately want to hide the original error location (rare)
- Consider using `throw new SomeException("Message", ex)` to wrap the exception while preserving the inner exception

### 27. What are the different ways to handle exceptions in C#?

**Answer:**
C# provides several mechanisms for exception handling:

1. **try-catch block:**
   ```csharp
   try
   {
       // Code that might throw an exception
   }
   catch (SpecificException ex)
   {
       // Handle specific exception
   }
   catch (Exception ex)
   {
       // Handle any other exception
   }
   ```

2. **try-catch-finally block:**
   ```csharp
   try
   {
       // Code that might throw an exception
   }
   catch (Exception ex)
   {
       // Handle exception
   }
   finally
   {
       // Code that always executes, whether exception occurred or not
       // Typically used for cleanup operations
   }
   ```

3. **try-finally block:**
   ```csharp
   try
   {
       // Code that might throw an exception
   }
   finally
   {
       // Cleanup code
   }
   ```

4. **Exception filters (C# 6+):**
   ```csharp
   try
   {
       // Code that might throw an exception
   }
   catch (WebException ex) when (ex.Status == WebExceptionStatus.Timeout)
   {
       // Handle timeout exceptions
   }
   ```

5. **using statement (for IDisposable objects):**
   ```csharp
   using (var resource = new SomeResource())
   {
       // Use resource - Dispose() is called automatically in a finally block
   }
   ```

6. **try-catch with exception propagation:**
   ```csharp
   try
   {
       // Code that might throw an exception
   }
   catch (Exception ex)
   {
       // Log or process exception
       throw; // Re-throw to propagate up the call stack
   }
   ```

7. **Global exception handling:**
   - WinForms: Application.ThreadException event
   - WPF: Application.DispatcherUnhandledException event
   - ASP.NET: Global.asax Application_Error method
   - ASP.NET Core: UseExceptionHandler middleware
   - Console: AppDomain.CurrentDomain.UnhandledException event

### 28. What is the difference between a Throw expression and a Throw statement?

**Answer:**
In C#, there are two ways to throw exceptions:

**Throw Statement:**
- Traditional way to throw exceptions
- Can be used as a standalone statement
- Available since C# 1.0
- Used in statement contexts

Example:
```csharp
if (value == null)
{
    throw new ArgumentNullException(nameof(value));
}
```

**Throw Expression (C# 7.0+):**
- Can be used within expressions
- Enables throwing exceptions in contexts where statements aren't allowed
- Returns a value of the appropriate type for the expression context
- Commonly used with null-coalescing, conditional, and expression-bodied members

Example:
```csharp
// In conditional operator
string name = firstName ?? throw new ArgumentNullException(nameof(firstName));

// In expression-bodied members
public string GetValue(string key) =>
    _dictionary.TryGetValue(key, out var value)
        ? value
        : throw new KeyNotFoundException($"Key '{key}' not found");

// In null-coalescing operator
public string Process(string input) =>
    ProcessNonNull(input ?? throw new ArgumentNullException(nameof(input)));
```

The key difference is that throw expressions can be used within expressions, while throw statements can only be used as standalone statements.

### 29. What is the difference between "is" and "as" operators?

**Answer:**
Both operators are used for type checking and conversion, but they work differently:

**is operator:**
- Checks if an object is compatible with a specified type
- Returns a boolean (true/false)
- Does not perform conversion
- Can be used with pattern matching (C# 7.0+)

```csharp
object obj = "Hello";
if (obj is string) // Returns true
{
    // obj is a string
    string str = (string)obj; // Explicit cast still needed
}

// With pattern matching (C# 7.0+)
if (obj is string str2) // Returns true and assigns to str2
{
    // Use str2 directly
}
```

**as operator:**
- Attempts to convert an object to a specified type
- Returns null if conversion fails (instead of throwing an exception)
- Can only be used with reference types and nullable value types
- Does not work with non-nullable value types

```csharp
object obj = "Hello";
string str = obj as string; // Returns "Hello"
if (str != null)
{
    // Use str
}

object num = 123;
string numStr = num as string; // Returns null (conversion not possible)
```

**Key differences:**

| Feature | is | as |
|---------|----|----|
| Purpose | Type checking | Type conversion |
| Return value | Boolean | Converted object or null |
| Failure behavior | Returns false | Returns null |
| Works with value types | Yes | Only with nullable value types |
| Exception throwing | Never throws | Never throws |
| Pattern matching | Supports (C# 7.0+) | Does not support |
| Performance | Slightly slower | Slightly faster for reference conversions |

**When to use each:**
- Use `is` when you only need to check the type without conversion
- Use `is` with pattern matching when you want to check and convert in one step
- Use `as` when you want to attempt a conversion that might fail
- Use explicit casting when you're certain about the type and want exceptions for invalid conversions

### 30. What are nullable types in C# and how do you use them?

**Answer:**
Nullable types in C# allow value types (like int, bool, DateTime) to represent all the values of the underlying type, plus an additional null value. This is useful when dealing with databases, user input, or any scenario where a value might be missing or undefined.

**Basic syntax:**
```csharp
// Declaration using ? syntax
int? nullableInt = null;
bool? nullableBool = null;
DateTime? nullableDate = null;

// Alternative syntax using Nullable<T>
Nullable<int> nullableInt2 = null;
Nullable<bool> nullableBool2 = null;
```

**Key properties and methods:**
- **HasValue:** Boolean property that returns true if the nullable type has a value
- **Value:** Gets the value (throws InvalidOperationException if HasValue is false)
- **GetValueOrDefault():** Gets the value or the default value of the underlying type
- **GetValueOrDefault(defaultValue):** Gets the value or a specified default value

**Usage examples:**
```csharp
// Checking for null
int? number = null;
if (number.HasValue)
{
    Console.WriteLine($"Value: {number.Value}");
}
else
{
    Console.WriteLine("No value");
}

// Using GetValueOrDefault
int result = number.GetValueOrDefault(); // result = 0
int result2 = number.GetValueOrDefault(10); // result2 = 10

// Null coalescing operator
int definiteValue = number ?? 42; // definiteValue = 42

// Conditional access
int? length = someString?.Length; // null if someString is null
```

**Nullable reference types (C# 8.0+):**
C# 8.0 introduced nullable reference types, which help prevent null reference exceptions by making nullability part of the type system for reference types as well.

```csharp
// Enable nullable reference types
#nullable enable

string nonNullableString = null; // Warning: assignment of null to non-nullable reference
string? nullableString = null; // OK: explicitly nullable reference

// Null-forgiving operator (!)
string nonNull = nullableString!; // Tells compiler to treat as non-null
```

**Nullable value types vs. nullable reference types:**
- Nullable value types add null capability to value types
- Nullable reference types add compiler warnings for potential null references
- Nullable value types are implemented using the Nullable<T> struct
- Nullable reference types are implemented using compiler analysis and warnings

**Common operations with nullable types:**
```csharp
// Implicit conversion from non-nullable to nullable
int regularInt = 10;
int? nullableInt = regularInt; // OK

// Explicit conversion from nullable to non-nullable
int backToRegular = (int)nullableInt; // Throws if nullableInt is null

// Safer conversion with null coalescing
int safeInt = nullableInt ?? 0;

// Comparing nullable values
int? a = 5;
int? b = 10;
bool? result = a < b; // true
bool? nullComparison = a < null; // null

// Nullable arithmetic
int? sum = a + b; // 15
int? product = a * null; // null
```

**Best practices:**
- Use nullable types when a value might legitimately be missing
- Always check HasValue before accessing Value
- Consider using null coalescing (??) or conditional access (?.) for cleaner code
- With C# 8.0+, enable nullable reference types to catch potential null references
- Be careful with operations that might produce null results
