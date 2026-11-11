### Amazon DynamoDB

AWS documentation:

* [Programming DynamoDB with the AWS SDK for Java 2.x](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/ProgrammingWithJava.html)
* [DynamoDB examples using SDK for Java 2.x](https://docs.aws.amazon.com/sdk-for-java/latest/developer-guide/java_dynamodb_code_examples.html)
* [Working with items and attributes](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/WorkingWithItems.html)

``` groovy
    implementation 'software.amazon.awssdk:dynamodb:2.58.0'
```

Create a client. When running in a Lambda, credentials and region come from the environment.

``` java
    DynamoDbClient dynamoDbClient = DynamoDbClient.create();
```

Or set the region explicitly:

``` java
    DynamoDbClient dynamoDbClient = DynamoDbClient.builder()
            .region(Region.US_EAST_2)
            .build();
```

Values in DynamoDB are wrapped in `AttributeValue`. Use `.s(...)` for Strings, `.n(...)` for numbers (as a String), and `.bool(...)` for booleans.

## Putting an item

``` java
    Map<String, AttributeValue> item = new HashMap<>();
    item.put("id", AttributeValue.builder().s(id).build());
    item.put("name", AttributeValue.builder().s(name).build());
    item.put("count", AttributeValue.builder().n(String.valueOf(count)).build());

    PutItemRequest putItemRequest = PutItemRequest.builder()
            .tableName(tableName)
            .item(item)
            .build();

    dynamoDbClient.putItem(putItemRequest);
```

You must give your Lambda `AmazonDynamoDBFullAccess` (or a more limited write policy).

## Getting an item

You look up an item by its primary key.

``` java
    Map<String, AttributeValue> key = new HashMap<>();
    key.put("id", AttributeValue.builder().s(id).build());

    GetItemRequest getItemRequest = GetItemRequest.builder()
            .tableName(tableName)
            .key(key)
            .build();

    Map<String, AttributeValue> item = dynamoDbClient.getItem(getItemRequest).item();
    if (item == null || item.isEmpty()) {
        // item was not found
        return;
    }

    String name = item.get("name").s();
    int count = Integer.parseInt(item.get("count").n());
```

You must give your Lambda `AmazonDynamoDBReadOnlyAccess` (or Full Access if it also writes).

## Querying items

Use `query` when you know the partition key and want matching items. Prefer this over `scan`.

``` java
    Map<String, AttributeValue> expressionValues = new HashMap<>();
    expressionValues.put(":id", AttributeValue.builder().s(id).build());

    QueryRequest queryRequest = QueryRequest.builder()
            .tableName(tableName)
            .keyConditionExpression("id = :id")
            .expressionAttributeValues(expressionValues)
            .build();

    List<Map<String, AttributeValue>> items = dynamoDbClient.query(queryRequest).items();
```

## Scanning a table

`scan` reads every item in the table. Use it only for small tables or when you do not know the key.

``` java
    ScanRequest scanRequest = ScanRequest.builder()
            .tableName(tableName)
            .build();

    List<Map<String, AttributeValue>> items = dynamoDbClient.scan(scanRequest).items();
```

## Deleting an item

``` java
    Map<String, AttributeValue> key = new HashMap<>();
    key.put("id", AttributeValue.builder().s(id).build());

    DeleteItemRequest deleteItemRequest = DeleteItemRequest.builder()
            .tableName(tableName)
            .key(key)
            .build();

    dynamoDbClient.deleteItem(deleteItemRequest);
```

You must give your Lambda `AmazonDynamoDBFullAccess` (or a more limited write policy).

## Storing an object as JSON

If you want to store a whole Java object, convert it with `Gson` and save it as a String attribute.

``` java
    String json = gson.toJson(myObject);

    Map<String, AttributeValue> item = new HashMap<>();
    item.put("id", AttributeValue.builder().s(id).build());
    item.put("data", AttributeValue.builder().s(json).build());

    dynamoDbClient.putItem(PutItemRequest.builder()
            .tableName(tableName)
            .item(item)
            .build());

    // later, when reading:
    MyObject myObject = gson.fromJson(item.get("data").s(), MyObject.class);
```
