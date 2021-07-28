# Read: 19 - Spring and Sockets

**Using WebSocket to build an interactive web application**
  * This guide walks you through the process of creating a “Hello, world” application that sends messages back and forth between a browser and a server. 
  * WebSocket - is a thin, lightweight layer above TCP. This makes it suitable for using “subprotocols” to embed messages. 
  * STOMP - is a subprotocol operating on top of the lower-level WebSocket.
  * Build a server that accepts a message that carries a user’s name. In response, the server will push a greeting into a queue to which the client is subscribed.
  * Start from scatch using Spring Initializer. Download and unzip the source repository for this guide, or clone it using Git: git clone https://github.com/spring-guides/gs-messaging-stomp-websocket.git. 
  * When you finish, you can check your results against the code in gs-messaging-stomp-websocket/complete.
  * Start with Spring Initializr or if you use Gradle, visit the Spring Initializr to generate a new project with the required dependency (Websocket). 
    - Add dependecies for either Maven or Gradle
    - Create a resource representation class by creating your STOMP message service. Begin the process by thinking about service interactions. The service will accept messages that contain a name in a STOMP message whose body is a JSON object.
    - Create a message-handling controller by using @Controller classes. e @MessageMapping annotation ensures that, if a message is sent to the /hello destination, the greeting() method is called. The payload of the message is bound to a HelloMessage object, which is passed into greeting(). 
    - Configure Spring for STOMP messaging by creating a Java class named WebSocketConfig. WebSocketConfig is annotated with @Configuration to indicate that it is a Spring configuration class. It is also annotated with @EnableWebSocketMessageBroker enables WebSocket message handling, backed by a message broker. configureMessageBroker() method implements the default method in WebSocketMessageBrokerConfigurer to configure the message broker. registerStompEndpoints() method registers the /gs-guide-websocket endpoint, enabling SockJS fallback options so that alternate transports can be used if WebSocket is not available.
    - Create a browser client with an index.html file. HTML file imports the SockJS and STOMP javascript libraries that will be used to communicate with our server through STOMP over websocket. We also import app.js, which contains the logic of our client application. Main pieces of the JavaScript file to understand are the connect() and sendName() functions. he connect() function uses SockJS and stomp.js to open a connection, and sendName() function retrieves the name entered by the user and uses the STOMP client to send it to the /app/hello destination.
    - Make the application executable - Spring Boot creates an application class for you. In this case, it needs no further modification. You can use it to run this application. 
    - Build an executable JAR - You can run the application from the command line with Gradle or Maven. You can also build a single executable JAR file that contains all the necessary dependencies, classes, and resources and run that. Building an executable jar makes it easy to ship, version, and deploy the service as an application throughout the development lifecycle, across different environments, and so forth.
    - If you use Gradle, you can run the application by using ./gradlew bootRun. Alternatively, you can build the JAR file by using ./gradlew build, and then run java -jar build/libs/gs-messaging-stomp-websocket-0.1.0.jar 
    - Test the service by having the browser at http://localhost:8080 and click the Connect button.
 