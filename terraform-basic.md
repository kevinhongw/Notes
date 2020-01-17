# Terraform Basic

## Basic Command

To initialize terraform, you will need to run `terraform init`.

You can view changes to be made after altering code with `terraform plan`

You can create and update the infrastructure by running `terraform apply`

You can destroy the infrastructure created by this code with `terraform destroy`

#### Adding resource

- `ami` need to use `{resource path}.id`.
- `security_groups` don't take `.id`. They take `.name`.

## Environments

### `main.tf` example

```terraform
provider "aws" {
  profile    = "default"
  region     = "us-east-1"
}

resource "aws_instance" "example" {
  ami           = "ami-2757f631"
  instance_type = "t2.micro"
}
```

`profile` refers to the AWS Config File in `~/.aws/credentials` on MacOS and Linux.
It is recommended that never hard code credentials into `.tf`

Terraform also wrote some data into the terraform.tfstate file. This state file is extremely important; it keeps track of the IDs of created resources so that Terraform knows what it is managing.

You can inspect the current state using `terraform show`

### `variables.tf`

Put all variables into one file
**Note:** the file can be named anything, since Terraform loads all files ending in .tf in a directory.

### Variables

#### List

##### implicitly by using brackets [...]

`variable "cidrs" { default = [] }`

###### explicitly

`variable "cidrs" { type = list }`

#### Map

```tf
variable "amis" {
  type = "map"
  default = {
    "us-east-1" = "ami-b374d5a5"
    "us-west-2" = "ami-4b32be2b"
  }
}
```

### output

Terraform will output the data when `apply` is called, and can be queried using the `terraform output` command.

## Modules

- reusable
- executed for each env

### Ecr

Folder for docker image. Save docker image so k8s can access later.

#### main.tf

#### output.tf

dump out value after running file. not required.

## backend

Store state data on cloud

# Ansible

### `/group_vars/dev/var`

env.json.j2
