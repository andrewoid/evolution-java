### AWS Lambda

``` groovy 

    implementation 'com.amazonaws:aws-lambda-java-core:1.2.2'
    implementation 'com.amazonaws:aws-lambda-java-events:3.11.1'

```

``` java 

public class HelloRequestHandler implements RequestHandler<String, String> {

    @Override
    public String handleRequest(String input, Context context) {
        return "Hello!";
    }
}

```

Copied from https://www.baeldung.com/gradle-fat-jar

In build.gradle put this at the **top** of the file.

``` groovy
buildscript {
    dependencies {
        classpath "gradle.plugin.com.github.johnrengelman:shadow:7.1.2"
    }
}
```

Then add this to the `plugins` block.

``` groovy
  id 'com.github.johnrengelman.shadow' version '7.1.2'
```

Then you can run the `shadowJar` gradle task and create a jar file that has the code and dependencies.

We can modify our `RequestHandler` to accept and return JSON by using an `Object` in `RequestHandler` instead of a
`String`.

``` java 
public class HelloRequestHandler implements RequestHandler<Request, Response> {

    @Override
    public String handleRequest(Request input, Context context) {
        return new Response();
    }
}
```