---
title: "Connect to the shell of you Linux EC2 instance"
date: 2021-01-09T22:27:47Z
draft: false
weight: 150
pre: '<b style="color:#fff;">2.5 </b>'
---
You can use the key pair to connect to your Linux EC2 instance by SHH client, for this purpose we are going to use [AWS Systems Manager](https://aws.amazon.com/systems-manager/) using [Session Manager](https://docs.aws.amazon.com/systems-manager/latest/userguide/session-manager.html).
Systems Manager Gain Operational Insight and Take Action on AWS Resources. We are going to take a look a just one of seven capabilities of Systems Manager.

2.5.1\. Open de AWS Systems Manager console at https://console.aws.amazon.com/systems-manager/. 

2.5.2\. From the menu on the left, scroll down and select **Session Manager**. Session Manager allows us to use IAM roles and policies to determine who has console access without having to manage SSH keys for our instances. In the main pane, click the **Start session** button. 

![Session Manager](../images/sm-home.png)

2.5.3\. Select the radio button next to the instance you wish to log into.

![Session Start](../images/sm-start.png)

2.5.4\. You will now receive a Bash shell prompt for that instance.

![Session Bash](../images/sm-bash.png)

**Great Job! You have deployed a server and launched a web site in a matter of minutes!!**