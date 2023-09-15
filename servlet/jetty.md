Add [Jetty](https://eclipse.dev/jetty/) as a dependency in `build.gradle`

    compileOnly 'jakarta.servlet:jakarta.servlet-api:6.0.0'
    implementation 'org.eclipse.jetty:jetty-server:11.0.14'
    implementation 'org.eclipse.jetty:jetty-servlet:11.0.14'

The code below allows you to run the server locally and then connect to it with a web browser

``` java
/**
* Runs the BasicGetServlet servlet locally.
* It can be accessed through the browser with at http://localhost:8080/basic?keyString1=Hello&keyString2=World
*/
public class JettyMain {

  public static void main(String[] args) throws Exception {
      // Starts loads the server on port 8080
      Server server = new Server();
      ServerConnector connector = new ServerConnector(server);
      connector.setPort(8080);
      server.setConnectors(new Connector[]{connector});

      // Adds the WordleDictionaryServlet to the Server
      ServletHandler handler = new ServletHandler();
      handler.addServletWithMapping(BasicGetServlet.class, "/basic");
      server.setHandler(handler);

      // Starts the server until this program exists.
      // You must stop the program manually
      server.start();
  }

}
 ```