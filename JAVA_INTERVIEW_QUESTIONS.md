# Java Developer Interview Questions

## Core Java Concepts

### 1. What are the main principles of Object-Oriented Programming in Java?
**Answer:** Java implements four main OOP principles:
- **Encapsulation:** Bundling data and methods within a single unit (class) and restricting direct access to some components through access modifiers.
- **Inheritance:** The mechanism by which one class can inherit properties and behavior from a parent class, promoting code reuse.
- **Polymorphism:** The ability of different objects to respond to the same method call in different ways, implemented through method overloading and overriding.
- **Abstraction:** Hiding implementation details and showing only functionality to users, implemented through abstract classes and interfaces.

### 2. Explain the difference between an interface and an abstract class in Java.
**Answer:**
- **Abstract Class:** Can have both abstract and concrete methods, can have constructors, instance variables, and can provide some implementation. A class can extend only one abstract class.
- **Interface:** Prior to Java 8, could only have abstract methods; now can have default and static methods. Cannot have constructors or instance variables (only constants). A class can implement multiple interfaces.
- **Usage:** Abstract classes are used when there's a base implementation to share among related classes. Interfaces are used to define a contract that unrelated classes can implement.

### 3. What is the difference between `==` and `.equals()` in Java?
**Answer:**
- `==` compares object references (checks if both references point to the same memory location).
- `.equals()` compares the content/values of objects. For custom classes, it needs to be overridden to provide meaningful equality comparison; otherwise, it behaves like `==`.
- For primitive types, `==` compares values directly since primitives don't have methods.

### 4. Explain Java's memory management and garbage collection.
**Answer:** Java manages memory through:
- **Stack:** Stores method invocations and local variables. Memory is allocated/deallocated automatically as methods are called/returned.
- **Heap:** Stores objects. Memory is allocated when objects are created and reclaimed by the garbage collector when objects are no longer referenced.
- **Garbage Collection:** Automatic process that identifies and removes objects no longer referenced by the program. Uses different algorithms (like Mark-Sweep, Generational Collection) to efficiently manage memory.
- **JVM Tuning:** Can be configured with different GC algorithms and memory settings to optimize performance for specific applications.

### 5. What are the differences between `ArrayList` and `LinkedList`?
**Answer:**
- **Implementation:** `ArrayList` is backed by a dynamic array, while `LinkedList` is implemented as a doubly-linked list.
- **Performance:**
  - `ArrayList` provides O(1) random access but O(n) insertion/deletion in the middle.
  - `LinkedList` provides O(1) insertion/deletion at both ends but O(n) random access.
- **Memory:** `ArrayList` is more memory-efficient for storage but might waste memory during resizing. `LinkedList` requires more memory per element due to storing references.
- **Usage:** Use `ArrayList` for scenarios requiring frequent random access and `LinkedList` for frequent insertions/deletions, especially at the beginning or end.

### 6. What is the purpose of the `final` keyword in Java?
**Answer:** The `final` keyword can be applied to:
- **Variables:** Makes them constants that cannot be reassigned after initialization.
- **Methods:** Prevents method overriding in subclasses.
- **Classes:** Prevents the class from being subclassed.
- **Parameters:** Prevents the parameter from being modified within the method.
- It's used for immutability, security, and optimization (compiler can make certain optimizations with final classes/methods).

### 7. Explain Java's exception handling mechanism.
**Answer:** Java uses a try-catch-finally mechanism:
- **Checked Exceptions:** Must be either caught or declared in the method signature (e.g., IOException).
- **Unchecked Exceptions:** Runtime exceptions that don't need explicit handling (e.g., NullPointerException).
- **try-catch:** Code that might throw an exception is placed in a try block, and exception handlers are defined in catch blocks.
- **finally:** Contains code that always executes, regardless of whether an exception occurred.
- **try-with-resources:** Automatically closes resources that implement AutoCloseable.
- **Custom Exceptions:** Developers can create custom exception classes by extending Exception or RuntimeException.

### 8. What is the difference between method overloading and overriding?
**Answer:**
- **Overloading:** Multiple methods with the same name but different parameters in the same class. Resolved at compile time (static binding).
- **Overriding:** Subclass provides a specific implementation of a method already defined in the parent class. Resolved at runtime (dynamic binding).
- **Rules:** Overriding methods must have the same return type (or a subtype), same method name, same parameters, and cannot have a more restrictive access modifier.

## Java Collections Framework

### 9. Explain the Java Collections Framework hierarchy.
**Answer:** The Java Collections Framework is organized around:
- **Interfaces:** Collection (root), List, Set, Queue, Deque, Map
- **Implementations:** ArrayList, LinkedList, HashSet, TreeSet, HashMap, TreeMap, etc.
- **Algorithms:** Utility methods for operations like sorting, searching, and shuffling
- **Key Characteristics:**
  - Lists maintain insertion order and allow duplicates
  - Sets don't allow duplicates
  - Maps store key-value pairs with unique keys
  - Queues and Deques provide FIFO/LIFO operations

### 10. What is the difference between `HashMap` and `ConcurrentHashMap`?
**Answer:**
- **Thread Safety:** `HashMap` is not thread-safe, while `ConcurrentHashMap` is designed for concurrent access.
- **Locking Mechanism:** `ConcurrentHashMap` uses segment-level locking (pre-Java 8) or node-level locking (Java 8+), allowing multiple threads to modify different parts of the map simultaneously.
- **Null Values:** `HashMap` allows one null key and multiple null values, while `ConcurrentHashMap` doesn't allow null keys or values.
- **Performance:** `ConcurrentHashMap` has better performance in concurrent environments, while `HashMap` might be faster in single-threaded scenarios.
- **Iterator:** `HashMap`'s iterator is fail-fast (throws ConcurrentModificationException), while `ConcurrentHashMap`'s iterator is weakly consistent.

### 11. How does `HashSet` maintain uniqueness of elements?
**Answer:** `HashSet` uses a `HashMap` internally where:
- The `HashSet` element becomes the key in the internal `HashMap`.
- A dummy object is used as the value for all entries.
- Uniqueness is maintained by:
  1. Using the element's `hashCode()` method to determine the bucket location.
  2. Using the element's `equals()` method to check for duplicates within the bucket.
- For proper functioning, classes used with `HashSet` should override both `hashCode()` and `equals()` methods consistently.

### 12. What is the difference between `Comparable` and `Comparator` interfaces?
**Answer:**
- **Comparable:**
  - Part of `java.lang` package
  - Classes implement this interface to define their natural ordering
  - Has a single method: `compareTo()`
  - Used with `Collections.sort()` or `Arrays.sort()` without additional parameters
  - Provides only one sort sequence

- **Comparator:**
  - Part of `java.util` package
  - Separate class that implements this interface to define custom ordering
  - Has a primary method: `compare()`
  - Passed as an additional parameter to sorting methods
  - Allows multiple different sort sequences for the same class

## Concurrency and Multithreading

### 13. Explain the different ways to create a thread in Java.
**Answer:** There are two primary ways to create a thread in Java:
1. **Extending the Thread class:**
   ```java
   class MyThread extends Thread {
       public void run() {
           // Thread code here
       }
   }
   // Usage: new MyThread().start();
   ```

2. **Implementing the Runnable interface:**
   ```java
   class MyRunnable implements Runnable {
       public void run() {
           // Thread code here
       }
   }
   // Usage: new Thread(new MyRunnable()).start();
   ```

3. **Using lambda expressions (Java 8+):**
   ```java
   Thread thread = new Thread(() -> {
       // Thread code here
   });
   thread.start();
   ```

4. **Using ExecutorService:**
   ```java
   ExecutorService executor = Executors.newSingleThreadExecutor();
   executor.submit(() -> {
       // Thread code here
   });
   ```

The Runnable approach is generally preferred as it doesn't consume the single inheritance option.

### 14. What is the difference between `synchronized` method and `synchronized` block?
**Answer:**
- **Synchronized Method:** Locks the entire object (instance method) or class (static method).
  ```java
  public synchronized void method() {
      // Method code here
  }
  ```

- **Synchronized Block:** Locks only the specified object, allowing finer-grained control.
  ```java
  public void method() {
      // Non-synchronized code
      synchronized(lockObject) {
          // Synchronized code
      }
      // More non-synchronized code
  }
  ```

- **Performance:** Synchronized blocks are generally more efficient as they lock resources for a shorter time and with more granularity.
- **Flexibility:** Synchronized blocks allow specifying which object to use as the monitor lock.

### 15. Explain the `volatile` keyword in Java.
**Answer:** The `volatile` keyword:
- Ensures that a variable is always read from and written to main memory, not from thread-local caches.
- Provides visibility guarantees but not atomicity for compound operations.
- Prevents instruction reordering optimizations by the compiler/JVM for the variable.
- Is useful for flag variables that might be accessed by multiple threads.
- Does not replace the need for proper synchronization when multiple operations need to be atomic.

## Spring Framework

### 16. Explain Dependency Injection and Inversion of Control in Spring.
**Answer:**
- **Dependency Injection (DI):** A design pattern where dependencies are "injected" into objects rather than created by the objects themselves.
- **Inversion of Control (IoC):** The framework controls the flow and lifecycle of objects, not the application code.
- **Spring Implementation:** Spring container manages object creation and wiring dependencies.
- **Benefits:** Loose coupling, easier testing, modular design, and configuration externalization.
- **Types of DI in Spring:**
  - Constructor Injection: Dependencies provided through constructors
  - Setter Injection: Dependencies provided through setter methods
  - Field Injection: Dependencies injected directly into fields (using annotations)

### 17. What are the different types of bean scopes in Spring?
**Answer:** Spring supports several bean scopes:
1. **singleton:** (Default) One instance per Spring container
2. **prototype:** New instance created each time the bean is requested
3. **request:** One instance per HTTP request (web-aware contexts)
4. **session:** One instance per HTTP session (web-aware contexts)
5. **application:** One instance per ServletContext (web-aware contexts)
6. **websocket:** One instance per WebSocket session (web-aware contexts)
7. **Custom scopes:** Developers can define custom scopes

### 18. Explain the Spring MVC architecture.
**Answer:** Spring MVC follows the Model-View-Controller pattern:
1. **DispatcherServlet:** Front controller that receives all requests
2. **HandlerMapping:** Maps requests to appropriate controllers
3. **Controller:** Processes requests and returns a model name and view
4. **ModelAndView:** Contains model data and view name
5. **ViewResolver:** Resolves the logical view name to an actual view implementation
6. **View:** Renders the model data
7. **Flow:**
   - Client request → DispatcherServlet → HandlerMapping → Controller → ModelAndView → ViewResolver → View → Response

### 19. What is Spring Boot and how does it simplify Spring application development?
**Answer:** Spring Boot simplifies Spring application development through:
1. **Auto-configuration:** Automatically configures Spring and third-party libraries based on dependencies
2. **Starter Dependencies:** Curated dependencies that work together without version conflicts
3. **Embedded Servers:** Built-in Tomcat, Jetty, or Undertow servers
4. **Production-Ready Features:** Metrics, health checks, externalized configuration
5. **No XML Configuration:** Relies on Java configuration and annotations
6. **Spring Boot CLI:** Command-line tool for quick prototyping
7. **Spring Initializr:** Web tool to bootstrap applications

### 20. How does Spring handle transactions?
**Answer:** Spring provides transaction management through:
1. **Declarative Transaction Management:**
   - Using `@Transactional` annotation
   - XML-based configuration
   - Aspect-oriented approach
2. **Programmatic Transaction Management:**
   - Using `TransactionTemplate`
   - Direct use of `PlatformTransactionManager`
3. **Key Features:**
   - Consistent programming model across different transaction APIs
   - Support for both global and local transactions
   - Transaction propagation options (REQUIRED, REQUIRES_NEW, etc.)
   - Isolation levels
   - Timeout settings
   - Read-only optimization
   - Exception-based rollback rules

## Microservices and Modern Java

### 21. How would you implement a RESTful API using Spring Boot?
**Answer:** Steps to implement a RESTful API with Spring Boot:
1. **Project Setup:**
   - Use Spring Initializr with "Spring Web" dependency
   - Add other dependencies like JPA, validation, etc.

2. **Model Definition:**
   ```java
   @Entity
   public class Product {
       @Id @GeneratedValue
       private Long id;
       private String name;
       private BigDecimal price;
       // Getters, setters, constructors
   }
   ```

3. **Repository Layer:**
   ```java
   public interface ProductRepository extends JpaRepository<Product, Long> {
       List<Product> findByNameContaining(String name);
   }
   ```

4. **Service Layer:**
   ```java
   @Service
   public class ProductService {
       @Autowired
       private ProductRepository repository;

       public List<Product> findAll() {
           return repository.findAll();
       }

       public Product save(Product product) {
           return repository.save(product);
       }
       // Other methods
   }
   ```

5. **Controller Layer:**
   ```java
   @RestController
   @RequestMapping("/api/products")
   public class ProductController {
       @Autowired
       private ProductService service;

       @GetMapping
       public List<Product> getAllProducts() {
           return service.findAll();
       }

       @PostMapping
       @ResponseStatus(HttpStatus.CREATED)
       public Product createProduct(@Valid @RequestBody Product product) {
           return service.save(product);
       }

       @GetMapping("/{id}")
       public ResponseEntity<Product> getProductById(@PathVariable Long id) {
           return service.findById(id)
                   .map(ResponseEntity::ok)
                   .orElse(ResponseEntity.notFound().build());
       }
       // Other endpoints
   }
   ```

### 22. Explain the key components of a microservices architecture using Spring Cloud.
**Answer:** Spring Cloud provides tools for building microservices:

1. **Service Discovery:**
   - Netflix Eureka or Consul for service registration and discovery
   - Allows services to find and communicate with each other without hardcoded URLs

2. **API Gateway:**
   - Spring Cloud Gateway or Zuul for routing, filtering, load balancing
   - Single entry point for clients, handles cross-cutting concerns

3. **Configuration Management:**
   - Spring Cloud Config Server for centralized, version-controlled configuration
   - Allows dynamic configuration updates without redeployment

4. **Circuit Breaker:**
   - Resilience4j or Hystrix for fault tolerance
   - Prevents cascading failures, provides fallbacks

5. **Distributed Tracing:**
   - Spring Cloud Sleuth with Zipkin for tracing requests across services
   - Helps troubleshoot and monitor distributed transactions

### 23. What are the new features in Java 8, 11, and 17?
**Answer:**
**Java 8:**
- Lambda expressions and functional interfaces
- Stream API for collection processing
- Optional class for null handling
- Default and static methods in interfaces
- New Date and Time API (java.time)
- CompletableFuture for asynchronous programming

**Java 11:**
- HTTP Client API (standardized)
- String API enhancements (isBlank, lines, strip)
- Collection.toArray(IntFunction) method
- Files.readString and Files.writeString
- Running Java files without compilation (java SourceFile.java)
- Local-variable syntax for lambda parameters

**Java 17 (LTS):**
- Sealed classes and interfaces (restrict which classes can implement/extend)
- Pattern matching for switch (preview)
- Foreign Function & Memory API (incubator)
- Vector API (incubator) for SIMD operations
- Strong encapsulation of JDK internals
- Context-specific deserialization filters
- Enhanced pseudo-random number generators

### 24. How would you implement caching in a Spring Boot application?
**Answer:** Spring Boot provides several caching options:

1. **Basic Setup:**
   ```java
   @EnableCaching
   @SpringBootApplication
   public class Application {
       public static void main(String[] args) {
           SpringApplication.run(Application.class, args);
       }
   }
   ```

2. **Method-Level Caching:**
   ```java
   @Service
   public class ProductService {
       @Cacheable(value = "products", key = "#id")
       public Product findById(Long id) {
           // Method will only execute if result not in cache
           return repository.findById(id).orElseThrow();
       }

       @CachePut(value = "products", key = "#product.id")
       public Product update(Product product) {
           // Method always executes but updates cache
           return repository.save(product);
       }

       @CacheEvict(value = "products", key = "#id")
       public void delete(Long id) {
           // Removes entry from cache
           repository.deleteById(id);
       }
   }
   ```

3. **Cache Providers:**
   - Simple in-memory cache (ConcurrentHashMap)
   - Caffeine (high-performance in-memory)
   - EhCache
   - Redis (distributed caching)
   - Hazelcast (distributed caching)

### 25. How would you implement security in a Spring Boot application?
**Answer:** Spring Security implementation in Spring Boot:

1. **Basic Setup:**
   ```java
   @EnableWebSecurity
   public class SecurityConfig extends WebSecurityConfigurerAdapter {

       @Override
       protected void configure(HttpSecurity http) throws Exception {
           http
               .authorizeRequests()
                   .antMatchers("/public/**").permitAll()
                   .antMatchers("/api/admin/**").hasRole("ADMIN")
                   .anyRequest().authenticated()
               .and()
               .formLogin()
                   .loginPage("/login")
                   .permitAll()
               .and()
               .logout()
                   .permitAll();
       }

       @Override
       protected void configure(AuthenticationManagerBuilder auth) throws Exception {
           auth
               .inMemoryAuthentication()
                   .withUser("user").password(passwordEncoder().encode("password")).roles("USER")
                   .and()
                   .withUser("admin").password(passwordEncoder().encode("admin")).roles("ADMIN");
       }

       @Bean
       public PasswordEncoder passwordEncoder() {
           return new BCryptPasswordEncoder();
       }
   }
   ```

2. **JWT Authentication:**
   ```java
   @Configuration
   public class JwtSecurityConfig extends WebSecurityConfigurerAdapter {

       @Autowired
       private JwtTokenProvider tokenProvider;

       @Override
       protected void configure(HttpSecurity http) throws Exception {
           http
               .csrf().disable()
               .sessionManagement().sessionCreationPolicy(SessionCreationPolicy.STATELESS)
               .and()
               .authorizeRequests()
                   .antMatchers("/auth/**").permitAll()
                   .anyRequest().authenticated()
               .and()
               .apply(new JwtConfigurer(tokenProvider));
       }
   }
   ```

## Interview Questions for Assessing Experience

### 26. Describe a complex Java application you've built from scratch.
**Look for:** Architecture decisions, technology choices, challenges faced, solutions implemented, performance considerations, team collaboration.

### 27. How did you handle authentication and authorization in your Java projects?
**Look for:** Security awareness, implementation details, framework knowledge, best practices, threat mitigation.

### 28. What strategies did you use for error handling and logging?
**Look for:** Structured approach, centralized logging, monitoring integration, error categorization, user experience considerations.

### 29. How did you ensure your Java applications were performant?
**Look for:** Profiling tools knowledge, optimization techniques, caching strategies, database query optimization, load testing experience.

### 30. Describe your experience with Java deployment pipelines.
**Look for:** CI/CD knowledge, build tools familiarity, containerization experience, environment management, automation practices.