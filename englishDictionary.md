### englishDictionary CSV

The file we are going to use comes from this [repo](https://github.com/benjihillard/English-Dictionary-Database) and is
located [here](englishDictionary.csv)

Add this to your build.gradle dependencies

``` groovy
implementation 'org.apache.commons:commons-csv:1.10.0'
```

To read the file use [Apache Commons CSV](https://commons.apache.org/proper/commons-csv/) which you can learn
about [here](https://www.baeldung.com/apache-commons-csv)