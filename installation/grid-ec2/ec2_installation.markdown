## Installing Grid on an EC2 Instance

We're going to quickly go over how you can quickly install a grid node on an ec2 instance. This is probably the fastest and easier way to set up a grid node if you have access to an AWS account.

## Step 1: Navigate to AWS account

![AWS HOME](../../resources/images/account_home.png)

## Step 2: EC2 Config Page

From the page above, you can click on EC2 and it will bring you to the EC2 configuration page.

![EC2 Config](../../resources/images/ec2_home.png)

## Step 3: Launch instance

Click on the launch instance button and it will start guiding you through the pages to launch an instance.

The first thing that needs to be done is we need to find the OpenMined AMI file. This is a community ami that can be accessed by anyone. The AMI makes it so that you don't need to do any of the complicated configuration of setting up a grid node. It is just a image of a server that was previously set up. **As of writing this it is only available in the us-east-1 AWS region.**

![Community AMI](../../resources/images/community-ami.png)

## Step 3: Go through the rest of the configuration

Next, you need to click the select button next to the OpenMined AMI and continue through the rest of the configuration. If there is nothing you want to change you can just click on through until it asks you to add a key pair.

![Tier Selection](../../resources/images/ec2_tier.png)

![Review and Launch](../../resources/images/launch_page.png)

![Key Pair](../../resources/images/keypair.png)

So, at this point you can just choose `Proceed without a key pair`. There was some issues with getting the AMI to actually use the the keys pairs chosen here so I created another account which can be logged into via a password. This is discussed further below. Once you've selected that and clicked the check box, you can click `Launch Instance`.

This will begin launching the EC2 instance and you can click on EC2 instance ID and it will take you to the status page. From here, you can get the EC2 IP address/host name.

![EC2 Address](../../resources/images/ec2_address.png)

## Step 4: SSH Into EC2 Instance

Now, we need to SSH into our EC2 instance and run a couple of commands to finish getting it set up.

```
ssh openmined@<ec2_address>
```

It will then prompt you for a password and you can supply the password `openmined`. You can change this if you feel like it!

## Step 5: IPFS Init and Start

We need to initialize IPFS and then start the daemon. Run the two commands below:

```
ipfs init
```

```
ipfs daemon --enable-pubsub-experiment
```

The first command initializes your IPFS environment, creating a public private key pair to use within the IPFS system. The second command launches the IPFS daemon so you can actually connect to other IPFS nodes.
