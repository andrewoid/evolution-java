### Amazon S3

``` groovy
    implementation 'software.amazon.awssdk:s3:2.20.36'
```

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

You must give your Lambda `S3ReadOnlyAccess`.