# The Rules

1. Do not create `static` variables or static methods. Only use static for `main()` or constants.
2. Always create a package for your classes. Do not use the "default package".
3. Always use {}s. Even if what you are wrapping is only one line.
4. Do not repeat yourself.

``` java
String firstName = list.get(i).getFirstName();
String lastName = list.get(i).getLastName();
String ssn = list.get(i).getSocialSecurityNumber();
```

is a lot harder to read than this

``` java
Person person = list.get(i);
String firstName = person.getFirstName();
String lastName = person.getLastName();
String ssn = person.getSocialSecurityNumber();
```

5. Do not read from a file multiple times. Read from the file once and save the data.
6. Do not use += when doing String concatenation.
   Use [StringBuilder](http://docs.oracle.com/javase/8/docs/api/java/lang/StringBuilder.html).
7. Do not write code like this:

``` java
        if (checkCondition()) {
            return true;
        } else {
            return false;
        }
```

Write it like this:

 ``` java
       return checkCondition();
```

8. Pay attention to warnings (code that is underlined in yellow). Sometimes warnings are a sign that there is a bug. Fix
   them if you see them.
9. Do not check in code that breaks unit tests.
10. Don't do an Assert like this:

        Assert.assertEquals(true, methodCall());

    Use `assertTrue()` and `assertFalse()` when you can

        Assert.assertTrue(methodCall());

11. Do not use `instanceof`.
12. Reformat your code with `CTRL + ALT + L`. Do not leave your code messy.
13. Output Exception data correctly. Don't do

``` java
    catch (Exception e) {
        System.out.println(e.getMessage());
    }
```

Always do this instead:

``` java
    catch (Exception e) {
        e.printStackTrace();
    }
```