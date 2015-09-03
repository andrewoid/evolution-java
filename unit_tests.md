### Projectile Class
In the Projectile problem the simplest solution is to write a main(). However, in the real world, requirements are rarely that simple and programs are rarely that small. 

The problem you were given was a math problem. How does the problem change if it's presented like this:

>You are working at a company making a baseball home run simulation program. For instance, a batter hits a ball at a 31 degree angle with a velocity of 20 meters/second. What is the location of the ball after 2.7 seconds?

What's changed in the above problem description is that you've now been asked to write a piece of a program, not the whole program itself. **This situation is way more common.** In this case your answer isn't a main(), it's a class.

Develop a class with the following methods

    public class Projectile {

	    public Projectile(double angle, double velocity) { ... }
	
	    public void setTime(double time) { ... }
	
	    public double getX() { ... }
	
	    public double getY() { ... }
	
    }
    
---

The code above is simple enough to write. The question is, **does it work?**

In the real world, code must be tested. You may have changed the main() you wrote to use the Projectile class instead and been satisfied with the results but in the real world you cannot create main() methods to test every class you write.

If you are asked to edit the Projectile class later on and accidentally change part of an equation, you'd never know it until the bug shows up as a result of running the larger program.

The answer to this issue is to use Unit Tests. A unit test is a small piece of code that tests a part of a program. The framework we will use to write unit tests is called [JUnit](http://www.junit.org).

Create the following class Called ProjectileTest

    class ProjectileTest {

	    @Test
	    public void testGetX() {
		    Projectile projectile = new Projectile(31, 20);
		    Assert.assertEquals(27.81, projectile.getX(), 0.1);
	    }
	

	    @Test
	    public void testGetY() {
		    Projectile projectile = new Projectile(31, 20);
		    Assert.assertEquals(10.56, projectile.getY(), 0.1);
	    }
	
}

A few things to notice.
1. The tests are in a seperate class. The class name is the same as the class you are testing with the words "Test" at the end.
2. Each method in this class begins with the word tests and has the @Test annotation.
3. You can run the test by right clicking on the file and selecting "Run".

Each method in ProjecileTest that is annotated with @Test is one unit test. Each method is also named for the functionality that it is testing. 

The [Assert](http://junit.org/apidocs/org/junit/Assert.html) class is used to test the results of code. The assert methods check a certain condition. In this case the condition is that the first a second parameter to .assertEquals() are equal to each other. Consult the javadocs for a list of available assert methods. If the assert fails, then an Exception is thrown and the test is marked as a failure.

(When comparing doubles in Java it is important to allow for small errors in calculation. The [assertEquals](http://junit.org/apidocs/org/junit/Assert.html#assertEquals(double, double, double%29) for doubles adds a "delta" parameter at the end to specify the range between the two numbers by which they could still be considered equal.)

Here is a good tutorial on JUnit.
http://www.vogella.com/tutorials/JUnit/article.html


    

