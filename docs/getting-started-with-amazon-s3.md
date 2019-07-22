# Publish a Static WebSite with Amazon S3

[!embed?max_width=1200](https://www.youtube.com/watch?v=_I14_sXHO8U)

[Amazon Simple Storage Service](https://aws.amazon.com/s3/) is storage for the Internet. It is designed to make web-scale computing easier for developers and also you can host a Static Website in an Amazon S3 bucket.

## 1. Create an Amazon S3 bucket

1.1\.	Open the Amazon S3 console at https://console.aws.amazon.com/s3/.

1.2\.	Choose **Create bucket**.

1.3\.	In the **Bucket name** field, type a unique DNS-compliant name for your new bucket, for example `<your-name>-website`.

* The name must be unique across all existing bucket names in Amazon S3.
* After you create the bucket you cannot change the name, so choose wisely.
* Choose a bucket name that reflects the objects in the bucket because the bucket name is visible in the URL that points to the objects that you're going to put in your bucket.

1.4\.	For Region, choose **US East (N. Virginia)** as the region where you want the bucket to reside.

1.5\.	Choose **Create**.

![S3 Create](images/s3-create.png)

## 2. Editing Public Access Settings for an S3 Bucket

2.1\.	Open the Amazon S3 console at https://console.aws.amazon.com/s3/.

2.2\.	In the **Bucket name** list, choose the name of the bucket that you created **`<your-name>-website`**.

2.3\.	Choose **Permissions** and choose **Edit** to change the public access settings for the bucket.

![S3 Permissions Edit](images/s3-permissions-edit.png)

2.4\.	Uncheck the following options and Choose **Save**.

* **Block all public access**

    * **Block public access to buckets and objects granted through new access control lists (ACLs)**
    * **Block public access to buckets and objects granted through any access control lists (ACLs)**

![S3 Permissions](images/s3-permissions.png)

2.5\.	When you're asked for confirmation, enter `confirm`. Then choose **Confirm** to save your changes.

## 3. Create a Cloud9 instance to upload your static Website

[AWS Cloud9](https://aws.amazon.com/cloud9/) is a cloud-based integrated development environment (IDE) that lets you write, run, and debug your code with just a browser. It combines the rich code editing features of an IDE such as code completion, hinting, and step-through debugging, with access to a full Linux server for running and storing code.

3.1\. Open the AWS Cloud9 console at https://console.aws.amazon.com/cloud9/.

3.2\. Click on **Create environment**.

![Cloud9 Create environment](images/cloud9-create.png)

3.3\. For the **Name** type `MyDevelopmentInstance`, and choose **Next step**.

![Cloud9 name environment](images/cloud9-name.png)

3.4\. For the **Environment settings** use the default values and choose **Next step**.

3.5\. Click on **Create environment**.

3.6\. Wait some seconds until your development environment is ready, you will see the following screen.

![Cloud9 Env](images/cloud9-env.png)

3.7\. Inside the bash terminal execute the following commands:

* Download static website from github.
```console
git clone https://github.com/aurbac/static-website.git
```
* Upload static website, change **`<your-name>-website`** with your bucket name.
```console
aws s3 cp static-website/ s3://<your-name>-website/ --recursive --exclude ".git/*" --acl public-read
```

## 4. Configure the S3 bucket for static website hosting

4.1\. Open the Amazon S3 console at https://console.aws.amazon.com/s3/.

4.2\. In the **Bucket name** list, choose the name of the bucket that you created **`<your-name>-website`**.

4.3\. Choose **Properties**.

4.4\. Choose **Static website hosting**.

![S3 Website](images/s3-website.png)

4.5\. Choose **Use this bucket to host a website** and for **Index document** type `index.html`, copy the **Endpoint** and click **Save**.

![S3 Website Conf](images/s3-website-conf.png)

4.6\. Open a new browser tab and browse the static website by entering the Endpoint copied. You should see a website that looks like the following:

![S3 Website](images/s3-website-live.png)

**Great Job! You have deployed a static website!!**