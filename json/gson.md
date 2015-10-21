# GSON

In the previous page we described a JSON file for a bookstore.

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


If we wanted to translate this into Java it would look something like.

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
    
The question is, how should we translate the JSON into Java classes. There are many answers to that. The one I'm most comfortable using is called [GSON](https://github.com/google/gson). GSON is a free product by Google to automatically take in Json and output Java objects.

To use GSON you need to first need to download the jar from the download link on the GSON github page. Place the jar file, gson-2.4.jar into your project folder. Make sure to refresh the Eclipse project after you do it. Now we need to tell Eclipse to use the jar file. Right click on the jar file, choose "Build Path" and "Add to Build Path". Now you should be able to use GSON in your project.

Using Gson is very simple. Assuming you had a String which held your JSON, you can easily turn it into classes using 

    String json = ...
    Gson gson = new Gson();
    Bookstore bookstore = gson.fromJson(json, Bookstore.class);

But you don't need to have the JSON already in a String in order to convert it to objects. GSON has other .fromJson() methods that can be used to read from a file.

    File file = new File("bookstore.json");
    FileReader reader = new FileReader(file);
    Bookstore bookstore = gson.fromJson(reader, Bookstore.class);
    



