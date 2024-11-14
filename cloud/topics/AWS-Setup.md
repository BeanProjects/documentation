# AWS Setup
## Organisation
- Management: peterbean
### IAM Identity Center
1. [What is IAM Identity Center?](https://docs.aws.amazon.com/singlesignon/latest/userguide/what-is.html)
2. [Enabling AWS IAM Identity Center](https://docs.aws.amazon.com/singlesignon/latest/userguide/get-set-up-for-idc.html)
    1. https://docs.aws.amazon.com/singlesignon/latest/userguide/get-started-prereqs-considerations.html
        2. [IAM Identity Center and AWS Organizations](https://docs.aws.amazon.com/singlesignon/latest/userguide/prereq-orgs.html)
            3. AWS Organizations is recommended, but not required, for use with IAM Identity Center. If you haven't set up an organization, you don't have to. When you enable IAM Identity Center, you will choose whether to enable the service with AWS Organizations. When you set up an organization, the AWS account that sets up the organization becomes the management account of the organization. The root user of the AWS account is now the owner of the organizational management account. Any additional AWS accounts you invite to your organization are member accounts. The management account creates the organizations resources, organizational units, and policies that manage the member accounts. Permissions are delegated to member accounts by the management account.
3. [IAM Identity Center instances](https://docs.aws.amazon.com/singlesignon/latest/userguide/identity-center-instances.html)
- An instance is a single deployment of IAM Identity Center. There are two types of instances available for IAM Identity Center: organization instances and account instances.
- AWS account types that can enable IAM Identity Center: To enable IAM Identity Center, sign in to the AWS Management Console by using one of the following credentials, depending on the instance type you want to create:
    - Your AWS Organizations management account **(recommended)** – Required to create an organization instance of IAM Identity Center. Use an organization instance for multi-account permissions and application assignments across the organization.
        - [Organization instances of IAM Identity Center](https://docs.aws.amazon.com/singlesignon/latest/userguide/organization-instances-identity-center.html)
            - [Enabling AWS IAM Identity Center](https://docs.aws.amazon.com/singlesignon/latest/userguide/get-set-up-for-idc.html)
                1. **Enabling in Oregon region** responded with: You have successfully created the organization instance of IAM Identity Center 79071b1d639012d4.
                2. https://us-west-2.console.aws.amazon.com/singlesignon/home?region=us-west-2#!/instances/79071b1d639012d4/dashboard
                3. **Enabled Identity-aware sessions** in Settings
                4. If you are using a multi-account environment, we recommend that you configure delegated administration. With delegated administration, you can limit the number of people who require access to the management account in AWS Organizations. For more information, see [Delegated administration](https://docs.aws.amazon.com/singlesignon/latest/userguide/delegated-admin.html).
                - Added admin.prod@beancloud.io to be delegated administrator.
                - This operation delegates IAM Identity Center administrative access to users in this member account. All users who have sufficient permissions to this delegated administrator account can perform all IAM Identity Center administrative tasks from the account, except for: deleting IAM Identity Center, registering other member accounts as delegated administrators, managing assignments to the management account, or managing permission sets provisioned in the management account.
                    - Member account Administrator registered successfully as an IAM Identity Center delegated administrator. It might take some time to grant administrative access to this account.
                5. [Temporary Elevated Access](https://docs.aws.amazon.com/singlesignon/latest/userguide/temporary-elevated-access.html) using [TEAM](https://aws-samples.github.io/iam-identity-center-team/docs/deployment/deployment_process.html#clone-team-repo)
                - TIL a disclaimer in the [Security section](https://aws-samples.github.io/iam-identity-center-team/docs/overview/security.html)
                ```
                The sample code; software libraries; command line tools; proofs of concept; templates; or other related technology (including any of the foregoing that are provided by our personnel) is provided to you as AWS Content under the AWS Customer Agreement, or the relevant written agreement between you and AWS (whichever applies). You are responsible for testing, securing, and optimizing the AWS Content, such as sample code, as appropriate for production grade use based on your specific quality control practices and standards. Deploying AWS Content may incur AWS charges for creating or using AWS chargeable resources, such as running Amazon EC2 instances or using Amazon S3 storage.
                ```
                6. [Single sign-on access to AWS accounts](https://docs.aws.amazon.com/singlesignon/latest/userguide/useraccess.html)
                - Interesting **AWS managed policies for job functions**


### Budget
1. Created **My Zero-Spend Budget**
