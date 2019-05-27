AWS ELB Public Agents
============
This module create a load balancer to acces public agents externally

EXAMPLE
-------

```hcl
module "dcos-elb-public-agents" {
  source  = "terraform-dcos/elb-public-agents/aws"
  version = "~> 0.1.0"

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
| cluster\_name | Name of the DC/OS cluster | string | n/a | yes |
| instances | List of instance IDs | list | n/a | yes |
| subnet\_ids | List of subnet IDs created in this network | list | n/a | yes |
| additional\_listener | List of additional listeners | list | `<list>` | no |
| https\_acm\_cert\_arn | ACM certifacte to be used. | string | `""` | no |
| internal | This ELB is internal only | string | `""` | no |
| security\_groups | Security Group IDs to use | list | `<list>` | no |
| tags | Add custom tags to all resources | map | `<map>` | no |

## Outputs

| Name | Description |
|------|-------------|
| dns\_name | DNS Name of the master load balancer |

