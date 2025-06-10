# **Secure a Private S3 Bucket for a Specific IAM User**
---

## **🎯 Goal:**

* Create a private S3 bucket
* Upload a file to it
* Block all public access
* Allow access only to a specific IAM user

## **Step 1: Create a Private S3 Bucket**

1) Log in to AWS Console
2) Go to S3 > Create bucket
3) Bucket name: my-private-bucket
4) Region: US East (N. Virginia) or your preferred region
5) Uncheck "Block all public access" (keep it blocked)
6) Enable versioning
7) Click Create bucket

## **Step 2: Upload a Test File**

1) Click on your bucket name
2) Go to Objects > Upload
3) Click Add files → Choose a file (e.g., test.txt)
4) Click Upload

## **Step 3: Create a New IAM User**

1) Go to IAM > Users > Add users
2) Username: s3-access-user
3) Access type: Programmatic access
4) Click Next > Next > Create user
5) Download the credentials (save access key & secret key securely)

## **Step 4: Create a Custom Policy to Allow Readonly Access**

1) Go to IAM > Policies > Create Policy
2) Switch to JSON tab
3) Paste the following JSON file

```
     {
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:GetObject",
        "s3:ListBucket"
      ],
      "Resource": [
        "arn:aws:s3:::my-private-bucket-shivraj",
        "arn:aws:s3:::my-private-bucket-shivraj/*"
      ]
    }
  ]
}
```

4) Click Next
5) Name: AllowAccessToPrivateBucket (my-private-bucket)
6) Click Create policy

## **Step 5: Attach Policy to the IAM User**

1) Go to IAM > Users > s3-access-user
2) Click Add permissions > Attach policies
3) Select AllowAccessToPrivateBucket
4) Click Add permissions




