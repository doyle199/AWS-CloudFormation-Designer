# AWS-CloudFormation-Designer
AWS CloudFormation Designer

To get started we will use the AWS CloudFormation designer tool to create a basic web server. It is an intuitive drag and drop tool that allows users to drag resources into a plane and connect them in different ways. You can then launch the infrastructure as a stack.
To start, navigate to AWS CloudFormation and click on designer in the left menu.

![alt text](https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/stacks1.png)

Then click on the edit icon in the lower left of the page. Name the environment and click enter.

![alt text](https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/params1.png)

In the resources pane in the left, open the drop down for EC2 and drag a VPC into the canvas. Then rename the VPC.

![alt text](https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/vpc2.png)

Expand the VPC and drag a Subnet into it. Then rename the subnet.

![alt text](https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/sub2.png)

Drag an instance into the subnet and rename it. The instance will be used to host a website.

![alt text](https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/drag2.png)

Drag and drop a security group into the VPC and rename it. The security group acts as a firewall and is required for the instance in a VPC.

![alt text](https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/dragvps.png)

Drag and drop an internet gateway into the VPC and rename it. The internet gateway will be the connection to the internet.

![alt text](https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/des1.png)

Attach the internet gateway from the AWS::EC2 VPCGatewayAttachment to the VPC. The VPC will turn green.

![alt text](https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/red1.png)

Add a route table and rename it. This changes the direction of the internet gateway VPC connection.

![alt text](https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/inter1.png)

Add a route table in the public route table and rename it. This is to add a rule to the public route table. 

![alt text](https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/pub2.png)

Connect the Public Route gateway ID to the Internet Gateway.

![alt text](https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/webser2.png)

Connect the PublicRoute Depends on node to the Internet Gateway to VPC attachment. Connect to the line that connects the resources not the resources themselves. 

![alt text](https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/sub3.png)

Create a dependency between the Web Server Instance and the Public Route resource because the web server needs the route to route traffic correctly.

![alt text](https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/sub4.png)

Connect the Public Route Table to the Public Subnet so the public subnet routes correctly.

![alt text](https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/sub5.png)

Click save in the upper left corner and save it locally.

![alt text](https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/save.png)

![alt text](https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/save2.png)

Now we will add parameters, mappings, and outputs. Click on a blank part of the editor. In the parameters tab and components view enter the following JSON script which specifies instance type, EC2 key-pair, and the IP address range for SSH: https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/template1.jscsrc

![alt text](https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/params2.png)

Next, in the mappings tab and components view enter the following JSON script which specifies an AMI ID for an EC2 instance: https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/template2.jscsrc

![alt text](https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/mapping.png)

In the Outputs tab and components view enter the following JSON script to output the website URL: https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/template3.jscsrc

![alt text](https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/outs.png)

Next, we will specify resource properties. Click on the VPC resource and in the properties tab components view paste the following JSON script between the “properties” brackets {}. This is for the DNS and CIDR: https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/template4.jscsrc

![alt text](https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/props4.png)

Click on the Public Subnet resource and in the properties tab components view paste the following JSON in the same place as the screenshot: https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/template5.jscsrc

![alt text](https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/props5.png)

Click on the Public Route resource and in the properties tab components view paste the following JSON in the same place as the screenshot. This directs traffic to the internet gateway: https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/template6.jscsrc

![alt text](https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/props7.png)

Click on the Web Server Security Group resource and in the properties tab components view paste the following JSON in the same place as the screenshot. This is for HTTP and SSH traffic: https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/template7.jscsrc

![alt text](https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/props8.png)

Click on the Web Server Instance resource and in the properties tab components view paste the following JSON script, replacing what’s there: https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/template8.jscsrc

![alt text](https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/props9.png)

In the Metadata tab components view in the metadata brackets after the closing bracket for AWS::CloudFormation::Designer put a comma then paste the following JSON script after the comma. This is to start the web server to create a webpage: https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/template9.jscsrc

![alt text](https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/Props10.png)

Click the checked box at the top to validate the template.

![alt text](https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/valid.png)

![alt text](https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/valid2.png)

Choose the cloud with the up-arrow icon to create a stack and click next.

![alt text](https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/ready.png)

Create a name, choose an EC2 Key Pair, and click next.

![alt text](https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/name.png)

Click next and create stack.

![alt text](https://github.com/doyle199/AWS-CloudFormation-Designer/blob/master/stack4.png)

This concludes the deployment of a basic web server using the CloudFormation designer. As you can see it is a fairly straight forward service that is good for visualizing your cloud infrastructures.











