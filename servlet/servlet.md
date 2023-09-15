### The Servlet Class

https://www.geeksforgeeks.org/introduction-java-servlets/

- Add to `dependencies` in `build.gradle`
```
    implementation 'com.google.code.gson:gson:2.10.1'
    compileOnly 'jakarta.servlet:jakarta.servlet-api:6.0.0'
```

``` java 
package lastname.project

public class BasicGetServlet extends HttpServlet {

    public void doGet(HttpRequest request, HttpResponse response) {
    
        // "keyString" is the "key" in the URL parameters.
        String value1 = request.getParameter("keyString1");
        String value2 = request.getParameter("keyString2");
        
        // ... do something with the value and return a result.
    
        response.setContentType("text/json");
        // use gson.toJson() to return an object as json to the browser.
        response.getWriter().println(...);
    }

}

```





