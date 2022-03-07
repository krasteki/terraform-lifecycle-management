# Learn Terraform Lifecycle Management

This is a companion repository for the [Learn Terraform Lifecycle Management tutorial](https://learn.hashicorp.com/tutorials/terraform/resource-lifecycle) on HashiCorp Learn. Follow along to learn more about resource management.

This configuration builds an EC2 instance and a security group rule to allow port 8080 access to the instance.

I. Create infrastructure

1. Clone the repo
```
$ git clone https://github.com/krasteki/terraform-lifecycle-management.git
```

2. Enter to the folder
```
$ cd terraform-lifecycle-management
```

3. Init and apply
```
$ terraform init
$ terraform apply
```

II. Prevent resource deletion

1. Add prevent_destroy to the EC2 instance.

+ lifecycle {
+   prevent_destroy = true
+ }

2. Run terraform destroy to observe the behavior.

```
$ terraform destroy
```

│ Error: Instance cannot be destroyed

III. Create resources before they are destroyed

For changes that may cause downtime but must happen, use the create_before_destroy attribute to create the new resource before destroying the old resource.

1. Update the security group rule to allow port `80` access instead of `8080`.

2. Update the EC2 instance to reflect this change by adding the `create_before_destroy` attribute and updating the VM so it runs on port `80`.



