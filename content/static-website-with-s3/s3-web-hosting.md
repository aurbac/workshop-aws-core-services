---
title: "Configure the S3 bucket for static website hosting"
date: 2021-01-09T21:49:25Z
draft: false
weight: 110
---
3.1\. Inside your Amazon S3 bucket, choose **Properties**.

![S3 Files](images/s3-properties.png)

3.2\. Scroll down to **Static website hosting** section and choose **Edit**.

![S3 Website](images/s3-website.png)

3.3\. For **Static website hosting** choose **Enable**, for **Index document** type `index.html` and for **Error document** type `error.html`, click **Save changes**.

![S3 Website Conf](images/s3-website-conf.png)

3.4\. Copy the **Bucket website endpoint** created for you website.

![Copy endpoint](images/s3-copy-endpoint.png)

3.5\. Open a new browser tab and browse the static website by entering the Endpoint copied. You should see a website that looks like the following:

![S3 Website](images/s3-website-live.png)

**Great Job! You have deployed a static website!!**