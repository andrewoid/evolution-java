# Gson

In the previous page we described a Json file for a bookstore.

``` json
    {
        "name" : "Bookstore on J",
        "address" "1234 Ave J",
        "books": [
            { 
                "title" : "Evolution Java",
                "author" : "Andrew Schwimmer",
                "isbn" : "978-3-16-148410-0" 
            },
            { 
                "title" : "Evolution Java",
                "author" : "Andrew Schwimmer",
                "isbn" : "978-3-16-148410-0" 
            },
            { 
                "title" : "Evolution Java",
                "author" : "Andrew Schwimmer",
                "isbn" : "978-3-16-148410-0" 
            }
        ]
    }
```

If we wanted to translate this into Java it would look something like.

``` java
    class Bookstore {
        String name;
        String address;
        Book books[];
    }
    
    class Book {
        String title;
        String author;
        String isbn;
    }
```

[Gson](https://github.com/google/gson) is a free product by Google to automatically take in Json and output Java
objects.

- Add to `dependencies` in `build.gradle`

``` groovy
    implementation 'com.google.code.gson:gson:2.10.1'
```

Using Gson is very simple. Assuming you had a String which held your Json, you can easily turn it into classes using

``` java
    String json = ...
    Gson gson = new Gson();
    Bookstore bookstore = gson.fromJson(json, Bookstore.class);
```

But you don't need to have the Json already in a String in order to convert it to objects. GSON has other .fromJson()
methods that can be used to read from a file.

``` java
    File file = new File("bookstore.json");
    FileReader reader = new FileReader(file);
    Bookstore bookstore = gson.fromJson(reader, Bookstore.class);
```
    



