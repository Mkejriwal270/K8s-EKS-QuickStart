# How to run your apps on EKS with just a few clicks

So it’s 2021 & everyone wants to push their apps to Kubernetes. But let’s face it, this is still unknown territory for a lot of teams, especially those trying to modernise their existing apps. Also, having to go through endless tutorials & blogs, just for getting started, can be daunting. We know there's Minikube & similar tools out there, but enterprise cloud environments & their constraints are often hard to replicate locally.

Not anymore, though!

Here is a solution that enables you to start deploying and testing your application on Amazon’s Elastic Kubernetes Service with practically zero knowledge of the underlying architecture. All you need is an AWS Account, an IAM Admin User, & your source code with its Dockerfile, & that’s it.  With just a few clicks, you'll be good to deploy a fully-managed Kubernetes cluster with a live runnning application accessible via a public/private URL. No CLIs, no utilities and no dependencies!

Let’s get started.

## Setting things up

### 1. Cloning the repository

For starters, clone [this](https://github.com/Mkejriwal270/K8s-EKS-QuickStart) repository in your GitHub account. It has been created as a [template](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template) so you can just click on **Use this template** to create a new repository of the same name directly in your account with the existing file structure intact.

### 2. AWS Setup

If you don't already have an AWS account, you can create one by following [these](https://aws.amazon.com/premiumsupport/knowledge-center/create-and-activate-aws-account) steps.

Make sure you have an IAM User with admin access which can provision resources\*\* on your behalf through GitHub Actions. Follow [this](https://docs.aws.amazon.com/IAM/latest/UserGuide/getting-started_create-admin-group.html) page for more details.

**\*\*Please note that implementing this solution will incur costs for provisioning and using AWS resources, even if you use a free-tier enabled account, so proceed at your own discretion. Go through the comprehensive list of provisioned resources below and use [AWS price calculator](https://calculator.aws/#/) to determine how much you may have to pay based on your usage:**

| AWS Resource               | # of Instances |
|----------------------------|----------------|
| EKS Cluster                | 1              |
| t2.small worker nodes      | 2              |
| NAT Gateway (For new VPCs) | 1              |

AWS Cloud Account, IAM Admin User, Access Key ID and Secret Key - Documentation

GitHub Actions Secret Creation



Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

\*\*

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/Mkejriwal270/K8s-EKS-QuickStart/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
