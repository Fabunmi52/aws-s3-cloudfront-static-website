```mermaid
flowchart TD
    User([User])
    Route53[Amazon Route 53]
    CloudFront[Amazon CloudFront]
    OAC[Origin Access Control]
    S3[(Amazon S3 Bucket)]

    User --> Route53
    Route53 --> CloudFront
    CloudFront --> OAC
    OAC --> S3
```
