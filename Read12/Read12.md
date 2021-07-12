# Read: 12 - Spring RESTful Routing & Static Files

**Spring RequestMapping**
* Main annotations in Spring MVC: 
  - @RequestMapping - used to map web requests to Spring Controller methods
    * @RequestMapping by Path example: 
    @RequestMapping(value = "/ex/foos", method = RequestMethod.GET)
    @ResponseBody
    public String getFoosBySimplePath() {
      return "Get some Foos";
    }
      - To test this use the command: curl -i http://localhost:8080/spring-rest/ex/foos
    * @RequestMapping the HTTP Method - the HTTP method parameter has no default, so its going to map to any HTTP request, if you don't specify a value.
  - RequestMapping and HTTP Headers
    *  @RequestMapping With the headers Attribute - mapping can be narrowed even further by specifying a header for the request
    * @RequestMapping Consumes and Produces 
      - can map a request based on its Accept header via the @RequestMapping headers attribute, and the matching for this way of defining the Accept header is flexible.  @RequestMapping annotation now has the produces and consumes attributes. Also, produces supports multiple values. The method-level annotations do not complement but override the type-level information.
    * RequestMapping With Path Variables
      - @PathVariable annotation - parts of the mapping URI can be bound to variables
      - You can have a single path variable, multipath path variable, or a @PathVariable with regex.
    * RequestMapping With Request Parameters
      - @RequestMapping allows easy mapping of URL parameters with the @RequestParam annotation, and can optionally define the parameters.
    * RequestMapping Corner Cases
      - A single @RequestMapping path value is usually used for a single controller method, but you can have multiple paths mapped to the same controller method.
      - Multiple requests using different HTTP verbs can be mapped to the same controller method.
      - @RequestMapping has a fallback for all requests
      - Ambiguous mapping error - occurs when Spring evaluates two or more request mappings to be the same for different controller methods. 
      - A request mapping is the same when it has the same HTTP method, URL, parameters, headers, and media type.
    * New Request Mapping Shortcuts
      - @GetMapping
      - @PostMapping
      - @PutMapping
      - @DeleteMapping
      - @PatchMapping
    * Spring MVC configuration - use the @Configuration class to enable the full MVC support and configure classpath scanning for the controller

**Accessing Data with JPA**
  * Start with Spring Initializr, and once that is set up define a simple entity.
  * Then create simple queries. Spring Data JPA focuses on using JPA to store data in a relational database, and one of its abilities is to create repository implementations automatically. 
  * Next, Spring Initializr creates a simple class for the application.
  * Build an executable JAR that contains all the necessary dependencies, classes, and resources and run that. Building an executable jar makes it easy to ship, version, and deploy the service as an application throughout the development lifecycle, across different environments, and so forth.

**CrudRepository, JpaRepository, and PagingAndSortingRepository in Spring Data**
* Spring Data Repositories
  - CrudRepository - provides CRUD functions
  - PagingAndSortingRepository - provides methods to do pagination and sort records
  - JpaRepository - provides JPA related methods such as flushing the persistence context and delete records in a batch, and contains the full API of CrudRepository and PagingAndSortingRepository due to their inheritance relationship
* CrudRepository -  CRUD functionality:
  - save(…) – save an Iterable of entities. Here, we can pass multiple objects to save them in a batch
  - findOne(…) – get a single entity based on passed primary key value
  - findAll() – get an Iterable of all available entities in database
  - count() – return the count of total entities in a table
  - delete(…) – delete an entity based on the passed object
  - exists(…) – verify if an entity exists based on the passed primary key value
* PagingAndSortingRepository - extends CrudRepository, provides a method, and you cancreate an object with certain properties.
* JpaRepository methods:
  - indAll() – get a List of all available entities in database
  - findAll(…) – get a List of all available entities and sort them using the provided condition
  - save(…) – save an Iterable of entities. Here, we can pass multiple objects to save them in a batch
  - flush() – flush all pending task to the database
  - saveAndFlush(…) – save the entity and flush changes immediately
  - deleteInBatch(…) – delete an Iterable of entities
* Downsides of Spring Data Repositories
  - We couple our code to the library and to its specific abstractions, but we do have to be careful not to expose these internal implementation details.
  - By extending a repository we expose a complete set of persistence method at once,but we might run into situations where we'd like to gain more fine-grained control over the methods exposed.
 