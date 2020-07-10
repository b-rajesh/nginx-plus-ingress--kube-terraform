# Pre-requsite  - Configure azure cli and enable the aks module


[Go back to main page](../README.md)


# Enable the aks module
Step 1
```
Append  `.disabled` to the file called local_module.tf. It should look like  'local_module.tf.disabled'
```
Step 2
```
Append  `.disabled` to the file called gke_module.tf. It should look like  'gke_module.tf.disabled'
```
Step 3
```
Remove `.disabled` from the file called aks_module.tf.disabled. It should look like 'aks_module.tf'
```
# Install appropriate azue roold
First, azure tools 
```
brew install azure-cli

```
Initialize it...

```shell
$ az login
```

# Pre-requsite - Important to read  terraform.tfvars and variable.tf

```
* Replace `terraform.tfvars` values with your `project_id` , `region` and other variables. Your  `project_id` &  `region`  must match the project you've initialized gcloud with. 

* You may not need project_id, region and few otehr variabled if you are running locally

* Do NOT use upper case for the value you are going to replace.
```
# Components created
```
* AKS with a default and application node
* Azure CNI is enabled
* Use ACR to store and pull the nginx plus ingress image
* Public load balancer
* Both node pool runs on internal subnet.
```

# Known challenges

```
* At least have Controbutor and Network Contributor role assigned before creating the cluster. Otherwise you would face issues in creating cluster in the private subnet.
```

[Go back to main page](../README.md)