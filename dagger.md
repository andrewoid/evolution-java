### Dagger

Main webpage: https://dagger.dev/

Access their GitHub page: https://github.com/google/dagger

``` gradle 
// Add Dagger dependencies
dependencies {
    implementation 'com.google.dagger:dagger:2.59.2'
    annotationProcessor 'com.google.dagger:dagger-compiler:2.59.2'
}
```

`@Inject` on a constructor tells dagger how to construct the class.

`@Singleton` on a class tells dagger there should only be one of these in your application.

`@Component` on an interface tells Dagger to generate the dependency graph and provide injected objects.

```java
@Component(modules = FrameModule.class)
interface FrameFactory {
    JFrame frame();
}
```
`@Module` on a class tells Dagger that the class contains dependency bindings.

```java
@Module
class FrameModule {

    @Provides
    static JFrame provideFrame() {
        return new JFrame("My App");
    }
}
```

`@Named` on a parameter tells Dagger which dependency to inject when multiple bindings of the same type exist.

```java
class WindowManager {

    @Inject
    WindowManager(@Named("main") JFrame frame) {
    }
}
class CoffeeMachine {

    @Inject
    CoffeeMachine(@Named("espresso") Heater heater) {
    }
}
```

`@Provides` on a method tells Dagger how to create an object.

```java
@Module
class FrameModule {

    @Provides
    static JFrame provideFrame() {
        return new JFrame("My App");
    }
}
class FrameModule {

    @Provides
    static Heater provideHeater() {
        return new ElectricHeater();
    }
}
```

