### Projectile Answer

Projectile math is the typically the first topic in any physics course. The correct answer is:

> x = 27.812056045142928

> y = 10.56603423791406

Did you get the correct answer? 

A common error is that you don't know how to use  [Math.sin()](http://docs.oracle.com/javase/7/docs/api/java/lang/Math.html#sin(double%29) and [Math.cos()](http://docs.oracle.com/javase/7/docs/api/java/lang/Math.html#cos(double%29) correctly. If you read the linked javadocs carefully you'll see that the those methods take an angle in **radians** not degrees.

The "correct" program is something like this:

    public class ProjectileMain {

	    public static void main(String[] args) {
		    double angle = 31;
		    double velocity = 20;
		    double time = 2.7;
		    double radians = Math.toRadians(angle);
		    double x = Math.sin(radians) * velocity * time;
		    double y = Math.cos(radians) * velocity * time
			    	- ( .5 * 9.8 * time * time );
		
		    System.out.println("x = " + x);
		    System.out.println("y = " + y);
	    }

    }
    
You might have been tempted to create a Scanner and ask the user for input for angle, velocity and time. **Don't write more code than you are asked to write.**