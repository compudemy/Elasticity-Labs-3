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
  
 1. After creating the launch template, now create the auto-scaling group from the launch template. From the left side panel, click on the Auto Scaling Groups under the Auto Scaling section.

  ![autogroup 1](https://user-images.githubusercontent.com/103466963/174806090-be0aff21-0869-4ffb-a623-6e4ce742489c.png)

 2. Click on the Create Auto Scaling group to create a new auto-scaling group.  
  
 ![autogroup 2](https://user-images.githubusercontent.com/103466963/174808399-ac9c5753-889f-4069-a993-d14642e4f2da.png)

 3. Enter the name of the auto-scaling group and select the launch template created in the previous step. You can also switch to launch configuration instead of launch template by clicking on the Switch to launch configuration, but we will stick to the launch template for this blog.

 ![autogroup 3](https://user-images.githubusercontent.com/103466963/174808733-f76da9d8-14a4-4a64-a81a-5f6ac9cce42a.png)

4. Click on the Next button after entering the above details, and it will ask for the instant purchase option and network details. Select the Adhere to launch template as an instant purchase option.
  
 ![autogroup 4](https://user-images.githubusercontent.com/103466963/174809238-d94bb9f1-f2fc-45dd-80ec-d3e49ec2673a.png)
  
5. For the network, select the VPC and subnets you want to deploy instances in. For this blog, we will use default VPC and two subnets. You can select as many subnets as you want.

![autogroup 6](https://user-images.githubusercontent.com/103466963/174810690-b39a39d3-b64c-445d-89c2-8e598d3035bf.png)
  
6. After entering the network details, click on the Next button, and it will ask for the advanced options. Click on the Next button without entering or selecting any parameter, and it will ask for group size and scaling policy. Auto scaling group size defines the maximum and the minimum number of instances to be launched in an auto-scaling group and can also be used to maintain a constant number of instances on AWS. Enter the same number for Desired capacity, Minimum capacity, and Maximum capacity to maintain a constant number of instances in the auto-scaling group.
  
  For this demo, enter the 1 instance as Desired capacity and Minimum capacity and 3 instances as Maximum capacity.

![autogroup 7](https://user-images.githubusercontent.com/103466963/174814147-88a01be9-dfbf-4ca8-97eb-4e3367deb606.png)

### Step 3: A scaling policy is a set of configurations that decides when to launch or terminate the instances in the auto-scaling group. Scaling policy tracks a target defined using the Metric type and Target value while configuring the scaling policy. Following are the metric types provided by AWS.
  
    . Average CPU utilization
    . Average network in (bytes)
    . Average network out (bytes)
    . Application load balancer request count per target

  Auto scaling group monitors the selected metric type of all the instances, and whenever the average target value of the selected metric type goes above the threshold, the auto-scaling group launches more instances to handle the load.
  
1. For this demo, select Target tracking scaling policy, enter the Scaling policy name, select Average CPU utilization as Metric type, and 10 as Target value.
  
 ![autogroup 8](https://user-images.githubusercontent.com/103466963/174815668-70be1328-6074-46a5-916d-67c20d53b133.png)

 The above configuration will maintain a minimum of 1 instance running. Whenever the instance dies, the auto-scaling group will automatically launch a new instance. Also, when the load on the instance reaches more than 10%, the auto-scaling group will automatically launch a new instance. The auto-scaling group will not launch more than 3 instances at a time even if the load is more than 10% on all the instances as we have specified a maximum number of 3 instances.
  
  Now click on the Skip to review button to skip the remaining steps and click on the Create auto scaling group button at the end of the page after reviewing the configuration to create the auto scaling group.
  
### Step 4: Test auto scaling group

  After creating the auto scaling group, it will launch one EC2 instance as we have specified the desired capacity to be one EC2 instance. The auto scaling group can be tested by either terminating the instance or increasing the CPU utilization of the instance.

1. First, we will test the auto scaling group by terminating the EC2 instance. From the left side of the panel, select the Instances under the INSTANCES section.
  
2. Select the instance launched by the auto scaling group and click on the Instance state button on the top right corner. It will open a list, click on the Terminate instance to terminate the instance manually.
  
  ![abi 2](https://user-images.githubusercontent.com/103466963/174820354-80df2191-3a42-487a-af52-68af51ff47dc.png)
  
3. After 3 minutes of terminating the instance, the auto-scaling group will launch a new instance.  
 
  ![abi 3](https://user-images.githubusercontent.com/103466963/174821881-0169a21f-f449-419e-9a54-30c98cf25671.png)

 Another way to test the auto scaling group is to increase the load on the EC2 instance, as we have configured the CPU utilization as a metric of the scaling policy. Whenever the load on the CPU goes above 10%, the auto-scaling group will launch another EC2 instance. For this purpose, SSH into the EC2 instance and run an infinite loop.

 ![abi 4](https://user-images.githubusercontent.com/103466963/174822157-99054146-0a15-46b3-8cc3-ce75b6954d65.png)
  
 4. On the terminal, run the following command. 
  
  ![abi 5](https://user-images.githubusercontent.com/103466963/174822420-6e407243-89c2-40a0-b4b2-0e5e105ea3c1.png)

  It will run an infinite loop, and the CPU utilization will reach a maximum that will trigger the auto-scaling group to launch another instance. Go to the instances section to see the instances.

![abi 6](https://user-images.githubusercontent.com/103466963/174822819-8758443d-6bc9-47a6-b7a0-d3908708fc07.png)
  
  ### Step 4 : Delete auto scaling group

  This section will discuss how we can delete the auto scaling group on AWS, as whenever an instance is deleted, the auto scaling group will create another instance to maintain a specific number of instances. In order to delete the auto-scaling group,
  
 1. First edit the desired capacity and a minimum number of instances to 0. Select the Auto Scaling Groups from the EC2 console.

 2. Select the auto scaling group and click on the Edit button.  
  
  ![abi 8](https://user-images.githubusercontent.com/103466963/174823437-2e138624-8307-4159-8a22-debf9d28eb0a.png)
  
 3. Set the desired capacity and the minimum capacity to 0 and click on the Update button at the end of the page.

 4. It will automatically terminate all the instances launched by the auto scaling group to maintain the size of the group. Go to the instances section to see all the instances available.
  
  ![mine](https://user-images.githubusercontent.com/103466963/174836648-d9896ba4-52ab-48a3-984c-a685d7353bcb.png)

 5. Both the instances are terminated, and now the auto-scaling group can be deleted. From the auto scaling group section, select the auto scaling group and click on the Delete button.
  
  Now it will ask for your confirmation to delete the auto scaling group. Enter delete in the input bar and click on the Delete button to delete the auto scaling group.  
  
  ![abi 10](https://user-images.githubusercontent.com/103466963/174837616-faf26212-4081-443d-807a-a77266476dea.png)
 
  After deleting the auto scaling group, go to the launch template section to delete the launch template.

  Select the launch template and click on the Actions button. It will display a list of different options. Select the Delete template option from the list.

  ![delete 1](https://user-images.githubusercontent.com/103466963/174838108-61ed2121-b5d1-4d9a-86ea-5896a08c570d.png)
  
 Now it will ask for confirmation before deleting the launch template. Enter delete in the input bar and click on the Delete button to delete the launch template.
  
  ![delete 2](https://user-images.githubusercontent.com/103466963/174838378-a3538b01-2b2f-4ca8-b927-aaf3327845ce.png)

  Conclusion
Auto scaling group is the feature provided by AWS to create a highly available and scalable infrastructure on AWS cloud. Auto scaling group uses launch template or launch configuration to launch instances to scale the infrastructure on AWS. Launch template includes all the configurations required to launch new instances in the group. Auto scaling group provides different types of target tracking policies used to launch and terminate instances in the group. This guide provides a step-by-step procedure to create, manage and delete an auto-scaling group on AWS.  
  
  
  
