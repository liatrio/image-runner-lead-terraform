## What is the image for?
The intended purpose of this image is for it to be used as a Github runner with extra dependencies installed for use in Terraform pipelines. 

> **_NOTE:_** For more information on using self-hosted runners in GitHub Actions workflows, read the [GitHub docs](https://docs.github.com/en/actions/hosting-your-own-runners/about-self-hosted-runners) on the topic.

## What is installed on this image?
- The GitHub Actions Runner [Base Image](https://hub.docker.com/r/summerwind/actions-runner/tags) 
- The [AWS CLI](https://aws.amazon.com/cli/)
- The [Azure CLI](https://packages.microsoft.com/repos/azure-cli/)
- Version [1.18.X](https://dl.google.com/go/go1.18.src.tar.gz) of the Go programming language
- Version [1.2.5](https://releases.hashicorp.com/terraform/1.2.5/) of infrastructure as code tool Terraform
- Version [0.38.X](https://github.com/gruntwork-io/terragrunt/releases/download/v0.38.4/terragrunt_linux_amd64) of Terraform wrapper Terragrunt 
- Version [0.10.X](https://github.com/loft-sh/vcluster/releases/download/v0.10.2/vcluster-linux-amd64) of vcluster, a tool for creating virtual Kubernetes clusters
- Version [1.24.X](https://storage.googleapis.com/kubernetes-release/release/v1.24.0/bin/linux/amd64/kubectl) of kubectl, a command-line tool that allows you to run commands against Kubernetes clusters
