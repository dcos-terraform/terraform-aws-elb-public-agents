AWS ELB Public Agents
============
This module create a load balancer to acces public agents externally


EXAMPLE
-------

```hcl
module "dcos-elb-public-agents" {
  source  = "terraform-dcos/elb-public-agents/aws"
  version = "~> 0.1"

  cluster_name = "production"

  subnet_ids = ["subnet-12345678"]
  security_groups = ["sg-12345678"]

  instances = ["i-00123456789e960f8"]

  https_acm_cert_arn = "arn:aws:acm:us-east-1:123456789123:certificate/ooc4NeiF-1234-5678-9abc-vei5Eeniipo4"
}
```


## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|:----:|:-----:|:-----:|
| additional_listener | Specify a list of listeners. That are set in addition to the default listeners. | string | `<list>` | no |
| cluster_name | Specify the cluster name all resources get named and tagged with | string | - | yes |
| https_acm_cert_arn | Specify an ACM certifacte to be used. | string | `` | no |
| instances | List of public agent instance IDs | list | - | yes |
| security_groups | Security Group IDs to be uses. | list | `<list>` | no |
| subnet_ids | Subnets to spawn the instances in. The module tries to distribute the instances | list | - | yes |
| tags | Add special tags to the resources created by this module | map | `<map>` | no |

## Outputs

| Name | Description |
|------|-------------|
| dns_name | DNS Name of the master load balancer |

