# The Rules

#### No Static

Do not create `static` variables or static methods. Only use static for `main()` or constants.

#### Use Packages

Always create a package for your classes. Do not use the "default package".

#### Always use curly braces

Always use {}s. Even if what you are wrapping is only one line.

#### Do not repeat yourself

This is a lot harder to read

``` java
String firstName = list.get(i).getFirstName();
String lastName = list.get(i).getLastName();
String ssn = list.get(i).getSocialSecurityNumber();
```

then this

``` java
Person person = list.get(i);
String firstName = person.getFirstName();
String lastName = person.getLastName();
String ssn = person.getSocialSecurityNumber();
```

#### File reading

Do not read from a file multiple times. Read from the file once and save the data.

#### String concatenation

Do not use += when doing String concatenation.
Use [StringBuilder](http://docs.oracle.com/javase/8/docs/api/java/lang/StringBuilder.html).

#### Return true/false

Do not write code like this:

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

#### Warnings in code

Pay attention to warnings (code that is underlined in yellow). Sometimes warnings are a sign that there is a bug. Fix
them if you see them.

#### Do not break unit tests

Do not check in code that breaks unit tests.

#### Use Assert correctly

Don't do an Assert like this:

``` java
Assert.assertEquals(true, methodCall());     
```

Use `assertTrue()` and `assertFalse()` when you can

``` java
Assert.assertTrue(methodCall());
```

#### No instanceof

Do not use `instanceof`.

#### Keep code clean

Reformat your code with `CTRL + ALT + L`. Do not leave your code messy.

#### Proper Exception Handling

Output Exception data correctly. Don't do

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