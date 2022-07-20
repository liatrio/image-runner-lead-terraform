Repo for image-runner-lead-terraform

## What is the image for?
The intended purpose of this image is for it to be used as a Jenkins agent. By using the installed features the user is able to create Jenkins pipelines that can trigger Terraform scripts to deploy and update infrastructure. Additionally, Terragrunt gives the ability to use extra tools for Terraform. An example of using this image as a Jenkins agent via [Kubernetes](https://plugins.jenkins.io/kubernetes/) can be seen below. 

First, an example of configuring the pod template in yaml to create the agent.

```yaml
jenkins:
  clouds:
    - kubernetes:
        name: "kubernetes"
        templates:
          - name: "image-builder-terraform"
            label: "image-builder-terraform"
            nodeUsageMode: NORMAL
            containers:
              - name: "image-terraform"
                image: "ghcr.io/liatrio/image-builder-terraform:${builder_images_version}"
```
And then specifying the agent in the Jenkinsfile for an example step.

```jenkins
stage('Build') {
  agent {
    label "image-builder-terraform"
  }
  steps {
    container('image-terraform') {
      sh "terragrunt plan"
      sh "terragrunt apply"
    }
  }
}
```

## What is installed on this image?
- The [AWS CLI](https://aws.amazon.com/cli/)
- The [Azure CLI](https://packages.microsoft.com/repos/azure-cli/)
- Version [1.18.X](https://dl.google.com/go/go1.18.src.tar.gz) of the Go programming language
- Version [1.2.5](https://releases.hashicorp.com/terraform/1.2.5/) of infrastructure as code tool Terraform
- Version [0.38.X](https://github.com/gruntwork-io/terragrunt/releases/download/v0.38.4/terragrunt_linux_amd64) of Terraform wrapper Terragrunt 
- Version [0.10.X](https://github.com/loft-sh/vcluster/releases/download/v0.10.2/vcluster-linux-amd64) of vcluster, a tool for creating virtual Kubernetes clusters
- Version [1.24.X](https://storage.googleapis.com/kubernetes-release/release/v1.24.0/bin/linux/amd64/kubectl) of kubectl, a command-line tool that allows you to run commands against Kubernetes clusters
