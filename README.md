# Terraform Basics Assignment Instructions

Welcome to the Terraform Basics assignment! Follow the steps below to complete your assignment.

## Prerequisites
Ensure you have Terraform installed on your machine:

[Install Terraform CLI](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli)

## Steps to Complete the Assignment

### 1. Initialize a New Terraform Project
- Create a file named `main.tf`.
- Run `terraform init` to initialize the project.

### 2. Write Your Terraform Configuration
In `main.tf`, define the provider and resources you need.
Example:

```terraform

terraform {
    required_providers {
        docker = {
        source  = "kreuzwerker/docker"
        version = "~> 3.0.1"
        }
    }
}

provider "docker" {}

resource "docker_image" "nginx" {
    name         = "nginx"
    keep_locally = false
}

resource "docker_container" "nginx" {
    image = docker_image.nginx.image_id
    name  = "tutorial"

    ports {
        internal = 80
        external = 8000
    }
}

```

### 3. Validate and Apply the Configuration
- Run `terraform validate` to check for syntax errors.
- Run `terraform plan` to see the execution plan.
- Run `terraform apply` to create the resources.

Go to `localhost:8000` to validate that terraform apply worked.


### 4. Update it
Utilize the resources on [the terraform provider registry docs](https://registry.terraform.io/providers/kreuzwerker/docker/latest/docs) to rewrite the above terraform to use one of our class api docker images from [dockerhub](https://hub.docker.com/r/bubbaj/class-api-it4200-2024-fall/tags)

For example you might use the `bubbaj/class-api-it4200-2024-fall:1.9.0` image instead of `nginx`.

- Run `terraform validate` to check for syntax errors.
- Run `terraform plan` to see the execution plan.
- Run `terraform apply` to create the resources.

Go to `localhost:8000` to validate that terraform apply worked and now is using our class api instead of the default nginx image.


### 5. Clean up

- Run `terraform destroy` to stop the docker container

## Submission
- Submit a link to this repo that has your `main.tf` file in it.