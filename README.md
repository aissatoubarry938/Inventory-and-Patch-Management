# Inventory-and-Patch-Management

## Introduction
In this lab you will apply the concepts of Infrastructure as Code and Operations as Code to the following activities:

- Deployment of Infrastructure
- Inventory Management
- Patch Management

## Goals:
- Automated deployment of infrastructure
- Dynamic management of resources
- Automated patch management

## Prerequisites:
- An AWS account that you are able to use for testing, that is not used for production or other purposes.
- An IAM user or role in your AWS account with full access to CloudFormation, EC2, VPC, IAM.

# Setup:

# 2.1 Create Administrator IAM User and Group
To create an administrator user for yourself and add the user to an administrators group:

1. Use your AWS account email address and password to sign in as the AWS account root user to the IAM console at https://console.aws.amazon.com/iam/.
2. In the IAM navigation pane, choose Users and then choose Add user.
3. In Set user details for User name, type a user name for the administrator account you are creating. The name can consist of letters, digits, and the following characters: plus (+), equal (=), comma (,), period (.), at (@), underscore (_), and hyphen (-). The name is not case sensitive and can be a maximum of 64 characters in length.
4. In Select AWS access type for Access type, select the check box next to AWS Management Console access, select Custom password, and then type your new password in the text box. If you’re creating the user for someone other than yourself, you can leave Require password reset selected to force the user to create a new password when first signing in. Clear the box next to Require password reset and then choose Next: Permissions.
5. In set permissions for user ensure Add user to group is selected.
6. Under Add user to group choose Create group.
7. In the Create group dialog box, type a Group name for the new group, such as Administrators. The name can consist of letters, digits, and the following characters: plus (+), equal (=), comma (,), period (.), at (@), underscore (_), and hyphen (-). The name is not case sensitive and can be a maximum of 128 characters in length. In the policy list, select the check box next to AdministratorAccess and then choose Create group.
8. Back at Add user to group, in the list of groups, ensure the check box for your new group is selected. Choose Refresh if necessary to see the group in the list. choose Next: Tags to optionally add key-value pair tags to an IAM entitiy. You can use tags to control an entity’s access to resources or to control what tags can be attached to an entitiy.
9. In Add tags (optional) enter a Key of “ROLE” and a Value of “Administrator”. Learn more about Tagging IAM users and roles.
10. Next choose Next: Review to see the list of group memberships to be added to the new user. When you are ready to proceed, choose Create user.
11. At the confirmation screen you do not need to download the user credentials for programmatic access at this time. You can create new credentials at any time.

![New user](https://github.com/aissatoubarry938/Inventory-and-Patch-Management/assets/115582067/b53c0697-617f-4156-8b6c-86b7b8697f75)

![permissions](https://github.com/aissatoubarry938/Inventory-and-Patch-Management/assets/115582067/8a201536-cef1-4ba0-b7fa-8828da49298d)

![groups](https://github.com/aissatoubarry938/Inventory-and-Patch-Management/assets/115582067/d67bcdfb-9861-42aa-a7f2-248b4455c06d)

![tags](https://github.com/aissatoubarry938/Inventory-and-Patch-Management/assets/115582067/8a50e3bc-2cab-44e9-88b3-8c1dd0b1f928)


# 2.2 Log in to the AWS Management Console using your administrator account
1. You can now use this administrator user instead of your root user for this AWS account. Choose the link https://<yourAccountNumber>.signin.aws.amazon.com/console and log in with your administrator user credentials.
2. Select the region you will use for the lab from the the list in the upper right corner.
3. Verify that you have 2 available VPCs (3 or less in use) in the selected region by navigating to the VPC Console (https://console.aws.amazon.com/vpc/) and in the Resources section reviewing the number of VPCs.
  
![vpc](https://github.com/aissatoubarry938/Inventory-and-Patch-Management/assets/115582067/9ad830c9-d737-41df-9638-d21f2c9d1dc2)
  
 # 2.3 Create an EC2 Key Pair
Amazon EC2 uses public-key cryptography to encrypt and decrypt login information. Public-key cryptography uses a public key to encrypt a piece of data, such as a password, then the recipient uses the private key to decrypt the data. The public and private keys are known as a key pair. To log in to the Amazon Linux instances we will create in this lab, you must create a key pair, specify the name of the key pair when you launch the instance, and provide the private key when you connect to the instance.

1. Use your administrator account to access the Amazon EC2 console at https://console.aws.amazon.com/ec2/.
2. In the EC2 navigation pane under Network & Security, choose Key Pairs and then choose Create Key Pair.
3. In the Create Key Pair dialog box, type a Key pair name such as OELabIPM and then choose Create.
4. Save the keyPairName.pem file for optional later use accessing the EC2 instances created in this lab.

  ![keypair](https://github.com/aissatoubarry938/Inventory-and-Patch-Management/assets/115582067/57fb28bb-2b1f-48a1-a69d-75ba14e19299)
  
