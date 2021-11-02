# **How to deploy your apps to EKS instantly**

So it’s 2021 & everybody wants to push their apps to Kubernetes. But let’s face it, this is still unknown territory for a lot of teams, especially those trying to modernise their existing legacy apps. Having to go through endless tutorials & blogs just for getting started can be daunting, especially when you have deadlines to meet. We know there's Minikube & similar other tools out there, but enterprise cloud environments & their constraints are often hard to replicate locally.

Not anymore, though!

Here is a solution that helps you start deploying and testing your application on Amazon’s Elastic Kubernetes Service with practically zero knowledge of the underlying architecture. It uses a combination of Terraform scripts, Helm Charts and GitHub Actions - Github's in-house CI-CD solution - to orchestrate the deployment seamlessly from your repository. All you need is an AWS Account, an IAM Admin User, & your source code with its Dockerfile. That’s it!  With just a few clicks, you'll be good to deploy a fully-managed Kubernetes cluster with a live runnning application accessible via a public/private URL. No CLIs, no utilities and no dependencies!

Let’s get started.

## **Setting things up**

### **1. Cloning the repository:**

For starters, clone [this](https://github.com/Mkejriwal270/K8s-EKS-QuickStart) repository in your GitHub account. It has been created as a [template](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template) so you can just click on **Use this template** on the homepage to create a new repository of the same name directly in your account with the existing file structure intact.

![Image](https://mktestweb.s3.amazonaws.com/K8s-Quickstart-Static/repo-page.png)

### **2. AWS Setup:**

If you don't already have an AWS account, you can create one by following [these](https://aws.amazon.com/premiumsupport/knowledge-center/create-and-activate-aws-account) steps.

Make sure you have an IAM User with admin access which can provision resources\*\* on your behalf through GitHub Actions. Follow [this](https://docs.aws.amazon.com/IAM/latest/UserGuide/getting-started_create-admin-group.html) page for more details.

**\*\*Please note that implementing this solution will incur costs for provisioning and using AWS resources, even if you use a free-tier enabled account, so proceed at your own discretion. Go through the comprehensive list of provisioned resources below and use [AWS price calculator](https://calculator.aws/#/) to determine how much you may have to pay based on your usage:**

| AWS Resource               | # of Instances |
|----------------------------|----------------|
| EKS Cluster                | 1              |
| t2.small worker nodes      | 2              |
| NAT Gateway (For new VPCs) | 1              |

Once your IAM user is configured, you will have to generate a programmatic access key for the user with which GitHub Actions can access your AWS account. Follow the instructions [here](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html) and save the credentials for the next steps.

Optionally, if you want to use an existing AWS account with already configured VPCs, subnets and other networking components, you can take a note of your **VPC ID, Subnet IDs (public and private, if any) and the region where these resources are set up.** You will still need an IAM user and the access key for provisioning the cluster and deploying the application.

Your AWS account is now all set to host your EKS cluster!

### **3. GitHub Actions Configuration:**

Now you need to configure your repository so that GitHub Actions can deploy resources in your account. Here you will need:

- Your Access Key ID and Secret Access Key generated in the previous step
- Your AWS Account ID - [How to know yours](https://docs.aws.amazon.com/general/latest/gr/acct-identifiers.html)
- A Personal Access Token for your GitHub Account with full access to your repo and workflows - [Generate yours](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)

Once you have all these details handy, go to your repository **Settings** > **Secrets** and add a new secret **AWS_ACCESS_KEY_ID** as shown below. Copy the AWS Access Key ID you created and paste in the secret value, without any spaces or line breaks.

![Image](https://mktestweb.s3.amazonaws.com/K8s-Quickstart-Static/Create-Secret.png)

Similarly create all the secrets as shown below:

![Image](https://mktestweb.s3.amazonaws.com/K8s-Quickstart-Static/Secret-List.png)

The secret names above refer to the following values:

- AWS_ACCESS_KEY_ID : Your AWS access key ID
- AWS_SECRET_ACCESS_KEY : Your AWS secret access key
- K8S_QS_TOKEN : Your Personal Access Token created earlier
- AWS_ACCOUNT : Your AWS account ID

These secret names are being referred in the GitHub Actions workflows, so it is recommended to store them exactly as shown here to avoid runtime issues.

For more details go through the [project documentation](https://github.com/Mkejriwal270/K8s-EKS-QuickStart/blob/main/README.md).

## **Running the solution**

Enough with all the setup. It's now time to see things in Action, literally!

On your repository homepage, go to **Actions** tab, and click on **Fire-it-Up** (I had to make it dramatic!).

![Image](https://mktestweb.s3.amazonaws.com/K8s-Quickstart-Static/Actions-intro.png)

![Image](https://mktestweb.s3.amazonaws.com/K8s-Quickstart-Static/Actions-dropdown.png)

