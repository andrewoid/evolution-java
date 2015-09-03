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
    
--

The code above is simple enough to write. The question is, **does it work?**

In the real world, code must be tested. You may have changed the main() you wrote to use the Projectile class instead and been satisfied with the results but in the real world you cannot create main() methods to test every class you write. 


    

