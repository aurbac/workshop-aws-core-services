---
title: "Create Iam Group"
date: 2021-01-09T21:14:36Z
draft: false
weight: 90
---
An IAM group is a collection of users. Groups are often based on job function or role. They allow you to manage permissions by applying policies to each group rather than individual users.

1.1\. Open the IAM console at https://console.aws.amazon.com/iam/.

1.2\. In the navigation pane, click **Groups** and then click **Create New Group**.

1.3\. In the **Group Name** box, type `Administrators` as the name of the group and then click **Next Step**.

![IAM Group Name](images/iam-group-name.png)

1.4\. In the list of policies, select the check box for **AdministratorAccess** policy that you want to apply to all members of the group. Then click **Next Step**.

![IAM Group Policy](images/iam-group-policy.png)

1.5\. Click **Create Group**.

![IAM Group Create](images/iam-group-create.png)