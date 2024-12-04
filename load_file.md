### From "resources" directory

``` java
InputStream in = ClassLoader.getSystemResourceAsStream("/file.in");
```

With an `InputStream` you can then use it in a `BufferedReader` or `Scanner`. The file **must** begin with a slash to be
able to get it from resources.

``` java 
BufferedReader reader = new BufferedReader(new InputStreamReader(in));
```

of

``` java
Scanner scanner = new Scanner(in);
```