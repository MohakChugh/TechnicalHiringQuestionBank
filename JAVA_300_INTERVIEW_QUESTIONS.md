# 300 Java Developer Interview Questions

## Table of Contents
- [300 Java Developer Interview Questions](#300-java-developer-interview-questions)
  - [Table of Contents](#table-of-contents)
  - [Core Java Concepts](#core-java-concepts)
  - [Object-Oriented Programming](#object-oriented-programming)
  - [Java Collections Framework](#java-collections-framework)
  - [Exception Handling](#exception-handling)
  - [Multithreading and Concurrency](#multithreading-and-concurrency)
  - [Java 8+ Features](#java-8-features)
  - [Java Memory Management](#java-memory-management)
  - [Java I/O and NIO](#java-io-and-nio)
  - [Java Database Connectivity](#java-database-connectivity)

## Core Java Concepts

1. What is Java and what are its key features?
2. Explain the difference between JDK, JRE, and JVM.
3. What is the Java platform independence feature and how does it work?
4. Explain the Java execution process from source code to execution.
5. What are primitive data types in Java?
6. What is autoboxing and unboxing in Java?
7. Explain the difference between `==` and `.equals()` method.
8. What is the difference between `String`, `StringBuilder`, and `StringBuffer`?
9. Why is `String` immutable in Java?
10. How do you create an immutable class in Java?
11. What are access modifiers in Java and what is their significance?
12. Explain the difference between method overloading and method overriding.
13. What is the `super` keyword used for in Java?
14. What is the `this` keyword used for in Java?
15. Explain the `static` keyword and its uses.
16. What is the `final` keyword and how can it be used?
17. What is the difference between `final`, `finally`, and `finalize`?
18. What are packages in Java and why are they used?
19. How does the `import` statement work?
20. What is the difference between default and explicit import?
21. What is a Java wrapper class?
22. Explain pass-by-value and pass-by-reference in Java.
23. What is type casting in Java?
24. What is the difference between implicit and explicit casting?
25. What are Java literals?
26. What is the difference between `break` and `continue` statements?
27. Explain the `switch` statement and its limitations.
28. What enhancements were made to the `switch` statement in recent Java versions?
29. What are variable arguments (varargs) in Java?
30. How does the `instanceof` operator work?
31. What is the purpose of the `transient` keyword?
32. What is the purpose of the `volatile` keyword?
33. What is the difference between `==` and `===` in Java?
34. What is the purpose of the `native` keyword?
35. What is the purpose of the `strictfp` keyword?
36. What is the difference between local variables, instance variables, and class variables?
37. What is a Java constant and how do you define it?
38. What is the difference between `++i` and `i++`?
39. What is operator precedence in Java?
40. What are bitwise operators in Java?

## Object-Oriented Programming

41. What are the four main principles of OOP in Java?
42. Explain encapsulation and how it's implemented in Java.
43. What is inheritance and what are its advantages?
44. What is polymorphism and how is it achieved in Java?
45. Explain abstraction and how it's implemented in Java.
46. What is the difference between an abstract class and an interface?
47. What changes were made to interfaces in Java 8?
48. What is the difference between method hiding and method overriding?
49. Can we override a private or static method in Java?
50. What is a marker interface?
51. What is the difference between aggregation and composition?
52. What is association in Java?
53. What is the diamond problem in inheritance?
54. How does Java handle multiple inheritance?
55. What is a nested class in Java?
56. What is the difference between a nested class and an inner class?
57. What is a static nested class?
58. What is an anonymous inner class?
59. What is a local inner class?
60. What are the advantages of inner classes?
61. What is method overloading resolution in Java?
62. What is the difference between early binding and late binding?
63. What is dynamic method dispatch?
64. What is the difference between `IS-A` and `HAS-A` relationships?
65. What is cohesion and coupling in OOP?
66. What is the Liskov Substitution Principle?
67. What is the Open/Closed Principle?
68. What is the Single Responsibility Principle?
69. What is the Interface Segregation Principle?
70. What is the Dependency Inversion Principle?
71. What is the difference between abstraction and encapsulation?
72. What is a concrete class in Java?
73. Can an abstract class have a constructor?
74. Can an interface have a constructor?
75. What happens if a class implements two interfaces with the same method signature?
76. What is a default method in an interface?
77. What is a static method in an interface?
78. What is a private method in an interface (Java 9+)?
79. What is a sealed class in Java (Java 17+)?
80. What is the purpose of the `@Override` annotation?

## Java Collections Framework

81. What is the Java Collections Framework?
82. Explain the collection hierarchy in Java.
83. What is the difference between Collection and Collections?
84. What is the difference between List, Set, and Map?
85. What is the difference between ArrayList and LinkedList?
86. What is the difference between HashSet and TreeSet?
87. What is the difference between HashMap and Hashtable?
88. What is the difference between HashMap and ConcurrentHashMap?
89. What is the difference between HashMap and LinkedHashMap?
90. What is the difference between TreeMap and HashMap?
91. How does HashSet maintain uniqueness of elements?
92. How does HashMap work internally?
93. What is the load factor and initial capacity in HashMap?
94. What is rehashing in HashMap?
95. What happens if we put a key that already exists in a HashMap?
96. What is the difference between fail-fast and fail-safe iterators?
97. What is the ConcurrentModificationException and when does it occur?
98. How do you make a collection read-only?
99. How do you make a collection thread-safe?
100. What is the difference between Enumeration and Iterator?
101. What is the difference between Iterator and ListIterator?
102. What is a Comparator and Comparable in Java?
103. How do you sort a collection of custom objects?
104. What is the difference between `Arrays.sort()` and `Collections.sort()`?
105. What is the difference between `Collection.toArray()` and `Collection.toArray(T[] a)`?
106. What is the purpose of the `equals()` and `hashCode()` methods in collections?
107. What happens if you don't override `hashCode()` when overriding `equals()`?
108. What is a WeakHashMap?
109. What is an EnumMap?
110. What is an EnumSet?
111. What is a PriorityQueue?
112. What is a BlockingQueue?
113. What is a DelayQueue?
114. What is a CopyOnWriteArrayList?
115. What is a CopyOnWriteArraySet?
116. What is a SynchronizedCollection?
117. What is an IdentityHashMap?
118. What is a NavigableMap and NavigableSet?
119. What is the difference between Stack and Queue?
120. What is a Deque?

## Exception Handling

121. What is an exception in Java?
122. What is the difference between checked and unchecked exceptions?
123. What is the difference between exception and error?
124. Explain the exception hierarchy in Java.
125. What is the purpose of the `try-catch-finally` block?
126. Can `finally` block be skipped?
127. What happens if an exception is thrown in a `finally` block?
128. What is the purpose of the `throw` keyword?
129. What is the purpose of the `throws` keyword?
130. What is exception propagation?
131. What is exception chaining?
132. What is a custom exception?
133. When should you create a custom exception?
134. What is the try-with-resources statement?
135. What is the multi-catch block?
136. What is the difference between `throw` and `throws`?
137. Can we have a `try` block without a `catch` block?
138. What happens when an exception is not caught?
139. What is the OutOfMemoryError?
140. What is the StackOverflowError?
141. What is the difference between `ClassNotFoundException` and `NoClassDefFoundError`?
142. What is the purpose of the `printStackTrace()` method?
143. How do you create a custom checked exception?
144. How do you create a custom unchecked exception?
145. What is the difference between `RuntimeException` and `Exception`?
146. What is the purpose of the `assert` keyword?
147. What is the difference between assertion and exception?
148. What is the suppressed exception?
149. How do you handle multiple exceptions in a single catch block?
150. What is the best practice for exception handling in Java?

## Multithreading and Concurrency

151. What is a thread in Java?
152. What is the difference between process and thread?
153. What are the different ways to create a thread in Java?
154. What is the difference between extending Thread and implementing Runnable?
155. What is the life cycle of a thread?
156. What is the difference between `sleep()` and `wait()`?
157. What is the purpose of `join()` method?
158. What is thread synchronization?
159. What is the difference between synchronized method and synchronized block?
160. What is the purpose of the `volatile` keyword in multithreading?
161. What is a deadlock?
162. What is a livelock?
163. What is a race condition?
164. What is thread starvation?
165. What is thread priority?
166. What is context switching in multithreading?
167. What is the `java.util.concurrent` package?
168. What is an Executor framework?
169. What is a ThreadPool?
170. What is the difference between Callable and Runnable?
171. What is a Future in Java concurrency?
172. What is a CompletableFuture?
173. What is a CountDownLatch?
174. What is a CyclicBarrier?
175. What is a Semaphore?
176. What is a Phaser?
177. What is an Exchanger?
178. What is a Lock interface?
179. What is the difference between ReentrantLock and synchronized?
180. What is a ReadWriteLock?
181. What is a StampedLock?
182. What is an atomic variable?
183. What is the Fork/Join framework?
184. What is a RecursiveTask?
185. What is a RecursiveAction?
186. What is a ThreadLocal?
187. What is a daemon thread?
188. What is thread interference?
189. What is memory consistency error?
190. What is the happens-before relationship?

## Java 8+ Features

191. What are the major features introduced in Java 8?
192. What are lambda expressions and how do they work?
193. What is a functional interface?
194. What are the built-in functional interfaces in Java 8?
195. What is the Stream API?
196. What is the difference between intermediate and terminal operations in streams?
197. What is method reference in Java 8?
198. What is the Optional class and why is it used?
199. What are default methods in interfaces?
200. What are static methods in interfaces?
201. What is the new Date and Time API in Java 8?
202. What is a Collector in Stream API?
203. What is the difference between `map()` and `flatMap()` in Stream?
204. What is the difference between `findFirst()` and `findAny()`?
205. What is the difference between `anyMatch()`, `allMatch()`, and `noneMatch()`?
206. What is a parallel stream?
207. What is the `forEach()` method in Iterable interface?
208. What is the difference between `Collection.stream()` and `Collection.parallelStream()`?
209. What are the major features introduced in Java 9?
210. What is the module system in Java 9?
211. What are private methods in interfaces (Java 9)?
212. What is the `takeWhile()` and `dropWhile()` in Stream API (Java 9)?
213. What is the `ofNullable()` method in Stream (Java 9)?
214. What are the major features introduced in Java 10?
215. What is local variable type inference (var) in Java 10?
216. What are the major features introduced in Java 11?
217. What is the `isBlank()` method in String (Java 11)?
218. What is the `lines()` method in String (Java 11)?
219. What are the major features introduced in Java 12-16?
220. What are text blocks in Java (Java 13-15)?
221. What are records in Java (Java 14-16)?
222. What are sealed classes in Java (Java 15-17)?
223. What is pattern matching for instanceof in Java (Java 14-16)?
224. What are the major features introduced in Java 17?
225. What is the difference between `var`, `val`, and `const` in Java?
226. What is the `toList()` collector in Java 16?
227. What are helpful NullPointerExceptions in Java 14?
228. What is the `stripIndent()` method in Java 15?
229. What is the `formatted()` method in Java 15?
230. What is the `transform()` method in Java 12?

## Java Memory Management

231. How does memory management work in Java?
232. What is the difference between stack and heap memory?
233. What is garbage collection in Java?
234. What are the different types of garbage collectors in Java?
235. What is the generational garbage collection?
236. What are the young and old generations in garbage collection?
237. What is the permanent generation (PermGen) and Metaspace?
238. What is the difference between Serial, Parallel, and CMS garbage collectors?
239. What is the G1 garbage collector?
240. What is the Z garbage collector?
241. What is the Shenandoah garbage collector?
242. What is a memory leak in Java?
243. How do you identify and fix memory leaks in Java?
244. What is the `OutOfMemoryError` and how do you handle it?
245. What is the `StackOverflowError` and how do you handle it?
246. What is the difference between shallow and deep copy?
247. What is the difference between `finalize()` and `dispose()`?
248. What is the purpose of the `System.gc()` method?
249. What is a soft reference, weak reference, and phantom reference?
250. What is the difference between `WeakReference` and `SoftReference`?
251. What is a memory pool in JVM?
252. What is the difference between heap dump and thread dump?
253. How do you analyze a heap dump?
254. How do you analyze a thread dump?
255. What is JVM tuning?
256. What are the important JVM parameters for memory tuning?
257. What is the `-Xmx` and `-Xms` JVM parameter?
258. What is the `-XX:MaxPermSize` JVM parameter?
259. What is the `-XX:MaxMetaspaceSize` JVM parameter?
260. What is escape analysis in JVM?

## Java I/O and NIO

261. What is the difference between I/O and NIO in Java?
262. What is a stream in Java I/O?
263. What is the difference between InputStream and OutputStream?
264. What is the difference between Reader and Writer?
265. What is a BufferedReader and BufferedWriter?
266. What is a FileInputStream and FileOutputStream?
267. What is a FileReader and FileWriter?
268. What is an ObjectInputStream and ObjectOutputStream?
269. What is serialization and deserialization in Java?
270. What is the `Serializable` interface?
271. What is the `serialVersionUID`?
272. What is the `transient` keyword in serialization?
273. What is externalization in Java?
274. What is the difference between `Serializable` and `Externalizable`?
275. What is a channel in Java NIO?
276. What is a buffer in Java NIO?
277. What is a selector in Java NIO?
278. What is the difference between blocking and non-blocking I/O?
279. What is memory-mapped file I/O?
280. What is the Path interface in Java NIO?
281. What is the Files class in Java NIO?
282. What is the difference between absolute and relative paths?
283. How do you read a file line by line in Java?
284. How do you write to a file in Java?
285. How do you copy a file in Java?
286. How do you move a file in Java?
287. How do you delete a file in Java?
288. How do you check if a file exists in Java?
289. How do you create a directory in Java?
290. How do you list files in a directory in Java?

## Java Database Connectivity

291. What is JDBC?
292. What are the steps to connect to a database in Java?
293. What is a JDBC driver?
294. What are the different types of JDBC drivers?
295. What is the DriverManager class?
296. What is a Connection object?
297. What is a Statement object?
298. What is a PreparedStatement object?
299. What is a CallableStatement object?
300. What is the difference between Statement and PreparedStatement?