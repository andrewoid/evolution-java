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

If the file in S3 is JSON then you can use `Gson` to turn it into an `Object`

``` java
    InputStream in = s3Client.getObject(getObjectRequest);
    MyJsonClass myJsonObject = gson.fromJson(new InputStreamReader(in), MyJsonClass.java);
```

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

If the content is an Object you want to store as JSON then you can use `Gson`.

``` java
    String content = gson.toJson(myJsonObject);
    s3Client.putObject(putObjectRequest, RequestBody.fromString(content));
```

### Checking Age in S3

The following code checks to see if the file in S3 was last modified over an hour ago.

``` java 
        HeadObjectRequest headObjectRequest = HeadObjectRequest.builder()
                .bucket(BUCKET)
                .key(KEY)
                .build();

        try {
            HeadObjectResponse headObjectResponse = s3Client.headObject(headObjectRequest);
            Instant lastModified = headObjectResponse.lastModified();
            return Duration.between(lastModified, Instant.now()).toHours() > 0;
        } catch (Exception e) {
            // either the file doesn't exist in S3 or you don't have access to it.
            return false;
        }
```
