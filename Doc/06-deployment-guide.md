# Deployment Guide

This section documents the exact steps I followed to deploy my static website on AWS using Amazon S3, CloudFront, Route 53, and AWS Certificate Manager (ACM).


## Step 1 - Request an SSL Certificate

The first step was securing my domain with HTTPS.

I switched to the **US East (N. Virginia)** region because CloudFront requires SSL certificates to be created there.

Using **AWS Certificate Manager (ACM)**, I requested a public SSL certificate for my domain:

- `edwardfabunmi.online`
- `edukare.edwardfabunmi.online`

I selected **DNS Validation**, copied the CNAME records provided by ACM, and added them to my DNS configuration. After a few minutes, the certificate status changed to **Issued**, confirming that my domain ownership had been successfully verified.


## Step 2 - Configure DNS with Amazon Route 53

Next, I created a **Hosted Zone** in Amazon Route 53 for my domain.

AWS generated four **Name Server (NS)** records, which I copied and replaced in my domain registrar's DNS settings. After DNS propagation was complete, Route 53 became the authoritative DNS service for my domain.


## Step 3 - Create the Amazon S3 Buckets

To support both my root domain and the **www** subdomain, I created two Amazon S3 buckets.

### Primary Bucket

```text
edwardfabunmi.online
```

This bucket stores all of my website files, including HTML, CSS, JavaScript, and images.

For security, I kept the bucket **private** so that it could only be accessed through CloudFront.


## Step 4 - Upload Website Files

After creating the buckets, I uploaded my website assets to the primary S3 bucket.

These included:

```text
index.html
css/
js/
images/
```

Because CloudFront accesses the bucket using **Origin Access Control (OAC)**, I did not need to make the bucket publicly accessible.


## Step 5 - Create the CloudFront Distribution

To improve performance and deliver my website securely, I created an Amazon CloudFront distribution.

I configured it with the following settings:

| Setting | Value |
|----------|-------|
| Origin | Amazon S3 Bucket (`edwardfabunmi.online`) |
| Viewer Protocol Policy | Redirect HTTP to HTTPS |
| Default Root Object | `index.html` |
| Alternate Domain Name | `edwardfabunmi.online` |
| Origin Access Control | Enabled |
| SSL Certificate | AWS Certificate Manager (ACM) |

After the distribution finished deploying, CloudFront began serving my website from AWS Edge Locations around the world.


## Step 6 - Update the S3 Bucket Policy

Next, I updated the S3 bucket policy to allow access **only** from my CloudFront distribution.

This was achieved using **Origin Access Control (OAC)**.

By doing this:

- Users cannot access the S3 bucket directly.
- CloudFront is the only service allowed to retrieve the website files.
- My website follows AWS security best practices.


## Step 7 - Configure Route 53 DNS Records

With CloudFront deployed, I configured my DNS records in Amazon Route 53.

I created:

- An **A (Alias)** record pointing `edwardfabunmi.online` to the CloudFront distribution.

This connected my custom domain to CloudFront.


## Step 8 - Verify the Deployment

Finally, I verified that everything was working correctly by confirming that:

- The website loads successfully over **HTTPS**.
- The SSL certificate is valid.
- The custom domain resolves correctly.
- CloudFront caches and serves content from the nearest AWS Edge Location.
- The website is accessible from different devices and networks.

With these checks completed successfully, my static website was securely deployed and available globally through AWS's content delivery network.
