# 300 .NET Developer Interview Questions

## Table of Contents
- [300 .NET Developer Interview Questions](#300-net-developer-interview-questions)
  - [Table of Contents](#table-of-contents)
  - [C# Fundamentals](#c-fundamentals)
  - [.NET Framework and .NET Core](#net-framework-and-net-core)
  - [Object-Oriented Programming](#object-oriented-programming)
  - [LINQ and Collections](#linq-and-collections)
  - [Asynchronous Programming](#asynchronous-programming)
  - [Memory Management and Garbage Collection](#memory-management-and-garbage-collection)
  - [Exception Handling](#exception-handling)
  - [Reflection and Attributes](#reflection-and-attributes)
  - [Entity Framework](#entity-framework)
  - [ASP.NET Core](#aspnet-core)
  - [Web API](#web-api)
  - [MVC Architecture](#mvc-architecture)
  - [Dependency Injection](#dependency-injection)
  - [Unit Testing](#unit-testing)
  - [Design Patterns](#design-patterns)

## C# Fundamentals

1. What is C# and what are its key features?
2. Explain the difference between value types and reference types in C#.
3. What are the access modifiers in C# and what do they do?
4. What is the difference between `const` and `readonly` in C#?
5. Explain the concept of boxing and unboxing in C#.
6. What are nullable types in C# and how do you use them?
7. What is the difference between `string` and `StringBuilder` in C#?
8. What are extension methods in C# and how do you create them?
9. What is the purpose of the `using` statement in C#?
10. What are anonymous types in C#?
11. What are implicitly typed local variables (var) and when should they be used?
12. What are generics in C# and why are they useful?
13. What is the difference between `==` and `Equals()` in C#?
14. What are indexers in C# and how do you implement them?
15. What is the difference between `is` and `as` operators in C#?
16. What are delegates in C# and how do they work?
17. What are events in C# and how are they different from delegates?
18. What are lambda expressions in C# and how do you use them?
19. What are expression-bodied members in C#?
20. What are pattern matching features in C#?
21. What are tuples in C# and how do you use them?
22. What are records in C# and how do they differ from classes?
23. What are init-only properties in C#?
24. What is the null-coalescing operator (`??`) and null-conditional operator (`?.`) in C#?
25. What are the different types of literals in C#?
26. What is the difference between `break` and `continue` statements?
27. What is the `yield` keyword in C# and how does it work?
28. What are partial classes and methods in C#?
29. What are operator overloading and method overloading in C#?
30. What are the different parameter types in C# (ref, out, params)?

## .NET Framework and .NET Core

31. What is the difference between .NET Framework and .NET Core?
32. What is .NET Standard and why is it important?
33. What is the Common Language Runtime (CLR) and what does it do?
34. What is the Common Type System (CTS) in .NET?
35. What is the Common Language Specification (CLS) in .NET?
36. What is the Global Assembly Cache (GAC)?
37. What is the difference between managed and unmanaged code?
38. What is the difference between JIT and AOT compilation?
39. What is the purpose of the app.config and web.config files?
40. What is the difference between Debug and Release builds?
41. What are the benefits of .NET Core over .NET Framework?
42. What is the IIS integration with .NET applications?
43. What is the role of the Microsoft Intermediate Language (MSIL)?
44. What is the difference between SDK and Runtime in .NET?
45. What is the purpose of the `AssemblyInfo.cs` file?
46. What are the different types of assemblies in .NET?
47. What is the difference between private and shared assemblies?
48. What is the purpose of strong naming in .NET assemblies?
49. What is the role of the Base Class Library (BCL) in .NET?
50. What is the difference between .NET Core and .NET 5/6?

## Object-Oriented Programming

51. What are the four pillars of Object-Oriented Programming?
52. What is encapsulation and how is it implemented in C#?
53. What is inheritance and what are its advantages?
54. What is polymorphism and how is it achieved in C#?
55. What is abstraction and how is it implemented in C#?
56. What is the difference between an abstract class and an interface?
57. What changes were made to interfaces in C# 8.0?
58. What is the difference between method hiding and method overriding?
59. Can we override a private or static method in C#?
60. What is a sealed class and sealed method in C#?
61. What is the difference between early binding and late binding?
62. What is the difference between a shallow copy and a deep copy?
63. What is the difference between `is-a` and `has-a` relationships?
64. What is cohesion and coupling in OOP?
65. What is the Liskov Substitution Principle?
66. What is the Open/Closed Principle?
67. What is the Single Responsibility Principle?
68. What is the Interface Segregation Principle?
69. What is the Dependency Inversion Principle?
70. What is the difference between abstraction and encapsulation?

## LINQ and Collections

71. What is LINQ and what are its advantages?
72. What are the different ways to write LINQ queries?
73. What is the difference between LINQ to Objects, LINQ to SQL, and LINQ to XML?
74. What is the difference between `IEnumerable` and `IQueryable`?
75. What is deferred execution in LINQ?
76. What is the difference between `Select` and `SelectMany` in LINQ?
77. What is the difference between `First`, `FirstOrDefault`, `Single`, and `SingleOrDefault` in LINQ?
78. What is the purpose of the `GroupBy` operator in LINQ?
79. What is the difference between `Join` and `GroupJoin` in LINQ?
80. What is the purpose of the `let` clause in LINQ?
81. What are the different types of collections in .NET?
82. What is the difference between `List<T>` and `Array` in C#?
83. What is the difference between `Dictionary<TKey, TValue>` and `Hashtable`?
84. What is the difference between `Stack` and `Queue`?
85. What is the difference between `IEnumerable<T>` and `ICollection<T>`?
86. What is the difference between `ICollection<T>` and `IList<T>`?
87. What is the difference between `List<T>` and `LinkedList<T>`?
88. What is the purpose of the `IComparable` and `IComparer` interfaces?
89. What is the difference between `SortedList<TKey, TValue>` and `SortedDictionary<TKey, TValue>`?
90. What is the purpose of the `yield` keyword in collections?

## Asynchronous Programming

91. What is asynchronous programming and why is it important?
92. What are the `async` and `await` keywords in C# and how do they work?
93. What is the difference between synchronous and asynchronous programming?
94. What is the Task Parallel Library (TPL) in .NET?
95. What is the difference between `Task` and `Thread` in .NET?
96. What is the difference between `Task.Run` and `Task.Factory.StartNew`?
97. What is the purpose of `ConfigureAwait(false)`?
98. What is the difference between `Task.WhenAll` and `Task.WhenAny`?
99. What is the difference between `Task.Delay` and `Thread.Sleep`?
100. What is the purpose of the `CancellationToken` in asynchronous programming?
101. What is the difference between `Task.FromResult` and `Task.CompletedTask`?
102. What is the async/await state machine in C#?
103. What is the difference between `Task.Run` and `Task.Factory.StartNew`?
104. What is the purpose of the `TaskCompletionSource` class?
105. What is the difference between `Parallel.ForEach` and `Task.WhenAll`?
106. What is the purpose of the `lock` statement in multithreaded programming?
107. What is a deadlock and how can it be avoided?
108. What is a race condition and how can it be prevented?
109. What is the difference between `Mutex` and `Semaphore`?
110. What is the purpose of the `Interlocked` class in .NET?

## Memory Management and Garbage Collection

111. How does memory management work in .NET?
112. What is the difference between stack and heap memory?
113. What is garbage collection in .NET?
114. What are the different generations in garbage collection?
115. What is the difference between Finalize and Dispose methods?
116. What is the purpose of the `IDisposable` interface?
117. What is the purpose of the `using` statement in resource management?
118. What is a memory leak in .NET and how can it occur?
119. What is the Large Object Heap (LOH) in .NET?
120. What is the difference between weak references and strong references?
121. What is the purpose of the `GC.Collect` method and when should it be used?
122. What is the difference between `GC.SuppressFinalize` and `GC.ReRegisterForFinalize`?
123. What is the purpose of the `GCSettings` class?
124. What is the difference between concurrent and non-concurrent garbage collection?
125. What is the purpose of the `GCHandle` class?
126. What is the difference between server and workstation garbage collection?
127. What is the purpose of the `MemoryCache` class in .NET?
128. What is the difference between `StringBuilder` and `string` in terms of memory usage?
129. What is the purpose of the `WeakReference` class?
130. What is the difference between managed and unmanaged resources?

## Exception Handling

131. What is exception handling in C#?
132. What is the difference between an exception and an error?
133. What is the exception hierarchy in .NET?
134. What is the purpose of the `try-catch-finally` block?
135. Can `finally` block be skipped?
136. What happens if an exception is thrown in a `finally` block?
137. What is the purpose of the `throw` keyword?
138. What is the purpose of the `throws` keyword?
139. What is exception propagation?
140. What is exception filtering in C#?
141. What is the purpose of the `when` clause in exception handling?
142. What is a custom exception and when should you create one?
143. What is the difference between `throw` and `throw ex`?
144. What is the purpose of the `ExceptionDispatchInfo` class?
145. What is the difference between `AggregateException` and regular exceptions?
146. What is the purpose of the `InnerException` property?
147. What is the purpose of the `StackTrace` property in exceptions?
148. What is the purpose of the `Exception.Data` property?
149. What is the best practice for exception handling in .NET?
150. What is the difference between checked and unchecked exceptions in .NET?

## Reflection and Attributes

151. What is reflection in .NET?
152. What is the purpose of the `System.Reflection` namespace?
153. How do you get the type of an object at runtime?
154. What is the purpose of the `GetType` method?
155. What is the purpose of the `typeof` operator?
156. What is the difference between `GetType` and `typeof`?
157. What is the purpose of the `Assembly` class?
158. How do you load an assembly dynamically?
159. What is the purpose of the `Activator` class?
160. How do you create an instance of a type dynamically?
161. What are attributes in .NET?
162. What is the purpose of the `AttributeUsage` attribute?
163. What is the difference between custom attributes and reflection?
164. What is the purpose of the `MemberInfo` class?
165. How do you get the properties of a class using reflection?
166. How do you get the methods of a class using reflection?
167. How do you invoke a method dynamically using reflection?
168. What is the purpose of the `BindingFlags` enumeration?
169. What is the performance impact of using reflection?
170. What is the purpose of the `TypeDescriptor` class?

## Entity Framework

171. What is Entity Framework and what are its advantages?
172. What is the difference between Entity Framework 6 and Entity Framework Core?
173. What are the different approaches to work with Entity Framework?
174. What is the Code First approach in Entity Framework?
175. What is the Database First approach in Entity Framework?
176. What is the Model First approach in Entity Framework?
177. What is a DbContext in Entity Framework?
178. What is a DbSet in Entity Framework?
179. What is the purpose of the `OnModelCreating` method?
180. What are migrations in Entity Framework?
181. How do you configure relationships in Entity Framework?
182. What is the difference between lazy loading and eager loading?
183. What is the purpose of the `Include` method in Entity Framework?
184. What is the difference between `ThenInclude` and `Include`?
185. What is the purpose of the `AsNoTracking` method?
186. What is change tracking in Entity Framework?
187. What is the purpose of the `SaveChanges` method?
188. What is the difference between `Add` and `Attach` methods?
189. What is the purpose of the `Entry` method?
190. What is the difference between `Update` and `Attach` methods?

## ASP.NET Core

191. What is ASP.NET Core and what are its advantages?
192. What is the difference between ASP.NET and ASP.NET Core?
193. What is the purpose of the `Startup` class in ASP.NET Core?
194. What is middleware in ASP.NET Core?
195. What is the purpose of the `Configure` method in the `Startup` class?
196. What is the purpose of the `ConfigureServices` method in the `Startup` class?
197. What is the request processing pipeline in ASP.NET Core?
198. What is the purpose of the `IApplicationBuilder` interface?
199. What is the purpose of the `IHostingEnvironment` interface?
200. What is the purpose of the `IConfiguration` interface?
201. What is the purpose of the `appsettings.json` file?
202. What is the purpose of the `launchSettings.json` file?
203. What is the purpose of the `Program.cs` file in ASP.NET Core?
204. What is the difference between `IServiceCollection` and `IServiceProvider`?
205. What is the purpose of the `AddTransient`, `AddScoped`, and `AddSingleton` methods?
206. What is the difference between `AddTransient`, `AddScoped`, and `AddSingleton`?
207. What is the purpose of the `UseStaticFiles` middleware?
208. What is the purpose of the `UseMvc` middleware?
209. What is the purpose of the `UseAuthentication` middleware?
210. What is the purpose of the `UseAuthorization` middleware?

## Web API

211. What is ASP.NET Core Web API?
212. What is the difference between ASP.NET Web API and ASP.NET Core Web API?
213. What is the purpose of the `ApiController` attribute?
214. What is content negotiation in Web API?
215. What is the purpose of the `Produces` and `Consumes` attributes?
216. What is the purpose of the `FromBody`, `FromQuery`, and `FromRoute` attributes?
217. What is the purpose of the `ActionResult<T>` type?
218. What is the difference between `IActionResult` and `ActionResult<T>`?
219. What is the purpose of the `CreatedAtAction` and `CreatedAtRoute` methods?
220. What is the purpose of the `ProducesResponseType` attribute?
221. What is the purpose of the `ApiExplorerSettings` attribute?
222. What is the purpose of the `NonAction` attribute?
223. What is the purpose of the `Route` attribute?
224. What is the purpose of the `HttpGet`, `HttpPost`, `HttpPut`, and `HttpDelete` attributes?
225. What is the purpose of the `ModelState` property?
226. What is model binding in ASP.NET Core Web API?
227. What is model validation in ASP.NET Core Web API?
228. What is the purpose of the `ValidationAttribute` class?
229. What is the purpose of the `IValidatableObject` interface?
230. What is the purpose of the `FluentValidation` library?

## MVC Architecture

231. What is the MVC architecture pattern?
232. What is the difference between MVC and Web API in ASP.NET Core?
233. What is the purpose of the `Controller` class in MVC?
234. What is the purpose of the `View` in MVC?
235. What is the purpose of the `Model` in MVC?
236. What is the purpose of the `ViewBag` and `ViewData` in MVC?
237. What is the purpose of the `TempData` in MVC?
238. What is the difference between `ViewBag`, `ViewData`, and `TempData`?
239. What is the purpose of the `PartialView` in MVC?
240. What is the purpose of the `ViewComponent` in MVC?
241. What is the purpose of the `TagHelper` in MVC?
242. What is the purpose of the `HtmlHelper` in MVC?
243. What is the difference between `TagHelper` and `HtmlHelper`?
244. What is the purpose of the `Layout` in MVC?
245. What is the purpose of the `_ViewStart.cshtml` file?
246. What is the purpose of the `_ViewImports.cshtml` file?
247. What is the purpose of the `Areas` in MVC?
248. What is the purpose of the `Filters` in MVC?
249. What is the purpose of the `ActionFilter` in MVC?
250. What is the purpose of the `ResultFilter` in MVC?

## Dependency Injection

251. What is Dependency Injection and why is it important?
252. What are the different types of Dependency Injection?
253. What is the purpose of the `IServiceCollection` interface?
254. What is the purpose of the `IServiceProvider` interface?
255. What is the difference between constructor injection and property injection?
256. What is the purpose of the `AddTransient` method?
257. What is the purpose of the `AddScoped` method?
258. What is the purpose of the `AddSingleton` method?
259. What is the difference between `AddTransient`, `AddScoped`, and `AddSingleton`?
260. What is the purpose of the `TryAddTransient`, `TryAddScoped`, and `TryAddSingleton` methods?
261. What is the purpose of the `ServiceDescriptor` class?
262. What is the purpose of the `IServiceScope` interface?
263. What is the purpose of the `IServiceScopeFactory` interface?
264. What is the purpose of the `ActivatorUtilities` class?
265. What is the purpose of the `ServiceProviderServiceExtensions` class?
266. What is the purpose of the `BuildServiceProvider` method?
267. What is the purpose of the `GetRequiredService` method?
268. What is the purpose of the `GetService` method?
269. What is the difference between `GetRequiredService` and `GetService`?
270. What is the purpose of the `IServiceCollection.AddOptions` method?

## Unit Testing

271. What is unit testing and why is it important?
272. What is the difference between unit testing, integration testing, and end-to-end testing?
273. What is the purpose of the `MSTest` framework?
274. What is the purpose of the `NUnit` framework?
275. What is the purpose of the `xUnit` framework?
276. What is the difference between `MSTest`, `NUnit`, and `xUnit`?
277. What is the purpose of the `TestInitialize` and `TestCleanup` methods?
278. What is the purpose of the `ClassInitialize` and `ClassCleanup` methods?
279. What is the purpose of the `Assert` class?
280. What is the purpose of the `CollectionAssert` class?
281. What is the purpose of the `StringAssert` class?
282. What is the purpose of the `ExpectedException` attribute?
283. What is the purpose of the `Ignore` attribute?
284. What is the purpose of the `TestCategory` attribute?
285. What is the purpose of the `TestContext` class?
286. What is the purpose of the `InlineData` attribute in xUnit?
287. What is the purpose of the `Theory` attribute in xUnit?
288. What is the purpose of the `Fact` attribute in xUnit?
289. What is the difference between `Theory` and `Fact` in xUnit?
290. What is the purpose of the `AutoData` attribute in AutoFixture?

## Design Patterns

291. What are design patterns and why are they important?
292. What is the Singleton design pattern and when would you use it?
293. What is the Factory design pattern and when would you use it?
294. What is the Abstract Factory design pattern and when would you use it?
295. What is the Builder design pattern and when would you use it?
296. What is the Prototype design pattern and when would you use it?
297. What is the Adapter design pattern and when would you use it?
298. What is the Bridge design pattern and when would you use it?
299. What is the Composite design pattern and when would you use it?
300. What is the Decorator design pattern and when would you use it?