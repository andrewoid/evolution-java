### Project Configuration

- Add to `plugins` in `build.gradle`
```
id 'war'
```

- Add to `dependencies` in `build.gradle`
```
    compileOnly 'javax.servlet:servlet-api:2.5'
```

- Create a `webapp` directory in `main`. This is where public HTML files will go.

- Create a `WEB-INF` directory in `webapp`. This is where private files will go.

- Create `web.xml` in `WEB-INF` directory. This is a configuration file.
  - `index.html` is the first web page displayed to the user.
  - Use a `display-name`, `servlet-name`, `servlet-class` and `url-pattern` unique to your project.

``` html

<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee
         http://xmlns.jcp.org/xml/ns/javaee/web-app_3_1.xsd"
         version="3.1">

    <welcome-file-list>
        <welcome-file>index.html</welcome-file>
    </welcome-file-list>

    <servlet>
        <display-name>Display Name</display-name>
        <servlet-name>Servlet Name</servlet-name>
        <servlet-class>full.package.path.to.Servlet</servlet-class>
    </servlet>

    <servlet-mapping>
        <servlet-name>Servlet Name</servlet-name>
        <url-pattern>/servletName</url-pattern>
    </servlet-mapping>

</web-app>

```

This is what your directory structure should look like.
![servlet directory structure](servlet-directory-structure.png)

### The Servlet Class

``` java 
package lastname.project

public class BasicGetServlet extends HttpServlet {

    public void doGet(HttpRequest request, HttpResponse response) {
    
        // "keyString" is the "key" in the URL parameters.
        String value = request.getParameter("keyString");
        
        // ... do something with the value and return a result.
    
        response.setContentType("text/json");
        response.getWriter().println(...);
    }

}

```





