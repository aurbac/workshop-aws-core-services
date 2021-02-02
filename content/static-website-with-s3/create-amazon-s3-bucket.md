---
title: "Create an Amazon S3 bucket"
date: 2021-01-09T21:48:25Z
draft: false
weight: 90
pre: '<b style="color:#fff;">1. </b>'
---
1.1\. Open the Amazon S3 console at https://console.aws.amazon.com/s3/.

1.2\. Choose **Create bucket**.

![S3 Create](../images/s3-create-bucket.png)

1.3\. In the **Bucket name** field, type a unique DNS-compliant name for your new bucket, for example `<your-name>-website`.

* The name must be unique across all existing bucket names in Amazon S3.
* After you create the bucket you cannot change the name, so choose wisely.
* Choose a bucket name that reflects the objects in the bucket because the bucket name is visible in the URL that points to the objects that you're going to put in your bucket.

1.4\. For **Region**, choose **US East (N. Virginia)** as the region where you want the bucket to reside.

1.5\. For **Bucket settings for Block Public Access**, uncheck **Block all public access**.

1.6\. Validate the configurations, check **I acknowledge...**  and choose **Create bucket**.

![S3 Create](../images/s3-create.png)