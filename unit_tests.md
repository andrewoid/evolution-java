### [JUnit5](https://junit.org/junit5/)

#### dependency

Add this to the dependencies block in `build.gradle`

``` groovy 
dependencies {
    testImplementation 'org.junit.jupiter:junit-jupiter-api:5.9.2'
    testRuntimeOnly 'org.junit.jupiter:junit-jupiter-engine:5.9.2'
}
```

#### Assertions

All assertions come from
the [org.junit.jupiter.api.Assertions](https://junit.org/junit5/docs/5.10.1/api/org.junit.jupiter.api/org/junit/jupiter/api/Assertions.html)
class in

`assertEquals(expected, actual)`

`assertEquals(expected, actual, delta)` -
Use [this](https://junit.org/junit5/docs/5.10.1/api/org.junit.jupiter.api/org/junit/jupiter/api/Assertions.html#assertEquals(double,double,double))
when comparing doubles or floats.

`assertNotEquals(expected, actual)`

`assertTrue(condition)`

`assertFalse(condition)`

`assertNull(object)`

`assertNotNull(object)`

`assertArrayEquals(expectedArray, actualArray)`

#### Writing tests

Each of our tests have 3 parts.

- `given` - where we create our objects, mocks and `doReturn` calls.
- `when` - the method call that we are testing.
- `then` - where we put our `assert` and `verify` calls.

``` java
// Class should be named for the class you are testing.
public class CalculatorTest {

    @Test
    // the name of the test should match the name of the method being tested.
    public void add() {
        // given
        Calculator calculator = new Calculator();
        
        // when
        int actual = calculator.add(5, 2);
        
        // then
        assertEquals(7, actual);
    }

}
```

### [Mockito](https://site.mockito.org/)

#### dependency

Add this to the dependencies block in `build.gradle`

``` groovy 
dependencies {
    testImplementation 'org.mockito:mockito-core:5.5.0'
}
```

#### Mocks

Suppose you have a method that returns `void`. How can you write a test that verifies what the method is supposed to do?

A mock is an object that you can use to "mimic" a real object in a test and then verify its interaction.

``` java 
public class OrderProcessor {

    public void processAll(List<Order> orders, PaymentMethod paymentMethod) {   
        for (Order order : orders) {
            paymentMethod.charge(order.getAmount())
        }
    }
}

// Class should be named for the class you are testing.
public class OrderProcessorTest {

    @Test
    // the name of the test should match the name of the method being tested.
    public void charge() {
        // given
        OrderProcessor processor = new OrderProcessor();
        PaymentMethod paymentMethod = mock();
        Order order = mock();
        List<Order> orders = List.of(order);
        doReturn(1234).whenever(order).getAmount();
        
        // when
        processor.processAll(orders, paymentMethod);
        
        // then
        verify(paymentMethod).charge(1234);
    }

}
```

#### doReturn()

Methods of a mock will have no effect and if a method of a mock returns a value it will either return `null`, `false`
or `0` depending on the return type.

`doReturn` allows us to set up our mock objects so that they return the data we want.

#### verify()

In order test what our method is doing, we can `verify` that methods of our mock were called with specific data.