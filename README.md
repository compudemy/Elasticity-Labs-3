# Elasticity-Labs-3
##  Labs on Amazon Auto Scaling Groups

### Description : Creating an auto scaling group from a launch template

<P> Auto Scaling helps you maintain application availability and allows you to scale your Amazon EC2 capacity up or down automatically according to the defined conditions. You can use Auto Scaling to help ensure that you are running your desired number of Amazon EC2 instances. Auto Scaling can also automatically increase the number of Amazon EC2 instances during demand spikes to maintain performance and decrease capacity during lulls to reduce costs. Auto Scaling is well suited to applications that have stable demand patterns, or that experience hourly, daily, or weekly variability in usage.
  
Also Auto scaling group is a feature of EC2 instances on AWS. An auto-scaling group consists of several EC2 instances, which can increase or decrease in numbers depending upon the scaling policy attached to the group. Auto scaling group monitors the health and load on the instances in the group, and depending upon the policy, it launches or terminates the instances to maintain a specific number of instances in the group. Auto-scaling groups are used to deploy a highly available and scalable infrastructure on AWS. In this guide, we will discuss the following steps to configure auto-scaling groups.
  
### Step 1:Create a launch template
Launch template is a kind of structure of the EC2 instances that includes all the instances’ details and parameters. All the instances in the auto-scaling group are launched using either the launch template or the launch configuration. Launch templates are newer to AWS than launch configuration and have more options to customize the EC2 instance configuration. That is why, in this blog, the launch template will be used to create an auto-scaling group.  
  
  In order to create a launch template, 
  
1. Log into the Amazon EC2 console at https://console.aws.amazon.com/ec2/. and select the region where all the infrastructure will be deployed.
  
2. From the top right corner of the management console, click on the region button and select the appropriate region. For this blog, we will deploy our infrastructure in the us-east-1 (N. Virginia) region.
  
  ![autoscale 2](https://user-images.githubusercontent.com/103466963/174792371-83521dde-fe68-405a-9512-f633d4571778.png)
  
3. Now search for the EC2 service from the management console.
  
  ![autoscale 3](https://user-images.githubusercontent.com/103466963/174792758-600b1e50-23fc-42c7-a3a0-62d2775205b9.png)
  
4. From the left side panel, go to the Launch Templates under the Instances section.
  
![autoscale 4](https://user-images.githubusercontent.com/103466963/174793622-952029d1-6b84-4b58-8df1-7a9cf16f7122.png)

5. Click on the Create launch template button to create a new launch template, and it will open a form asking for different parameters for the launch template.  
  
6. Enter the Launch template name under the Launch template name and description section.  
  
 ![autoscale 5](https://user-images.githubusercontent.com/103466963/174794427-4a4121f1-0f49-403b-ac41-3c8d19491c85.png)
  
6. Select the AMI under the Amazon machine image and the Instance type under the Instance type section.

  ![autoscale 6](https://user-images.githubusercontent.com/103466963/174795313-92749aeb-9f2f-4259-a1ad-650144969ba4.png)
  
7. Select the specific Key pair you want to use while logging into your server over SSH. If you do not have any key, create one by clicking on the Create new key pair.
  
  ![autoscale 7](https://user-images.githubusercontent.com/103466963/174797078-8d6b3cbd-901c-44be-8105-91213aea4d44.png)

8. Under the Network settings, select the Networking platform and security groups.

 ![autoscale 9](https://user-images.githubusercontent.com/103466963/174797591-35f5db33-f7d6-4b36-9315-1bcf73c0340d.png)

  Leave the rest of the parameters default and click on the create launch template button to create the launch template.

### Step 2: Create an auto-scaling group from the launch template  
  
  After creating the launch template, now create the auto-scaling group from the launch template. From the left side panel, click on the Auto Scaling Groups under the Auto Scaling section.

  

  
  
  
  
  
