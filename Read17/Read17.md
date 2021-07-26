# Read: 17 - Spring Authorization

  * Examples of single page apps:
    - simple - a very basic static app with just a home page and unconditional login via Spring Boot’s OAuth 2.0 configuration properties
    - click - adds an explicit link that the user has to click to login
    - logout - adds a logout link as well for authenticated users
    - two-providers - adds a second login provider so the user can choose on the home page which one to use
    - custom-error - adds an error message for unauthenticated users, and a custom authentication based on GitHub’s API
  * Each app can be imported into an IDE, and can run the main method in SocialApplication to start an app. They all come up with a home page on http://localhost:8080.
  * Can run all the apps on the command line using mvn spring-boot:run or by building the jar file and running it with mvn package and java -jar target/*.jar.
  * Creating a New Project:
    - create a Spring Boot application by go to https://start.spring.io and generate an empty project and put these commands into the command line:  mkdir ui && cd ui
     curl https://start.spring.io/starter.tgz -d style=web -d name=simple | tar -xzvf -
     - Add a home page - create a index.html in the src/main/resources/static folder 
     - Securing the application with GitHub and Spring Security 
       * To make the application secure, you can simply add Spring Security as a dependency.
       <dependency>
	      <groupId>org.springframework.boot</groupId>
	      <artifactId>spring-boot-starter-oauth2-client</artifactId>
      </dependency>
    - Add a New GitHub app - To use GitHub’s OAuth 2.0 authentication system for login, Select "New OAuth App" and then the "Register a new OAuth application" page is presented. Enter an app name and description. Then, enter your app’s home page, which should be http://localhost:8080, in this case. Finally, indicate the Authorization callback URL as http://localhost:8080/login/oauth2/code/github and click Register Application.
    - Configure application.yml - use the OAuth 2.0 credentials you just created with GitHub, replacing github-client-id with the client id and github-client-secret with the client secret.
    - Boot up the application
    - Add a welcome page
    - Conditional Content on the Home Page
      * To render content on the condition that the user is authenticated, you can either do it server-side or client-side rendering.
    - /user endpoint - add the server-side endpoint just mentioned, calling it /user. It will send back the currently logged-in user, which we can do quite easily in our main class
    - Make the home page public by extending the WebSecurityConfigurerAdapter
    - Add a logout button
    - Add a logout endpoint
    - Add the CSRF token in the client
    - Login with GitHub do the intitial setup, set the redirect URI
    - Add the client registration
    - Add the login link
    - Add local user database
    - Add an error page for unauthenticated users
    - Add an Error message
    - Generate a 401 in the server