# AWS Solution Architect Associate study notes
**TABLE OF CONTENTS**
1. [AWS Global Infrastructure](#aws-global-infrastructurehttpsawsamazoncomabout-awsglobal-infrastructureregionsaz)
2. [IAM and AWS CLI](#iam-and-aws-cli)


## [AWS Global Infrastructure](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/)
- Regions
    - Are around the world
    - They have names (us-east-1, eu-west-3)
    - Regions are a cluster of data centers
    - Most services are region scoped
    - How to choose a region for a service?
        - Compliance
        - Proximity
        - Pricing
        - Available services [click to view services per region](https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/?p=ngi&loc=4)
- Availability Zones (AZ)
    - Multiple AZs compose a region (Min 2 / Max 6 || usually 3), example Sydney region has:
        - ap-southeast-2a
        - ap-southeast-2b
        - ap-southeast-2c
    - Each AZ has one or more data centers with own power, networking and connectivity
    - Each data center is isolated form each other to isolate disasters
    - Each AZ are connected with ultra low latency and high bandwidth networking
- Data Centers
- Points of presence (Edge locations)
    - Deviler content to end users with lower latency

-------------------------------------------------------------

## IAM and AWS CLI
IAM is Identity and Access Management and is a global service.

### Users, groups and policies
- Root user is created by default
    - Shouldn't be used or shared
- Users are people in the organization, can be inside groups
- Groups contain users only, not groups
- Users are not required to be in a group
- Users can be in multiple groups

### IAM Password and MFA
**Password**
Can apply security measures to the password for a better security, as the followings:
- Minimum password length
- Required characters:
    - Uppercase letters
    - Lowercase letters
    - numbers
    - non alphanumeric characters
    - Allow users to change their own password
    - Password expiration
    - Prevent reusage of password

**MFA**
Multi Factor Authenticator
Combinations of the password and a security device.
Devices:
- Virtual MFA:
    - Google authenticator
    - Authy
- Universal Second Factor (U2F) security key:
    - YubiKey
- Hardware Key Fob MFA devices:
    - Gemalto tokens
- Hardware Key Fob MFA devices for AWS GovCloud(US)
    - SurePassID

### IAM Permissions
- Users and groups are assigned JSON policies
- Policies describe permissions (allow actions)
- Alway provide the **least privilage principal**, no more permissions that the ones needed

### IAM Policies
High level overview of how policies work

#### Policy inheritance
- When policies are assigned to groups, all the users in the groups get the permissions from the policy.
- Single users can have inline policies if hey do not belong to any group.
- Users can belong to multiple groups when will get the policies permissions from the groups they belong to.

#### Policy Structure
Policies are composed by the following attributes:
- Version: Policy language version
- Id: Is an identifier for the policy **(optional)**.
- Statement: One or more individual statements, and consist of the following:
    - Sid: Identifier for the statement **(optional)**.
    - Effect: Determines if the statement is *Allow* or *Deny*.
    - Principal: Is the account/user/role where the policy will be applied.
    - Action: Lists of actions that the policy allows or denies.
    - Resource: List of resources to which the actions are applied.
    - Condition: Conditions for when the policy is applied **(optional)**

*Example of a policy:*

```JSON
{
    "version": "yyyy-mm-dd",
    "Id": "S3-bucket-permission",
    "Statement": [
        {
            "Sid": "1",
            "Effect": "Allow",
            "Principal": {
                "AWS": ["arn:aws:iam::123456789012:root"]
            },
            "Action": [
                "s3:getObject",
                "s3:putObject"
            ],
            "Resource": ["arn:aws:s3:::myBucket/*"]
        }
    ]
}
```

### Acess keys, CLI and SDK
To access to the AWS account their are multiple options, the portal (which uses the password), CLI and SDKs.

CLI and SDKs use access key for authentication.

**Access Keys**
- They are meant to be use per user.
- Are composed of a Access Key and Secret Access.
- Do not share them with any one
- Access key is like a username and Secret Access is like the password.

**AWS CLI**
- Use to interact with AWS resources via command line
- Direct access to public AWS APIs for the services
- Useful to develop scripts to manage resources

**[AWS SDK](https://aws.amazon.com/tools/)**
- Software Development Kit
- Programming language specific
- Use to embedded within an application
- Supports:
    - SDKs(Javascript, Python, Java, C++, Go, Node.js, PHP, .NET, Ruby)
    - Mobile SDKs (Android, iOS)
    - IoT SDK (Embedded C, Arduino)
