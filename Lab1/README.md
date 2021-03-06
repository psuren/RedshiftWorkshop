# LAB 1 - Launching a Redshift Clusters in your account using Cloud Formation. 
In this lab you will launch a new Redshift Cluster, Install the client tool of your preference and setup connectivity to stablish a connectivity with Amazon Redshift Cluster.

## Contents
  - [Prerequisites](#Prerequisites)
  - [Cloud Formation](#Cloud-Formation)
  - [Launching Redshift Cluster](#Launching-Redshift-Cluster)
  - [Installing client tool](#Installing-client-tool)
  - [Connecting to your Redshift Cluster](#Connecting-to-your-Redshift-Cluster)

### **Important**

If you are attending one of the Redshift Days at AWS Loft and you were provided an AWS account for the labs. Please skip the Cloud Formation and Launching a Redshift Cluster steps. Start from **[Installing client tool](#Installing-client-tool)** 

## Prerequisites
In this lab, you will launch a Redshift Cluster in your account using a Cloud Formation template provided in the link bellow. For better performance and to avoid cost transfer between Amazon Redshift cluster and S3, make sure you are in the US-EAST-1 region.



## Cloud Formation
Using the Cloudformation template provided, we will launch a Redshift Cluster in your account. The CloudFormation template will create a Amazon Redshift cluster and aditional resources that are required for security and to make your cluster accessible from public endpoint. 

Here are the following resources we will create in your account
* Amazon Redshift Cluster with 2 dc.xlarge nodes  
* VPC and Subnet 
* Security Groups for Amazon Redshift access 
* Internet Gateway to make Amazon Redshift accessible publicy 
* Route Table with a route to the internet
* IAM Role that will be attached to your Amazon Redshift Cluster 
  

## Launching Redshift Cluster

Go ahead and click on `Launch Stack` to launch a Redshift Cluster in your account using the Cloud Formation template provided. You should be able see the initial `Create Stack` page. Choose `Next` to specify the parameters.  

[![Launch](https://github.com/andrehass/RedshiftWorkshop/blob/master/Images/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?#/stacks/new?stackName=RedshiftDay&templateURL=https://s3.amazonaws.com/reinvent-hass/code/redshiftTemplate.json)  

On Specify stack details, provide a `MasterUserName` and `MasterUserPassword` of your choice. Leave all the other parameters unchanged and choose next. 

MasterUserPassword Must contain at least 1 lowercase letter. Password may not contain ",/,@, or unprintable characters.

![Cloud Formation](https://github.com/andrehass/RedshiftWorkshop/blob/master/Images/CloudFormationParameter1.jpg "Cloud Formation Template")

In the `Configure stack options`, Click Next 

In the Review, scroll down to the end of the page and check the option `I acknowledge that AWS CloudFormation might create IAM resources.` to acknowledge the creation of IAM resources and click Create Stack. Wait a few minutes for the cluster to become available.

![Cloud Formation Acknowledgment](https://github.com/andrehass/RedshiftWorkshop/blob/master/Images/CloudFormationAck.jpg "Cloud Formation Acknowledgment")


## Installing client tool

You will need to install a client tool to be able to connect on your Amazon Redshift Cluster. The following client tools are suggested for this Lab. Please feel free to use any tool you prefer. If you are familiar with Postgres command line client tool (psql), you can also use as your client tool. 


* [TablePlus](https://tableplus.com/) - Java is not required run this client tool. 
* [DB Beaver](https://dbeaver.io/download/)
* [WorkbenchJ](https://www.sql-workbench.eu/downloads.html) 
* [Aginity - Windows Only](https://www.aginity.com/main/workbench-for-amazon-redshift/)


## Connecting to your Redshift Cluster

On AWS console main page, go to Services and select Amazon Redshift. Alternatively, type Redshift in the search field and choose Amazon Redshift when you see in the results.
In the Redshift dashboard, choose Clusters on the left-hand side. You should see your cluster recently launched listed with the name `redshiftday`. Check the Cluster Status. You are ready to connect if the status says `available`. Choose `redshiftday` cluster to access cluster details and connections parameters. 

![alt text](https://github.com/andrehass/RedshiftWorkshop/blob/master/Images/Redshift_WS_Console.jpg "Logo Title Text 1")

Copy the endpoint details and save it to connect on the cluster. The endpoint will look similar to this one `redshiftday.xxxxxxxxxx.us-east-1.redshift.amazonaws.com:5439`

You may need the JDBC URL depending on the tool you are using to connect to the Redshift Cluster. Scroll down on the same page and look for JDBC URL.  

JDBC URL will look similar to the JDBC URK bellow;  

`jdbc:redshift:/redshiftday.xxxxxxxxxx.us-east-1.redshift.amazonaws.com:5439/dev`

Use the connection information to access your cluster. 

Credentials to log into the Redshift cluster.  

**Username:** `dwuser`  

**Password:**  `redshiftDay2019` 


You should now connect to your Amazon Redshift Cluster. You now can move to the Lab 2. 

**Important** If you leave earlier or don't have plans to complete the remaining Labs. Make sure you delete the resources created in your acoount to avoid any unespected charges. Please refer to [Remove CloudFormation Stack](https://github.com/andrehass/RedshiftWorkshop/blob/master/cleanresources.md) for instructions on how to remove the CloudFormation Stack.  

