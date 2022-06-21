# Elasticity-Labs-3
##  Labs on Amazon Auto Scaling Groups

### Description : Creating an auto scaling group from a launch template

<P> Auto Scaling helps you maintain application availability and allows you to scale your Amazon EC2 capacity up or down automatically according to the defined conditions. You can use Auto Scaling to help ensure that you are running your desired number of Amazon EC2 instances. Auto Scaling can also automatically increase the number of Amazon EC2 instances during demand spikes to maintain performance and decrease capacity during lulls to reduce costs. Auto Scaling is well suited to applications that have stable demand patterns, or that experience hourly, daily, or weekly variability in usage.
  
Also Auto scaling group is a feature of EC2 instances on AWS. An auto-scaling group consists of several EC2 instances, which can increase or decrease in numbers depending upon the scaling policy attached to the group. Auto scaling group monitors the health and load on the instances in the group, and depending upon the policy, it launches or terminates the instances to maintain a specific number of instances in the group. Auto-scaling groups are used to deploy a highly available and scalable infrastructure on AWS. In this guide, we will discuss the following steps to configure auto-scaling groups.
  
###  Create a launch template
Launch template is a kind of structure of the EC2 instances that includes all the instances’ details and parameters. All the instances in the auto-scaling group are launched using either the launch template or the launch configuration. Launch templates are newer to AWS than launch configuration and have more options to customize the EC2 instance configuration. That is why, in this blog, the launch template will be used to create an auto-scaling group.  
  
  In order to create a launch template, 
  
1. Log into the Amazon EC2 console at https://console.aws.amazon.com/ec2/. and select the region where all the infrastructure will be deployed.
  
2. From the top right corner of the management console, click on the region button and select the appropriate region. For this blog, we will deploy our infrastructure in the us-east-1 (N. Virginia) region.
  
  ![autoscale 2](https://user-images.githubusercontent.com/103466963/174792371-83521dde-fe68-405a-9512-f633d4571778.png)
  
3. Now search for the EC2 service from the management console.
  
  ![autoscale 3](https://user-images.githubusercontent.com/103466963/174792758-600b1e50-23fc-42c7-a3a0-62d2775205b9.png)
  
4. From the left side panel, go to the Launch Templates under the Instances section.
  
![autoscale 4](https://user-images.githubusercontent.com/103466963/174793622-952029d1-6b84-4b58-8df1-7a9cf16f7122.png)

  
  
  
  
  
