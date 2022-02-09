
# The Rules

1. Do not create static variables or static methods.
2. Always create a package for your classes. Do not use the "default package".
3. Always use {}s. Even if what you are wrapping is only one line.
4. Do not repeat yourself.
5. Do not repeat yourself.
6. Do not read from a file multiple times. Read from the file once and save the data.
7. Do not use += when doing String concatenation. Use [StringBuilder](http://docs.oracle.com/javase/8/docs/api/java/lang/StringBuilder.html). Don't use [StringBuffer](http://docs.oracle.com/javase/8/docs/api/java/lang/StringBuffer.html) unless you are using multiple Threads.
8. Do not write code like this:

        if (checkCondition()) {
            return true;
        } else {
            return false;
        }
	
    Instead write it like this:
	
        return checkCondition();
9. Pay attention to warnings (code that is underlined in yellow). Sometimes warnings are a sign that there is a bug. Fix them if you see them.
10. Do not check in code that breaks unit tests. 
11. Don't do an Assert like this:
        Assert.assertEquals(true, methodCall());

    Use assertTrue() and assertFalse() when you can
        Assert.assertTrue(methodCall());
    
12. Do not use `instanceof`.
13. Reformat your code with CTRL + ALT + L. Do not leave your code messy.
