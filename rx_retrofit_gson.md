[Json](json/json_format.md) is a data format

[RxJava](https://reactivex.io/) is for asynchronous (multi-threaded) programming

[Retrofit](https://square.github.io/retrofit/) is for making requests
for [Json](https://www.w3schools.com/whatis/whatis_json.asp) data

[Gson](https://github.com/google/gson) for turning [Json into Java objects]((json/gson.md)).

Together these make requests for Json over the internet very easy.

Add to your dependencies in `build.gradle`

```
    implementation 'com.squareup.retrofit2:retrofit:2.11.0'
    implementation 'com.squareup.retrofit2:converter-gson:2.11.0'
    implementation 'com.squareup.retrofit2:adapter-rxjava3:2.11.0'
```

[DummyJson](https://dummyjson.com/) will return json data for us to build applications around.

https://dummyjson.com/products/1

``` json
{
  "id": 1,
  "title": "iPhone 9",
  "description": "An apple mobile which is nothing like apple",
  "price": 549,
  "discountPercentage": 12.96,
  "rating": 4.69,
  "stock": 94,
  "brand": "Apple",
  "category": "smartphones",
  "thumbnail": "https://i.dummyjson.com/data/products/1/thumbnail.jpg",
  "images": [
    "https://i.dummyjson.com/data/products/1/1.jpg",
    "https://i.dummyjson.com/data/products/1/2.jpg",
    "https://i.dummyjson.com/data/products/1/3.jpg",
    "https://i.dummyjson.com/data/products/1/4.jpg",
    "https://i.dummyjson.com/data/products/1/thumbnail.jpg"
  ]
}
```

``` java
public class ProductResponse {
    public int id;
    public String title;
    public String description;
    public int price;
    public double discountPercentage;
    public double rating;
    public int stock
    public String brand;
    public String category;
    public String thumbnail;
    public String images[];
}
```

Using Path Variables

``` java

public interface ProductService {

    @GET("/products/{id}")
    Single<ProductResponse> getProductById(@Path("id") int id);

}

```

Using Query Parameters

``` java
public interface OpenWeatherMapService {
    @GET("/data/2.5/weather")
    Single<CurrentWeather> currentWeather(@Query("q") String city);
}
```

``` java 
    // configure Retrofit for the dummyjson website
    Retrofit retrofit = new Retrofit.Builder()
                .baseUrl("https://dummyjson.com/")
                // Configure Retrofit to use Gson to turn the Json into Objects
                .addConverterFactory(GsonConverterFactory.create())
                // Configure Retrofit to use Rx 
                .addCallAdapterFactory(RxJava3CallAdapterFactory.create())
                .build();
                
    ProductService service = retrofit.create(ProductService.class);
```

Use this code in tests **ONLY**

``` java 
    // given
    // create your service...
    
    // when
    // blockingGet() will wait until the data is downloaded and should only be used in tests.
    ProductResponse response = service.getProductById(1).blockingGet();
    
    // then
    assertNotNull(response.title);
    assertNotNull(response.description);
```

Use this in application code.

``` java 
    // This will make a request for the ProductResponse on a separate Thread.
    Disposable disposable = service.getProductById(1)
                // tells Rx to request the data on a background Thread
                .subscribeOn(Schedulers.io())
                // tells Rx to handle the response on Swing's main Thread
                .observeOn(Schedulers.from(SwingUtilities::invokeLater))
                //.observeOn(AndroidSchedulers.mainThread()) // Instead use this on Android only
                .subscribe(
                        (response) -> handleResponse(response),
                        Throwable::printStackTrace);
```

Controller Tests Should have this at the top of the class.

``` java
    // Put this ONCE at the top of your Controller Tests
    // This makes it so that our Service returns immediately.
    static {
        RxJavaPlugins.setIoSchedulerHandler(scheduler -> Schedulers.trampoline());
        RxSwingPlugins.setOnEdtScheduler(scheduler -> Schedulers.trampoline());
        // Use this instead if you are doing Android.
        // RxAndroidPlugins.setMainThreadSchedulerHandler(scheduler -> Schedulers.trampoline());
    }
```

