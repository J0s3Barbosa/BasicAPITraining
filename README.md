# BasicAPITraining

- create an API
- follow RestAPI best practices
  - Use HTTP methods
    - GET: Retrieve resource(s) from the server.
    - POST: Create a new resource on the server.
    - PUT: Update an existing resource on the server or create it if it doesn't exist.
    - DELETE: Remove a resource from the server.
    - PATCH: Update a resource partially.
    - HEAD: Retrieve metadata about a resource without the body.
    - OPTIONS: Retrieve the HTTP methods supported by a resource or server.
    - Example : GET /customers, POST /shipment, PUT /products/{id}, DELETE /orders/{id}
  - Use clear and consistent resource naming conventions
    - Example : /customers, /orders, /shipment, /products
  - Use HTTP status codes correctly
    - Exapmle: 200 OK, 201 Created, 400 Bad Request, 404 Not Found, etc.
  - Make your API stateless by design
    - each request from a client contains all the information necessary to fulfill that request
    -  Authenticate each request with an access token rather than relying on server-side sessions.
  - Authentication
    - Token-based Authentication: Clients obtain a token (such as JSON Web Tokens) after authenticating with credentials. This token is then sent with subsequent requests for authentication.
    - OAuth: A more complex authentication framework allowing delegated access to resources. It involves token-based authentication but with additional features like scopes and refresh tokens.
    - API Keys: Clients use a unique key provided by the API provider to authenticate their requests.
  - Make use of the proper mechanisms for authentication and authorization
    -  Implement OAuth 2.0 or JWT-based authentication and define roles/permissions for authorized users.
    -  authentication
        -  crucial for protecting sensitive data and preventing unauthorized access to APIs
        -  process of verifying the identity of a user or client accessing an API
        -  ensures that the entity requesting access is who they claim to be.
        -  Common authentication methods include username/password, OAuth, OpenID Connect, and JWT.
        -  OAuth enables delegated access to resources by allowing third-party applications to obtain limited access tokens on behalf of users.
        -  Authentication is typically performed before authorization to ensure that only authenticated users are granted access to protected resources.
    -  Authorization
        -  determining what actions a user or client is allowed to perform within an API
        -  verifies the identity of a user and checks if they have the necessary permissions to access or manipulate resources
        -  Authorization mechanisms include role-based access control (RBAC), attribute-based access control (ABAC), and JSON Web Tokens (JWT).
        -  RBAC assigns roles to users and defines permissions based on those roles
        -  JWT is a token-based authentication method that securely transmits claims between parties and can be used for authorization purposes.
  - Use JSON
  - Pagination
    - technique used in APIs to break large sets of data into smaller, more manageable chunks called pages
    - allows clients to retrieve data incrementally rather than all at once, which can improve performance and reduce the load on both the server and the client.
    - Commonly, pagination is implemented by including parameters in API requests to specify the size of each page and which page to retrieve. For example:
      - page: Indicates the page number to retrieve.
      - limit: Specifies the number of items per page.
  - Versioning
    - practice of managing changes to the API's functionality and structure over time
    - crucial for maintaining backward compatibility with existing clients while introducing new features or making modifications
    - Example: /v1/orders, /v2/customers
  - sort and filter
    - allow clients to retrieve data in a structured and customized manner
    - Sorting: Sorting enables clients to arrange retrieved data based on specific criteria
    - Filtering: Filtering allows clients to narrow down the dataset by specifying criteria that the returned data must match
    - often applied using query parameters in the API request
  - Error handling
    - To eliminate confusion for API users when an error occurs, we should handle errors gracefully and return HTTP response codes that indicate what kind of error
    - Implement error handling to handle exceptions and errors that may occur during API requests   
  - Caching
    - stores API responses to serve them faster for identical requests in the future
    - Improves performance by reducing the need to process or fetch data repeatedly
    - Cached responses retrieved directly for subsequent identical requests (cache hits)
    - Cached responses invalidated periodically or in response to data changes
    - Effective caching reduces latency, bandwidth usage, and server load, enhancing API scalability and responsiveness
  - use HTTPS and SSL
  - Validate input parameters

- Working with code-first migration using Entity Framework Core
  - technique where changes to the database schema are made by writing code in your application, and then applying those changes to the actual database.
  - models represent the structure of your data and will be used to generate the database schema
  - As you make changes to your models,create migrations to reflect those changes int the database
  - Review the generated migration code to ensure it accurately reflects the intended changes
- rollback migrations, allowing you to address any issues that arise and revert the database to a previous state

- Dependenci injection
  - technique that makes a class independent of its dependencies
  - achieves that by decoupling the usage of an object from its creation
  - helps you to follow SOLID's dependency inversion and single responsibility principles

- Solid
  - Single Responsibility Principle
    - class should have only one job or responsability
  - Open-Closed Principle
    - open for extention but closed for modification
      - can be applied using the following approaches
          - Using Function Parameters
          - Using Extension methods
            - enable you to add methods to existing types without creating a new derived type, recompiling, or otherwise modifying the original type
            - are static methods, but they're called as if they were instance methods on the extended type
          - Using Classes, Abstract class, or Interface-based Inheritance
          - Generics
            - maximize code reuse, type safety, and performance, and are commonly used to create collection classes.
            - a type that is not limited to a specific data type
            - is a template from which other types can be constructed
          - Composition and Dependency Injection
            - Composition
              -   classes should favor polymorphic behavior and code reuse by their composition
              -   greater flexibility, reduced complexity, and improved maintainability
              -   can also avoid problems associated with multiple inheritance
              -   implement the "has-a" relationship
              -   functionality is acquired dynamically at run-time
              -   use an object as a field within another class
  - Liskov Substitution Principle
    - Subtypes must be substitutable for their base type.
    - if S is a subtype of T, then objects of type T can be replaced with objects of type S without altering the desirable properties of the program.
  - Interface Segregation Principle
    - interfaces with methods they actually need and use
    - Clients should not be forced to depend on methods they do not use.
  - Dependency Inversion Principle
    - high level dependencies should not depend on low level, both should depend on abstraction

- Unit test
  - xunit,moq, assertions

- Integration tests
  - rest client
  - json
  - xunit

- Middleware 
  - crucial role in the ASP.NET Core pipeline
  - allowing you to handle requests and responses at various stages of the HTTP request lifecycle
  - Middleware components
    - are classes that handle requests and responses in the ASP.NET Core pipeline.
    - Each middleware component is responsible for performing a specific task, such as logging, authentication, authorization, or error handling.
  - Request Pipeline
    - The ASP.NET Core request pipeline is composed of middleware components arranged in a sequence.
    - When a request is received, it travels through the pipeline, and each middleware component has an opportunity to process the request or modify the response.
  - Use Middleware
    - To use middleware in your application, you typically add it to the request pipeline in the Configure method of your Startup class.
    - This is done using the Use extension method provided by the IApplicationBuilder interface.
  - Middleware Ordering
    - Middleware components are executed in the order they are added to the pipeline.
    - The order in which you add middleware can significantly impact the behavior of your application.
    - Middleware components added earlier in the pipeline are executed first.
  - Built-in Middleware
    - ASP.NET Core provides a set of built-in middleware components for common tasks such as routing, static file serving, HTTPS redirection, and authentication.
    - These components can be added to the pipeline using methods like UseRouting, UseStaticFiles, UseHttpsRedirection, and UseAuthentication.
  - Custom Middleware
    - You can also create custom middleware components to implement specific functionality tailored to your application's requirements.
    - Custom middleware components are classes that implement the IMiddleware interface or use a delegate with the RequestDelegate signature.
  - Middleware Configuration
    - Middleware components can be configured using options and parameters passed to their constructors or through extension methods provided by the middleware itself.
    - This allows you to customize the behavior of middleware components based on your application's needs.
   
- Garbage Collector (GC)
  - automatically manages memory allocation and deallocation
  - identifies and frees memory that is no longer in use, preventing memory leaks and improving application performance
  - GC periodically scans the managed heap to identify and reclaim unused objects.
  - It uses various algorithms such as mark-and-sweep, generational, and concurrent collection to efficiently reclaim memory.
  - Failing to dispose of unmanaged resources can lead to memory leaks.
  - GC operates asynchronously, pausing application execution briefly during garbage collection cycles, which may result in minor performance overhead.

- memory leaks
  - Unintentional Object Retention
    - Objects are kept in memory longer than necessary due to unintentional references that prevent them from being garbage collected. This can happen if objects are stored in static variables, event handlers, or long-lived collections without being properly released.
  - Event Handlers
    - Subscribing to events without properly unsubscribing can lead to memory leaks.
    -  If event handlers are not removed when they are no longer needed, objects referenced by event handlers can remain in memory indefinitely.
  - Circular References
    - Circular references occur when objects reference each other in a loop, preventing them from being garbage collected even if they are not reachable from the root of the object graph. This commonly happens in scenarios involving bidirectional associations or parent-child relationships.
  - Large Object Heap Fragmentation
    - Large object heap (LOH) fragmentation can occur when large objects are allocated and deallocated frequently, leading to inefficient memory usage and potential performance issues. Fragmentation can prevent the garbage collector from reclaiming memory effectively, leading to memory leaks over time.
  - Finalizers and Dispose
    - Improper use of finalizers or failure to implement the IDisposable pattern can result in memory leaks. Objects that implement IDisposable should be properly disposed of to release unmanaged resources and prevent memory leaks.
  - Memory Profiling
    - In some cases, memory leaks may be caused by third-party libraries, framework components, or native interop code. Memory profiling tools can help identify memory leaks by analyzing memory usage and object lifetimes in your application.

- stack memory
  - is used for storing local variables and function-related data with fast memory allocation
  - It's a LIFO (Last In, First Out) data structure, meaning that the last item added to the stack is the first one to be removed.
  - stores variables created by each function in the call stack.
  - is used for storing
    - local variables, function parameters, return addresses, and other function-related data.
  - Memory allocation and deallocation on the stack is fast, as memory is automatically allocated when a function is called and deallocated when the function exits.
  - size is typically limited
  - size of each variable must be known at compile time.
  
- heap memory
  - is a region of memory used for dynamic memory allocation
  - is used for dynamic memory allocation of objects with longer lifespans and manual memory management.
  - where objects are stored and managed.
  - Memory on the heap is allocated and deallocated manually using memory allocation functions like new and delete in C#
  - Objects on the heap have a longer lifespan than those on the stack and can be accessed from anywhere in the program.
  - allocation is slower than on the stack, as it involves searching for a suitable block of free memory and managing memory fragmentation.
  - Memory on the heap must be manually deallocated to avoid memory leaks, as garbage collection (in languages like C#) does not manage memory on the heap directly. Instead, it tracks references to objects and deallocates memory when objects are no longer reachable.
  
- Async await Tasks
  - mechanism for writing asynchronous code
  - making it easier to develop responsive and scalable applications that leverage asynchronous programming patterns
  - Inside an async method, you can use the await keyword to asynchronously wait for the completion of asynchronous operations.
  - Async-await is based on the Task-based asynchronous pattern
    - represents asynchronous operations as tasks that can be awaited
  - Tasks are objects that encapsulate asynchronous operations and provide features such as cancellation, continuation, and error handling.
  - does not block the calling thread while waiting for asynchronous operations to complete.
    - Instead, it allows the calling thread to be freed up to perform other tasks while waiting, improving the responsiveness and scalability of applications.
  - simplifies exception handling in asynchronous code
    - by allowing you to use try-catch blocks as you would in synchronous code.
    - Exceptions thrown from asynchronous operations are propagated to the caller, making error handling more straightforward.
  - Async methods can return void, Task, or Task<T>.
  - result is allocated in the heap

