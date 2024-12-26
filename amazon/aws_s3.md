### Amazon S3

``` groovy
    implementation 'software.amazon.awssdk:s3:2.20.36'
```

## Reading a file

In order to read a file from S3 you must upload it, keeping track of the Bucket and Key of the file.

``` java

        S3Client s3Client = S3Client.create();

        GetObjectRequest getObjectRequest = GetObjectRequest
                .builder()
                .bucket(bucketName)
                .key(key)
                .build();

        InputStream in = s3Client.getObject(getObjectRequest);
```

You must give your Lambda `AmazonS3ReadOnlyAccess`.

## Writing a file to S3

``` java 

        Region region = Region.US_EAST_1;
        S3Client s3Client = S3Client.builder()
                .region(region)
                .build();
                
        PutObjectRequest putObjectRequest = PutObjectRequest.builder()
              .bucket(bucketName)
              .key(keyName)
              .build();

       s3Client.putObject(putObjectRequest, RequestBody.fromString(content));
            
```

You must give your Lambda `AmazonS3FullAccess`.

## Turning an Object into JSON

``` java
    
    StationsResponse response...
    Gson gson = new Gson();
    String content = gson.toJson(response);

```
