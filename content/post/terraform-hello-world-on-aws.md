+++
date = "2015-05-20T20:22:44+11:00"
title = "Terraform Hello World on AWS"

+++

So you've heard about [Terraform](https://terraform.io/), you here that its another cool product developed by [HashiCorp](https://www.hashicorp.com/) and so you want it try it out. 

Here's one of the simplest tutorials possible.


```
provider "aws" {
    access_key = "ABC123"
    secret_key = "DEF456"
    region = "us-east-1"
}

resource "aws_instance" "web" {
    ami = "ami-1ecae776"
    instance_type = "t2.micro"
}
```

```
$ terraform plan
Refreshing Terraform state prior to plan...


The Terraform execution plan has been generated and is shown below.
Resources are shown in alphabetical order for quick scanning. Green resources
will be created (or destroyed and then created if an existing resource
exists), yellow resources are being changed in-place, and red resources
will be destroyed.

Note: You didn't specify an "-out" parameter to save this plan, so when
"apply" is called, Terraform can't guarantee this is what will execute.

+ aws_instance.web
    ami:                      "" => "ami-1ecae776"
    availability_zone:        "" => "<computed>"
    ebs_block_device.#:       "" => "<computed>"
    ephemeral_block_device.#: "" => "<computed>"
    instance_type:            "" => "t2.micro"
    key_name:                 "" => "<computed>"
    placement_group:          "" => "<computed>"
    private_dns:              "" => "<computed>"
    private_ip:               "" => "<computed>"
    public_dns:               "" => "<computed>"
    public_ip:                "" => "<computed>"
    root_block_device.#:      "" => "<computed>"
    security_groups.#:        "" => "<computed>"
    subnet_id:                "" => "<computed>"
    tenancy:                  "" => "<computed>"
    vpc_security_group_ids.#: "" => "<computed>"
```

```
$ terraform apply
aws_instance.web: Creating...
  ami:                      "" => "ami-1ecae776"
  availability_zone:        "" => "<computed>"
  ebs_block_device.#:       "" => "<computed>"
  ephemeral_block_device.#: "" => "<computed>"
  instance_type:            "" => "t2.micro"
  key_name:                 "" => "<computed>"
  placement_group:          "" => "<computed>"
  private_dns:              "" => "<computed>"
  private_ip:               "" => "<computed>"
  public_dns:               "" => "<computed>"
  public_ip:                "" => "<computed>"
  root_block_device.#:      "" => "<computed>"
  security_groups.#:        "" => "<computed>"
  subnet_id:                "" => "<computed>"
  tenancy:                  "" => "<computed>"
  vpc_security_group_ids.#: "" => "<computed>"
aws_instance.web: Creation complete

Apply complete! Resources: 1 added, 0 changed, 0 destroyed.

The state of your infrastructure has been saved to the path
below. This state is required to modify and destroy your
infrastructure, so keep it safe. To inspect the complete state
use the `terraform show` command.

State path: terraform.tfstate
```

```
$ terraform show
aws_instance.web:
  id = i-b6724f60
  ami = ami-1ecae776
  availability_zone = us-east-1c
  ebs_block_device.# = 0
  ebs_optimized = false
  ephemeral_block_device.# = 0
  instance_type = t2.micro
  private_dns = ip-172-31-57-177.ec2.internal
  private_ip = 172.31.57.177
  public_dns = ec2-52-4-4-18.compute-1.amazonaws.com
  public_ip = 52.4.4.18
  root_block_device.# = 1
  root_block_device.0.delete_on_termination = true
  root_block_device.0.iops = 24
  root_block_device.0.volume_size = 8
  root_block_device.0.volume_type = gp2
  security_groups.# = 0
  subnet_id = subnet-3025cd1b
  tags.# = 0
  tenancy = default
  vpc_security_group_ids.# = 1
  vpc_security_group_ids.324056906 = sg-901700f5
```

```
$ terraform destroy
Do you really want to destroy?
  Terraform will delete all your managed infrastructure.
  There is no undo. Only 'yes' will be accepted to confirm.

  Enter a value: yes

aws_instance.web: Refreshing state... (ID: i-b6724f60)
aws_instance.web: Destroying...
aws_instance.web: Destruction complete

Apply complete! Resources: 0 added, 0 changed, 1 destroyed.
```



### Creating an Amazon Account & Generating Keys

This assumes you have an Amazon Web Services (AWS) account 
[Free Tier](http://aws.amazon.com/free/). 

Identity and Access Management (IAM)
Create new User and generate an access key
